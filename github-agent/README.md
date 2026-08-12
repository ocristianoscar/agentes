> 🌐 **English** · [Español](README.es.md)

# github-agent

An AI agent that manages my GitHub — repositories, profile, and visibility
strategy — from a single folder on my machine.

It was not written by hand. It was designed by another agent I built: the
**MÁQUINA CREADORA DE AGENTES** — Spanish for "agent creation machine" — a
prompt-architecture agent that interviews, maps the domain, and specifies a new
agent before a single line of its script exists.

So this repository is two things at once: a working tool, and proof that I
design agents that design agents.

---

## What it does

**Repository operations.** Creates, clones, configures and maintains repos.
Branches, commits, pull requests, issues, releases, tags, Actions, Pages,
topics, descriptions, licenses, default branch, visibility.

**Profile management.** Bio, display name, company, location, website, profile
README, pinned repositories, avatar.

**Visibility strategy.** Audits every repository against what a recruiter
actually looks at — missing READMEs, empty descriptions, absent topics, no
license, dead projects left unarchived, an empty profile page, repos pinned
badly or not at all. Then it reports the *count* and waits. It never dumps
advice unasked.

**Instruction.** Explains any part of Git or GitHub the moment it becomes
relevant, at the depth the person needs and no deeper. Teaching here is a
first-class function, not a side effect of doing.

---

## Safety model

The agent operates under one hard rule:

> **Reversible and low-impact → it acts.**
> **Irreversible or publicly visible → never without explicit authorization,
> and never without showing the exact change first.**

Deleting a repo, force-pushing, rewriting history, flipping private to public,
transferring or renaming, publishing a release, editing the profile a recruiter
will read — all of it stops and asks. When in doubt whether something is
reversible, it is treated as if it isn't.

One exception overrides the "ask before speaking" rule in the other direction:
**an exposed secret is reported immediately, unprompted.** A leaked token is
compromised in minutes, not days, and the only correct response is to revoke
it — not to delete it.

---

## Connection

The agent adapts to whatever machine it lands on. It detects the environment
and picks the highest available path — it does not make you choose:

1. **GitHub CLI** — `gh auth login` through the browser. The credential is
   stored encrypted by the operating system. No token is ever written to a
   file. Preferred.
2. **Personal Access Token** — kept in a local, gitignored file, with the
   minimum scopes the task requires. Used only when the CLI is not an option.
   The agent refuses a token if `.gitignore` doesn't cover it.
3. **Browser-guided** — no credentials handled at all. The agent instructs, you
   click. Last resort, and it says plainly what it loses in this mode.

---

## Reuse

Nothing personal is hardcoded into the agent's script. Everything that varies
from one person to another lives in `config.md`: username, real name, target
role, stack, organization, language, and how much Git you already know.

You are not expected to fill that file in. The agent deduces what it can from
the API and asks only what it cannot — once, never twice, and only at the
moment the answer actually matters. Nothing is mandatory except what is
technically required to connect.

Clone it, point your agent runtime at `GITHUB AGENT.md`, and it is your agent,
not mine. See **[INSTALL.md](INSTALL.md)**.

---

## Repository contents

| File | Purpose |
|---|---|
| `GITHUB AGENT.md` | The agent script — the whole thing |
| `config.md` | Per-person variables, written by the agent |
| `INSTALL.md` / `INSTALL.es.md` | Setup guide, English and Spanish |
| `README.md` / `README.es.md` | This file, English and Spanish |
| `.gitignore` | Credential containment |

`changelog.md` is not in this repository, and its absence is deliberate. The
agent writes it itself on first invocation, with the date verified against the
system clock at that moment. This folder is a cradle, not a creature.

---

## Lineage

Designed by the **MÁQUINA CREADORA DE AGENTES**.
