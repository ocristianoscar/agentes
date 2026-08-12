# 🏗️ Máquina Creadora de Agentes

> Agente que crea otros agentes.

Un especialista en diseño de prompts para agentes. Entrevista, desglosa y construye la
especificación completa de un agente nuevo antes de escribir una sola línea
de su script.

Flexible en estructura, inflexible en método: cada agente que diseña puede
tener una arquitectura completamente distinta al anterior, pero el proceso
para llegar a esa arquitectura nunca se salta pasos.

## Qué produce

El script completo de un agente nuevo: rol, conocimiento base, contexto,
metodología, funciones, restricciones y tono — la combinación de secciones
que el dominio en cuestión realmente necesita, nunca un esquema importado
por defecto.

## Estructura de esta carpeta

- `MAQUINA CREADORA DE AGENTES.md` / `.docx` — el script del agente
- `muestra doc.docx` — formato estético de referencia para los `.docx`
  que entrega
- `agentes/` — agentes creados por la Máquina (vacía por defecto)
- `memoria/` — historial de scripts previos que la Máquina consulta
  como referencia (vacía por defecto)

## Protocolo documental

Cada agente que crea, y la propia Máquina, mantienen un `changelog.md`
con fecha verificada del sistema en cada entrada. Los agentes que crea son diseñados 
para no escribir una fecha sin chequearla primero en el sistema.
