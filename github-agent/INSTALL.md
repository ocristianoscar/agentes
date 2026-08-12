> 🌐 **English** · [Español](INSTALL.es.md)

# Installing github-agent

About 10 minutes the first time.

---

## 1. Requirements

| You need | What for | How to check |
|---|---|---|
| **Git** | Local repository operations | `git --version` |
| **A GitHub account** | Self-explanatory | github.com |
| **An agent runtime** | To run the script | Claude Code, or any LLM you can hand the script to |
| **GitHub CLI** *(optional, recommended)* | Connecting without plaintext tokens | `gh --version` |

If `gh --version` says the command doesn't exist, nothing is broken. The agent
detects that on its own and offers you the alternatives.

---

## 2. Get the agent

```bash
git clone https://github.com/<YOUR_USERNAME>/github-agent.git
```

Or download the ZIP from the web page if you don't know `git clone` yet. The
agent will teach you that later.

---

## 3. How it connects

The agent tries three paths, best to worst, and picks the highest one your
machine allows. **Don't choose — start the agent and let it detect.** This
section is here so you understand what it's doing, not so you decide.

### Path A — GitHub CLI (preferred)

Install it:

```bash
winget install --id GitHub.cli
```

*(macOS: `brew install gh` · Linux: your package manager)*

Then, once:

```bash
gh auth login
```

It opens the browser, you sign in, and your operating system stores the
credential encrypted. **No token ends up in any file.** This is the safest path
and the one that gives the agent the most capability.

### Path B — Personal Access Token

Only if you can't install `gh`.

1. GitHub → Settings → Developer settings → Personal access tokens →
   Fine-grained tokens → Generate new token
2. Grant only the scopes the work requires. The agent tells you which ones — it
   never asks for extras "just in case".
3. Copy the token **once**. GitHub never shows it again.
4. Paste it into `credenciales.local.md`.

> ⚠️ That file is already covered by `.gitignore`. Don't move it, don't rename
> it, don't paste the token into a chat. A token leaked into a public repo is a
> compromised account within minutes — there are bots scanning new commits for
> exactly that. If it ever happens: **revoke it, don't delete it.** Deleting the
> commit leaves it in the history.

### Path C — Browser-guided

No credentials at all. The agent tells you exactly where to click. Always
works, but the agent can't act on its own.

---

## 4. Configuration — you don't do this part

**Don't fill anything in.** Start the agent and answer what it asks.

It pulls whatever it can from the API by itself — username, name, email, your
repository inventory — and asks only what it can't deduce. Nothing is mandatory
except what's technically required to connect: every other answer improves what
it produces, but never blocks it. Say nothing and it writes `undefined` and
moves on without comment.

It also defers questions to the moment they matter. If you never ask it for a
bio, it never needs to know your target role, so it never asks.

When it's done, it writes `config.md` itself. If you'd rather have no files at
all, say so — it will hold the configuration in the conversation instead, and
mention exactly once that this is lost when the session ends.

See the appendix below if you prefer to fill it in by hand.

---

## 5. Start it

Open your agent runtime in this folder and give it the contents of
`GITHUB AGENT.md`.

On first run, the agent will:

1. Verify the system date and write its own `changelog.md` — the entry that
   begins `HE NACIDO`. That is the moment it is born.
2. Detect `git`, `gh` and your authentication status.
3. Tell you which connection path it picked.
4. Read `config.md`, or interview you if it's empty.
5. Audit your GitHub and tell you **how many** findings it has — without
   telling you what they are until you ask for them.

---

## 6. Verify

```bash
gh auth status
```

Should say `Logged in to github.com as <your_username>`.

And before any first push, always:

```bash
git status
```

If `credenciales.local.md` shows up there, **stop.** The `.gitignore` isn't
doing its job. Tell the agent before touching anything else.

---

## Troubleshooting

**`gh: command not found` right after installing it** — close and reopen the
terminal. PATH doesn't refresh in sessions that were already open.

**`Permission denied (publickey)`** — you're on SSH without a configured key.
Ask the agent to switch you to HTTPS, or to walk you through generating one.

**The agent says it can't find `config.md`** — your runtime isn't sitting in
the repository folder.

**The agent refuses your token** — `.gitignore` isn't covering the credentials
file. That refusal is deliberate; fix the coverage rather than working around
it.

---

## Appendix — `config.md` variables

Only needed if you're filling it in manually. Keys are in English because they
are identifiers the agent reads; the conversation happens in your language.

| Key | Example | What the agent does with it |
|---|---|---|
| `github_user` | `gnosin` | Every API operation. The only required field |
| `full_name` | `Cristian Oscar` | Profile and commit authorship |
| `git_email` | `you@example.com` | Commit authorship |
| `target_role` | `Backend Developer` | Shapes bio, topics, which repos to feature |
| `stack` | `Python, Node, SQL` | Repository topics and project priority |
| `organization` | *(empty)* | If you work under an org |
| `content_language` | `English` | Language of READMEs, descriptions, bio |
| `git_level` | `principiante` | How much it explains before acting |
| `connection_method` | *(agent fills this)* | Which path it detected |

`git_level` is the one that changes the experience most: at `principiante` the
agent explains every command before running it and names which of Git's four
places it's operating on; at `avanzado` it acts and stays quiet. Leave it unset
and it behaves as intermediate.
