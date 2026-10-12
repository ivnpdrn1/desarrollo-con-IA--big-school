# Ejercicio práctico — Catálogo de fuentes y plan de actualización

**Fecha:** 2026-10-11. **Origen:** MoureDev Pro, «Ejercicio práctico: Fuentes» (captura proporcionada).  
**Estado:** plan documentado; suscripciones y revisiones aún no realizadas.  
**Conexiones:** [Lección Fuentes](../01-Class-Notes/2026-10-11-Fuentes-Informacion-y-Verificacion.md), [Plan estudio 5×60](./2026-10-11-Plan-de-Estudio-Personalizado.md), [Plan práctica semanal](./2026-10-11-Plan-de-Practica-Semanal.md).

## Propósito
Mantener un **registro reducido de fuentes confiables**, escoger 1–2 canales de novedades pertinentes, dedicar 30 minutos semanales (dentro de las 5 horas previstas) a revisión deliberada y conservar notas que permitan recuperar contexto sin repetir investigaciones.

## 1. Fuentes por competencia

| Área | Documentación primaria | Actualización complementaria |
| --- | --- | --- |
| Python | https://docs.python.org/3/ | https://blog.python.org/ |
| JavaScript | https://developer.mozilla.org/en-US/docs/Web/JavaScript | https://tc39.es/ecma262/ |
| TypeScript | https://www.typescriptlang.org/docs/ | https://devblogs.microsoft.com/typescript/ |
| React/Next | https://react.dev/ ; https://nextjs.org/docs | notas de versiones oficiales |
| Backend | https://fastapi.tiangolo.com/ | GitHub releases del proyecto |
| PostgreSQL/Supabase | https://www.postgresql.org/docs/ ; https://supabase.com/docs | changelogs del proveedor |
| AWS | https://docs.aws.amazon.com/ | https://aws.amazon.com/new/ |
| n8n | https://docs.n8n.io/ | anuncios y releases oficiales |
| GitHub | https://docs.github.com/ | https://github.blog/changelog/ |
| MCP | https://modelcontextprotocol.io/ | especificaciones/versiones del proyecto |
| Jetson | https://docs.nvidia.com/jetson/ | notas de compatibilidad JetPack |

**Cursos complementarios:** MoureDev Pro/Big School, AWS Cloud Institute y Digital Cloud Training. Los cursos explican; la fuente técnica versionada se utiliza para comprobar detalles vigentes. No asumir que una URL por sí sola prueba un contrato vigente.

## 2. Selección inicial de dos canales
- **Python Insider** — https://blog.python.org/ — versiones del lenguaje principal.
- **AWS What's New** — https://aws.amazon.com/new/ — servicios aplicados en AWS-Onion y Nubelai.

**Estado de suscripción:** pendiente. Enlaces para consulta confirmados como referencias; no afirmar suscripción efectuada ni que ambos ofrezcan necesariamente envío por correo bajo iguales condiciones. Antes de suscribirse revisar opciones oficiales RSS/email.

**Otras fuentes en reserva:** GitHub Changelog, TypeScript blog, releases de Next.js, n8n y MCP. Incorporar solo cuando un proyecto requiera seguimiento sostenido.

## 3. Presupuesto semanal: 5×60 minutos

Una sesión de 60 minutos distribuye **30 minutos de actualización + 30 minutos de práctica/revisión**:
- 10 minutos: novedades de las dos fuentes seleccionadas.
- 10 minutos: escoger como máximo una noticia y contrastar fecha, versión y alcance.
- 10 minutos: clasificar relevancia y crear/actualizar nota en Obsidian.
- 30 minutos: continuar el ejercicio práctico ya previsto.

**No crear una sexta sesión ni añadir media hora externa.** Si hay entregas urgentes de Python, posponer novedades. La quinta sesión semanal sigue incluyendo retrospectiva: integrar la lectura con revisión, no eliminar la reflexión de avances.

## 4. Matriz para decidir qué merece atención
Clasificación:
- **A — Acción necesaria ahora:** corrige un riesgo, incompatibilidad o bloqueo concreto del proyecto activo. Investigar y probar.
- **B — Útil en el siguiente ciclo:** guardar enlace con breve motivo y fecha para después.
- **C — Interesante sin aplicación actual:** descartar o registrar solo en backlog, sin dedicar desarrollo.

Preguntas: ¿afecta tecnología que realmente usamos?, ¿cuál versión?, ¿riesgo, seguridad, costo o beneficio?, ¿requiere decisión esta semana?, ¿existe documentación primaria?, ¿cómo lo comprobaríamos?

## 5. Formato de nota reutilizable

```yaml
---
tipo: fuente-tecnica
tema:
proyecto:
url:
editor:
fecha_consulta:
fecha_publicacion:
version_aplicable:
prioridad: B
estado: por-verificar
---
```

```markdown
# [Título del recurso]
## Pregunta que responde
## Resumen propio (3–5 líneas)
## Evidencia y fuente oficial
## Qué se confirmó / qué permanece incierto
## Impacto sobre proyecto
## Acción: aplicar / guardar / descartar
## Próxima fecha de revisión (solo si necesaria)
```

Estados: **pendiente de contraste**, **contrastada**, **probada en entorno**, **descartada**, **obsoleta**. Evitar archivar artículos completos o copiar contenido protegido.

## 6. Aplicaciones específicas

- AWS-Onion: verificar nuevas capacidades de IAM/EC2/VPC y relevancia para examen/prácticas antes de estudiar.
- MarketMirrorAI: cambios de API, latencia y permisos del proveedor de datos; no activar trading.
- Gas Station Operations: releases de frontend, protección de datos y necesidades verificadas de la estación; sin tocar producción por una novedad.
- AI Health Agent CRM: privacidad, auditoría, APIs y requisitos federales/estatales comprobados con fuentes normativas y asesoría profesional cuando corresponda.
- byDebut: cambios de autenticación, base de datos, Gemini y compatibilidad de frameworks.
- JetImage: JetPack, TensorRT, cámaras y compatibilidad de hardware.
- Agents/Harness: especificación MCP y releases verificadas; no adoptar frameworks nuevos por popularidad.

## 7. Métricas de calidad (sin inventar resultados)
- 1 bloque de 30 minutos previsto semanalmente.
- 1–2 fuentes recurrentes como máximo al inicio.
- 0–1 novedad registrada con relevancia clara, no cuota forzosa.
- Cada decisión técnica importante referencia fuente, versión, prueba y fecha.
- Revisión mensual: eliminar suscripciones, enlaces o notas que no aportan.
- Prioridad a tiempo de práctica y autonomía, no al número de artículos consumidos.

## 8. Checklist de puesta en marcha
- [x] Seleccionar fuentes oficiales iniciales.
- [x] Diseñar catálogo y clasificación de información.
- [x] Reservar 30 minutos de una sesión semanal de 60.
- [ ] Revisar y, si se desea, suscribirse a los canales oficiales.
- [ ] Realizar primer bloque de revisión semanal.
- [ ] Registrar primera novedad y su pertinencia en Obsidian.
- [ ] Evaluar después de cuatro semanas si vale la pena mantener ambas fuentes.

## 9. Método completo
**Pregunta → fuente oficial → fecha/versión → contraste → aplicación/prueba (si corresponde) → nota corta → decisión → recuperación futura.**

La fuente se archiva por la *decisión que permite tomar*, no por su volumen de información.
