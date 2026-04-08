# ✍️ SIGMA Rule Generator

**Describe an attack. Get a detection rule.**

→ **[Live tool](https://dgiry.github.io/sigma-generator)**

---

## What it does

Describe an attack in plain English, paste a raw log / alert, or enter an IOC — and get a complete, ready-to-use SIGMA detection rule plus platform conversions.

| Input | Example |
|-------|---------|
| **Plain English** | "PowerShell downloading and executing a file from the internet" |
| **Log line / Alert** | CrowdStrike JSON, Sysmon EventID 1, Windows Security Event 4625 |
| **IOC** | IP address, domain, file hash, registry key |

| Output | Description |
|--------|-------------|
| **SIGMA rule** | Complete valid YAML — title, id, status, logsource, detection, falsepositives, level |
| **Splunk SPL** | Ready-to-run SPL search query |
| **Microsoft KQL** | Sentinel / Defender query |
| **Elastic DSL / EQL** | Elastic Security query |
| **QRadar AQL** | IBM QRadar query |
| **MITRE ATT&CK** | Mapped techniques with clickable links |
| **Explanation** | What it detects, why it matters, what to investigate |

---

## Options

| Option | Values | Description |
|--------|--------|-------------|
| **Log source** | Auto / Windows / Sysmon / Linux / Network / Cloud / Web / Proxy | Override source detection |
| **Confidence** | High (strict) / Medium / Low (wide net) | Controls specificity vs. coverage |
| **Target SIEM** | All / Splunk first / Sentinel first / Elastic first | Prioritize a platform |

---

## Built-in examples

5 real-world attack scenarios ready to load:
- 💻 **PowerShell download + exec** — dropper pattern
- 🧠 **LSASS credential dump** — Mimikatz / Procdump
- 🔗 **PsExec lateral movement** — ransomware pivoting
- 💉 **Process injection** — CreateRemoteThread into browser
- 🔑 **RDP brute force** — Event 4625/4624 pattern

---

## Usage

```
https://dgiry.github.io/sigma-generator
```

Enter attack description → click **Generate SIGMA Rule** → copy rule + platform queries.

Requires an OpenAI API key. Stored in `localStorage` only — never transmitted except directly to OpenAI.

Shared key with CVE Enricher and Alert Explainer (`cv_oai_key`).

---

## Part of the SecOps pipeline

```
🧪 defang-ioc  →  🔭 ioc-pivot  →  🔬 cve-enricher  →  🚨 alert-explainer  →  ✍️ sigma-generator
   (extract)        (pivot)           (enrich)              (explain)               (detect)
```

- **[🧪 Defang IOC](https://dgiry.github.io/defang-ioc)** — extract and defang/refang IOCs
- **[🔭 IOC Pivot Hub](https://dgiry.github.io/ioc-pivot)** — pivot any IOC to 30+ threat intel platforms
- **[🔬 CVE Enricher](https://dgiry.github.io/cve-enricher)** — full CVE context: KEV, threat actors, patch priority
- **[🚨 Alert Explainer](https://dgiry.github.io/alert-explainer)** — understand any SIEM alert in plain English

---

## Deploy your own

Static HTML — works on GitHub Pages, Netlify, Vercel, or any web server.

```bash
git clone https://github.com/dgiry/sigma-generator
# open index.html in your browser
```

## License

MIT
