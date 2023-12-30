# Spark-note

## 1. Why Spark?

#### 1.1 Intro:
- Simple, powerful, and fast computing system
- Free and open-source software
- Runs on Hadoop, Mesos, Kubernetes, standalone, or in the cloud
- Compatible with various data sources like Amazon S3, Hadoop HDFS, and relational databases
- Integrates with many data applications
- Reads/writes in both row-based (e.g., Avro) and column-based (e.g., Parquet, ORC) data formats
- Provides a rich and straightforward set of APIs for ETL processes

#### 1.2 Further

## 2. Notebook
To find each user's favorite genre, we can follow these steps:

1. Start with the original dataset that contains information about `user_id` and `genre`.
2. Group the data by both `user_id` and `genre`. This helps us count the occurrences of each `user_id` and `genre` combination.
3. Use the `agg` function to apply an aggregation operation on the grouped data. In this case, we count the occurrences of each combination using `count('*').alias('count')`. This creates a new column called 'count' that represents the number of times a specific `user_id` and `genre` combination appears in the dataset.
4. Now, we have a DataFrame that shows the count of occurrences for each `user_id` and `genre` combination. We can display this DataFrame to see the results.

Example:

Let's say we have the following dataset:

```
+--------+-------+
|user_id | genre |
+--------+-------+
|   1    |  Rock |
|   1    |  Rock |
|   1    |  Pop  |
|   2    |  Pop  |
|   2    |  Jazz |
|   2    |  Jazz |
|   2    |  Rock |
|   3    |  Pop  |
|   3    |  Pop  |
|   3    |  Pop  |
+--------+-------+
```

Applying the steps mentioned earlier:

Step 1: Start with the original dataset.

```
+--------+-------+
|user_id | genre |
+--------+-------+
|   1    |  Rock |
|   1    |  Rock |
|   1    |  Pop  |
|   2    |  Pop  |
|   2    |  Jazz |
|   2    |  Jazz |
|   2    |  Rock |
|   3    |  Pop  |
|   3    |  Pop  |
|   3    |  Pop  |
+--------+-------+
```

Step 2: Group the data by `user_id` and `genre`.

```
+--------+-------+
|user_id | genre |
+--------+-------+
|   1    |  Rock |
|   1    |  Pop  |
|   2    |  Pop  |
|   2    |  Jazz |
|   2    |  Rock |
|   3    |  Pop  |
+--------+-------+
```

Step 3: Apply the `agg` function to count the occurrences of each combination.

```
+--------+-------+-------+
|user_id | genre | count |
+--------+-------+-------+
|   1    |  Rock |   2   |
|   1    |  Pop  |   1   |
|   2    |  Pop  |   1   |
|   2    |  Jazz |   2   |
|   2    |  Rock |   1   |
|   3    |  Pop  |   3   |
+--------+-------+-------+
```

Step 4: Display the resulting DataFrame.

```
+--------+-------+
|user_id | genre |
+--------+-------+
|   1    |  Rock |
|   2    |  Jazz |
|   3    |  Pop  |
+--------+-------+
```

Based on the count, we can see that for each `user_id`, their favorite genre is the one with the maximum count. In this example, User 1's favorite genre is 'Rock', User 2's favorite genre is 'Jazz', and User 3's favorite genre is 'Pop'.
