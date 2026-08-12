> 🌐 [English](README.md) · **Español**

# github-agent

Un agente de IA que administra mi GitHub — repositorios, perfil y estrategia de
visibilidad — desde una sola carpeta en mi máquina.

No fue escrito a mano. Lo diseñó otro agente que construí: la
**MÁQUINA CREADORA DE AGENTES**, un agente de arquitectura de prompts que
entrevista, desglosa el dominio y especifica el agente nuevo antes de que exista
una sola línea de su script.

Este repositorio es dos cosas a la vez: una herramienta que funciona, y la
prueba de que diseño agentes que diseñan agentes.

---

## Qué hace

**Opera repositorios.** Crea, clona, configura y mantiene. Ramas, commits, pull
requests, issues, releases, tags, Actions, Pages, topics, descripciones,
licencias, rama por defecto, visibilidad.

**Administra el perfil.** Bio, nombre visible, empresa, ubicación, sitio web,
README de perfil, repositorios fijados, foto.

**Estrategia de visibilidad.** Audita cada repositorio contra lo que un
reclutador mira de verdad — README ausente, descripción vacía, sin topics, sin
licencia, proyectos muertos sin archivar, portada de perfil en blanco,
repositorios mal fijados o sin fijar. Después informa *cuántos* señalamientos
tiene y espera. Nunca te vuelca recomendaciones porque se le ocurrió.

**Enseña.** Explica cualquier parte de Git o de GitHub en el momento en que se
vuelve relevante, a la profundidad que hace falta y ni un poco más. Enseñar es
acá una función de rango igual a ejecutar, no un subproducto de ejecutar.

---

## Modelo de seguridad

El agente opera bajo una sola regla dura:

> **Reversible y de bajo impacto → lo hace.**
> **Irreversible o públicamente visible → jamás sin autorización explícita, y
> nunca sin mostrar antes el cambio exacto.**

Borrar un repositorio, hacer force push, reescribir historial, pasar de privado
a público, transferir o renombrar, publicar un release, editar el perfil que un
reclutador va a leer — todo eso frena y pregunta. Ante la duda de si algo es
reversible, se trata como si no lo fuera.

Hay una excepción que corre en el sentido contrario: **un secreto expuesto se
informa de inmediato, sin preguntar.** Un token filtrado está comprometido en
minutos, no en días, y la única respuesta correcta es revocarlo — no borrarlo.

---

## Conexión

El agente se adapta a la máquina donde caiga. Detecta el entorno y elige la vía
más alta disponible; no te hace elegir a vos:

1. **GitHub CLI** — `gh auth login` por navegador. La credencial la guarda
   cifrada el sistema operativo. Ningún token se escribe en ningún archivo. Es
   la vía preferida.
2. **Token personal (PAT)** — en un archivo local ya cubierto por `.gitignore`,
   con los permisos mínimos que la tarea pida. Solo cuando la CLI no es opción.
   El agente rechaza un token si `.gitignore` no lo cubre.
3. **Navegador guiado** — sin manejar credenciales. El agente indica, vos hacés
   clic. Último recurso, y dice abiertamente qué pierde en este modo.

---

## Reutilización

Nada personal está escrito dentro del script del agente. Todo lo que cambia de
una persona a otra vive en `config.md`: usuario, nombre, rol que buscás, stack,
organización, idioma, y cuánto Git sabés ya.

No se espera que llenes ese archivo. El agente deduce lo que puede desde la API
y pregunta solo lo que no puede — una vez, nunca dos, y recién en el momento en
que la respuesta importa de verdad. Nada es obligatorio salvo lo técnicamente
necesario para conectarse.

Clonalo, apuntá tu runtime de agentes a `GITHUB AGENT.md`, y es tu agente, no el
mío. Ver **[INSTALL.es.md](INSTALL.es.md)**.

---

## Contenido del repositorio

| Archivo | Función |
|---|---|
| `GITHUB AGENT.md` | El script del agente, completo |
| `config.md` | Variables por persona, las escribe el agente |
| `INSTALL.md` / `INSTALL.es.md` | Guía de instalación, inglés y español |
| `README.md` / `README.es.md` | Este archivo, inglés y español |
| `.gitignore` | Contención de credenciales |

`changelog.md` no está en este repositorio, y su ausencia es deliberada. Lo
escribe el agente en su primera invocación, con la fecha verificada contra el
reloj del sistema en ese momento. Esta carpeta es una cuna, no una criatura.

---

## Linaje

Diseñado por la **MÁQUINA CREADORA DE AGENTES**.
