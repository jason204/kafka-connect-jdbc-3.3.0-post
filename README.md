# kafka-connect-jdbc-3.3.0-post


this version for syncing the tables incrementally or fully in realtime mode

fixed the follow problems:
1. fixed postgresql boolean problem (t/f)
2. sync the part(or full) data of the table: increment_start_value >-1 or timestamp_start_value>'1970-01-01'
3. fixed the performance  for syncing the whole table with large dataset: increment_step_value or timestamp_step_day

how to package

mvn package -Dmaven.test.skip=true


how to install

if system install kafka, you cd /usr/share/java/kafka-connect-jdbc/, then update kafka-connect-jdbc-3.3.0.jar file

how to deploy

edit the source conf file 






