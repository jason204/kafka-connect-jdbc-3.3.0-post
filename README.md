# kafka-connect-jdbc-3.3.0-post
1. fixed postgresql boolean problem (t/f)
2. sync the part(or full) data of the table: increment_start_value >-1 or timestamp_start_value>'1970-01-01'
3. fixed the performance  for syncing the whole table with large dataset: increment_step_value or timestamp_step_day
