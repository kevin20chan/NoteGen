# doris常用操作

### 查看分区数据量

```sql
select count(*) from quality_monitoring_report_batch_fee_detail PARTITION(p202102);

select DISTINCT table_name from  `_statistics_`.table_statistic_v1
where 
(column_name like  '%depart_code%' 
or column_name like '%department_code%'
or column_name like '%level%%'
or column_name like '%tag%')
and db_name like '%uat_coofd%'
and table_name in ('uat_coofd.quality_monitoring_customer_batch_detail','uat_coofd.quality_monitoring_customer_batch_summary_dat','uat_coofd.tb_goods_impala_day5','uat_coofd.tb_goods_impala_day4','uat_coofd.tb_depot_goods_handover_hour_distinct','uat_coofd.operation_quality_control_overtime_ticket_temp1','uat_coofd.pickup_delivery_batch_overtime_detail','uat_coofd.pickup_delivery_waybill_overtime_detail','uat_coofd.operation_quality_report_customer_basic_dat','uat_coofd.operation_quality_report_customer_basic_month','uat_coofd.tb_goods_impala_kuasheng_new','uat_coofd.tb_goods_detain_detail','uat_coofd.tb_goods_detain_detail_oper','uat_coofd.quality_monitoring_report_line_day','uat_coofd.quality_monitoring_report_line_week','uat_coofd.quality_monitoring_report_line_month','uat_coofd.tb_goods_impala_day2','uat_coofd.tb_kuesheng_report_customer_code_detail_day_month','uat_coofd.quality_monitoring_weight_segment_day','uat_coofd.quality_monitoring_weight_segment_week','uat_coofd.quality_monitoring_weight_segment_month','uat_coofd.quality_monitoring_customer_batch_summary_month','uat_coofd.quality_monitoring_report_market_day','uat_coofd.quality_monitoring_report_market_month','uat_coofd.tb_sameterm_customer_code_summary','uat_coofd.quality_monitoring_report_market_day_10min','uat_coofd.operation_quality_control_pressure_waybill_detail','uat_coofd.fraud_checkin_detail_app','uat_coofd.operation_quality_control_overtime_ticket_temp3','uat_coofd.administrative_division_prescription','uat_coofd.quality_monitoring_report_batch_fee_detail','uat_coofd.quality_monitoring_report_batch_fee_level','uat_coofd.quality_monitoring_report_batch_fee_waybill_detail','uat_coofd.operation_quality_peak_assist_car_detail','uat_coofd.schedule_person_detail_business_department','uat_coofd.tb_operation_quality_lading_overtime_det','uat_coofd.tb_goods_impala_day4_10min');

```

### 临时分区查看与删除

```sql
-- 查看分区
show PARTITIONS from ods_coo.tb_car_goods_temporary;

-- 删除分区的数据(分区还在)
ALTER TABLE ods_coo.tb_car_track_temporary TRUNCATE PARTITION p202308;

--查看临时分区
SHOW TEMPORARY PARTITIONS FROM quality_monitoring_report_line_month;

--删除临时分区
ALTER TABLE quality_monitoring_report_line_month DROP TEMPORARY PARTITION tp202012;

-- 增加分区
ALTER TABLE uat_coofd.tb_waybill_time_effect_monitor SET ("dynamic_partition.enable" = "false");
ALTER TABLE uat_coofd.tb_waybill_time_effect_monitor ADD PARTITION p202007 VALUES [("1970-01-01"), ("2020-08-01"));
ALTER TABLE uat_coofd.tb_waybill_time_effect_monitor SET ("dynamic_partition.enable" = "true");
```

### routine load 操作

```sql
-- 查看实时导入任务状态
SHOW ROUTINE LOAD FOR test1;
SHOW ROUTINE LOAD where State = 'RUNNING';
show routine load where Name = 'tb_car_track_temporary_1721981000273' \G;

-- 暂停实时导入任务状态
PAUSE ROUTINE LOAD FOR test1;

-- 恢复实时导入任务状态
RESUME ROUTINE LOAD FOR test1;

-- 停止实时导入任务状态
STOP ROUTINE LOAD FOR test1;

-- 创建routine load
CREATE ROUTINE LOAD tb_department_new_1720526523000 ON tb_department_new
COLUMNS TERMINATED BY ",",
COLUMNS (
   id,department_id,department_name,charge_id,charge_name,parent_id,duty_id,duty_name,hierarchy,hierarchy_code,department_code,department_code1,department_code2,department_code3,department_code4,department_code5,department_code6,department_code7,department_code8,department_code9,department_route,virtual_department,code,left_value,right_value,enabled_flag,organization_type,check_update_time,check_name,check_update_name,is_deconsolidation,start_time,end_time,create_time,start_date,end_date,department_id_route,part_time_flag,depart_type,level1,level2,level3,level4,level5,level6,level7,level8,level9,department_id_route_coo,tag,tag_value,department_route_coo,level_number,area_type,province,city,county,town,address,address_config,lv1_dept_id,lv2_dept_id,lv3_dept_id,lv4_dept_id,lv5_dept_id,lv6_dept_id,lv7_dept_id,lv8_dept_id,lv9_dept_id
)
PROPERTIES
(
   "desired_concurrent_number"="1",
   "format"="json",  
   "json_root"="$.data"
)
FROM KAFKA
(
    "kafka_broker_list"="coo-uat-tidb-kafka1.kyeapi.com:9092,coo-uat-tidb-kafka2.kyeapi.com:9092,coo-uat-tidb-kafka3.kyeapi.com:9092",
    "kafka_topic" = "doris.tos.department.new",
    "property.group.id" = "kafka_group_tb_department_new"
);

CREATE ROUTINE LOAD tb_car_track_forever_20220922 ON tb_car_track_forever
COLUMNS TERMINATED BY ",",
COLUMNS (
   dt=from_unixtime(`create_time`, '%Y-%m-%d %H:%i:%s'),id,car_no,driver,driver_code,driver_belong_network_id,driver_belong_network,driver_belong_department_id,driver_phone,original,original_id,original_code,target,target_id,target_code,trunk_line_code,agent_code,agent_name,agent_total_weight,agent_total_package_num,agent_total_fee,fee_rating,start_time,arrive_time,allocate_time,trunk_line_time,create_time,update_time,sys_id,route_desc,estimated_arrival_time,distance,import_export,longitude,latitude,chartered_car_task_number,delivery_date,lading_date,lading_finish_date,flight_takeoff_time,flight_landing_time,flight_date,land_transport_type,actual_lading_by_count,total_ticket,transport_mode,total_volume_weight,actual_kilometre_number,empty_return_flag,stopover,driver_inner_flag,start_time_is_dmv,end_time_is_dmv,agent,parentId,fetch_or_dispatch,theory_kilometre_number,reference_kilometre_number,total_weight,estimated_arrival_time_source,data_source,upload_id,upload_name,pad_batch_number,track_type,original_nine_code,target_nine_code,driver_belong_network_code9,carriage_length,trips,share_fee_all,share_flag,share_load,share_weight_all,site_type_flag,status_code,rule_departure_time,enabled_flag,loading_complete_time,loading_complete_node_id,end_time,follow_driver,miss_goods_flag,loading_rate,lading_status,actual_lading_by,stowage_analyze_type,trunkline_type,change_flight_number,trunk_code,leave_start_time,total_cost,inner_flag,vms_destination_time,departure_time,stop_station,pda_loading_end_time,original_department_id,target_department_id,dispatcher_1_id,dispatcher_2_id,first_unloading_time,first_loading_time,type_flag
),
where ifnull(`create_time`, 0) > 1656604800
PROPERTIES
(
   "desired_concurrent_number"="1",
   "format"="json",  
   "json_root"="$.data"
)
FROM KAFKA
(
    "kafka_broker_list"="10.120.212.5:9092,10.120.212.14:9092,10.120.212.16:9092",
    "kafka_topic" = "doris.tos.cartrack.forever",
    "property.group.id" = "kafka_group_tb_car_track_forever"
);

-- 修改routine load offset
ALTER ROUTINE LOAD FOR tb_goods_info_001
PROPERTIES
(
    "desired_concurrent_number" = "3"
)
FROM kafka
(
    "kafka_partitions" = "0,1,2",
    "kafka_offsets" = "OFFSET_END,OFFSET_END,OFFSET_END"
);
```

### broker load操作

```sql
# 查看导入信息
SHOW LOAD FROM uat_coofd WHERE LABEL Like "table" ORDER BY LoadStartTime DESC;
# 取消load
CANCEL LOAD [FROM db_name] WHERE LABEL = "label_name";

# 导入异常任务查询
SELECT job_id, label, state, scan_rows, filtered_rows, unselected_rows,
       sink_rows, error_msg, tracking_sql, properties
FROM information_schema.loads
WHERE 1=1 
and label like '%dwd_coo_damaged_control_improve_config_result_m%'
ORDER BY create_time DESC
LIMIT 100;

# 查询异常日志
select * from information_schema.load_tracking_logs where job_id=366849123
```

### 原子替换

```sql
ALTER TABLE tb_goods_impala_day1_temp SWAP WITH tb_goods_impala_day1;
```

刷新元数据

```sql
refresh EXTERNAL table  coo_hive_catalog.dwd_coo.dwd_coo_damaged_control_improve_config_waybill_m;
```

### 定位慢查询sql

```sql
SELECT query_id,
       digest,
       mem_cost_bytes / 1024 / 1024 AS '内存消耗M',
       cpu_cost_ns,
       query_time,
       return_rows,
       scan_bytes
FROM auditdb.audit_log
WHERE is_query = 1
AND   TIME> '2024-03-02 16:30:00'
AND   TIME< '2024-03-02 16:50:59'
AND   query_time > 3000
AND   scan_bytes > 0
-- AND   digest = 'acd55601e61a0617269f5c983940e020'
-- ORDER BY scan_bytes DESC LIMIT 5;
ORDER BY query_time DESC LIMIT 5;

WITH tmp AS
(
  SELECT queryId
         ,digest
         ,returnRows
         ,queryTime
         ,TIMESTAMP
         ,ROUND(cpuCostNs / 1000000000,2) AS avgcpuCost_S
         ,ROUND(memCostBytes / 1024 / 1024,2) AS avgMemCost_M
         ,ROW_NUMBER() OVER (PARTITION BY digest ORDER BY cpuCostNs DESC,TIMESTAMP asc) AS `rn`
         ,stmt
  FROM auditdb.audit_log
  WHERE 1 = 1
   AND   TIMESTAMP> days_add(CURDATE(), -2)
  AND   TIMESTAMP<= days_add(CURDATE(), -1)
-- AND  TIMESTAMP > '2025-05-09 11:14:00'
--  AND   TIMESTAMP < '2025-05-09 11:19:00'
--  cpu 耗时超10s
   and  cpuCostNs >   10000000000
  and `user` = 'app_coo_user_query'
)
SELECT 
regexp_extract(stmt,"sqlId=([^ ]*)",1) AS sqlId
,queryId
,queryTime
,digest
,returnRows
,TIMESTAMP
,avgcpuCost_S
,avgMemCost_M
FROM tmp
WHERE   1=1 
and  rn = 1 
order by avgcpuCost_S  desc 
LIMIT 10;

SELECT queryId,
       digest,
       memCostBytes / 1024 / 1024 AS '内存消耗M',
       cpuCostNs,
       queryTime,
       returnRows,
       scanBytes
FROM auditdb.audit_log
WHERE isQuery = 1
AND   timestamp> '2025-03-06 21:05:00'
AND   timestamp < '2025-03-06 21:11:59'
AND   queryTime > 3000
AND   scanBytes > 0
-- AND   digest = 'acd55601e61a0617269f5c983940e020'
-- ORDER BY scan_bytes DESC LIMIT 5;
ORDER BY queryTime DESC LIMIT 5;

SELECT regexp_extract(stmt,"sqlId=([^ ]*)",1) AS sqlId,
       CAST(percentile_approx (queryTime,0.99) AS FLOAT) AS P99,
       ROUND(AVG(queryTime),2) AS avgQueryTime,
       MAX(queryTime),
       COUNT(1),
       ROUND(AVG(memCostBytes) / 1024 / 1024,2) AS avgMemCost_M,
       ROUND(AVG(cpuCostNs) / 1000000000 ,2) AS avgcpuCost_S,
       MAX(returnRows)
FROM auditdb.audit_log
WHERE TIMESTAMP> '2024-07-23 20:00:00'
AND   TIMESTAMP< '2024-07-23 20:10:00'
group  by regexp_extract(stmt,"sqlId=([^ ]*)",1)
ORDER BY COUNT(1) DESC
         LIMIT 30;

WITH tmp
AS
(SELECT query_id,
       digest,
       mem_cost_bytes / 1024 / 1024 AS '内存消耗M',
       cpu_cost_ns,
       query_time,
       return_rows,
       scan_bytes
FROM auditdb.audit_log
WHERE is_query = 1
AND   TIME> '2023-07-01 00:00:00'
AND   TIME< '2023-08-01 23:59:59'
AND   query_time > 3000
AND   scan_bytes > 0) 
SELECT digest FROM tmp
GROUP BY digest
HAVING COUNT(digest) > 3;

SELECT `DIGEST`,
       COUNT(1)
FROM auditdb.audit_log
WHERE is_query = 1
AND   TIME> '2023-07-01 00:00:00'
AND   TIME< '2023-08-01 23:59:59'
AND   query_time > 3000
GROUP BY `digest`
ORDER BY COUNT(1) DESC LIMIT 50
```

&nbsp;