# Privacy & Anonymity Guide

> **Scope:** This repository documents best practices for achieving the highest practical level of digital privacy and anonymity using consumer hardware and open-source software.
>
> **Non-goals:** This guide does **not** guarantee protection against targeted nation-state adversaries, physical compromise, or illegal activity. It focuses on defense against ISPs, advertisers, data brokers, mass surveillance, and opportunistic attacks.

---

## 1. Threat Modeling

Privacy begins with understanding your adversary.

### Covered Adversaries
- Internet Service Providers (ISPs)
- Websites and tracking networks
- Advertising platforms
- Data brokers
- Local network attackers
- Mass, non-targeted surveillance

### Not Fully Covered
- Targeted nation-state operations
- Physical device seizure
- Supply-chain compromise
- Zero-day exploitation

Privacy is layered. No single tool is sufficient.

---

## 2. Hardware Strategy

### 2.1 Dedicated Privacy Hardware

Recommended characteristics:
- Old laptop (preferably pre-2018)
- Mechanical HDD (no SSD)
- No biometric hardware
- No discrete GPU
- Minimal peripherals

Why avoid SSDs:
- Wear-leveling prevents reliable erasure
- Data remnants persist after formatting
- Destruction is difficult to verify

Rules:
- Never log into real-identity accounts
- Never reuse for personal computing
- Never connect to cloud services

---

### 2.2 Firmware & BIOS

- Update BIOS if possible
- Disable:
  - Secure Boot (unless required)
  - Intel AMT / ME (if supported)
  - Bluetooth
  - Webcam (or physically remove)
  - Thunderbolt
- Set a strong BIOS password

---

## 3. Operating Systems

### 3.1 Tails OS (Maximum Anonymity)

Use case: High-risk or short-lived sessions

Properties:
- Runs from USB
- Tor-enforced networking
- RAM wiped on shutdown
- No logs by default

Limitations:
- Not suitable for daily use
- Limited software persistence
- Slower performance

---

### 3.2 Linux (Daily Privacy OS)

Recommended distributions:
- Debian (minimal)
- Fedora (SELinux enabled)
- Arch Linux (advanced users)

Avoid:
- Ubuntu (telemetry history)
- Any distro requiring online accounts

Disk setup:
- Full disk encryption (LUKS)
- Strong passphrase (20+ characters)

---

## 4. MAC Address Management

### 4.1 Verify MAC Randomization

```bash
ip link show
```

---

### 4.2 Manual MAC Spoofing

Install macchanger:

```bash
sudo apt install macchanger
```

Generate a random MAC address:

```bash
sudo macchanger -r wlan0
```

Set a random vendor MAC:

```bash
sudo macchanger -A wlan0
```

Best practices:
- Change MAC before connecting
- Never reuse MACs across locations
- Disable Wi-Fi before spoofing

---

## 5. Network Strategy

### 5.1 Network Access

Preferred:
- Public Wi-Fi
- Libraries
- Cafes (paid preferred)

Avoid:
- Home networks
- Work or school networks
- Personal hotspots

---

### 5.2 VPN Usage

#### Mullvad VPN (Recommended)

Why Mullvad:
- No email required
- Anonymous account number
- Cash and Monero accepted
- Independently audited
- No-logs policy

Configuration:
- WireGuard protocol
- Kill switch enabled
- Block LAN access
- Disable IPv6

---

### 5.3 VPN and Tor Order

| Configuration | Use Case |
|--------------|----------|
| VPN → Tor | Hide Tor usage from ISP |
| Tor → VPN | Rare, advanced scenarios |

Note: Tails enforces Tor-only routing.

---

## 6. DNS, IPv6, and Leak Prevention

### 6.1 Disable IPv6

```bash
sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
```

Persist via /etc/sysctl.conf.

---

### 6.2 DNS Hardening

Use only:
- Mullvad DNS
- NextDNS (anonymous profile)
- DNS over HTTPS (DoH)

Never use ISP DNS resolvers.

---

## 7. Browser Hardening

### 7.1 Tor Browser (Preferred)

Rules:
- Do not install extensions
- Do not resize the window
- Do not log into personal accounts
- Use default security levels

---

### 7.2 Firefox (Hardened)

Required settings:
- Disable telemetry
- Enable HTTPS-only mode
- Enable privacy.resistFingerprinting
- Use container tabs

Recommended extensions:
- uBlock Origin
- NoScript (advanced users)
- ClearURLs
- Temporary Containers

---

## 8. Account & Identity Compartmentalization

- One identity per purpose
- One email per service
- One password per account
- Use password managers (KeePassXC)

Never:
- Reuse usernames
- Link phone numbers
- Cross-login identities

---

## 9. File Handling & Metadata

### 9.1 Metadata Removal

```bash
exiftool -all= file.jpg
```

---

### 9.2 Secure Deletion (HDD only)

```bash
shred -u -z file.txt
```

---

## 10. Payments & Financial Privacy

Preferred methods:
- Cash
- Monero

Avoid:
- Credit cards
- PayPal
- KYC-required services

---

## 11. Physical Security

- Cover webcam
- Disable microphone when possible
- Power off when not in use
- Never leave device unattended

---

## 12. Common Mistakes

- Logging into real-identity accounts
- Browser fingerprint inconsistency
- Reusing usernames
- Over-customizing Tor Browser
- Trusting a single privacy tool

---

## 13. Final Notes

Privacy is a process, not a product.

Assume:
- You will make mistakes
- Tools can fail
- Correlation is the primary risk

Minimize attack surface, compartmentalize aggressively, and reassess regularly.

---

## Disclaimer

This guide is provided for educational purposes only.  
The authors assume no liability for misuse.
