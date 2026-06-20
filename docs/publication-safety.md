# Publication Safety

### How to turn a working project into a safe public repository

> Applies to any AI-native editorial system built on the [AI-native Newsroom](../README.md) framework.

A working runtime is not a public repository. The architecture is strong enough to show; the raw working archive is not safe to upload as-is. Publish a **sanitized export**, not the live project.

## Do not publish the working archive directly

Build a public export from an allowlist — include only what you intend to share, rather than excluding things one by one and hoping you caught everything. At minimum, keep these **out** of the public repo:

```text
.env*                    secrets and tokens
db/**                    runtime databases
logs/**                  logs
intake/**                raw runtime intake
publishing/**            private runtime state, ledgers, drafts (unless sanitized)
.venv/**                 virtual environments
__MACOSX/**              OS cruft
.pytest_cache/**
.ruff_cache/**
```

Also strip, by hand:

- API keys, tokens, passwords, connection strings;
- local paths (`/Users/<name>/...`, machine names);
- private channel names, people, and internal project references;
- operational files: `CURRENT_CONTEXT.md`, agent inboxes, internal rules — publish the *pattern*, not the running instance.

## Recommended public companion files

- `LICENSE` — choose intentionally: permissive open source, documentation license (CC BY 4.0), or portfolio-only.
- `SECURITY.md` — how to report vulnerabilities, and a statement that secrets are never part of the repo.
- `.env.example` — document required variable **names** without real values.
- `CONTRIBUTING.md` — only if outside contributions are actually welcome.
- `docs/architecture.md` — keep deep architecture out of the first README screen; link to it instead.

## A pre-publication checklist

- [ ] Export built from an allowlist, not the full working tree.
- [ ] No secrets, tokens, or `.env*` files.
- [ ] No local paths or machine names.
- [ ] No private channel/people/project references.
- [ ] Operational files removed; only self-contained, context-free docs remain.
- [ ] Heavy diagrams live in `docs/`, not above the fold in README.
- [ ] `LICENSE`, `SECURITY.md`, `.env.example` added as needed.
- [ ] Diagrams render correctly on GitHub (test each Mermaid block).
- [ ] Language is consistent within each file (no mixed-language diagrams).

---

**See also:** [framework overview](../README.md) · [build guide](../GUIDE.md)
