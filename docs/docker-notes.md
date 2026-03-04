# Docker Notes - Day 9

## Docker Version
Client:
 Version:           29.2.1
 API version:       1.53
 Go version:        go1.25.6
 Git commit:        a5c7197
 Built:             Mon Feb  2 17:20:16 2026
 OS/Arch:           windows/amd64
 Context:           desktop-linux

Server: Docker Desktop 4.63.0 (220185)
 Engine:
  Version:          29.2.1
  API version:      1.53 (minimum version 1.44)
  Go version:       go1.25.6
  Git commit:       6bc6209
  Built:            Mon Feb  2 17:17:24 2026
  OS/Arch:          linux/amd64
  Experimental:     false

## Hello World Test
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
17eec7bbc9d7: Pull complete
ea52d2000f90: Download complete
Digest: sha256:ef54e839ef541993b4e87f25e752f7cf4238fa55f017957c2eb44077083d7a6a
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

## Postgres Container
Command used:
```bash
docker run -d \
  --name pg-prework \
  -e POSTGRES_PASSWORD=prework \
  -p 5432:5432 \
  postgres:15-alpine
```
## Startup Logs
 docker logs pg-prework
The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.utf8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/data ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... UTC
creating configuration files ... ok
running bootstrap script ... ok
sh: locale: not found
2026-03-04 19:08:09.829 UTC [35] WARNING:  no usable system locales were found
performing post-bootstrap initialization ... ok
syncing data to disk ... ok


Success. You can now start the database server using:

    pg_ctl -D /var/lib/postgresql/data -l logfile start

initdb: warning: enabling "trust" authentication for local connections
initdb: hint: You can change this by editing pg_hba.conf or using the option -A, or --auth-local and --auth-host, the next time you run initdb.
waiting for server to start....2026-03-04 19:08:10.591 UTC [41] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 19:08:10.595 UTC [41] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 19:08:10.605 UTC [44] LOG:  database system was shut down at 2026-03-04 19:08:10 UTC
2026-03-04 19:08:10.613 UTC [41] LOG:  database system is ready to accept connections
 done
server started

/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

waiting for server to shut down....2026-03-04 19:08:10.697 UTC [41] LOG:  received fast shutdown request
2026-03-04 19:08:10.701 UTC [41] LOG:  aborting any active transactions
2026-03-04 19:08:10.704 UTC [41] LOG:  background worker "logical replication launcher" (PID 47) exited with exit code 1
2026-03-04 19:08:10.704 UTC [42] LOG:  shutting down
2026-03-04 19:08:10.708 UTC [42] LOG:  checkpoint starting: shutdown immediate
2026-03-04 19:08:10.728 UTC [42] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.007 s, sync=0.003 s, total=0.025 s; sync files=2, longest=0.002 s, average=0.002 s; distance=0 kB, estimate=0 kB
2026-03-04 19:08:10.732 UTC [41] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-04 19:08:10.856 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 19:08:10.858 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 19:08:10.858 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 19:08:10.862 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 19:08:10.868 UTC [55] LOG:  database system was shut down at 2026-03-04 19:08:10 UTC
2026-03-04 19:08:10.875 UTC [1] LOG:  database system is ready to accept connections
0.025 s; sync files=2, longest=0.002 s, average=0.002 s; distance=0 kB, estimate=0 kB
2026-03-04 19:08:10.732 UTC [41] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-04 19:08:10.856 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 19:08:10.858 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 19:08:10.858 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 19:08:10.862 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 19:08:10.868 UTC [55] LOG:  database system was shut down at 2026-03-04 19:08:10 UTC
2026-03-04 19:08:10.875 UTC [1] LOG:  database system is ready to accept connections
PostgreSQL init process complete; ready for start up.

2026-03-04 19:08:10.856 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 19:08:10.858 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 19:08:10.858 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 19:08:10.862 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 19:08:10.868 UTC [55] LOG:  database system was shut down at 2026-03-04 19:08:10 UTC
2026-03-04 19:08:10.875 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 19:08:10.858 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 19:08:10.862 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 19:08:10.868 UTC [55] LOG:  database system was shut down at 2026-03-04 19:08:10 UTC
2026-03-04 19:08:10.875 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 19:08:10.868 UTC [55] LOG:  database system was shut down at 2026-03-04 19:08:10 UTC
2026-03-04 19:08:10.875 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 19:08:10.875 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 19:11:40.310 UTC [1] LOG:  received fast shutdown request
2026-03-04 19:11:40.314 UTC [1] LOG:  aborting any active transactions
2026-03-04 19:11:40.317 UTC [1] LOG:  background worker "logical replication launcher" (PID 58) exited with exit code 1
2026-03-04 19:11:40.317 UTC [53] LOG:  shutting down
2026-03-04 19:11:40.321 UTC [53] LOG:  checkpoint starting: shutdown immediate
2026-03-04 19:11:40.357 UTC [53] LOG:  checkpoint complete: wrote 43 buffers (0.3%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.009 s, sync=0.014 s, total=0.040 s; sync files=11, longest=0.005 s, average=0.002 s; distance=252 kB, estimate=252 kB
2026-03-04 19:11:40.361 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-04 19:11:51.706 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 19:11:51.707 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 19:11:51.707 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 19:11:51.712 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 19:11:51.720 UTC [30] LOG:  database system was shut down at 2026-03-04 19:11:40 UTC
2026-03-04 19:11:51.728 UTC [1] LOG:  database system is ready to accept connections

## Stop and Restart
> docker stop pg-prework
pg-prework

> docker restart pg-prework
pg-prework

> docker logs pg-prework
2026-03-04 19:11:40.310 UTC [1] LOG:  received fast shutdown request
2026-03-04 19:11:40.314 UTC [1] LOG:  aborting any active transactions
2026-03-04 19:11:40.317 UTC [53] LOG:  shutting down
2026-03-04 19:11:40.321 UTC [53] LOG:  checkpoint starting: shutdown immediate
2026-03-04 19:11:40.357 UTC [53] LOG:  checkpoint complete: wrote 43 buffers (0.3%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.009 s, sync=0.014 s, total=0.040 s; sync files=11, longest=0.005 s, average=0.002 s; distance=252 kB, estimate=252 kB
2026-03-04 19:11:40.361 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-04 19:11:51.706 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 19:11:51.707 LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 19:11:51.720 UTC [30] LOG:  database system was shut down at 2026-03-04 19:11:40 UTC
2026-03-04 19:11:51.728 UTC [1] LOG:  database system is ready to accept connections

## Issues Encountered
Windows WSL2 backend does not show the Resources slider in Docker Desktop. I resolved this by creating a .wslconfig file in my user directory and setting memory=4GB to meet the program requirements.