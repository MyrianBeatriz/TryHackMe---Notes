# Subdomain Enumeration Cheat Sheet

Subdomain enumeration is a critical step in the reconnaissance phase of penetration testing. It helps you discover additional attack surfaces by identifying subdomains associated with a target domain.

## Table of Contents
1. [Why Subdomain Enumeration?](#why-subdomain-enumeration)
2. [Common Techniques](#common-techniques)
   - [DNS Zone Transfer](#dns-zone-transfer)
   - [Brute Forcing](#brute-forcing)
   - [Search Engines](#search-engines)
   - [Certificate Transparency](#certificate-transparency)
   - [Web Archives](#web-archives)
   - [Third-Party Services](#third-party-services)
3. [Tools](#tools)
   - [Sublist3r](#sublist3r)
   - [Amass](#amass)
   - [Assetfinder](#assetfinder)
   - [Subfinder](#subfinder)
   - [dnsenum](#dnsenum)
   - [Aquatone](#aquatone)
   - [Knock](#knock)
   - [Findomain](#findomain)
   - [AltDNS](#altdns)
4. [Best Practices](#best-practices)
5. [Automation](#automation)
6. [Final Thoughts](#final-thoughts)

## Why Subdomain Enumeration?
- **Expanding the Attack Surface:** Subdomains can host different applications, which may have varying security levels.
- **Uncovering Hidden Content:** Developers often leave staging, development, or admin panels under subdomains.
- **Understanding the Target:** Helps in building a complete picture of the target's infrastructure.

## Common Techniques

### DNS Zone Transfer
- Attempt a DNS zone transfer with `dig` or `host` command.
- Example: `dig axfr @ns1.target.com target.com`

### Brute Forcing
- Use wordlists to brute-force possible subdomains.
- Combine it with DNS resolvers to filter out non-existent subdomains.
- Tools: `dnsenum`, `massdns`, `dnscan`.

### Search Engines
- Utilize search engines like Google and Bing to find indexed subdomains.
- Search Query: `site:*.target.com -www`

### Certificate Transparency
- Check Certificate Transparency logs for subdomains.
- Tools: `crt.sh`, `certspotter`.

### Web Archives
- Use services like Wayback Machine to find subdomains that might have been active in the past.
- Tool: `waybackurls`.

### Third-Party Services
- Gather subdomains from services like VirusTotal, Shodan, or Censys.
- Tools: `Amass`, `Sublist3r`.

## Tools

### Sublist3r
- Python tool for enumerating subdomains using multiple search engines and APIs.
- Command: `sublist3r -d target.com`

### Amass
- Comprehensive network mapping tool that includes subdomain enumeration.
- Command: `amass enum -d target.com`

### Assetfinder
- Fast and simple subdomain discovery tool.
- Command: `assetfinder --subs-only target.com`

### Subfinder
- Fast passive subdomain enumeration tool.
- Command: `subfinder -d target.com`

### dnsenum
- Perl script for DNS enumeration, including subdomain brute-forcing.
- Command: `dnsenum target.com`

### Aquatone
- Tool for domain flyover reconnaissance.
- Command: `aquatone-discover --domain target.com`

### Knock
- Python-based subdomain enumeration tool.
- Command: `knockpy target.com`

### Findomain
- Fast subdomain discovery tool with optional brute force.
- Command: `findomain -t target.com`

### AltDNS
- Permutation generator to discover potential subdomains.
- Command: `altdns -i subdomains.txt -o permutations.txt`

## Best Practices
- **Combine Multiple Tools:** Use a combination of passive and active tools to maximize coverage.
- **Use Fresh Wordlists:** Regularly update your wordlists with common and custom subdomain names.
- **Monitor DNS Responses:** Pay attention to wildcard DNS records and DNS-based load balancing that may skew results.
- **Leverage APIs:** Use APIs from VirusTotal, SecurityTrails, and Shodan for additional data sources.
- **Timing Considerations:** Be mindful of rate limits and IP blocking; distribute requests if necessary.

## Automation
- **Bash/Python Scripts:** Create scripts that combine multiple tools and automate the enumeration process.
- **Continuous Monitoring:** Set up recurring tasks or cron jobs to detect newly created subdomains over time.

## Final Thoughts
- Subdomain enumeration is an iterative process; always revisit and recheck as your knowledge of the target expands.
- Document all findings systematically to inform subsequent phases of penetration testing.

