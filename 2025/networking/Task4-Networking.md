# Network Commands Cheat Sheet

## 1. `ping` (Check Connectivity)
**Purpose:** Tests the reachability of a host on a network.

**Usage:**
```sh
ping <hostname or IP>
```

**Example:**
```sh
ping google.com
```
**Output:**
```
PING google.com (142.250.183.14): 56 data bytes
64 bytes from 142.250.183.14: icmp_seq=0 ttl=118 time=12.3 ms
```

## 2. `traceroute` / `tracert` (Trace Packet Routes)
**Purpose:** Displays the route packets take to a network destination.

**Usage:**
```sh
traceroute <hostname or IP>  # Linux/macOS
tracert <hostname or IP>     # Windows
```

**Example:**
```sh
traceroute google.com
```
**Output:**
```
1  192.168.1.1  1.23 ms  
2  10.0.0.1  5.67 ms  
3  142.250.183.14  12.34 ms  
```

## 3. `netstat` (Network Statistics)
**Purpose:** Displays active network connections and statistics.

**Usage:**
```sh
netstat -tulnp  # Linux/macOS
netstat -an     # Windows
```

**Example:**
```sh
netstat -tulnp
```
**Output:**
```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1234/sshd
```

## 4. `curl` (Make HTTP Requests)
**Purpose:** Transfers data from or to a server using various protocols (HTTP, HTTPS, FTP, etc.).

**Usage:**
```sh
curl <URL>
```

**Example:**
```sh
curl -I https://www.google.com
```
**Output:**
```
HTTP/2 200  
content-type: text/html; charset=ISO-8859-1  
```

## 5. `dig` / `nslookup` (DNS Lookup)
**Purpose:** Queries DNS servers for domain name records.

**Usage:**
```sh
dig <domain>        # Linux/macOS
nslookup <domain>   # Windows
```

**Example (`dig`):**
```sh
dig google.com
```
**Output:**
```
;; ANSWER SECTION:
google.com.   299  IN  A  142.250.183.14
```

**Example (`nslookup`):**
```sh
nslookup google.com
```
**Output:**
```
Server:  8.8.8.8  
Address: 8.8.8.8#53  

Non-authoritative answer:
Name: google.com  
Address: 142.250.183.14  
