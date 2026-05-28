# 06 - Threat Intel Mapping

```markdown
<p align="center">
  <img src="../Pictures/OSINT_Globe.jpg" alt="OSINT Threat Intel Mapping" width="80%">
</p>
```

## Objective

The objective of this section is to connect the OSINT findings from the previous sections to practical threat intelligence and SOC triage concepts.

Because the selected target, `cloudflare.com`, is a legitimate public domain owned by Cloudflare, this section does not attempt to classify Cloudflare as malicious. Instead, it explains how the same OSINT workflow could be used to investigate suspicious domains, IP addresses, and URLs during a security investigation.

## Why This Matters

OSINT findings become more useful when an analyst can connect the technical evidence to security questions such as:

- Is this domain legitimate or suspicious?
- Is this IP address associated with known malicious activity?
- Does the infrastructure match the claimed organization?
- Are the DNS, certificate, URL, and reputation findings consistent?
- Does the activity suggest phishing, command and control, scanning, or other adversary behavior?
- Should the indicator be blocked, monitored, escalated, or closed as benign?

## Summary of Collected OSINT Evidence

| Evidence Area | Key Finding |
|---|---|
| Domain Registration | `cloudflare.com` is a long-established domain created in 2009 |
| Registrar | Cloudflare, Inc. |
| Nameservers | Cloudflare-controlled nameservers |
| DNSSEC | Enabled |
| DNS A/AAAA Records | Resolved to Cloudflare-owned IPv4 and IPv6 addresses |
| MX Records | Used Cloudflare email security infrastructure |
| TXT Records | Included SPF and multiple third-party verification records |
| Certificate Transparency | Showed large certificate history and Cloudflare-related identities |
| VirusTotal IP Review | 0 / 91 vendors flagged `104.16.132.229` as malicious |
| AbuseIPDB Review | Historical reports existed, but confidence of abuse was 0% |
| Shodan Review | IP associated with Cloudflare, AS13335, CDN, web ports, and reverse proxy behavior |
| Censys Review | Confirmed Cloudflare Load Balancer, Cloudflare WAF, and AS13335 |
| URLScan Review | No malicious classification for `https://www.cloudflare.com/` |
| VirusTotal URL Review | 0 / 92 vendors flagged the URL as malicious |

## Analyst Assessment

Based on the collected OSINT evidence, the investigated domain, IP address, and URL appear consistent with legitimate Cloudflare-owned infrastructure.

The findings from multiple independent sources aligned with each other:

- ICANN showed Cloudflare as the registrar
- DNS records pointed to Cloudflare-controlled infrastructure
- VirusTotal did not identify malicious reputation indicators
- AbuseIPDB showed historical reports but a 0% confidence of abuse
- Shodan and Censys identified Cloudflare-owned infrastructure and web-facing services
- URLScan and VirusTotal did not classify the Cloudflare URL as malicious

This consistency is important in SOC investigations. When multiple OSINT sources support the same conclusion, analysts can make stronger triage decisions.

## MITRE ATT&CK Context

No malicious activity was confirmed in this investigation. However, the OSINT workflow used in this project can support investigations involving several MITRE ATT&CK tactics and techniques.

| ATT&CK Area | Relevance to OSINT Workflow |
|---|---|
| Reconnaissance | OSINT can help identify domains, infrastructure, certificates, and exposed services |
| Resource Development | Certificate and domain analysis can help identify attacker-controlled infrastructure |
| Initial Access | URL and domain reputation checks can support phishing investigation |
| Command and Control | IP/domain enrichment can help evaluate suspicious external communications |
| Collection / Exfiltration Support | Reputation and infrastructure analysis can help determine whether an endpoint contacted suspicious external systems |

### Example ATT&CK Techniques That OSINT Can Support

| Technique | Name | How OSINT Helps |
|---|---|---|
| T1595 | Active Scanning | Shodan/Censys may reveal externally visible services that attackers could discover |
| T1596 | Search Open Technical Databases | CT logs, WHOIS/RDAP, DNS records, and internet scan data are public technical databases |
| T1583.001 | Acquire Infrastructure: Domains | Domain registration review can help assess suspicious or newly created domains |
| T1583.004 | Acquire Infrastructure: Server | IP and hosting analysis can help identify infrastructure ownership |
| T1566 | Phishing | URL/domain reputation checks can support phishing link analysis |
| T1071.001 | Web Protocols | URL and HTTP transaction analysis can help investigate suspicious web traffic |

## Final Threat Intelligence Judgment

The indicators reviewed in this project should not be treated as malicious based on the collected evidence.

### Final Classification

```text
Benign / Legitimate Infrastructure
```

### Confidence

```text
High
```

### Recommended SOC Action

```text
No blocking action recommended based on the reviewed OSINT evidence.
Continue to monitor only if internal telemetry shows unusual behavior involving these indicators.
```

## Lessons Learned

This project demonstrated that OSINT tools are most useful when they are used together.

A single tool may not provide enough context. For example, AbuseIPDB showed historical reports for a Cloudflare IP address, but the confidence score was 0%, and multiple other sources confirmed that the IP belonged to legitimate Cloudflare infrastructure.

This highlights an important SOC lesson:

```text
Do not rely on one OSINT result by itself. Correlate multiple sources before making a decision.
```

## Portfolio Takeaway

This investigation demonstrates practical familiarity with OSINT tools commonly referenced in cybersecurity job descriptions, including:

- ICANN Lookup
- DNS lookups with nslookup
- DNSChecker
- crt.sh
- VirusTotal
- AbuseIPDB
- Shodan
- Censys
- urlscan.io
- MITRE ATT&CK mapping

The project also demonstrates an analyst-style workflow: collect evidence, compare sources, document findings, assess risk, and make a recommendation.
