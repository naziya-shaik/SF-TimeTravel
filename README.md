# Time Travel

What is Snowflake Time Travel?

Snowflake Time Travel is a feature of the Snowflake data warehousing platform that allows users to query historical data as it existed at a specific point in time. This means that users can view data as it existed in the past, without having to create and maintain separate copies of the data.
### Why Use Snowflake Time Travel?

There are several reasons why you might want to use Snowflake Time Travel:

- **Auditing:** Time Travel makes it easy to audit data changes over time. You can quickly see how data has changed and who made the changes.
- **Recovery:** If you accidentally delete or modify data, you can use Time Travel to recover the data as it existed before the change.
- **Trend Analysis:** Time Travel allows you to analyze data trends over time. You can see how data has changed over time and identify patterns or trends.
  ### How to Use Snowflake Time Travel

Using Snowflake Time Travel is a simple process. You can use different methods to travel back in time. Here are three different methods:

### Method 1: Using Timestamp

1. Identify the time you want to travel back to. This can be any point in time within the retention period of your data.
2. Use the AS OF clause in your SQL query to specify the time you want to travel back to. For example, if you want to see data as it existed two days ago, you would use the following query:
    
    ```sql
    SELECT * FROM my_table AS OF TIMESTAMP '2 days ago';
    ```
    
    This query will return all the data from `my_table` as it existed two days ago.
    
3. That's it! You can now view the data as it existed at the specified point in time.

### Method 2: Using Query ID

1. Identify the Query ID of the query you want to time travel to. You can find the Query ID in the HISTORY tab of the Snowflake web interface or by running a query against the QUERY_HISTORY table.
2. Use the SYSTEM$TIME_TRAVEL function in your SQL query to specify the Query ID you want to time travel to. For example, if you want to see the results of Query ID 1234567890, you would use the following query:
    
    ```sql
    SELECT * FROM TABLE(RESULT_SCAN(SYSTEM$TIME_TRAVEL(QUERY_ID=>'1234567890')));
    ```
    
    This query will return the results of the query as it existed at the time it was run.
### Method 3: Using Named Time Travel

1. Create a named time travel object by specifying the time you want to travel back to. For example, if you want to create a named time travel object for data as it existed two days ago, you would use the following query:
    
    ```sql
    CREATE SNAPSHOT my_snapshot AS SELECT * FROM my_table AS OF TIMESTAMP '2 days ago';
    ```
    
2. Use the named time travel object in your SQL query to specify the data you want to query. For example, if you want to query the data in `my_table` as it existed two days ago, you would use the following query:
    
    ```sql
    SELECT * FROM my_snapshot;
    ```
    
    This query will return all the data from `my_table` as it existed two days ago.

   
