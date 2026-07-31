# 📘 Day 15 – Defense in Depth for Industrial Control Systems

## 🎯 Learning Objective

Understand the **Defense in Depth** security strategy and learn why industrial control systems rely on multiple layers of protection instead of a single security control.

---

# 📖 What is Defense in Depth?

Defense in Depth is a cybersecurity strategy that uses **multiple independent security layers** to protect industrial systems.

Instead of relying on one security control, multiple safeguards work together so that if one layer fails, others continue protecting the system.

This approach is considered a best practice for securing SCADA and Industrial Control Systems (ICS).

---

# 🤔 Why is Defense in Depth Important?

Industrial systems control critical infrastructure such as:

- Power Plants
- Water Treatment Facilities
- Oil & Gas Pipelines
- Manufacturing Plants
- Transportation Systems

A single vulnerability should never allow an attacker to compromise an entire industrial process.

Defense in Depth helps reduce that risk.

---

# 🛡️ Security Layers

## 1. Physical Security

Protect industrial equipment from unauthorized physical access.

Examples:

- Locked control rooms
- Security cameras
- Access cards
- Security guards

---

## 2. Network Security

Protect communication between industrial devices.

Examples:

- Firewalls
- VLANs
- Network segmentation
- Secure VPNs

---

## 3. Endpoint Security

Protect industrial computers and servers.

Examples:

- Antivirus
- Endpoint Detection and Response (EDR)
- Operating system updates
- Application whitelisting

---

## 4. Identity and Access Management

Ensure only authorized users can access industrial systems.

Examples:

- Strong passwords
- Multi-factor authentication (MFA)
- Role-based access control (RBAC)
- Least privilege principle

---

## 5. Monitoring and Detection

Continuously monitor the network for suspicious activity.

Examples:

- Security logs
- Intrusion Detection Systems (IDS)
- Security Information and Event Management (SIEM)
- Industrial anomaly detection

---

## 6. Backup and Recovery

Prepare for equipment failures and cyber incidents.

Examples:

- Configuration backups
- PLC program backups
- Disaster recovery plans
- Regular backup testing

---

# 🏭 Industrial Security Zones

Industrial environments are often divided into security zones.

```text
           Corporate IT Network
                    │
              Enterprise Firewall
                    │
                 DMZ Zone
                    │
            Industrial Firewall
                    │
          SCADA / Control Network
                    │
          PLCs • RTUs • HMIs
                    │
             Field Devices
```

Each layer limits how traffic moves between different parts of the network.

---

# 🌍 Real-World Example

Imagine an engineer accidentally opens a malicious email.

If Defense in Depth is properly implemented:

- Email filtering may block the message.
- Endpoint protection may stop the malware.
- Firewalls may prevent it from reaching the OT network.
- Network segmentation limits its movement.
- Monitoring tools generate alerts.
- Backups allow systems to recover if needed.

Multiple layers reduce the chance of a successful attack.

---

# 💡 Key Takeaways

- Defense in Depth uses multiple security layers.
- No single security control is enough.
- Physical security is just as important as cybersecurity.
- Network segmentation reduces cyber risk.
- Monitoring and backups improve resilience.

---

# 🛠️ Practical Exercise

Imagine you are securing a small manufacturing plant.

Answer the following:

1. What physical security measures would you implement?
2. How would you separate the IT and OT networks?
3. Which users should have administrator access?
4. Why are backups important?

Write your answers before moving to Day 16.

---

# 📝 Knowledge Check

1. What is Defense in Depth?

2. Why shouldn't industrial systems rely on a single security control?

3. Name four layers of Defense in Depth.

4. What is the purpose of a DMZ?

5. Why is network segmentation important?

---

# 📚 References

- NIST SP 800-82 – Guide to Industrial Control Systems (ICS) Security
- ISA/IEC 62443 Series – Industrial Automation and Control Systems Security
- CISA – Industrial Control Systems Security Resources
- SANS Institute – ICS Security
- MITRE ATT&CK for ICS

---

# ⏭️ Next Lesson

**Day 16 – The Purdue Enterprise Reference Architecture (PERA)**

We'll explore:

- What the Purdue Model is
- The six levels of industrial networks
- IT vs OT separation
- DMZ placement
- Why the Purdue Model remains important in industrial cybersecurity

---

> **"Strong security isn't built with one wall—it's built with many layers working together."**
