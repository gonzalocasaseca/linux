# iptables

## Drop packages from one host

~~~bash
iptables -A INPUT -s 1.2.3.4 -j DROP
~~~
