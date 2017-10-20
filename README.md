# kafka-connect-jdbc-3.3.0-post


this version is for syncing the tables incrementally or fully in realtime mode

fixed the follow problems:
1. fixed postgresql boolean problem (t/f)
2. sync the part(or full) data of the table: increment_start_value >-1 or timestamp_start_value>'1970-01-01'
3. fixed the performance for syncing the whole table with large dataset: increment_step_value or timestamp_step_day

how to package

mvn package -Dmaven.test.skip=true


how to install

if system install kafka, you cd /usr/share/java/kafka-connect-jdbc/, then update kafka-connect-jdbc-3.3.0.jar file

how to deploy

edit the source conf file 

{
"name": "src_test_id",
"config": {
       "connector.class": "io.confluent.connect.jdbc.JdbcSourceConnector",
       "tasks.max": "5",
       "connection.url": "jdbc:postgresql://192.168.1.1:5432/test?currentSchema=test",
       "connection.user": "test",
       "connection.password": "test",
       "mode": "incrementing",
       "table.whitelist": "test1,test2",
       "incrementing.column.name": "id",
       "validate.non.null": "true",
       "topic.prefix": "ods_",
       "incrementing.value": "-1",  # -1 表示增量；0或1表示全量；>1表示部分数据开始全量
       "incrementing.step.value":"1000", # 每次读取数据的id范围大小
       "timestamp.value": "1970-01-01 00:00:00",# 1970-01-01表示增量；大于1970-01-01表示全量
       "timestamp.step.day": "10",#每次读取数据的时间范围大小（天）
       "poll.interval.ms": "50000",#每次轮询的时间
       "table.poll.interval.ms": "60000",
       "timestamp.delay.interval.ms": "5000",
       "request.timeout.ms": "3100",
       "offset.flush.interval.ms": "5000",
       "heartbeat.interval.ms": "6000",
       "session.timeout.ms": "3000",
       "max.poll.records": "10001"
   }
}







