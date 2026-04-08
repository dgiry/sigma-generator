# ✍️ SIGMA Rule Generator

**Describe an attack. Get a detection rule.**

→ **[Live tool](https://dgiry.github.io/sigma-generator)**

---

## What it does

Describe an attack in plain English, paste a raw log / alert, or enter an IOC — and get a complete, ready-to-use SIGMA detection rule plus 6 platform conversions.

| Input | Example |
|-------|---------|
| **Plain English** | "PowerShell downloading and executing a file from the internet" |
| **Log line / Alert** | CrowdStrike JSON, Sysmon EventID 1, Windows Security Event 4625 |
| **IOC** | IP address, domain, file hash, registry key |

| Output | Description |
|--------|-------------|
| **SIGMA rule** | Complete valid YAML — title, UUID, status, logsource, detection block, falsepositives, level |
| **⬇ Download .yml** | One-click download with slug-based filename |
| **Splunk SPL** | Ready-to-run SPL search query |
| **Microsoft KQL (Sentinel)** | Sentinel / Log Analytics KQL query |
| **Elastic DSL / EQL** | Elastic Security EQL or DSL query |
| **QRadar AQL** | IBM QRadar AQL query |
| **Trend Vision One XDR** | Search App query — processCmd, processFilePath, eventSubId syntax |
| **Microsoft Defender XDR** | Advanced Hunting KQL — DeviceProcessEvents, DeviceNetworkEvents, DeviceFileEvents |
| **MITRE ATT&CK** | Min. 2 techniques mapped, sub-techniques included, clickable links |
| **False positives** | 3–5 concrete realistic scenarios surfaced per rule |
| **Explanation** | What it detects, why it matters, what to investigate first |

---

## Options

| Option | Values | Description |
|--------|--------|-------------|
| **Log source** | Auto / Windows / Sysmon / Linux / Network / Cloud / Web / Proxy | Override source detection |
| **Confidence** | High (strict, low FP) / Medium / Low (wide net) | Controls specificity vs. coverage |
| **Target SIEM** | All / Splunk / Sentinel / Elastic / Trend Vision One / Defender XDR | Prioritize one platform's output |
| **Model** | gpt-4o-mini (fast) / gpt-4o (best) | OpenAI model selection |

---

## Built-in examples

5 real-world attack scenarios ready to load:
- 💻 **PowerShell download + exec** — dropper pattern (Invoke-WebRequest + IEX)
- 🧠 **LSASS credential dump** — Mimikatz / Procdump / MiniDumpWriteDump
- 🔗 **PsExec lateral movement** — ransomware pivoting with explicit credentials
- 💉 **Process injection** — CreateRemoteThread into browser process (Sysmon EID 8)
- 🔑 **RDP brute force** — Event 4625/4624 spike pattern

---

## Usage

```
https://dgiry.github.io/sigma-generator
```

Enter attack description → click **Generate SIGMA Rule** → copy rule + platform queries or download as `.yml`.

Requires an OpenAI API key. Stored in `localStorage` only — never transmitted except directly to OpenAI.

Key shared with CVE Enricher and Alert Explainer (`cv_oai_key`).

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

OpenAI API key required. Key stored in `localStorage` only — never transmitted anywhere except directly to OpenAI.

## License

MIT
