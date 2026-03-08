# ServiceNow Skill for Claude

Production-ready ServiceNow skill package for Claude, organized for both direct use and upstream contribution.

The actual uploadable skill lives at [skills/servicenow](skills/servicenow). The rest of this repository exists to make the skill easy to test, publish, and contribute.

## Coverage

This skill covers:

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

## Why This Skill Is Useful

Most ServiceNow answers fail in one of two ways: they are too generic to be safely implemented, or they are narrowly correct for one product family and wrong for the rest of the platform.

This skill is designed to solve that by combining:

- broad platform routing across major ServiceNow product families
- explicit coding standards for GlideRecord, Flow Designer, security, and performance
- domain references that keep ITSM, ITAM, FSM, SecOps, SPM, CSDM, and IntegrationHub guidance separate and consistent
- a helper CLI that can generate templates, lint scripts, and validate the packaged skill

## Example Prompts

These are the kinds of requests the skill is designed to handle well:

- `Create a before Business Rule on incident that blocks resolution when close notes are empty`
- `Build a Vulnerability Response triage flow that routes exceptions to governance`
- `Design a CSDM model for business applications, business services, and service offerings`
- `Create an IntegrationHub action pattern for a paginated external REST API`

Typical outputs include:

- ServiceNow-specific code snippets
- architecture and workflow guidance
- plugin and role assumptions
- testing and deployment notes
- safer patterns than generic JavaScript answers usually provide

## Repo Layout

```text
servicenow-skill-public/
├── .github/workflows/validate.yml
├── ANTHROPIC_PR.md
├── LICENSE
├── README.md
└── skills/
    └── servicenow/
        ├── SKILL.md
        ├── references/
        └── scripts/
```

`README.md` stays at repo root on purpose. The skill folder does not contain a README so it remains compliant with Anthropic's skill packaging guidance.

## Install

For Claude.ai:

1. Zip [skills/servicenow](skills/servicenow).
2. Upload it in Claude.ai via `Settings > Capabilities > Skills`.

For Claude Code:

1. Place [skills/servicenow](skills/servicenow) in your skills directory.
2. Enable it in the environment where you use Claude Code.

## Validate

From the repo root:

```bash
python3 skills/servicenow/scripts/snow_helper.py validate-skill skills/servicenow
python3 skills/servicenow/scripts/test_snow_helper.py
```

## Trigger Matrix

These are example prompts to help validate when the skill should and should not activate.

Should trigger:

- `Write a GlideRecord query for active P1 incidents opened this week`
- `Create a before Business Rule on incident that blocks closure without close notes`
- `Build a Flow Designer pattern for routing vulnerable items to the right assignment group`
- `Create a Scripted REST API that returns a user by employee number`
- `Design a CSDM model for business applications, services, and service offerings`
- `Show a safe IntegrationHub action pattern for a paginated external API`
- `Help me reconcile SAM Pro entitlements against software installs`
- `Build an FSM dispatch flow using territory and technician skills`

Should not trigger:

- `Write a generic Node.js Express API`
- `Help me optimize a PostgreSQL query`
- `Create a React component for a dashboard`
- `Explain Python list comprehensions`
- `Debug this AWS Lambda timeout issue`

## Review Shortcuts

If you are evaluating the repo quickly, start here:

1. Read [skills/servicenow/SKILL.md](skills/servicenow/SKILL.md) for trigger scope and platform standards.
2. Skim one or two domain references such as [skills/servicenow/references/vulnerability-response.md](skills/servicenow/references/vulnerability-response.md) or [skills/servicenow/references/integrationhub.md](skills/servicenow/references/integrationhub.md).
3. Run the validation commands from this README.
4. Use [ANTHROPIC_PR.md](ANTHROPIC_PR.md) as the reviewer-facing summary for upstream submission.

## Useful Helper Commands

```bash
python3 skills/servicenow/scripts/snow_helper.py query "find all active incidents assigned to me"
python3 skills/servicenow/scripts/snow_helper.py query "find all security incidents in state containment"
python3 skills/servicenow/scripts/snow_helper.py template integrationhub-action --table incident
python3 skills/servicenow/scripts/snow_helper.py lint < myscript.js
```

## Publishing to GitHub

Recommended approach:

1. Create a public repository.
2. Push this repo as-is.
3. Tag the initial public release as `1.0.0`.
4. Attach a zip of `skills/servicenow/` to releases if you want non-technical users to install it easily.

## Submitting to Anthropic

Use [ANTHROPIC_PR.md](ANTHROPIC_PR.md) as the starting point for your upstream PR.

The expected contribution shape is the skill folder itself:

```text
skills/servicenow/
```

That means your upstream PR to Anthropic should mainly add the contents of [skills/servicenow](skills/servicenow), not the extra repo scaffolding around it.

## Disclaimer

This is a community-maintained skill and is not affiliated with or endorsed by ServiceNow.

## License

MIT. See [LICENSE](LICENSE).
