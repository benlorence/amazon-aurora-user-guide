# Database Engine Versions for Amazon Aurora PostgreSQL<a name="AuroraPostgreSQL.Updates.20180305"></a>

Following, you can find information about updates to the Aurora with PostgreSQL compatibility database engine\. 

The following table shows the version of PostgreSQL that each Aurora PostgreSQL release is compatible with\.


****  

| Aurora with PostgreSQL Compatibility | Compatible PostgreSQL Release | 
| --- | --- | 
| [Version 2\.2\.0](#AuroraPostgreSQL.Updates.20180305.22) | [10\.6](https://www.postgresql.org/docs/current/static/release-10-6.html) | 
| [Version 2\.1](#AuroraPostgreSQL.Updates.20180305.21) | [10\.5](https://www.postgresql.org/docs/current/static/release-10-5.html) | 
| [Version 2\.0](#AuroraPostgreSQL.Updates.20180305.20) | [10\.4](https://www.postgresql.org/docs/current/static/release-10-4.html) | 
| [Version 1\.4\.0](#AuroraPostgreSQL.Updates.20180305.14) | [9\.6\.11](https://www.postgresql.org/docs/9.6/release-9-6-11.html) | 
| [Version 1\.3](#AuroraPostgreSQL.Updates.20180305.13) | [9\.6\.9](https://www.postgresql.org/docs/current/static/release-9-6-9.html) | 
| [Version 1\.2](#AuroraPostgreSQL.Updates.20180305.12) | [9\.6\.8](https://www.postgresql.org/docs/current/static/release-9-6-8.html) | 
| [Version 1\.1](#AuroraPostgreSQL.Updates.20180305.11) | [9\.6\.6](https://www.postgresql.org/docs/current/static/release-9-6-6.html) deprecated | 
| Version 1\.0 | [9\.6\.3](https://www.postgresql.org/docs/current/static/release-9-6-3.html) deprecated | 

The following updates are available for Aurora PostgreSQL\.

## Version 2\.2\.0<a name="AuroraPostgreSQL.Updates.20180305.22"></a>

You can find the following improvements in this engine update\.

**New features**
+ This version of Aurora PostgreSQL is compatible with PostgreSQL 10\.6\. For more information about the improvements in release 10\.6, see [PostgreSQL Release 10\.6](https://www.postgresql.org/docs/current/static/release-10-6.html)\.
+ Added the restricted password management feature\. Restricted password management enables you to restrict who can manage user passwords and password expiration changes by using the parameter `rds.restrict_password_commands` and the role `rds_password`\. For more information, see [Restricting Password Management](AuroraPostgreSQL.Security.md#RestrictPasswordMgmt)\. 

## Version 2\.1<a name="AuroraPostgreSQL.Updates.20180305.21"></a>

You can find the following improvements in this engine update\.

**New features**
+ This version of Aurora PostgreSQL is compatible with PostgreSQL 10\.5\. For more information about the improvements in release 10\.5, see [PostgreSQL Release 10\.5](https://www.postgresql.org/docs/current/static/release-10-5.html)\.
+ General availability of Aurora Query Plan Management, which enables customers to track and manage any or all query plans used by their applications, to control query optimizer plan selection, and to ensure high and stable application performance\. For more information, see [Managing Query Execution Plans for Aurora PostgreSQL](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/AuroraPostgreSQL.Optimize.html)\. 
+ Updated the `libprotobuf` extension to version 1\.3\.0\. This is used by the PostGIS extension\.
+ Updated the `pg_similarity` extension to version 1\.0\.
+ Updated the `log_fdw` extension to version 1\.1\.
+ Updated the `pg_hint_plan` extension to version 1\.3\.1\.

**Improvements**
+ Network traffic between the writer and reader nodes is now compressed to reduce network utilization\. This reduces the chance of read node unavailability due to network saturation\.
+ Implemented a high performance, scalable subsystem for PostgreSQL subtransactions\. This improves the performance of applications which make extensive use of savepoints and `PL/pgSQL` exception handlers\.
+ The `rds_superuser` role can now set the following parameters on a per\-session, database, or role level: 
  + `log_duration`
  + `log_error_verbosity`
  + `log_executor_stats`
  + `log_lock_waits`
  +  `log_min_duration_statement`
  +  `log_min_error_statement`
  +  `log_min_messages`
  +  `log_parser_stats`
  +  `log_planner_stats`
  +  `log_replication_commands`
  +  `log_statement_stats`
  + `log_temp_files `
+ Fixed a bug whereby the SQL command "ALTER FUNCTION \.\.\. OWNER TO \.\.\." might fail with error "improper qualified name \(too many dotted names\)"\.
+ Fixed a bug whereby a crash could occur while committing a transaction with more than two million subtransactions\.
+ Fixed a bug in community PostgreSQL code related to GIN indexes which can cause the Aurora Storage volume to become unavailable\.
+ Fixed a bug whereby an Aurora PostgreSQL replica of an RDS for PostgreSQL instance might fail to start, reporting error: "PANIC: could not locate a valid checkpoint record"\.
+ Fixed a bug whereby passing an invalid parameter to the `aurora_stat_backend_waits` function could cause a crash\.

**Known issues**
+ The `pageinspect` extension is not supported in Aurora PostgreSQL\.

## Version 2\.0<a name="AuroraPostgreSQL.Updates.20180305.20"></a>

You can find the following improvements in this engine update\.

**New features**
+ This version of Aurora PostgreSQL is compatible with PostgreSQL 10\.4\. For more information about the improvements in release 10\.4, see [Release 10\.4](https://www.postgresql.org/docs/current/static/release-10-4.html)\.

**Improvements**
+ This release contains all fixes, features, and improvements present in [Version 1\.3](#AuroraPostgreSQL.Updates.20180305.13)\.
+ The temporary file size limitation is user\-configurable\. You require the **rds\_superuser** role to modify the `temp_file_limit` parameter\.
+ Updated the `GDAL` library, which is used by the `PostGIS` extension\. 
+ Updated the `ip4r` extension to version 2\.1\.1\.
+ Updated the `pg_repack` extension to version 1\.4\.3\. 
+ Updated the `plv8` extension to version 2\.1\.2\.
+ Parallel queries – When you create a new Aurora PostgreSQL version 2\.0 instance, parallel queries are enabled for the `default.postgres10` parameter group\. The parameter `max_parallel_workers_per_gather` is set to 2 by default, but you can modify it to support your specific workload requirements\.

## Version 1\.4\.0<a name="AuroraPostgreSQL.Updates.20180305.14"></a>

You can find the following improvements in this engine update\.

**New features**
+ This version of Aurora PostgreSQL is compatible with PostgreSQL 9\.6\.11\. For more information about the improvements in release 9\.6\.11, see [PostgreSQL Release 9\.6\.11](https://www.postgresql.org/docs/9.6/release-9-6-11.html)\. 
+ Support is added for the `pg_similarity` extension version 1\.0\.

**Improvements**
+ This release contains all fixes, features, and improvements present in [Version 1\.3](#AuroraPostgreSQL.Updates.20180305.13)\.
+ Performance of subtransactions has improved under high concurrency workloads\.
+ An update for the `pg_hint_plan` extension to version 1\.2\.3\.
+ Fixed an issue where on a busy system, a commit with millions of subtransactions \(and sometimes with commit timestamps enabled\) can cause Aurora to crash\.
+ Fixed an issue where an `INSERT` statement with `VALUES` could fail with the message "Attempting to read past EOF of relation"\.
+ An upgrade of the `apg_plan_mgmt` extension to version 1\.0\.1\. The `apg_plan_mgmt` extension is used with query plan management\. For more about how to install, upgrade, and use the `apg_plan_mgmt` extension, see [Managing Query Execution Plans for Aurora PostgreSQL](AuroraPostgreSQL.Optimize.md)\.

  The `apg_plan_mgmt` extension new features include the following:
  + A new `update_plan_hash` parameter is available for the `validate_plans` function\. This parameter updates the `plan_hash` for plans that can't be reproduced exactly\. The `update_plan_hash` parameter also enables you to fix a plan by rewriting the SQL\. You can then register the good plan as an `Approved` plan for the original SQL\. Following is an example of using `update_plan_hash`\.

    ```
    UPDATE apg_plan_mgmt.dba_plans SET plan_hash = new _plan_hash, plan_outline = good_plan_outline 
       WHERE sql_hash = bad_plan_sql_hash AND plan_hash = bad_plan_plan_hash;
    SELECT apg_plan_mgmt.validate_plans(bad_plan_sql_hash, bad_plan_plan_hash, 'update_plan_hash');
    SELECT apg_plan_mgmt.reload();
    ```
  + A new `get_explain_stmt` function is available that generates the text of an `EXPLAIN` statement for the specified SQL statement\. It includes the parameters `sql_hash`, `plan_hash` and `explain_options`\. 

    The parameter `explain_options` can be any comma\-separated list of valid `EXPLAIN` options, as shown following\.

    ```
    analyze,verbose,buffers,hashes,format json
    ```

    If the parameter `explain_options` is NULL or an empty string, the `get_explain_stmt` function generates a simple `EXPLAIN` statement\. 

    To create an `EXPLAIN` script for your workload or a portion of it, use the `\a` , `\t`, and `\o` options to redirect the output to a file\. For example, you can create an `EXPLAIN` script for the top\-ranked \(top\-K\) statements by using the PostgreSQL `pg_stat_statements` view sorted by `total_time` in `DESC` order\.
  + The precise location of the Gather parallel query operator is determined by costing, and may change slightly over time\. To prevent these differences from invalidating the entire plan, query plan management now computes the same `plan_hash` even if the Gather operators move to different places in the plan tree\.
  + Support is added for nonparameterized statements inside pl/pgsql functions\.
  + Overhead is reduced when the `apg_plan_mgmt` extension is installed on multiple databases in the same cluster while two or more databases are being accessed concurrently\. Also, this release fixed a bug in this area that caused plans to not be stored in shared memory\.

  The `apg_plan_mgmt extension` improvements include the following:
  + Improvements to the `evolve_plan_baselines` function\.
    + The `evolve_plan_baselines` function now computes a `cardinality_error` metric over all nodes in the plan\. Using this metric, you can identify any plan where the cardinality estimation error is large, and the plan quality is more doubtful\. Long\-running statements with high `cardinality_error` values are high\-priority candidates for query tuning\.
    + Reports generated by `evolve_plan_baselines` now include `sql_hash`, `plan_hash`, and the plan `status`\.
    + You can now allow `evolve_plan_baselines` to approve previously `Rejected` plans\.
    + The meaning of `speedup_factor` for `evolve_plan_baselines` is now always relative to the baseline plan\. For example, a value of 1\.1 now means 10 percent faster than the baseline plan\. A value of 0\.9 means 10 percent slower than the baseline plan\. The comparison is made using execution time alone instead of total time\.
    + The `evolve_plan_baselines` function now warms the cache in a new way\. It does this by running the baseline plan, then running the baseline plan one more time, and then running the candidate plan once\. Previously, `evolve_plan_baselines` ran the candidate plan twice\. This approach added significantly to execution time, especially for slow candidate plans\. However, running the candidate plan twice is more reliable when the candidate plan uses an index that isn't used in the baseline plan\.
  + Query plan management no longer saves plans that refer to system tables or views, temporary tables, or the query plan management's own tables\.
  + Bug fixes include caching a plan immediately when saved and fixing a bug that caused the back end to terminate\.

## Version 1\.3<a name="AuroraPostgreSQL.Updates.20180305.13"></a>

You can find the following improvements in this engine update\.

**New features**
+ This version of Aurora PostgreSQL is compatible with PostgreSQL 9\.6\.9\. For more information about the improvements in version 9\.6\.9, see [Release 9\.6\.9](https://www.postgresql.org/docs/9.6/static/release-9-6-9.html)\.

**Improvements**
+ This release contains all fixes, features, and improvements present in [Version 1\.2](#AuroraPostgreSQL.Updates.20180305.12)\.
+ Updated the GDAL library, which is used by the `PostGIS` extension\. 
+ Updated the following PostgreSQL extensions: 
  + `ip4r` updated to version 2\.1\.1\.
  + `pgaudit` updated to version 1\.1\.1\. 
  + `pg_repack` updated to version 1\.4\.3\. 
  + `plv8` updated to version 2\.1\.2\.
+ Fixed an issue in the monitoring system that could incorrectly cause a failover when local disk usage is high\.
+ Fixed a bug whereby Aurora PostgreSQL can repeatedly crash, reporting:

  `PANIC: new_record_total_len (8201) must be less than BLCKSZ (8192), rmid (6), info (32)`
+ Fixed a bug whereby an Aurora PostgreSQL read node might be unable to rejoin a cluster due to recovery of a large buffer cache\. This issue is unlikely to occur on instances other than **r4\.16xlarge\.**
+ Fixed a bug whereby inserting into an empty GIN index leaf page imported from pre\-9\.4 engine versions can cause the Aurora storage volume to become unavailable\.
+ Fixed a bug whereby, in rare circumstances, a crash during transaction commit could result in the loss of `CommitTs` data for the committing transaction\. The actual durability of the transaction was not impacted by this bug\.
+ Fixed a bug in the `PostGIS` extension whereby `PostGIS` can crash in the function `gserialized_gist_picksplit_2d()`\.
+ Improved the stability of read\-only nodes during heavy write traffic on instances smaller than **r4\.8xl**\. This specifically addresses a situation where the network bandwidth between the writer and the reader is constrained\.
+ Fixed a bug whereby an Aurora PostgreSQL instance acting as a replication target of an RDS for PostgreSQL instance crashed with the following error:

  `FATAL: could not open file "base/16411/680897_vm": No such file or directory" during "xlog redo at 782/3122D540 for Storage/TRUNCATE"`
+ Fixed a memory leak on read\-only nodes whereby the heap size for the "aurora wal replay process" will continue to grow\. This is observable via Enhanced Monitoring\.
+ Fixed a bug whereby Aurora PostgreSQL can fail to start, with the following message reported in the PostgreSQL log:

  `FATAL: Storage initialization failed.`
+ Fixed a performance limitation on heavy write workloads that caused waits on the `LWLock:buffer_content` and `IO:ControlFileSyncUpdate` events\.

## Version 1\.2<a name="AuroraPostgreSQL.Updates.20180305.12"></a>

You can find the following improvements in this engine update\.

**New features**
+ This version of Aurora PostgreSQL is compatible with PostgreSQL 9\.6\.8\. For more information about the improvements in version 9\.6\.8, see [Release 9\.6\.8](https://www.postgresql.org/docs/9.6/static/release-9-6-8.html)\.
+ Introduced the `aurora_stat_memctx_usage()` function\. This function reports internal memory context usage for each PostgreSQL backend\. You can use this function to help determine why certain backends are consuming large amounts of memory\.

**Improvements**
+ This release contains all fixes, features, and improvements present in version 1\.1\. For the complete list of improvements, see [Version 1\.1](#AuroraPostgreSQL.Updates.20180305.11)\.
+ Updates the following PostgreSQL extensions:
  + `pg_hint_plan` updated to version 1\.2\.2
  + `plv8` updated to version 2\.1\.0
+ Improves efficiency of traffic between writer and reader nodes\.
+ Improves connection establishment performance\.
+ Improve the diagnostic data provided in the PostgreSQL error log when an out\-of\-memory error is encountered\.
+ Multiple fixes to improve the reliability and performance of snapshot import from Amazon RDS for PostgreSQL to Aurora with PostgreSQL compatibility\.
+ Multiple fixes to improve the reliability and performance of Aurora PostgreSQL read nodes\.
+ Fixes a bug in which an otherwise idle instance can generate unnecessary read traffic on an Aurora storage volume\.
+ Fixes a bug in which duplicate sequence values can be encountered during insert\. The problem only occurs when migrating a snapshot from RDS for PostgreSQL to Aurora PostgreSQL\. The fix prevents the problem from being introduced when performing the migration\. Instances migrated before this release can still encounter duplicate key errors\.
+ Fixes a bug in which an RDS for PostgreSQL instance migrated to Aurora PostgreSQL using replication can run out of memory doing insert/update of GIST indexes, or cause other issues with GIST indexes\.
+ Fixes a bug in which vacuum can fail to update the corresponding `pg_database.datfrozenxid` value for a database\.
+ Fixes a bug in which a crash while creating a new MultiXact \(contended row level lock\) can cause Aurora PostgreSQL to hang indefinitely on the first access to the same relation after the engine restarts\.
+ Fixes a bug in which a PostgreSQL backend can't be terminated or canceled while invoking an `fdw` call\.
+ Fixes a bug in which one vCPU is fully utilized at all times by the Aurora storage daemon\. This issue is especially noticeable on smaller instance types, such as r4\.large, where it can lead to 25–50 percent CPU usage when idle\.
+ Fixes a bug in which an Aurora PostgreSQL writer node can fail over spuriously\.
+ Fixes a bug in which, in a rare scenario, an Aurora PostgreSQL read node can report: 

  "FATAL: lock buffer\_io is not held"
+ Fixes a bug in which stale relcache entries can halt vacuuming of relations and push the system close to transaction ID wraparound\. The fix is a port of a PostgreSQL community patch scheduled to be released in a future minor version\.
+ Fixes a bug in which a failure while extending a relation can cause Aurora to crash while scanning the partially extended relation\.

## Version 1\.1<a name="AuroraPostgreSQL.Updates.20180305.11"></a>

You can find the following improvements in this engine update:

**New features**
+ This version of Aurora PostgreSQL is compatible with PostgreSQL 9\.6\.6\. For more information about the improvements in version 9\.6\.6 see, [Release 9\.6\.6](https://www.postgresql.org/docs/9.6/static/release-9-6-6.html)\.
+ Introduced the `aurora_stat_utils` extension\. This extension includes two functions:
  + aurora\_wait\_report\(\) function for wait event monitoring
  + aurora\_log\_report\(\) for log record write monitoring
+ Added support for the following extensions:
  + orafce 3\.6\.1
  + pgrouting 2\.4\.2
  + postgresql\-hll 2\.10\.2
  + prefix 1\.2\.6

**Improvements**
+ This release contains all fixes, features, and improvements present in version 1\.0\.11\. For the complete list of improvements see, [Version 1\.0\.11](#AuroraPostgreSQL.Updates.20180305.1011)
+ Updates for the following PostgreSQL extensions:
  + postgis extension updated to version 2\.3\.4
  + geos library updated to version 3\.6\.2
  + pg\_repack updated to version 1\.4\.2
+ Access to the pg\_statistic relation enabled\.
+ Disabled the 'effective\_io\_concurrency' guc parameter, as it does not apply to Aurora storage\.
+ Changed the 'hot\_standby\_feedback' guc parameter to not\-modifiable and set the value to '1'\.
+ Improved heap page read performance during a vacuum operation\.
+ Improved performance of snapshot conflict resolution on read nodes\.
+ Improved performance of transaction snapshot acquisition on read nodes\.
+ Improved write performance for GIN meta page updates\.
+ Improved buffer cache recovery performance during startup\.
+ Fixes a bug that caused a database engine crash at startup while recovering prepared transactions\.
+ Fixes a bug that could result in the inability to start a read node when there are a large number of prepared transactions\.
+ Fixes a bug that could cause a read node to report:

  ERROR: could not access status of transaction 6080077 

  DETAIL:\* \*Could not open file "pg\_subtrans/005C": No such file or directory\.
+ Fixes a bug that could cause the error below when replicating from RDS PostgreSQL to Aurora PostgreSQL:

  FATAL: lock buffer\_content is not held

  CONTEXT: xlog redo at 46E/F1330870 for Storage/TRUNCATE: base/13322/8058750 to 0 blocks flags 7
+ Fixes a bug that could cause Aurora PostgreSQL to hang while replaying a multixact WAL record when replicating from RDS PostgreSQL to Aurora PostgreSQL\.
+ Multiple improvements to the reliability of importing snapshots from RDS PostgreSQL to Aurora PostgreSQL\.

## Version 1\.0\.11<a name="AuroraPostgreSQL.Updates.20180305.1011"></a>

You can find the following improvements in this engine update:
+ Fixes an issue with parallel query execution that can lead to incorrect results\.
+ Fixes an issue with visibility map handling during replication from Amazon RDS for PostgreSQL that can cause the Aurora storage volume to become unavailable\. 
+ Corrects the pg\-repack extension\.
+ Implements improvements to maintain fresh nodes\.
+ Fixes issues that can lead to an engine crash\.

## Version 1\.0\.10<a name="AuroraPostgreSQL.Updates.20180305.1010"></a>

This update includes a new feature\. You can now replicate an Amazon RDS PostgreSQL DB instance to Aurora PostgreSQL\. For more information, see [Replication with Amazon Aurora PostgreSQL](AuroraPostgreSQL.Replication.md)\.

You can find the following improvements in this engine update:
+ Adds error logging when a cache exists and a parameter change results in a mismatched buffer cache, storage format, or size\.
+ Fixes an issue that causes an engine reboot if there is an incompatible parameter value for huge pages\. 
+ Improves handling of multiple truncate table statements during a replay of a write ahead log \(WAL\) on a read node\.
+ Reduces static memory overhead to reduce out\-of\-memory errors\.
+ Fixes an issue that can lead to out\-of\-memory errors while performing an insert with a GiST index\.
+ Improves snapshot import from RDS PostgreSQL, removing the requirement that a vacuum be performed on uninitialized pages\.
+ Fixes an issue that causes prepared transactions to return to the previous state following an engine crash\.
+ Implements improvements to prevent read nodes from becoming stale\.
+ Implements improvements to reduce downtime with an engine restart\.
+ Fixes issues that can cause an engine crash\.

## Version 1\.0\.9<a name="AuroraPostgreSQL.Updates.20180305.109"></a>

In this engine update, we fix an issue that can cause the Aurora storage volume to become unavailable when importing a snapshot from RDS PostgreSQL that contained uninitialized pages\.

## Version 1\.0\.8<a name="AuroraPostgreSQL.Updates.20180305.108"></a>

You can find the following improvements in this engine update:
+ Fixes an issue that prevented the engine from starting if the `shared_preload_libraries` instance parameter contained `pg_hint_plan`\. 
+ Fixes the error "Attempt to fetch heap block XXX is beyond end of heap \(YYY blocks\)," which can occur during parallel scans\. 
+ Improves the effectiveness of prefetching on reads for a vacuum\.
+ Fixes issues with snapshot import from RDS PostgreSQL, which can fail if there are incompatible pg\_internal\.init files in the source snapshot\.
+ Fixes an issue that can cause a read node to crash with the message "aurora wal replay process \(PID XXX\) was terminated by signal 11: Segmentation fault"\. This issue occurs when the reader applied a visibility map change for an uncached visibility map page\.

## Version 1\.0\.7<a name="AuroraPostgreSQL.Updates.20180305.107"></a>

This is the first generally available release of Amazon Aurora with PostgreSQL compatibility\.