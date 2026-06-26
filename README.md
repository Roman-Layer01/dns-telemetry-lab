# DNS Telemetry Lab – Raspberry Pi Network Detection Pipeline

## Objective
Build a network telemetry pipeline using Raspberry Pi devices to capture DNS activity, monitor network behavior, and implement alerting for suspicious or unauthorized activity.

---

## Lab Architecture

Client Devices (Windows / Lab Machines)  
↓  
Pi-hole (DNS Sinkhole + Logging)  
↓  
Docker (Containerized Services on Pi 5)  
↓  
Portainer (Container Management)  
↓  
Future: Elastic Stack (SIEM Integration)  

---

## Environment

- Raspberry Pi 3B+ (initial DNS server)
- Raspberry Pi 5 (upgraded telemetry node)
- Raspberry Pi OS (Linux)
- Docker (container runtime)
- Portainer (container management UI)
- Pi-hole (DNS server and logging platform)

---

## Lab Evolution

### Initial Deployment (Raspberry Pi 3B+)

- Deployed Pi-hole on Raspberry Pi 3B+ as a dedicated DNS sinkhole
- Configured local network devices to use Pi-hole for DNS resolution
- Verified DNS query logging and visibility into outbound connections

This deployment provided baseline DNS telemetry and introduced network monitoring concepts.

---

### Upgraded Telemetry Node (Raspberry Pi 5)

- Migrated environment to Raspberry Pi 5 for improved performance and scalability
- Installed Docker to support containerized services
- Deployed Portainer for web-based container management
- Prepared platform for running multiple monitoring and detection services

This upgrade transitioned the lab from a single-use DNS server into a scalable network telemetry node.

---

## Implementation

### Container Infrastructure (Pi 5)

- Installed Docker and configured user permissions
- Deployed Portainer for centralized container management
- Verified container creation, lifecycle management, and networking

---

### DNS Telemetry (Pi-hole)

#### Objective
Capture and analyze DNS queries across the network to understand outbound connectivity and detect suspicious activity.

#### Deployment
- Deployed Pi-hole as the primary DNS resolver
- Routed client DNS traffic through Pi-hole
- Verified successful query logging via Pi-hole dashboard

---

## Network Monitoring & Alerting

### New Device Detection

#### Objective
Identify when new or unknown devices connect to the network.

#### Implementation
- Leveraged Pi-hole visibility into client IPs and DNS activity
- Monitored for new client entries in DNS logs
- Established process to identify previously unseen devices

---

### Email Alerting

#### Objective
Receive real-time notifications when new devices appear on the network.

#### Implementation
- Configured alerting mechanism integrated with Pi-hole monitoring
- Triggered email notifications when new network clients are detected
- Validated successful alert delivery through testing

---

## Data Visibility

Pi-hole provides insight into:

- DNS queries per client
- Top requested domains
- Blocked vs allowed traffic
- Query frequency and timestamps

This enables baseline network behavior analysis and anomaly detection.

---

## Detection Opportunities

### Potential Use Cases

- Detect repeated DNS queries (possible beaconing behavior)
- Identify unusual or suspicious domain requests
- Monitor spikes in DNS traffic volume
- Detect new or unauthorized devices on the network
- Identify rare or newly observed domains

---

## Future SIEM Integration

### Planned Pipeline

DNS Logs (Pi-hole)  
→ Log Forwarder (Filebeat / syslog)  
→ Elasticsearch  
→ Kibana  

---

## Correlation Strategy (Planned)

Combine DNS telemetry with endpoint logs:

- Correlate DNS queries with PowerShell activity
- Identify command execution followed by outbound connections
- Detect potential command-and-control (C2) behavior
- Link process activity to network communication

---

## Troubleshooting & Lessons Learned

- DNS logging provides high-value visibility with minimal overhead
- Containerization greatly improves flexibility and scalability
- Monitoring network devices provides early detection opportunities
- Alerting on environmental changes (e.g., new devices) is a practical security control

---

## Key Lessons Learned

- DNS is a critical telemetry source for detecting malicious activity
- Network-level monitoring complements endpoint detection strategies
- Infrastructure upgrades (Pi 3 → Pi 5) enable scalability and flexibility
- Effective detection engineering requires combining multiple data sources
- Simple alerting mechanisms (e.g., new device detection) can provide immediate security value

---

## Current Status

✅ Pi-hole DNS logging operational  
✅ Raspberry Pi 5 telemetry node deployed  
✅ Docker and Portainer functioning  
✅ New device detection implemented  
✅ Email alerting for network changes working  

---

## Next Steps

- Forward DNS logs to Elastic Stack  
- Build DNS-based detection rules  
- Correlate DNS + endpoint activity  
- Simulate suspicious domains and beaconing behavior  
- Expand alerting for abnormal DNS activity  

