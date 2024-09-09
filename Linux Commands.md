
## ss Command in Debian Systems

In Debian-based systems, the `ss` command is part of the `iproute2` package. It is included by default, but if not installed, it can be added using the following command:

```bash
sudo apt-get install iproute2
```

### Syntax

```bash
ss [options] [filter]
```

### 1. Installing ss Command

The `ss` command is part of the `iproute2` package, which is typically pre-installed on most modern Linux distributions. If not installed, use the package manager to install it:

- For Debian-based systems (like Ubuntu), run:

```bash
sudo apt-get install iproute2
```

### 2. Basic Usage

The basic syntax of the `ss` command is:

```bash
ss [options] [filter]
```

Where `options` are command-line options, and `filter` is an expression used to filter the output. Common options include:

- `-n`, `--numeric`: Show addresses and ports in numeric format.
- `-t`, `--tcp`: Show only TCP socket information.
- `-u`, `--udp`: Show only UDP socket information.
- `-l`, `--listening`: Show only sockets in the listening state.
- `-a`, `--all`: Show all socket information, both listening and non-listening.
- `-r`, `--resolve`: Attempt to resolve service names to hostnames.
- `-p`, `--processes`: Show process information (PID and name) associated with each socket.
- `-e`, `--extended`: Show detailed TCP socket information.
- `-s`, `--summary`: Show socket statistics summary.

### 2.1 View All Sockets

Without any options, `ss` displays all types of sockets:

```bash
ss
```

### 2.2 View Specific Types of Sockets

You can filter sockets by type using options like `-t` (TCP), `-u` (UDP), or `-a` (all sockets):

```bash
ss -t    # Display only TCP sockets
ss -u    # Display only UDP sockets
ss -a    # Display all types of sockets
```

### 2.3 View Listening Ports

To view sockets in the listening state, use the `-l` option:

```bash
ss -l
```

### 2.4 View Specific Ports

You can filter sockets by port using the `-p` option. For example, to see sockets on port 8080:

```bash
ss -lnp | grep :8080
```

Explanation of options:

- `-l`: Show listening sockets.
- `-n`: Show numeric addresses and ports.
- `-p`: Display process information.

To view only TCP or UDP sockets for a specific port:

```bash
ss -tlnp | grep :8080  # TCP
ss -ulnp | grep :8080  # UDP
```

### 2.5 View Detailed Socket Information

Use the `-o` option to view detailed information about sockets, such as state and buffer sizes:

```bash
ss -o state established '( dport = :22 or sport = :22 )'
```

### 2.6 View Sockets by Specific State

Filter sockets by their state using the `state` option, such as `established` or `listen`:

```bash
ss state established
```

### 2.7 Resolve IP and Port Names

The `-r` option resolves service names to hostnames when displaying TCP protocol sockets:

```bash
ss -tlr
```

### 2.8 Local and Destination Address Filters

To match specific local or remote addresses and ports:

- Match local address and port:

  ```bash
  ss src 192.168.2.152
  ```

- Match remote address and port:

  ```bash
  ss dst 192.168.2.152
  ss dst 192.168.2.153:50460
  ss dst 192.168.2.153:mysql
  ```

### 2.9 Filter by TCP State

The `ss` command can filter connections by TCP state, such as `established`, `fin-wait-1`, `listen`, etc.

- List all TCP sockets in the `FIN-WAIT-1` state for source ports 80 or 443 and destination network `192.168.2/24`:

  ```bash
  ss -o state FIN-WAIT-1 dst 192.168.2/24
  ```

- Show all established HTTP connections:

  ```bash
  ss state listening '( sport = :http or dport = :http )'
  ```

- IPv4 filtering:

  ```bash
  ss -4n state listening
  ```

### 2.10 List All Connections and Listens on Port 2181

To list all connections to and from port 2181:

```bash
ss -r state all dport = :2181
```

### Conclusion

The `ss` command is a powerful tool that provides in-depth insights into network sockets on a Linux system. By using a variety of options and filters, you can quickly retrieve the network information you need, enabling you to manage and troubleshoot network connections more effectively.

For more detailed usage, consult the help options:

```bash
ss --help
```
