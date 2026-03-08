# Suggested Anthropic PR

## Suggested Title

`Add ServiceNow platform skill covering scripting, architecture, SecOps, ITAM/SAM, FSM, SPM, CSDM, and IntegrationHub`

## Suggested Summary

This PR adds a new `servicenow` skill under `skills/servicenow/`.

The skill is designed as a broad ServiceNow platform assistant rather than a narrow scripting helper. It covers:

- ITSM
- ITOM
- ITAM and SAM Pro
- FSM
- HRSD and CSM
- SPM / PPM
- Vulnerability Response
- Security Incident Response
- IRM / GRC / SecOps
- CSDM and CMDB governance
- IntegrationHub
- App Engine
- Service Portal
- UI Builder / Now Experience
- Virtual Agent
- testing, security, performance, update sets, and CI/CD

The package includes:

- `SKILL.md` with explicit routing and platform standards
- curated reference packs under `references/`
- a reusable helper CLI under `scripts/snow_helper.py`
- smoke tests under `scripts/test_snow_helper.py`

## Why This Skill Is Useful

ServiceNow is broad enough that users often need both domain routing and implementation guardrails. This skill is intended to reduce incorrect patterns around:

- unsafe auth and hardcoded configuration
- GlideRecord misuse
- incorrect aggregate/query patterns
- recursive Business Rule updates
- weak platform-context routing across product families

What differentiates it from a narrow scripting-only skill:

- it routes across major product families instead of focusing on only ITSM or only server-side scripting
- it keeps domain guidance separated into focused reference packs instead of one long monolithic instruction file
- it includes a reusable CLI helper for template generation, linting, and package validation
- it emphasizes safer defaults around auth, scoped-app `get()` handling, aggregates, and recursion risks

## Validation Performed

```bash
python3 skills/servicenow/scripts/snow_helper.py validate-skill skills/servicenow
python3 skills/servicenow/scripts/test_snow_helper.py
```

## Reviewer Shortcuts

If reviewing quickly, these files give the best signal:

- `skills/servicenow/SKILL.md`
- `skills/servicenow/references/vulnerability-response.md`
- `skills/servicenow/references/security-incident-response.md`
- `skills/servicenow/references/integrationhub.md`
- `skills/servicenow/scripts/snow_helper.py`

## Trigger Examples

Should trigger:

- `Write a GlideRecord query for active incidents assigned to me`
- `Create a Business Rule for change requests that prevents closure without implementation notes`
- `Build a Vulnerability Response routing workflow`
- `Create a Scripted REST resource for ServiceNow`
- `Design CSDM relationships for business applications and service offerings`

Should not trigger:

- `Write a generic JavaScript array helper`
- `Build a React modal component`
- `Optimize a MySQL schema`
- `Explain Python decorators`
- `Design an AWS IAM policy`

## Notes

- The skill folder itself does not contain a README so it stays compatible with current skill packaging guidance.
- The helper and references were aligned so the examples reinforce the standards defined in `SKILL.md`.
