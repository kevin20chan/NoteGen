# mysql常用命令

### 客户端登录

```sql
mysql -h10.124.207.10 -uapp_coo_user -P6666 -A -p
password

## mysql常用命令

```sql
# 新增分区
ALTER TABLE attendance_day ADD PARTITION(
 PARTITION p20240101 VALUES LESS THAN (TO_DAYS('2024-01-01'))
);

ALTER TABLE tb_car_track_vms_info ADD PARTITION(
 PARTITION p202312 VALUES LESS THAN (UNIX_TIMESTAMP('2024-01-01')),
 PARTITION p202401 VALUES LESS THAN (UNIX_TIMESTAMP('2024-02-01')),
 PARTITION p202402 VALUES LESS THAN (UNIX_TIMESTAMP('2024-03-01')),
 PARTITION p202403 VALUES LESS THAN (UNIX_TIMESTAMP('2024-04-01')),
 PARTITION p202404 VALUES LESS THAN (UNIX_TIMESTAMP('2024-05-01')),
 PARTITION p202405 VALUES LESS THAN (UNIX_TIMESTAMP('2024-06-01')),
 PARTITION p202406 VALUES LESS THAN (UNIX_TIMESTAMP('2024-07-01')),
 PARTITION p202407 VALUES LESS THAN (UNIX_TIMESTAMP('2024-08-01')),
 PARTITION p202408 VALUES LESS THAN (UNIX_TIMESTAMP('2024-09-01')),
 PARTITION p202409 VALUES LESS THAN (UNIX_TIMESTAMP('2024-10-01')),
 PARTITION p202410 VALUES LESS THAN (UNIX_TIMESTAMP('2024-11-01')),
 PARTITION p202411 VALUES LESS THAN (UNIX_TIMESTAMP('2024-12-01')),
 PARTITION p202412 VALUES LESS THAN (UNIX_TIMESTAMP('2025-01-01'))
);

# 删除分区数据
ALTER TABLE tos_vehicle.tb_car_track_vms_info TRUNCATE PARTITION p202209,p202210;

# 删除分区
ALTER TABLE tos_vehicle.tb_car_track_vms_info DROP PARTITION p202209,p202210;

# 新增加索引
ALTER TABLE `tb_wooden_frame` ADD INDEX `idx_waybill_number`(`waybill_number`) USING BTREE;
```

### mysql导出

```sql
mysqldump --add-drop-table -h10.120.25.200 -P4800 -uapp_coo_user -p --default-character-set=utf8 tos_base tb_department > tb_department_1221.sql
```

```sql
mysql -h10.120.25.1 -P4800 -uapp_coo_user -p tos_depot -e "select waybill_number from tb_depot_goods where update_time > UNIX_TIMESTAMP('2020-05-29 15:50:00') and update_time < UNIX_TIMESTAMP('2020-05-29 18:30:00') group by waybill_number " > /home/dev/depotWaybillNumber0529.txt

mysql -h10.124.46.68 -p -P9030 -A -uapp_coo_user_admin -Dprd_coofd -e " SELECT tg.waybill_number FROM prd_coofd.tb_goods_new tg LEFT JOIN prd_coofd.tb_goods_new_active tg1 ON tg1.waybill_number = tg.waybill_number AND tg1.dt >= '2023-08-01' AND tg1.dt < '2023-09-01' WHERE tg.dt > '2023-08-01' AND   tg.dt < '2023-09-01' AND   (ifnull(tg.sign_time,0) > 0 OR tg.is_abort = 1) AND   tg1.waybill_number IS NOT NULL ; " > goods_tode202309071154.txt
```

### 查看是否大小写敏感

```sql
show VARIABLES like '%case%';
```

### 字符集修改

```sql
# 先查询当前数据集
select TABLE_COLLATION, count(1) num from information_schema.`TABLES` where TABLE_SCHEMA = 'tos_mix' group by TABLE_COLLATION;
# 生成修改字符集的语句
select CONCAT('ALTER TABLE ', TABLE_NAME, ' CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;') from information_schema.tables where TABLE_SCHEMA='tos_mix' and TABLE_COLLATION='utf8_general_ci';
```

### 拼接sql

```sql
INSERT INTO _gravity.gravity_positions (name, stage, `position`, created_at, updated_at) 
SELECT 'tms2kudu_public_order' as name, 'stream', `position`, created_at, updated_at
FROM _gravity.gravity_positions
WHERE name = 'tms2kudu_public';
```

### 查询分区表

```sql
SELECT TABLE_SCHEMA
,TABLE_NAME, PARTITION_NAME,PARTITION_METHOD,PARTITION_EXPRESSION,PARTITION_DESCRIPTION,
TABLE_ROWS
FROM information_schema.PARTITIONS 
WHERE TABLE_SCHEMA  like 'tos_%' AND TABLE_SCHEMA NOT IN ('tos_test') 
and  length(PARTITION_NAME) >0   
group by TABLE_NAME
ORDER BY TABLE_SCHEMA,TABLE_NAME;

SELECT 
    TABLE_NAME, 
    PARTITION_NAME, 
    TABLE_ROWS 
FROM 
    INFORMATION_SCHEMA.PARTITIONS 
WHERE 
    TABLE_SCHEMA = 'tos_vehicle' 
    AND TABLE_NAME = 'tb_car_goods_temporary';
```

查询库表记录

```sql
## 库记录信息
select 
table_schema as '数据库',
sum(table_rows) as '记录数',
sum(truncate(data_length/1024/1024/1024, 2)) as '数据容量(GB)',
sum(truncate(index_length/1024/1024/1024, 2)) as '索引容量(GB)'
from information_schema.tables
group by table_schema
order by sum(data_length) desc, sum(index_length) desc;

## 表记录信息
select 
table_schema as '数据库',
table_name as '表名',
table_rows as '记录数',
truncate(data_length/1024/1024/1024, 2) as '数据容量(GB)',
truncate(index_length/1024/1024/1024, 2) as '索引容量(GB)'
from information_schema.tables  
where 1=1
-- and table_schema like 'tos%'
and table_name = 'vehicle_unfettered_no_delivery'
order by data_length desc, index_length desc
LIMIT 20;

## 生成删除数据的sql
SELECT CONCAT('TRUNCATE table ',TABLE_SCHEMA,'.',TABLE_NAME),
       TABLE_NAME,
       TABLE_SCHEMA,
       data_length AS data_length2,
       data_length / 1024 / 1024 / 1024 AS data_size,
       index_length / 1024 / 1024 / 1024 AS index_length,
       table_rows
FROM information_schema.tables
ORDER BY data_size DESC

```

&nbsp;