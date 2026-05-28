<img src="https://capsule-render.vercel.app/api?type=waving&color=0:020617,45:0369A1,100:22D3EE&height=170&section=header&text=OSINT%20Tools%20Project&fontSize=38&fontColor=ffffff&animation=fadeIn&fontAlignY=38" />

<p align="center">
  <img src="Pictures/OSINT_Main_ReadMe.jpg" alt="OSINT Tools Project Main Banner" width="100%">
</p>

<h1 align="center">OSINT Tools Project</h1>

<p align="center">
  A passive Open Source Intelligence investigation focused on domain analysis, DNS review, certificate transparency, IP reputation, URL analysis, and analyst-style threat intelligence mapping.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Discipline-OSINT-0A66C2?style=for-the-badge" alt="OSINT Badge">
  <img src="https://img.shields.io/badge/Focus-Threat%20Intelligence-1F6FEB?style=for-the-badge" alt="Threat Intelligence Badge">
  <img src="https://img.shields.io/badge/Workflow-SOC%20Triage-2563EB?style=for-the-badge" alt="SOC Triage Badge">
  <img src="https://img.shields.io/badge/Method-Passive%20Investigation-0F766E?style=for-the-badge" alt="Passive Investigation Badge">
</p>

---

## Overview

This project demonstrates how commonly used OSINT tools can support cybersecurity investigations, SOC triage, threat intelligence enrichment, and public exposure analysis.

The investigation focused on `cloudflare.com` as a safe, legitimate, and cybersecurity-relevant target. Publicly available information was collected and reviewed across multiple sources to determine whether the domain, associated IP address, and related URL appeared suspicious or legitimate.

This repository consolidates the full walkthrough, screenshots from external tools, and a final analyst-style investigation report.

---

## Objective

The objective of this project was to build a repeatable OSINT investigation workflow that can be used to:

- Review domain registration and RDAP information
- Analyze DNS records and related infrastructure
- Identify subdomains and certificate data using Certificate Transparency logs
- Enrich public IP addresses with reputation and exposure intelligence
- Analyze URL behavior using sandboxed web scanning tools
- Correlate multiple OSINT sources before making a security judgment
- Map findings to practical SOC and threat intelligence workflows

---

## Investigation Scope

### Target Domain

```text
cloudflare.com
```

### Target URL

```text
https://www.cloudflare.com/
```

### Reviewed IP Address

```text
104.16.132.229
```

### Investigation Type

```text
Passive OSINT Investigation
```

### Rules of Engagement

This project was limited to safe, passive, and publicly available sources only.

No exploitation, vulnerability scanning, credential access, authentication bypass, intrusive enumeration, social engineering, or unauthorized access attempts were performed.

---

## Tools Used

| Tool | Purpose |
|---|---|
| ICANN Lookup | Domain registration and RDAP review |
| nslookup | DNS record analysis |
| DNSChecker | Web-based DNS validation |
| crt.sh | Certificate Transparency review |
| VirusTotal | IP and URL reputation analysis |
| AbuseIPDB | Historical abuse report review |
| Shodan | Public service and host intelligence |
| Censys | Public host and exposure intelligence |
| urlscan.io | URL behavior and webpage analysis |
| MITRE ATT&CK | Threat intelligence context and mapping |

---

## Walkthrough Sections

### Project Walkthrough

- [01 - Project Overview](Walkthrough/01-project-overview.md)
- [02 - Domain Investigation](Walkthrough/02-domain-investigation.md)
- [03 - Certificate Transparency](Walkthrough/03-certificate-transparency.md)
- [04 - IP Reputation Analysis](Walkthrough/04-ip-reputation-analysis.md)
- [05 - URL Analysis](Walkthrough/05-url-analysis.md)
- [06 - Threat Intel Mapping](Walkthrough/06-threat-intel-mapping.md)

### Final Report

- [OSINT Final Investigation Report](Reports/osint-final-investigation-report.md)

---

## Repository Structure

```text
OSINT Tools Project/
│
├── README.md
├── Pictures/
│   ├── OSINT_Main_ReadMe.jpg
│   ├── OSINT_Palm.png
│   ├── OSINT_Pinch.jpg
│   ├── OSINT_Point.jpg
│   ├── OSINT_Thumbprint.jpg
│   ├── OSINT_Face.jpg
│   ├── OSINT_Globe.jpg
│   └── OSINT_Palm.jpg
├── Reports/
│   └── osint-final-investigation-report.md
├── Screenshots/
│   ├── 02-Domain-Investigation/
│   ├── 03-DNS-Analysis/
│   ├── 04-Certificate-Transparency/
│   ├── 05-IP-Reputation/
│   └── 06-URL-Analysis/
└── Walkthrough/
    ├── 01-project-overview.md
    ├── 02-domain-investigation.md
    ├── 03-certificate-transparency.md
    ├── 04-ip-reputation-analysis.md
    ├── 05-url-analysis.md
    └── 06-threat-intel-mapping.md
```

---

## Key Findings

- `cloudflare.com` is a long-established domain created in 2009 and registered through Cloudflare, Inc.
- DNS records pointed to Cloudflare-controlled infrastructure and authoritative nameservers.
- DNSSEC was enabled, supporting DNS integrity.
- MX records showed Cloudflare-managed email security infrastructure.
- Certificate Transparency results revealed a large historical certificate footprint and multiple Cloudflare-related identities.
- VirusTotal did not flag the reviewed IP address or URL as malicious in the captured results.
- AbuseIPDB showed historical reports for the reviewed IP, but the abuse confidence score was `0%`.
- Shodan and Censys both identified the IP as Cloudflare-owned infrastructure under `AS13335`.
- urlscan.io showed no malicious classification for `https://www.cloudflare.com/`.
- Multiple OSINT sources supported the same conclusion: the investigated indicators were consistent with legitimate Cloudflare-owned infrastructure.

---

## Final Assessment

### Classification

```text
Benign / Legitimate Infrastructure
```

### Confidence

```text
High
```

### Recommended SOC Action

```text
No blocking action recommended based solely on the reviewed OSINT evidence.
Continue monitoring only if internal telemetry shows unusual or suspicious behavior involving these indicators.
```

---

## Skills Demonstrated

This project demonstrates practical familiarity with:

- Open Source Intelligence
- Passive reconnaissance
- Domain registration analysis
- DNS record analysis
- Certificate Transparency research
- IP reputation enrichment
- URL behavior analysis
- Public exposure review
- ASN and ownership validation
- Threat intelligence interpretation
- MITRE ATT&CK contextual mapping
- Analyst-style documentation
- SOC triage decision-making

---

## Key Takeaway

One of the most important lessons from this project is that no single OSINT source should be trusted on its own.

For example, AbuseIPDB showed historical reports for a Cloudflare IP address, but additional context from VirusTotal, Shodan, Censys, DNS analysis, and ownership data showed that the IP belonged to legitimate Cloudflare reverse proxy infrastructure.

```text
Correlate multiple OSINT sources before making a security decision.
```

---

## Conclusion

This project provides a repeatable OSINT workflow that can be adapted for future investigations involving suspicious domains, IP addresses, URLs, phishing triage, threat intelligence enrichment, and SOC analysis.

Although the selected target in this project was legitimate, the workflow and methodology demonstrated here are directly applicable to real-world cybersecurity investigations.

---

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:22D3EE,45:0369A1,100:020617&height=120&section=footer" />
