---
title: "MySQL Partition"
seoDescription: "Optimize MySQL with partitioning by DATETIME column, splitting tables into monthly partitions, reducing latency, size, and cost"
datePublished: Fri Jun 09 2023 19:43:56 GMT+0000 (Coordinated Universal Time)
cuid: clioz75bu000109ml9itx5zzl
slug: mysql-partition
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686339483007/fc297093-7442-4b77-8e2c-53f511d26a8d.png
tags: mysql, databases, partition, database-partitioning, databasemanagement

---

## Why are Partitions Essential? 🤔

A few partitions, like India and Pakistan, were not essential, but partitioning an SQL table might be necessary based on the use cases.

You have created the best schema for your table. All were going smoothly. Clients are happy, DevOps teams are so glad, less expense on Infra; Cloud is the best.

* **<mark>Latency:</mark>** However, as the clients increase and your management feels happy, the table expands with rows and rows of data every second. Your DB JOIN queries have become slower. That Index is also throwing results after an increased latency. What is the solution?
    
* **<mark>Size:</mark>** There are millions of rows you do not need, but to delete those will take days, and it may end up as a time-out and, in the worst case, data corruption. What is the solution?
    
* **<mark>Cost:</mark>** The table size reached into TBs, the replica you have created for high availability adding another few TBs extra. The AWS or any other cloud instance sends you large bills for the data you do not need. What is the solution?
    

## Dynamic partition creation ♻

MySQL (v5.7.41 onwards) snippet for partitioning your table by a DATETIME data type column.

```sql
/* Create command */
CREATE TABLE `awesome_product` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `account_id` bigint(10) unsigned NOT NULL,
  `product_id` bigint(10) unsigned NOT NULL,
  `created_at` DATETIME(6) NOT NULL,
  PRIMARY KEY (`id`, `created_at`),
) ENGINE=InnoDB AUTO_INCREMENT=0 DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci
PARTITION BY LIST(month(created_at)%3) (
    PARTITION p0 VALUES IN (0),
    PARTITION p1 VALUES IN (1),
    PARTITION p2 VALUES IN (2)
);

/* Truncate command */
ALTER TABLE awesome_product TRUNCATE PARTITION p0;
```

* Here we split the \`awesome\_product\` table into three partitions monthly. For example:
    
    * January month number 01, 1%3 = 1 =&gt; Therefore, January rows will go to the p1 Partition.
        
    * February is 02, 2 % 3 = 2 =&gt; It goes to p2 partition
        
    * March is 03, 3 % 3 = 0 =&gt; It goes to p0 partition
        
    * April is 04, 4 % 3 = 1 =&gt; If we do not truncate p1, it will append (not overwrite) to the existing records of January.
        
* If you want to keep more months of data, you may increase the % three formula to a higher number.
    
* You can manually remove the records of partition p1 using the alter truncate command provided above. However, we can schedule it automatically.
    

## Event for auto truncation of partition ☠️

An event can be created per the above schema to delete the oldest partition before the new month's data is ingested.

```sql
DROP EVENT IF EXISTS awesome_product_truncate_partition; 
delimiter $$
 
CREATE EVENT awesome_product_truncate_partition  
    ON SCHEDULE 
        EVERY '1' DAY
    DO 
        BEGIN
            DECLARE day_of_month SMALLINT;
            DECLARE month_of_year SMALLINT;
            DECLARE NOW DATETIME;
            SET NOW = NOW();
            SET day_of_month = dayofmonth(NOW); 
            SET month_of_year = MONTH(NOW); 
        IF day_of_month >= 22 AND day_of_month <=28 THEN
            CASE month_of_year % 3 
                WHEN 0 THEN ALTER TABLE awesome_product TRUNCATE PARTITION p1;
                WHEN 1 THEN ALTER TABLE awesome_product TRUNCATE PARTITION p2;
                WHEN 2 THEN ALTER TABLE awesome_product TRUNCATE PARTITION p0;
            END CASE; 
        END IF;
    END
$$
```

* We have created a daily MySQL event kind of CRON job.
    
* It tries to delete the oldest partition on the 22nd of every month. Suppose it could not truncate on the 22nd; it retries again on the 23rd, 24th, till 28th.
    
* As every month has a minimum of 28 days, we have taken a maximum of 28 as the retry date.
    
* Around 7 days retry period is taken for truncation of the oldest partition.
    

## Data retention period ⏳

With the above dynamic partition and event, let's calculate the minimum days' data will get stored in the table.

* Suppose we inserted a row on 28 Feb. It will be inserted on the partition, p2, i.e., 2 % 3
    
* March 1 will go to p0
    
* 22 March p1 will get truncated
    
* 22 April, p2 will get truncated.
    
* Therefore our data has a minimum retention period of <mark>1 month and 21 days.</mark>
    
* You can change the modulo divisor (in this case, 3) to increase or decrease retention. Or You can use a year-wise partition.
    

## Summary 📝

In this post, we learned the following:

1. Why do we need to partition our tables
    
2. How to create dynamic partitions and
    
3. How to create an event to delete the oldest partition
    

Thank you.