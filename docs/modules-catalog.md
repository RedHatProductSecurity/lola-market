# Lola Modules Catalog

> A curated list of awesome Lola modules for AI assistants

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

## Contents

- [Module Development](#module-development)
- [Security Modules](#security-modules)
- [Learning & Examples](#learning--examples)

---

## Module Development

*Tools for creating and managing Lola modules*

### lola-manager

Build Lola modules with intelligent workflow guidance following
Agent Skills best practices.

**Repository:** https://github.com/mrbrandao/lola-manager
**Author:** Igor Brandao
**Version:** 0.1.0
**Tags:** `module-builder`, `workflow`, `scaffolding`
**Assistants:** Claude Code, Cursor, Gemini CLI

**Features:**
- Interactive module creation
- Pattern recognition (Simple, Reference, Workflow, Automation)
- Template generation
- Validation and linting

---

## Security Modules

A curated list of AI Context Modules for Security Workflow

### openssf-skill

A comprehensive Claude Code/Copilot skill that helps developers build secure 
applications following 
[OpenSSF (Open Source Security Foundation)](https://openssf.org/) best practices.

**Repository:** https://github.com/ryanwaite/openssf-skill
**Author:** Ryan Waite
**Version:** v0.1.0
**Tags:** `openssf`, `security`, `workflow`
**Assistants:** Claude Code, Cursor, Gemini CLI

**Features:**
- Threat Modeling: STRIDE methodology guide with templates
- Security Policies: SECURITY.md and vulnerability disclosure templates
- OpenSSF Scorecard: All 20 checks explained with remediation steps
- OSPS Baseline: Level 1 compliance checklist
- SBOM Generation: Tools for 12+ languages/ecosystems
- SLSA Provenance: GitHub Actions workflows for Level 3
- Dependency Security: Scanning tools and vulnerability response
- Security Code Review: OWASP Top 10 focused review guide

---

### secdevai

AI-powered secure development assistant that integrates security analysis
capabilities directly into AI coding assistants. Provides context-aware
security review using OWASP Top 10 and WSTG patterns with multi-language support.

**Repository:** https://github.com/RedHatProductSecurity/secdevai
**Author:** Jeremy Choi
**Version:** 0.1.0
**Tags:** `security`, `owasp`, `wstg`, `security-review`, `sarif`
**Assistants:** Claude Code, Cursor, Gemini CLI

**Features:**
- Security Code Review: OWASP Top 10 + WSTG pattern analysis for any language
- AI-Powered Remediation: Fix suggestions with approval workflow
- Tool Integration: Bandit (Python) and OSSF Scorecard integration
- Multi-Language Support: Adapts Python security patterns to JS, Java, Go, Ruby, PHP, C#, Rust
- Export Capabilities: Markdown and SARIF v2.1.0 formats for CI/CD integration
- Severity Classification: Critical, High, Medium, Low, Info levels
- Extensible Rules: Customizable security patterns

**Skills Included:**
- `/secdevai review` - Security analysis with scope detection (full codebase, file, git commit, selection)
- `/secdevai fix` - Apply security fixes with before/after diffs
- `/secdevai tool` - Run Bandit, Scorecard, or all tools
- `/secdevai export` - Export findings to JSON/Markdown/SARIF
- `/secdevai help` - Display all available commands

---

## Learning & Examples

*Demonstrations and tutorials for Lola concepts*

### chef-buddy

Lazy context loading demonstration with an enthusiastic baking
chef persona.

**Repository:** https://github.com/mrbrandao/cheff-buddy
**Author:** Igor Brandao
**Version:** 0.1.0
**Tags:** `demo`, `lazy-loading`, `tutorial`
**Assistants:** Cursor

**Features:**
- On-demand context injection
- Step-by-step workflows
- Script integration
- Modular contexts

---

## Contributing

Want to add your module to this catalog? See
[CONTRIBUTING.md](../CONTRIBUTING.md) for guidelines on
submitting your module.

## License

This catalog is CC0. Individual modules have their own licenses.
