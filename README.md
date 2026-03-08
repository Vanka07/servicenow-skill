# ServiceNow Skill for Claude

A comprehensive ServiceNow development skill that teaches Claude how to write platform code, design architecture, and follow best practices across every major ServiceNow module.

## What It Does

When you ask Claude a ServiceNow question, this skill automatically activates and provides:

- **Correct, production-ready code** — GlideRecord queries, Business Rules, Script Includes, REST APIs, Flow Designer patterns
- **Platform-aware guidance** — scoped app security, performance optimization, deployment pipelines
- **Full module coverage** — ITSM, ITOM, HRSD, CSM, SecOps, ITAM, FSM, SPM, Virtual Agent, Service Portal, and more

## Coverage

| Module | Reference |
|--------|-----------|
| ITSM (Incident, Problem, Change, SLA, Knowledge) | `references/itsm.md` |
| Glide APIs (GlideRecord, GlideAjax, GlideForm, etc.) | `references/glide-api.md` |
| Scripting Patterns (BR, SI, CS, UI Policy/Action) | `references/scripting-patterns.md` |
| REST API (Table API, Scripted REST, outbound) | `references/rest-api.md` |
| Flow Designer & PAD | `references/flow-designer.md` |
| Playbooks | `references/playbooks.md` |
| Now Experience / UI Builder | `references/now-experience.md` |
| Security & ACLs | `references/security.md` |
| Performance & Indexing | `references/performance.md` |
| Testing & ATF | `references/testing.md` |
| Service Catalog | `references/service-catalog.md` |
| Notifications | `references/notifications.md` |
| Update Sets & CI/CD | `references/update-sets-cicd.md` |
| ITOM / Discovery | `references/itom.md` |
| HRSD & CSM | `references/hrsd-csm.md` |
| Service Portal | `references/service-portal.md` |
| App Engine Studio | `references/app-engine.md` |
| Virtual Agent & NLU | `references/virtual-agent.md` |
| ITAM (HAM/SAM) | `references/itam.md` |
| FSM (Field Service) | `references/fsm.md` |
| IRM / GRC / SecOps | `references/irm-secops.md` |
| SPM / PPM | `references/spm.md` |
| Vulnerability Response | `references/vulnerability-response.md` |
| Security Incident Response | `references/security-incident-response.md` |
| SAM Pro | `references/sam-pro.md` |
| CSDM / CMDB Governance | `references/csdm-cmdb-governance.md` |
| IntegrationHub | `references/integrationhub.md` |
| Advanced (CMDB, Predictive Intelligence, etc.) | `references/advanced.md` |

## Install

### Claude.ai
1. Download or clone this repo
2. Zip the folder
3. Go to **Settings → Capabilities → Skills**
4. Upload the zip
5. Done — skill activates automatically on ServiceNow questions

### Claude Code
Drop this folder into your project's skills directory. Claude Code picks it up automatically.

## CLI Helper

Included Python CLI for quick tasks:

```bash
# Generate GlideRecord from natural language
python3 scripts/snow_helper.py query "find active incidents assigned to me"

# Generate code templates
python3 scripts/snow_helper.py template business-rule --table incident --when before --insert --update
python3 scripts/snow_helper.py template script-include --name MyUtils --client-callable

# Lint a script for antipatterns
python3 scripts/snow_helper.py lint < myscript.js
```

Requires Python 3.8+.

## Stats

- **31 files** | **384 KB** | **31,000+ words** of reference material
- **28 reference modules** covering every major ServiceNow product
- **Follows the official Claude Skills specification** (YAML frontmatter, progressive disclosure, examples, troubleshooting)

## License

MIT

## Author

**Jamiu Awoke** — Senior ServiceNow Developer & Claude Community Builder

[@lagosboyeth](https://x.com/lagosboyeth) · [GitHub](https://github.com/Vanka07)
