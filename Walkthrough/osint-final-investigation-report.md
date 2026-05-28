# OSINT Final Investigation Report

<p align="center">
  <img src="../Pictures/OSINT_Palm.jpg" alt="OSINT Final Investigation Report" width="80%">
</p>

## Executive Summary

This report documents a passive Open Source Intelligence (OSINT) investigation of `cloudflare.com`, a legitimate public domain owned by Cloudflare, Inc.

The purpose of this project was to demonstrate how OSINT tools can support cybersecurity investigations, SOC triage, threat intelligence enrichment, and public exposure analysis.

The investigation reviewed public registration data, DNS records, certificate transparency logs, IP reputation, exposed service intelligence, URL behavior, and threat intelligence context.

Based on the collected evidence, the reviewed domain, IP address, and URL appear consistent with legitimate Cloudflare-owned infrastructure. No malicious classification was identified during the investigation.

## Scope

### Target Domain

```text
cloudflare.com
```

### URL Reviewed

```text
https://www.cloudflare.com/
```

### IP Address Reviewed

```text
104.16.132.229
```

### Investigation Type

```text
Passive OSINT investigation
```

### Activity Not Performed

The following activities were not performed:

- Exploitation
- Vulnerability scanning
- Authentication bypass
- Credential access
- Intrusive enumeration
- Unauthorized access attempts
- Social engineering
- Contacting the target organization

All findings were collected from publicly available OSINT sources.

## Tools Used

| Tool | Purpose |
|---|---|
| ICANN Lookup | Domain registration and RDAP review |
| nslookup | DNS record analysis |
| DNSChecker | Web-based DNS record validation |
| crt.sh | Certificate Transparency review |
| VirusTotal | IP and URL reputation analysis |
| AbuseIPDB | IP abuse report review |
| Shodan | Public service and host intelligence |
| Censys | Public host, service, and exposure intelligence |
| urlscan.io | URL behavior and webpage analysis |
| MITRE ATT&CK | Threat intelligence and adversary behavior mapping |

## Key Findings

### Domain Registration

ICANN Lookup showed that `cloudflare.com` is a long-established domain created on February 17, 2009, with an expiration date extending to February 17, 2033.

The domain is registered through Cloudflare, Inc. and uses Cloudflare-controlled nameservers.

The domain also has DNSSEC enabled, which supports DNS integrity by allowing DNS responses to be cryptographically validated.

### DNS Analysis

DNS lookups showed that `cloudflare.com` resolved to both IPv4 and IPv6 addresses.

Observed IPv4 addresses included:

```text
104.16.132.229
104.16.133.229
```

Observed IPv6 addresses included:

```text
2606:4700::6810:84e5
2606:4700::6810:85e5
```

MX records showed that Cloudflare uses Cloudflare-controlled email security infrastructure for inbound mail handling.

TXT records included SPF and multiple third-party verification records, which is expected for a large organization using many enterprise services.

NS and SOA records were consistent with Cloudflare-managed DNS infrastructure.

### Certificate Transparency

crt.sh showed a large certificate history for `cloudflare.com` and related subdomains.

The wildcard certificate transparency search returned many results and displayed a truncation warning, showing that large organizations may have extensive historical certificate records.

Visible results included Cloudflare-related identities such as:

```text
ajax.cloudflare.com
anti-virus.cloudflare.com
cdnjs.cloudflare.com
cloudflare.com
www.cloudflare.com
```

This demonstrated how Certificate Transparency logs can reveal public-facing names and historical certificate data associated with an organization.

### IP Reputation

The IP address `104.16.132.229` was reviewed using VirusTotal, AbuseIPDB, Shodan, and Censys.

#### VirusTotal

VirusTotal showed that `104.16.132.229` had a detection ratio of:

```text
0 / 91
```

No participating security vendors flagged the IP address as malicious in the captured results.

#### AbuseIPDB

AbuseIPDB showed that the IP had been reported 25 times, but the confidence of abuse was:

```text
0%
```

The IP was identified as part of Cloudflare infrastructure and a Cloudflare reverse proxy subnet.

This was an important example of why analysts must interpret OSINT findings in context. Historical abuse reports do not automatically mean the IP is malicious, especially when the IP belongs to shared CDN or reverse proxy infrastructure.

#### Shodan

Shodan identified the IP address as Cloudflare-owned infrastructure under AS13335.

Observed details included:

```text
Organization: Cloudflare, Inc.
ISP: Cloudflare, Inc.
ASN: AS13335
Tag: CDN
```

Shodan also showed multiple open web-related ports and technologies such as Cloudflare, Nginx, HSTS, and reverse proxy behavior.

#### Censys

Censys also associated the IP with Cloudflare infrastructure under AS13335.

Censys identified technologies such as:

```text
Cloudflare Load Balancer
Cloudflare WAF
```

This supported the Shodan findings and reinforced that the IP was part of Cloudflare's public-facing infrastructure.

### URL Analysis

The URL `https://www.cloudflare.com/` was reviewed using urlscan.io and VirusTotal.

#### urlscan.io

urlscan.io successfully loaded the Cloudflare webpage and showed no malicious classification.

Observed details included:

```text
Main IP: 104.16.124.96
ASN: AS13335 - CLOUDFLARENET
HTTP Transactions: 117
Contacted IPs: 4
Domains Contacted: 4
```

Detected technologies included:

```text
Cloudflare Bot Management
Cloudflare Browser Insights
Google Tag Manager
OneTrust
```

These technologies were consistent with a legitimate enterprise website.

#### VirusTotal URL Review

VirusTotal showed that `https://www.cloudflare.com/` had a detection ratio of:

```text
0 / 92
```

No participating vendors flagged the URL as malicious in the captured results.

## MITRE ATT&CK Context

No malicious activity was confirmed during this investigation.

However, the OSINT workflow used in this project can support investigations related to several MITRE ATT&CK areas.

| Technique | Name | Relevance |
|---|---|---|
| T1595 | Active Scanning | Shodan and Censys can reveal externally visible services that attackers may discover |
| T1596 | Search Open Technical Databases | CT logs, DNS records, RDAP, and internet scan engines are public technical databases |
| T1583.001 | Acquire Infrastructure: Domains | Domain registration review can support suspicious domain analysis |
| T1583.004 | Acquire Infrastructure: Server | IP and ASN analysis can help identify hosting or infrastructure ownership |
| T1566 | Phishing | URL reputation and scanning tools can support phishing link triage |
| T1071.001 | Web Protocols | URL and HTTP transaction analysis can support investigation of suspicious web traffic |

## Final Assessment

### Classification

```text
Benign / Legitimate Infrastructure
```

### Confidence

```text
High
```

### Supporting Evidence

The final classification is based on the following evidence:

- The domain is long-established and registered through Cloudflare, Inc.
- DNS records point to Cloudflare-controlled infrastructure
- Nameservers and SOA records align with Cloudflare-managed DNS
- DNSSEC is enabled
- Certificate Transparency records show Cloudflare-related identities
- VirusTotal did not flag the reviewed IP or URL as malicious
- AbuseIPDB showed a 0% confidence of abuse despite historical reports
- Shodan and Censys confirmed Cloudflare-owned infrastructure
- urlscan.io did not classify the Cloudflare URL as malicious
- Findings were consistent across multiple independent OSINT sources

## Recommended SOC Action

No blocking action is recommended based solely on the reviewed OSINT evidence.

Recommended action:

```text
Close as benign if observed activity matches expected Cloudflare traffic.
Continue monitoring only if internal telemetry shows unusual behavior, suspicious user activity, unexpected redirects, or abnormal endpoint communications involving these indicators.
```

## Lessons Learned

This project demonstrated that OSINT tools are most valuable when used together.

A single tool may provide incomplete or misleading context. For example, AbuseIPDB showed historical reports for the reviewed IP address, but other context showed that the IP belonged to Cloudflare reverse proxy infrastructure and had a 0% confidence of abuse.

The key lesson is:

```text
Do not rely on one OSINT result by itself. Correlate multiple sources before making a decision.
```

## Skills Demonstrated

This project demonstrated practical familiarity with:

- Passive OSINT collection
- Domain registration analysis
- DNS record analysis
- Certificate Transparency research
- IP reputation enrichment
- URL behavior analysis
- Public service exposure review
- ASN and ownership validation
- Threat intelligence interpretation
- MITRE ATT&CK mapping
- Analyst-style documentation
- SOC triage decision-making

## Conclusion

The OSINT investigation of `cloudflare.com`, `https://www.cloudflare.com/`, and `104.16.132.229` found no malicious classification indicators in the reviewed public sources.

The collected evidence consistently showed that the indicators are associated with legitimate Cloudflare-owned infrastructure.

This project provides a repeatable OSINT workflow that can be adapted for future SOC triage, phishing investigations, domain analysis, IP reputation checks, and threat intelligence enrichment.
