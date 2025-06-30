# NIST Cybersecurity Framework 2.0 Golden Configurations

This repository contains enterprise-grade golden configuration templates implementing the NIST Cybersecurity Framework (CSF) 2.0 for network infrastructure security. These configurations are designed for production deployment on Cisco IOS devices with comprehensive security controls aligned to the six CSF functions.

## Overview

The NIST CSF 2.0, released in February 2024, provides a comprehensive approach to managing cybersecurity risk through six core functions:

- **Govern (GV)** - Cybersecurity governance and risk management
- **Identify (ID)** - Asset management and risk assessment  
- **Protect (PR)** - Implementation of appropriate safeguards
- **Detect (DE)** - Timely discovery of cybersecurity events
- **Respond (RS)** - Response activities for detected incidents
- **Recover (RC)** - Resilience and recovery activities

## Repository Structure

```
├── configs/
│   ├── access-control/           # Identity and access management controls
│   ├── network-segmentation/     # Network isolation and microsegmentation
│   ├── data-protection/          # Data security and encryption controls
│   └── logging-monitoring/       # Security monitoring and detection
├── variables/
│   ├── production.yml           # Production environment variables
│   ├── staging.yml              # Staging environment variables
│   └── development.yml          # Development environment variables
├── scripts/
│   ├── deploy.py               # Automated deployment script
│   ├── validate.py             # Configuration validation
│   └── backup.py               # Configuration backup utility
├── docs/
│   ├── implementation-guide.md  # Detailed implementation guide
│   ├── compliance-mapping.md    # CSF control mappings
│   └── troubleshooting.md       # Common issues and solutions
└── tests/
    ├── unit/                   # Unit tests for configurations
    └── integration/            # Integration tests
```

## Quick Start

### Prerequisites
- Cisco IOS devices (12.4 or later)
- Network management access (SSH/Console)
- Centralized logging server (syslog)
- NTP server for time synchronization
- SNMP monitoring system

### Basic Deployment

1. **Clone the repository:**
   ```bash
   git clone https://github.com/keepithuman/nist-csf-2.0-golden-configs.git
   cd nist-csf-2.0-golden-configs
   ```

2. **Update variables for your environment:**
   ```bash
   cp variables/production.yml.example variables/production.yml
   # Edit variables/production.yml with your specific values
   ```

3. **Deploy configurations:**
   ```bash
   python scripts/deploy.py --environment production --device-type cisco-ios
   ```

## Configuration Components

### Access Control (PR.AC)
- Role-based authentication with AAA
- Privilege level separation
- Strong password policies
- SSH-only access with key-based authentication
- Session timeout and automatic logoff
- Legal banners and access notifications

### Network Segmentation (PR.AC, PR.PT)
- VLAN-based microsegmentation
- Access Control Lists (ACLs) for traffic control
- Inter-VLAN communication restrictions
- DMZ and production environment isolation
- Port security with MAC address learning

### Data Protection (PR.DS)
- Encryption for management protocols
- Secure SNMP configuration
- Protected configuration storage
- Secure backup procedures
- Time synchronization with NTP authentication

### Logging and Monitoring (DE.CM, DE.AE)
- Centralized syslog with detailed timestamps
- SNMP monitoring with security traps
- NetFlow traffic analysis
- Configuration change tracking
- Automated incident response scripts
- Security event correlation

## Environment Variables

The following variables must be configured for your environment:

| Variable | Description | Example |
|----------|-------------|---------|
| `organization_name` | Your organization name | "ExampleCorp" |
| `domain_name` | Domain name for certificates | "example.com" |
| `syslog_server` | Centralized logging server | "10.1.100.10" |
| `ntp_server1` | Primary NTP server | "time.nist.gov" |
| `mgmt_vlan` | Management VLAN ID | "100" |
| `enable_secret` | Enable password (encrypted) | "C1sc0Secure123!" |

## NIST CSF 2.0 Compliance Mapping

### Govern (GV)
- **GV.OC-01**: Cybersecurity policy framework
- **GV.RM-01**: Risk management strategy integration
- **GV.SC-01**: Supply chain risk management

### Identify (ID)
- **ID.AM-01**: Physical devices and systems inventory
- **ID.AM-02**: Software platforms and applications inventory
- **ID.RA-01**: Asset vulnerabilities identification

### Protect (PR)
- **PR.AC-01**: Identity and credential management
- **PR.AC-04**: Access permissions and authorizations
- **PR.DS-01**: Data-at-rest protection
- **PR.PT-01**: Audit/log records determination

### Detect (DE)
- **DE.AE-01**: Baseline of network operations
- **DE.CM-01**: Network monitoring performance
- **DE.DP-01**: Role-based detection processes

### Respond (RS)
- **RS.RP-01**: Response plan execution
- **RS.CO-01**: Personnel response coordination
- **RS.AN-01**: Notifications from detection systems

### Recover (RC)
- **RC.RP-01**: Recovery plan execution
- **RC.IM-01**: Recovery activities coordination
- **RC.CO-01**: Public relations management

## Security Features

### Network Security Controls
- **Access Control Lists**: Granular traffic filtering based on source, destination, and service
- **Port Security**: MAC address learning and violation responses
- **Storm Control**: Broadcast/multicast traffic rate limiting
- **DHCP Snooping**: Protection against rogue DHCP servers
- **Dynamic ARP Inspection**: ARP packet validation

### Management Security
- **SSH Only Access**: Disabled Telnet and HTTP services
- **Certificate-Based Authentication**: RSA 2048-bit keys
- **Session Management**: Automatic timeout and absolute session limits
- **Command Authorization**: Role-based command execution
- **Configuration Archive**: Automatic backup with change notifications

### Monitoring and Alerting
- **Real-time Monitoring**: SNMP traps for security events
- **Traffic Analysis**: NetFlow collection for anomaly detection
- **Event Correlation**: EEM scripts for automated response
- **Audit Trails**: Comprehensive logging of all activities

## Deployment Guide

### Pre-Deployment Checklist
- [ ] Network topology documented
- [ ] IP addressing scheme finalized
- [ ] VLAN assignments planned
- [ ] Monitoring infrastructure ready
- [ ] Backup procedures tested
- [ ] Change management approval obtained

### Deployment Steps
1. **Environment Preparation**
2. **Variable Configuration**
3. **Pilot Deployment**
4. **Testing and Validation**
5. **Production Rollout**
6. **Post-Deployment Verification**

### Validation Tests
- [ ] Administrative access functionality
- [ ] Network segmentation enforcement
- [ ] Logging data collection
- [ ] Monitoring alert generation
- [ ] Incident response procedures

## Maintenance

### Regular Tasks
- **Weekly**: Review security logs and alerts
- **Monthly**: Update access control lists
- **Quarterly**: Security assessment and penetration testing
- **Annually**: Framework review and updates

### Updates and Patches
- Monitor NIST CSF updates and guidance
- Apply security patches following change management
- Update configurations based on threat intelligence
- Maintain compliance documentation

## Support and Resources

### Documentation
- [NIST CSF 2.0 Official Documentation](https://www.nist.gov/cyberframework)
- [Cisco IOS Security Configuration Guide](https://cisco.com/security)
- [Implementation Guide](docs/implementation-guide.md)

### Community
- [NIST CSF Community](https://www.nist.gov/cyberframework/community)
- [Cisco Security Community](https://community.cisco.com/security)

### Professional Services
For implementation assistance, contact:
- Enterprise Architecture Team
- Network Security Team
- Compliance and Risk Management

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Disclaimer

These configurations are provided as templates and should be thoroughly tested in your environment before production deployment. Security requirements may vary based on your specific infrastructure and compliance needs.

---

**Last Updated**: June 30, 2025  
**Version**: 1.0  
**NIST CSF Version**: 2.0
