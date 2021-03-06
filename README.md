# orazabbix
Oracle Database Monitoring on Zabbix, Blazing Fast via Golang.

## Build Steps:
1. Clone repo
2. Setup oracle instant client and environment variables. [Guide](https://gocodecloud.com/blog/2016/08/09/accessing-an-oracle-db-in-go/)
3. `go build main.go`

```
Usage:
  orazabbix [flags]

Flags:
      --alsologtostderr                  log to standard error as well as files
  -c, --connectionstring string          ConnectionString to the Database, Format: username/password@ip:port/sid (default "system/oracle@localhost:1521/xe")
  -h, --help                             help for orazabbix
  -H, --host string                      Hostname of the monitored object in zabbix server (default "server1")
      --log_backtrace_at traceLocation   when logging hits line file:N, emit a stack trace (default :0)
      --log_dir string                   If non-empty, write log files in this directory
      --logtostderr                      log to standard error instead of files
  -p, --port int                         Zabbix Server/Proxy Port (default 10051)
      --stderrthreshold severity         logs at or above this threshold go to stderr (default 2)
  -v, --v Level                          log level for V logs
      --vmodule moduleSpec               comma-separated list of pattern=N settings for file-filtered logging
  -z, --zabbix string                    Zabbix Server/Proxy Hostname or IP address (default "localhost")
  ```
  
  ## Installation:
  1. Import template file in Zabbix server.
  2. Add cron entry:
  
  ```
  * * * * * oracle source /home/oracle/.bash_profile;/home/oracle/main -c <user>/<password>@<instance ip or hostname>:<port>/<sid> -z <zabbix server ip> -p <zabbix server(trapper) port>-H <hostname in zabbix server> 2>&1 >/dev/null
  ```
  3. Restart cron service
  4. Latest data in Zabbix frontend should start populating after a minute.
  
## Features:
- Autodiscovery for tablespaces
- Autodiscovery for ASM Diskgroups
- Tablespace size (bytes/percent)
- ASM Diskgroups size (bytes)
- ASM Diskgroups Offline Disks Count
- Alive
- Archivelog switch
- Blocking Sessions
- Blocking Sessions Full Information
- DB Block Changes
- DB Block Gets
- DB Consistent Gets
- DB Files Size
- DB Hit Ratio
- DB Physical Reads
- DB Version
- Hit ratio - BODY
- Hit ratio - SQLAREA
- Hit ratio - TABLE/PROCEDURE
- Hit ratio - TRIGGER
- Max Processes
- Max Sessions
- Miss Latch
- PGA
- PGA Aggregate target
- PHI/O Datafile Reads
- PHI/O Datafile Writes
- PHI/O Redo Writes
- Pin hit ratio - BODY
- Pin hit ratio - SQLAREA
- Pin hit ratio - TABLE-PROCEDURE
- Pin hit ratio - TRIGGER
- Pool dict cache
- Pool free mem
- Pool lib cache
- Pool misc
- Pool sql area
- Processes
- Session Active
- Session Inactive
- Sessions
- Session System
- SGA buffer cache
- SGA fixed
- SGA java pool
- SGA large pool
- SGA log buffer
- SGA shared pool
- Uptime
- Waits Controlfile I/O
- Waits direct path read
- Waits File I/O
- Waits Logsync
- Waits Logwrite
- Waits multiblock read
- Waits single block read
- Waits SQLNet
