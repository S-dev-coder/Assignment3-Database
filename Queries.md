 1. Fetch all users name from database.
```sql
 SELECT name FROM users;
```

 2. Fetch all tweets of user by user id most recent tweets first.
```sql
SELECT tweetContent FROM tweets
WHERE userId = 1
ORDER BY created_at DESC;
```

 3. Fetch like count of particular tweet by tweet id.
```sql
SELECT COUNT(*) AS total_likes FROM likes
WHERE tweetId = 2;
```

 4. Fetch retweet count of particular tweet by tweet id.
```sql
SELECT COUNT(*) AS total_retweets FROM retweets
WHERE tweetId = 3;
```

 5. Fetch comment count of particular tweet by tweet id.
```sql
SELECT COUNT(*) AS total_comments FROM tweets
WHERE is_comment = TRUE AND comment_on_tweet_id = 2;
```

 6. Fetch all users' names who have retweeted a particular tweet by tweet id.
```sql
SELECT U.name FROM users U
JOIN retweets R ON U.id = R.userId
WHERE R.tweet_id = 3;
```
 7. Fetch all commented tweet’s content for particular tweet by tweet id.
```sql
SELECT T.tweetContent FROM tweets T
WHERE T.is_comment = TRUE
AND T.comment_on_tweet_id = 3;
```

 8. Fetch user’s timeline (All tweets from users whom I am following with tweet content and user name who has tweeted it)
```sql
SELECT U.name, T.tweetContent FROM tweets T
JOIN users U ON T.userId = U.id
JOIN user_followers UF ON UF.followingId = T.userId
WHERE UF.followerId = 2
ORDER BY T.created_at DESC;
```
#
