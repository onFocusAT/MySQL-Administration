# MySQL RAM Usage

## select max usage from database

```
select *,  "-----" as "--------", concat(round(server_buffers/1024/1024/1024,2)," GB") as server_buffers, concat(round(total_buffers/1024/1024/1024,2)," GB") as total_buffers, concat(round((server_buffers + total_buffers)/1024/1024/1024,2)," GB") as sum from (SELECT @@read_buffer_size, @@read_rnd_buffer_size, @@sort_buffer_size, @@thread_stack, @@max_allowed_packet, @@join_buffer_size,@@max_connections, @@max_heap_table_size, @@key_buffer_size, @@innodb_buffer_pool_size, (@@read_buffer_size + @@read_rnd_buffer_size  + @@sort_buffer_size + @@thread_stack + @@max_allowed_packet + @@join_buffer_size ) * @@max_connections as total_buffers, if(@@max_heap_table_size > @@max_heap_table_size, @@max_heap_table_size, @@max_heap_table_size) + @@key_buffer_size + @@innodb_buffer_pool_size as server_buffers) as t\G
```


## list free and used memory on your system
```
/bin/free -h
```
