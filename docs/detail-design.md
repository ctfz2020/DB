# 详细设计

#### 元信息管理模块

元信息包括用户构建的用户表,数据源,表,字段信息, 系统文件路径信息, 节点信息, 监控信息等.

##### 用户表

| 字段名      | 类型   | 备注               |
| ----------- | ------ | ------------------ |
| username    | string | 用户名             |
| password    | string | 密码               |
| datasources | array  | 持有哪些数据源权限 |

##### 数据源

| 字段名          | 类型   | 备注       |
| --------------- | ------ | ---------- |
| datasource_id   | int    | 自增id     |
| datasource_name | string | 数据源名称 |

##### 粒度表

| 字段名           | 类型   | 备注     |
| ---------------- | ------ | -------- |
| granularity_id   | int    | 自增id   |
| datasource_id    | int    | 数据源id |
| granularity_name | string | 粒度     |
| retention_time   | string | 保留时间 |

##### 表信息

| 字段名        | 类型   | 备注     |
| ------------- | ------ | -------- |
| table_id      | int    | 表id     |
| datasource_id | int    | 数据源id |
| table_name    | string | 表名     |

##### 字段信息

| 字段名         | 类型   | 备注     |
| -------------- | ------ | -------- |
| field_id       | int    | 字段id   |
| table_id       | int    | 表id     |
| field_name     | string | 字段名   |
| type           | string | 类型     |
| aggregate_type | string | 聚合方式 |

##### 文件路径信息

| 字段名     | 类型  | 备注         |
| ---------- | ----- | ------------ |
| id         | int   | 增长id       |
| start_time | long  | 起始时间     |
| end_time   | long  | 结束时间     |
| row_num    | long  | 数据条数     |
| file_size  | long  | 文件大小     |
| node_ids   | array | 存储的节点id |
|            |       |              |