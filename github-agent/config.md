# config.md — github-agent

No hace falta que completes nada acá. Arrancá el agente y él llena este archivo.
You don't need to fill this in. Start the agent and it writes this file for you.

Lo que pueda deducir solo (usuario, nombre, email, repositorios) lo saca de la API.
Lo demás te lo pregunta una vez, y solo cuando hace falta. Ninguna respuesta es
obligatoria: lo que quede `sin definir` tiene un comportamiento por defecto.

---

| Clave / Key | Valor / Value |
|---|---|
| `github_user` | sin definir |
| `full_name` | sin definir |
| `git_email` | sin definir |
| `target_role` | sin definir |
| `stack` | sin definir |
| `organization` | sin definir |
| `content_language` | sin definir |
| `git_level` | sin definir |
| `connection_method` | sin definir |

---

## Referencia / Reference

**`github_user`** — Usuario de GitHub. El único dato técnicamente indispensable.
*GitHub username. The only technically required field.*

**`full_name`** — Nombre real, para el perfil y la autoría de commits.
*Real name, for profile and commit authorship.*

**`git_email`** — Email de autoría de commits.
*Commit authorship email.*

**`target_role`** — Puesto o tipo de trabajo que buscás. Orienta la bio, los topics
y qué repositorios conviene destacar. Sin definir: el agente escribe en registro
técnico general.
*Role you're targeting. Drives bio, topics and which repos to highlight.*

**`stack`** — Tecnologías principales. Alimenta los topics de cada repositorio.
*Main technologies. Feeds repository topics.*

**`organization`** — Organización o empresa, si trabajás bajo una.
*Organization or company, if any.*

**`content_language`** — Idioma de READMEs, descripciones y bio. Sin definir: sigue
el idioma de la conversación.
*Language for READMEs, descriptions and bio. Unset: follows the conversation.*

**`git_level`** — `principiante` · `intermedio` · `avanzado`. Es la variable que más
cambia la experiencia: en `principiante` el agente explica cada comando antes de
correrlo; en `avanzado` ejecuta y calla. Sin definir: se comporta como `intermedio`.
*Calibrates how much the agent explains. Unset: behaves as intermediate.*

**`connection_method`** — Vía A (GitHub CLI), B (token) o C (navegador guiado).
No la completes vos: la detecta y la escribe el agente.
*Connection path. The agent detects and writes this one.*
