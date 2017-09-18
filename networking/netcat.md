# netcat

## Check if an UDP port is open

~~~bash
nc -z -v -u 1.2.3.4 2049
-u                      UDP mode
-z                      zero-I/O mode [used for scanning]
-v                      verbose [use twice to be more verbose]
~~~
