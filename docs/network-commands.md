# Network Commands & Security Tools

## Network Configuration

### Interface Management
```bash
# Modern network tools (ip command)
ip addr show                        # Show all interfaces
ip addr show eth0                   # Show specific interface
ip link show                        # Show link layer info
ip route show                       # Show routing table
ip route add default via 192.168.1.1  # Add default route
ip route del 192.168.1.0/24         # Delete route

# Legacy tools (still widely used)
ifconfig                            # Show all interfaces
ifconfig eth0                       # Show specific interface
ifconfig eth0 up                    # Bring interface up
ifconfig eth0 down                  # Bring interface down
ifconfig eth0 192.168.1.100 netmask 255.255.255.0  # Set IP

# Network interface control
sudo ip link set eth0 up            # Bring interface up
sudo ip link set eth0 down          # Bring interface down
sudo ip addr add 192.168.1.100/24 dev eth0  # Add IP address
sudo ip addr del 192.168.1.100/24 dev eth0  # Remove IP address
```

### Wireless Networking
```bash
# Wireless tools
iwconfig                            # Wireless interface configuration
iwlist scan                         # Scan for wireless networks
iwlist eth1 scan | grep ESSID       # List network names
iw dev                              # Show wireless devices
iw dev wlan0 scan                   # Scan with iw command

# NetworkManager (Ubuntu/Debian)
nmcli dev status                    # Show device status
nmcli con show                      # Show connections
nmcli con up "WiFi-Name"            # Connect to WiFi
nmcli dev wifi list                 # List available WiFi
nmcli dev wifi connect "SSID" password "password"  # Connect to WiFi

# WPA Supplicant
wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf
wpa_cli                             # Interactive WPA client
```

## Network Diagnostics

### Connectivity Testing
```bash
# Basic connectivity
ping google.com                     # Test connectivity
ping -c 4 google.com                # Ping 4 times only
ping -i 0.2 google.com              # Ping every 0.2 seconds
ping6 ipv6.google.com               # IPv6 ping

# Advanced ping options
ping -f google.com                  # Flood ping (root only)
ping -s 1024 google.com             # Large packet size
ping -W 1 google.com                # 1 second timeout

# Traceroute
traceroute google.com               # Trace route to destination
traceroute -n google.com            # Don't resolve hostnames
tracepath google.com                # Alternative traceroute
mtr google.com                      # Continuous traceroute
mtr --report google.com             # Generate report
```

### DNS Resolution
```bash
# DNS lookup tools
nslookup google.com                 # Basic DNS lookup
nslookup google.com 8.8.8.8         # Use specific DNS server

# Dig (more detailed)
dig google.com                      # DNS query
dig @8.8.8.8 google.com             # Use specific DNS server
dig google.com MX                   # Query MX records
dig google.com NS                   # Query name servers
dig google.com ANY                  # Query all records
dig -x 8.8.8.8                     # Reverse DNS lookup

# Host command
host google.com                     # Simple DNS lookup
host -t MX google.com               # Query MX records
host -a google.com                  # All records
```

### Port and Service Scanning
```bash
# Netstat (show network connections)
netstat -tuln                       # Show listening ports
netstat -tulpn                      # Show with process names
netstat -an                         # All connections
netstat -rn                         # Routing table
netstat -i                          # Interface statistics

# SS (modern replacement for netstat)
ss -tuln                            # Show listening ports
ss -tulpn                           # Show with process names
ss -an                              # All connections
ss -s                               # Summary statistics
ss -o state established             # Show established connections

# Nmap (network scanner)
nmap localhost                      # Scan local ports
nmap 192.168.1.1                   # Scan specific host
nmap 192.168.1.0/24                # Scan network range
nmap -sV localhost                  # Service version detection
nmap -O localhost                   # OS detection
nmap -A localhost                   # Aggressive scan
nmap -p 80,443 google.com           # Scan specific ports
nmap -p- localhost                  # Scan all ports
```

## Network Monitoring

### Traffic Analysis
```bash
# TCPDump (packet capture)
tcpdump -i eth0                     # Capture on interface
tcpdump -i any                      # Capture on all interfaces
tcpdump host google.com             # Capture traffic to/from host
tcpdump port 80                     # Capture HTTP traffic
tcpdump -w capture.pcap             # Write to file
tcpdump -r capture.pcap             # Read from file
tcpdump -n -i eth0 'port 22'        # SSH traffic, no DNS resolution

# Wireshark (GUI packet analyzer)
wireshark                           # Launch GUI
tshark -i eth0                      # Command-line version
tshark -i eth0 -w capture.pcap      # Capture to file
tshark -r capture.pcap              # Read from file

# Network usage monitoring
iftop                               # Network usage by connection
iftop -i eth0                       # Monitor specific interface
nethogs                             # Network usage by process
nethogs eth0                        # Monitor specific interface
bandwhich                           # Modern network monitor
vnstat                              # Network statistics
vnstat -i eth0                      # Interface statistics
```

### Bandwidth Testing
```bash
# Iperf (bandwidth testing)
iperf3 -s                           # Start server
iperf3 -c server_ip                 # Connect as client
iperf3 -c server_ip -t 30           # Test for 30 seconds
iperf3 -c server_ip -P 4            # 4 parallel streams

# Speedtest
speedtest-cli                       # Command-line speed test
curl -s https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python -
```

## Firewall Management

### UFW (Uncomplicated Firewall)
```bash
# Basic UFW commands
sudo ufw status                     # Check firewall status
sudo ufw enable                     # Enable firewall
sudo ufw disable                    # Disable firewall
sudo ufw reset                      # Reset to defaults

# Allow/deny rules
sudo ufw allow 22                   # Allow SSH
sudo ufw allow ssh                  # Allow SSH (by name)
sudo ufw allow 80/tcp               # Allow HTTP
sudo ufw allow from 192.168.1.0/24 # Allow from subnet
sudo ufw deny 23                    # Deny telnet
sudo ufw delete allow 80            # Delete rule

# Advanced rules
sudo ufw allow from 192.168.1.100 to any port 22  # Specific source
sudo ufw limit ssh                  # Rate limiting
sudo ufw --dry-run allow http       # Test rule without applying
```

### Iptables (Advanced Firewall)
```bash
# List rules
iptables -L                         # List all rules
iptables -L -n                      # List without resolving names
iptables -L -v                      # Verbose listing
iptables -t nat -L                  # List NAT table

# Basic rules
iptables -A INPUT -p tcp --dport 22 -j ACCEPT     # Allow SSH
iptables -A INPUT -p tcp --dport 80 -j ACCEPT     # Allow HTTP
iptables -A INPUT -j DROP           # Drop all other input
iptables -I INPUT 1 -i lo -j ACCEPT # Allow loopback (insert at top)

# Delete rules
iptables -D INPUT -p tcp --dport 80 -j ACCEPT     # Delete specific rule
iptables -F                         # Flush all rules
iptables -F INPUT                   # Flush INPUT chain

# Save/restore rules
iptables-save > /etc/iptables/rules.v4           # Save rules
iptables-restore < /etc/iptables/rules.v4        # Restore rules
```

## SSH and Remote Access

### SSH Client
```bash
# Basic SSH
ssh user@hostname                   # Connect to remote host
ssh -p 2222 user@hostname           # Connect to specific port
ssh -i ~/.ssh/private_key user@host # Use specific key
ssh -X user@hostname                # Enable X11 forwarding
ssh -L 8080:localhost:80 user@host  # Local port forwarding
ssh -R 8080:localhost:80 user@host  # Remote port forwarding
ssh -D 1080 user@hostname           # SOCKS proxy

# SSH key management
ssh-keygen -t rsa -b 4096           # Generate RSA key
ssh-keygen -t ed25519               # Generate Ed25519 key
ssh-copy-id user@hostname           # Copy public key to remote
ssh-add ~/.ssh/private_key          # Add key to agent
ssh-agent bash                      # Start SSH agent

# SSH configuration (~/.ssh/config)
Host myserver
    HostName 192.168.1.100
    User myuser
    Port 2222
    IdentityFile ~/.ssh/mykey
```

### SSH Server Configuration
```bash
# SSH server control
sudo systemctl status ssh           # Check SSH service status
sudo systemctl start ssh            # Start SSH service
sudo systemctl enable ssh           # Enable SSH at boot
sudo systemctl reload ssh           # Reload configuration

# SSH security hardening (/etc/ssh/sshd_config)
# PermitRootLogin no
# PasswordAuthentication no
# PubkeyAuthentication yes
# Port 2222
# AllowUsers myuser
```

## Network Security Tools

### Network Scanning and Reconnaissance
```bash
# Nmap advanced scanning
nmap -sS target                     # SYN scan (stealth)
nmap -sU target                     # UDP scan
nmap -sN target                     # NULL scan
nmap -sF target                     # FIN scan
nmap -sX target                     # Xmas scan
nmap --script vuln target           # Vulnerability scan
nmap --script=http-enum target      # HTTP enumeration

# Masscan (fast port scanner)
masscan -p1-65535 192.168.1.0/24 --rate=1000

# Zmap (Internet-wide scanner)
zmap -p 80 -o results.txt 10.0.0.0/8
```

### Web Security Testing
```bash
# Nikto (web vulnerability scanner)
nikto -h http://target.com          # Basic web scan
nikto -h http://target.com -p 80,443 # Multiple ports

# Dirb/Dirbuster (directory brute force)
dirb http://target.com              # Directory enumeration
dirb http://target.com /usr/share/dirb/wordlists/common.txt

# Gobuster (fast directory/file brute forcer)
gobuster dir -u http://target.com -w /usr/share/wordlists/dirb/common.txt
gobuster dns -d target.com -w /usr/share/wordlists/subdomains.txt
```

### SSL/TLS Testing
```bash
# OpenSSL testing
openssl s_client -connect google.com:443  # Test SSL connection
openssl s_client -connect google.com:443 -servername google.com  # SNI
echo | openssl s_client -connect google.com:443 2>/dev/null | openssl x509 -noout -dates

# SSLyze (SSL configuration scanner)
sslyze google.com:443

# Testssl.sh (comprehensive SSL tester)
./testssl.sh google.com
```

## VPN and Tunneling

### OpenVPN
```bash
# OpenVPN client
openvpn --config client.ovpn        # Connect with config file
openvpn --daemon --config client.ovpn  # Run as daemon

# OpenVPN server management
systemctl status openvpn@server     # Check server status
systemctl start openvpn@server      # Start server
```

### WireGuard
```bash
# WireGuard management
wg show                             # Show WireGuard interfaces
wg-quick up wg0                     # Bring up interface
wg-quick down wg0                   # Bring down interface
wg genkey | tee private.key | wg pubkey > public.key  # Generate keys
```

## Network File Systems

### NFS (Network File System)
```bash
# NFS client
showmount -e nfs-server             # Show exports
mount -t nfs nfs-server:/path /mnt  # Mount NFS share
umount /mnt                         # Unmount

# NFS server
exportfs -a                         # Export all filesystems
exportfs -r                         # Re-export filesystems
exportfs -v                         # Verbose export list
```

### SMB/CIFS
```bash
# SMB client (smbclient)
smbclient -L //server              # List shares
smbclient //server/share            # Connect to share
smbclient //server/share -U username # Connect with username

# Mount SMB share
mount -t cifs //server/share /mnt -o username=user,password=pass
mount -t cifs //server/share /mnt -o credentials=/path/to/creds
```

## Network Troubleshooting

### Common Network Issues
```bash
# Check network connectivity
ping -c 1 8.8.8.8                  # Test internet connectivity
ping -c 1 $(ip route | grep default | awk '{print $3}')  # Test gateway

# DNS troubleshooting
cat /etc/resolv.conf                # Check DNS servers
dig @8.8.8.8 google.com             # Test specific DNS server
nslookup google.com                 # Basic DNS test

# Route troubleshooting
ip route show                       # Show routing table
traceroute 8.8.8.8                 # Trace route to destination
mtr --report-cycles 10 8.8.8.8     # Network quality report

# Interface troubleshooting
ethtool eth0                        # Check interface details
dmesg | grep eth0                   # Check kernel messages
cat /sys/class/net/eth0/carrier     # Check link status
```

### Performance Analysis
```bash
# Network performance
iperf3 -c iperf.he.net              # Test bandwidth to public server
curl -w "@curl-format.txt" -o /dev/null -s "http://wordpress.com/"  # HTTP timing

# Packet loss testing
ping -c 100 8.8.8.8 | tail -1      # Packet loss summary
mtr --report --report-cycles 100 8.8.8.8  # Detailed loss report
```

## Network Aliases and Shortcuts

### Useful Aliases
```bash
# Add to ~/.bashrc or ~/.zshrc
alias ports='netstat -tulanp'
alias listening='ss -tuln'
alias portscan='nmap -sS -O'
alias myip='curl -s ifconfig.me'
alias localip='ip route get 1 | awk "{print \$NF;exit}"'
alias netinfo='ip addr show && echo && ip route show'
alias pingtest='ping -c 4 8.8.8.8'
alias dnstest='dig @8.8.8.8 google.com'

# Functions
netcheck() {
    echo "=== Network Connectivity Check ==="
    ping -c 3 8.8.8.8
    echo "=== DNS Resolution Check ==="
    nslookup google.com
    echo "=== Route Check ==="
    ip route show
}

portscan() {
    nmap -sS -O ${1:-localhost}
}
```

This comprehensive network and security reference covers essential tools for network administration, troubleshooting, and security testing.
