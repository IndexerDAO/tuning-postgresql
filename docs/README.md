## Getting Started with PostgreSQL Performance Tuning

### Why bother?

### Commonly Tuned Parameters

| Parameter | Description | Recommended Setting (to start) |
| --- | --- | --- | 
| [shared_buffers](https://www.postgresql.org/docs/current/runtime-config-resource.html#GUC-SHARED-BUFFERS) | Sets the amount of memory the database server uses for shared memory buffers. | LEAST(RAM/2, 10GB) |
| [wal_buffers](https://www.postgresql.org/docs/current/runtime-config-wal.html#GUC-WAL-BUFFERS) | The amount of shared memory used for WAL data that has not yet been written to disk. | 64MB |
| [effective_cache_size](https://www.postgresql.org/docs/current/runtime-config-query.html#GUC-EFFECTIVE-CACHE-SIZE) | Sets the planner's assumption about the effective size of the disk cache that is available to a single query. This is factored into estimates of the cost of using an index; a higher value makes it more likely index scans will be used, a lower value makes it more likely sequential scans will be used. | smaller value of either 0.75* total ram amount, "or the sum of buff/cache, free ram and shared buffers in the output of free command" |
| [work_mem](https://www.postgresql.org/docs/current/runtime-config-resource.html#GUC-WORK-MEM) | Sets the base maximum amount of memory to be used by a query operation (such as a sort or hash table) before writing to temporary disk files. | ((Total RAM - shared_buffers)/(16 x CPU cores)) |
| [maintenance_work_mem](https://www.postgresql.org/docs/current/runtime-config-resource.html#GUC-MAINTENANCE-WORK-MEM) | This determines the maximum amount of memory used for maintenance operations like VACUUM, CREATE INDEX, ALTER TABLE ADD FOREIGN KEY, and data-loading operations. | value of 1GB is a good start |
| [max_connections](https://www.postgresql.org/docs/current/runtime-config-connection.html#GUC-MAX-CONNECTIONS) | Determines the maximum number of concurrent connections to the database server.	| GREATEST(4 x CPU cores, 100) |

### Next steps

### Resources
