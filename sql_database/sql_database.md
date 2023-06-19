
This serves as a short tutorial on how to install and query the Reddit SQL database. 

Due to the vast amounts of data (21TB uncompressed), it can be difficult to analyse and manage the data you'll need for your projects. Databases like PostgreSQL can be used exactly for this purpose. 

A PostgreSQL database is being made available, containing all the Reddit data up to **2009-12**. It should be enough data for testing project queries, which if you wish can be sent to me to run against the full dataset. The database is based on Debian 11.7, with zfs and PostgreSQL 15. 

## Data available

The SQL database contains only submission and comment metadata. The data for each table is as follows:

### reddit.comments  table
- `dataset`: data timestamp in the format YYYY-MM (string)
- `id`: comment id (string)
- `created_utc`: UNIX timestamp of comment creation (integer)
- `retrieved_utc`: UNIX timestamp of when the data was retrieved. Varies considerably (integer)
- `author_created_utc`: UNIX timestamp of author creation. Missing in the first few years of data (integer)
- `score`: comment karma (integer)
- `stickied`: if the comment was stickied by moderators (boolean)
- `link_id`: id of the submission the comment belongs to (string)
- `parent_id`: id of the comment this comment replies to (string)
- `author`: author name (string)
- `subreddit`: subreddit name (string)

### reddit.submissions table
- `dataset`: data timestamp in the format YYYY-MM (string)
- `id`: submission id (string)
- `created_utc`: UNIX timestamp of comment creation (integer)
- `retrieved_utc`: UNIX timestamp of when the data was retrieved. Varies considerably (integer)
- `num_comments`: number of comments of the submission. Differs slightly from the data you obtain from the comments table (integer)
- `score`: submission karma (integer)
- `subreddit_subscribers`: number of subscribers of the subreddit at retrieval time. Missing from the first years of data (integer)
- `stickied`: if the submission was stickied by moderators (boolean)
- `author`: author name (string)
- `subreddit`: subreddit name (string)
- `domain`: domain of the content the submission links to, it can be a news site like `news.bbc.co.uk`. Submissions without a link typically have `self.[subreddit name]` in this field (string)
- `title`: submission title (string)

## Installation

You will need to

- Install VirtualBox 7.0.8: https://www.virtualbox.org/wiki/Downloads
- Download the VM: [dropbox link](https://www.dropbox.com/s/4dxcpctzprtz99i/database.ova?dl=0)
- Install a SQL GUI client like pgAdmin: https://www.pgadmin.org/download/ 

After installing VirtualBox, you need to import the `database.ova` VM image into it. The image is 8GB and uncompresses to about 15GB.  After importing it should look like this:

![[reddit_sql1.png]]

The important part is that you should have two network adapters: one for internet (NAT) and one for accessing the VM from the host computer (Host-only adapter). 

For login, the username is **user** and the password is **99**. Root is **passwordless**. 

After starting the VM, you need to figure out its internal ip address. Here it is **192.168.56.103**, but it can change. You can check by running `ip a` and checking the inet address of the last interface. 

![[reddit_sql2.png]]

You can now add the database server on pgAdmin: 

![[reddit_sql3.png]]

The reddit data lies in the `datasets` database, on the `reddit.submissions` and `reddit.comments` tables. If you wish, you can change the amount of cores/RAM the VM uses on VirtualBox. To change the resources PostgreSQL uses you need to edit the `/etc/postgresql/15/main/postgresql.conf` file, taking values from [pgTune](https://pgtune.leopard.in.ua/). For this scale of data it should not be necessary, however.

## Using the database

You can query the database by right-clicking on the `datasets` database and selecting **Query Tool**. It is recommended to first check how the data looks like. In the **Object Explorer**, you can click on `Databases > datasets > Schemas > reddit > Tables`. You can then right click on the submissions and comments tables and select **View/Edit Data > First 100 Rows**. 

From there, many exploratory queries can be run. Below are some examples.

- Rank the authors in a subreddit by number of comments, and display their total karma
```sql
SELECT AUTHOR,
	COUNT(*) AS count,
	SUM(SCORE) AS comment_score
FROM REDDIT.COMMENTS
WHERE SUBREDDIT = 'nba'
GROUP BY AUTHOR
ORDER BY COUNT DESC
LIMIT 100
```

- Rank the subreddits by number of comments, and display the count of submissions and unique authors
```sql
SELECT SUBREDDIT,
	COUNT(*) AS submissions,
	SUM(NUM_COMMENTS) AS comments,
	COUNT(DISTINCT AUTHOR) AS unique_authors
FROM REDDIT.SUBMISSIONS
GROUP BY SUBREDDIT
ORDER BY SUBMISSIONS DESC
LIMIT 100
```

- Count the number of submissions per author in a subreddit and for specific months. Also count the number of comments in those submissions and the aggregated submission score.

```sql
SELECT AUTHOR,
	COUNT(*) AS count,
	SUM(NUM_COMMENTS) AS submission_comments,
	SUM(SCORE) AS submission_score
FROM REDDIT.SUBMISSIONS
WHERE SUBREDDIT = 'nba'
	AND DATASET in ('2009-10','2009-11','2009-12')
GROUP BY AUTHOR
ORDER BY COUNT DESC
LIMIT 100
```

- Find the number of unique commenters per submission in a subreddit, and rank the submissions by it. Include the submission title and score
```sql
SELECT
  reddit.submissions.id,
  reddit.submissions.title,
  sum(reddit.submissions.score) AS submission_score,
  COUNT(DISTINCT reddit.comments.author) AS unique_commenters
FROM
  reddit.comments
JOIN
  reddit.submissions ON REPLACE(reddit.comments.link_id, 't3_', '') = reddit.submissions.id
WHERE
  reddit.comments.subreddit = 'nba'
GROUP BY
  reddit.submissions.id
ORDER BY
  unique_commenters DESC
LIMIT 100
```

- Find the number of shared comment authors (**subreddit network**) between all subreddits in a list
```sql
WITH subreddits AS (
    SELECT unnest(ARRAY[
        'politics', 
        'pics', 
        'funny', 
        'worldnews', 
        'science'
    ]) AS subreddit
),

subreddit_authors AS (
    SELECT subreddit, ARRAY_AGG(DISTINCT author) AS authors
    FROM reddit.comments
    WHERE subreddit IN (SELECT subreddit FROM subreddits)
    GROUP BY subreddit
)

SELECT 
    s1.subreddit AS sub1, 
    s2.subreddit AS sub2, 
    (SELECT COUNT(*) FROM 
        (SELECT unnest(s1.authors) INTERSECT SELECT unnest(s2.authors)) AS shared_authors) AS shared_authors_count
FROM 
    subreddit_authors s1
JOIN 
    subreddit_authors s2 
ON 
    s1.subreddit < s2.subreddit
ORDER BY 
    shared_authors_count DESC;
```

You can save the results of a query by pressing **F8** or by wrapping the query with a COPY statement:
```sql
COPY(
...
) TO 'results.csv' DELIMITER ',' CSV HEADER;
```

However, note that this saves the data *inside* of the VM and you must set up **Shared Folders** to export it.

## Tips

- You can check the live status of any submission/comment by going to `https://redd.it/[content id]`. 
- Use ChatGPT to make queries. You can feed it the query you want plus the data fields description from the beginning of this file and it will usually return the correct query. ChatGPT Plus (with GPT-4) is better, but even the free one should be good enough.
- Use ChatGPT to understand queries, and to try to speed up queries that are taking too long. You can check exactly what a query is doing by adding `EXPLAIN` before it. 
