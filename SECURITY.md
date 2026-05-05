# Security Policy

## Reporting a Vulnerability

If you discover a security issue in this repository, please report it privately rather than opening a public issue.

Email: **gui@adside.ai**

Please include:
- A description of the issue and its potential impact
- Steps to reproduce
- Any relevant logs, screenshots, or proof-of-concept

We aim to acknowledge reports within **3 business days** and to provide a remediation plan or fix within **30 days**, depending on severity and complexity.

## Scope

This repository contains Claude Code skills (Markdown instructions) for ad-operations workflows. There is no runtime application or dependency manifest, so the most relevant concerns are:

- Prompt-injection patterns embedded in skill instructions
- Inadvertent inclusion of credentials, API keys, or PII in examples
- Links to malicious external resources

Reports outside this scope (e.g. issues in Claude Code itself) should be directed to the corresponding upstream project.
