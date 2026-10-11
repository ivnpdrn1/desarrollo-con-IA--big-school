# Ejercicio práctico — Plan de acción integral de desarrollo con IA

**Fecha:** 2026-10-11  
**Estado:** plan propuesto; revisar cada cuatro semanas  
**Horizonte orientativo:** octubre 2026 a junio 2027; ajustar según evidencias, cursos y disponibilidad  
**Vinculado a:** [Estrategia Maestra](../00-Project-Overview/Estrategia-Maestra.md) y [Propósito](../00-Project-Overview/Declaracion-de-Proposito.md)

## 1. Objetivo principal

Convertirme progresivamente en arquitecto y desarrollador de soluciones de inteligencia artificial (AI Software Engineering), capaz de definir, comprender, diseñar, implementar, probar, desplegar, observar y mantener productos propios. Aprender programación no como colección de sintaxis sino como capacidad de control técnico sobre sistemas construidos con IA.

**Resultado observable:** poder explicar y modificar con criterio una solución real de punta a punta, demostrar pruebas reproducibles y justificar decisiones técnicas, de seguridad y costo.

## 2. Diagnóstico de situación: experiencia y brecha

**Fortalezas documentadas de trabajo:** identificación de problemas reales; pensamiento de producto; especificación y revisión con ChatGPT; desarrollo asistido con Claude Code; arquitectura AWS; experiencia práctica con GitHub, Supabase, n8n y aplicaciones web; capacidad de integrar procesos de negocio.

**Brecha aún por medir (no presumir dominio):** lectura y escritura independiente de Python/TypeScript, depuración, pruebas automatizadas, diseño de interfaces de datos, seguridad, manejo de errores y diagnóstico operacional.

**Línea base pendiente:** seleccionar programa de 50–100 líneas y evaluar lectura, explicación, modificación, pruebas y depuración. Registrar fecha, rúbrica y evidencia sin inventar resultados.

## 3. Proyectos como laboratorios (no ejecución simultánea)

| Proyecto | Competencias | Experimento verificable siguiente | Riesgo/control |
| --- | --- | --- | --- |
| AWS-Onion | redes, IAM, EC2, Linux, SSM, cloud, DevOps | IaC y comprobación de rutas/permisos en entorno controlado | costos y privilegios mínimos |
| MarketMirrorAI | Python, APIs, datos, eventos, n8n, agentes | ingesta con datos simulados, normalización, pruebas y simulador determinista | aislar de trading real, no ejecutar órdenes |
| Gas Station Operations Platform | reglas de negocio, UI, persistencia, reconciliación | módulo puro de conciliación de caja con pruebas de invariantes | proteger datos de operación y evitar cambios en producción |
| AI - Health - Agent - CRM | SaaS, entidades, roles, consentimiento, auditoría | prototipo con registros sintéticos, autorización y pruebas | privacidad, seguridad, regulación aplicable; sin PHI real |
| byDebut | TS, React/Next.js, Auth, Supabase, IA generativa | prueba end-to-end de una historia y acceso por roles | permisos y propiedad intelectual |
| JetImage | Python, OpenCV, inferencia Edge AI | pipeline cámara → detección → evaluación con métricas | privacidad e integración física |
| Nubelai | producto y arquitectura cloud | despliegue de referencia con logs, presupuesto y rollback | autorización de gastos |
| Bitcoin Book y edición KDP | documentos, automatización, IA | verificador de metadatos y flujo editorial reproducible | derechos de autor y calidad |
| Del Fundador al Legado | agentes, memoria, conocimiento y herramientas | prototipo acotado con aprobación antes de actuar | evitar clonación invasiva, proteger conocimiento empresarial |

**Política WIP:** máximo un laboratorio principal y uno secundario de estudio; los demás permanecen en backlog. Se propone comenzar con un módulo de conciliación de ventas/pagos **en Python, independiente del sistema de producción**: permite practicar variables, funciones, tipos, validación, pruebas y lógica de negocio; alternativa: ingesta de datos simulados MarketMirrorAI.

## 4. Herramientas y lenguajes seleccionados

| Prioridad | Lenguajes/herramientas | Dominio pretendido |
| --- | --- | --- |
| P1 | Python, Git, terminal, VS Code, pytest | lectura, código, depuración y pruebas |
| P1 | SQL, JSON, HTTP, REST | datos e integración |
| P2 | FastAPI, Pydantic, PostgreSQL/Supabase | backend de producto |
| P2 | TypeScript, React, Next.js | aplicaciones full-stack |
| P3 | Docker, CI/CD, AWS IAM, Lambda, EC2, API Gateway, CloudWatch | operación confiable |
| P3 | n8n, APIs LLM, tool calling, MCP, Harness, evaluaciones | agentes y automatización supervisada |
| Especialización | OpenCV, PyTorch/TensorRT, Jetson | Edge AI según prioridad del proyecto |

**No aprender todo a la vez.** La tecnología se incorpora después de un caso de uso y prueba de valor.

## 5. Metodología de aprendizaje

**Bucle:** clase Big School → 5 conceptos → 3 relaciones → 1 ejemplo real → especificación ChatGPT → pequeño cambio de código con Claude Code o propio → revisión humana → pruebas → GitHub → síntesis Obsidian → retrospectiva.

**Regla de autonomía:** el estudiante debe poder responder sin leer el prompt: ¿qué entra?, ¿qué función transforma los datos?, ¿qué sale?, ¿cómo sé que está correcto?, ¿cómo se comporta con un error?, ¿qué ocurre si cambio un requisito?

**Plantilla por ejercicio:** problema; contexto/proyecto; objetivo; prerrequisitos; concepto; diseño; criterios de aceptación; pseudocódigo; implementación; casos normales, borde y error; evidencias; explicación propia; riesgos; dudas; siguiente paso; enlace a commit.

**Cadencia sugerida:** nota tras cada clase, una práctica pequeña semanal, revisión quincenal del bloqueo más importante, demo cada cuatro semanas y revisión estratégica cada trimestre. Ajustar a estudios AWS y disponibilidad.

## 6. Plan de 9 meses (hipótesis revisable)

### Ciclo I — Octubre–diciembre 2026: fundamentos
- Python: tipos, operadores, condicionales, loops, funciones, módulos, excepciones, diccionarios/listas y estructuras de datos.
- Git: ramas, commits, diff, merge y resolución de conflictos.
- Pruebas: pytest, casos normales/borde/error, debugging.
- Introducción a HTTP/JSON y SQL.
- **Salida:** módulo Python ejecutable y probado, explicación propia y registro de fallas.

### Ciclo II — Enero–marzo 2027: aplicaciones
- FastAPI, validación, REST, PostgreSQL, SQL, modelos de datos, auth y manejo de errores.
- TypeScript/React/Next.js aplicados cuando hagan falta.
- **Salida:** pequeño servicio con API + persistencia + UI mínima y pruebas de integración.

### Ciclo III — Abril–junio 2027: IA, agentes, operación
- APIs de modelos, herramientas, context engineering, MCP, Harness, estado, guardrails, evals y observabilidad.
- n8n y eventos; Docker/CI/CD; AWS/IAM; despliegue y rollback.
- **Salida:** agente acotado, evaluado, seguro, con logs, aprobación humana para efectos externos y despliegue controlado.

**Certificaciones AWS:** llevar en paralelo los objetivos Solutions Architect Associate, Developer Associate y AI Practitioner según su plan específico, aprovechando sin sustituir las prácticas de programación; fechas de examen no confirmadas aquí.

## 7. Plan detallado primeros 30 días (desde inicio efectivo)

| Semana | Actividad | Evidencia y aceptación |
| --- | --- | --- |
| 1 | línea base + entorno Python/Git + seleccionar laboratorio | autoevaluación, README y tests iniciales |
| 2 | variables, condicionales, funciones y validación con datos sintéticos | 3 funciones pequeñas explicables |
| 3 | listas/diccionarios, archivos JSON, errores y pytest | pruebas de casos normales, negativos y límites |
| 4 | refactorización, Git, revisión guiada y demo | ejecución reproducible, demo y retrospectiva |

**Primer ejercicio recomendado — Conciliación simplificada de una estación de servicio, fuera de producción:**
- Entrada: volumen por producto, precios configurados y pagos por medio.
- Salida: total esperado de ventas, suma de pagos, diferencia y estado de conciliación.
- Validaciones: valores no negativos, tipos correctos, productos conocidos, evitar redondeos flotantes para dinero (usar Decimal) y umbral configurable de tolerancia.
- Tests: balance correcto, faltante, sobrante, medio de pago desconocido, negativos, redondeo y datos vacíos.
- Ningún dato real de clientes/isleros ni escritura sobre el proyecto operativo.

**Criterios de terminado:** al menos 8 casos de prueba especificados y ejecutados; ejecución con instrucciones reproducibles; capacidad de explicar cada función; ningún secreto o dato personal; commit vinculado. La cifra es criterio propuesto, no resultado ya alcanzado.

## 8. Competencias y métricas

Puntuar de 0 a 4 cada 4 semanas: 0 sin evidencia; 1 explica conceptos con ayuda; 2 resuelve ejercicio guiado; 3 resuelve y depura con autonomía; 4 enseña, adapta y justifica decisiones.

| Competencia | Evidencia |
| --- | --- |
| Python | cambio funcional y pruebas |
| Git/GitHub | commit y explicación del diff |
| Datos/SQL | consulta, modelo y validación |
| APIs | endpoint documentado y probado |
| TypeScript/web | interfaz conectada a servicio |
| Pruebas/seguridad | casos borde, pruebas automatizadas y revisión de permisos |
| Agentes | evaluación, límite de herramientas y trazabilidad |
| AWS/operaciones | despliegue, logs, presupuesto y rollback |
| Autonomía | explicación propia y cambio sin dependencia ciega de IA |

**No asignar puntuaciones iniciales sin realizar la evaluación.**

## 9. Backlog, riesgos y mitigación

- **Dispersión:** WIP 1 laboratorio, backlog explícito, revisión mensual.
- **Dependencia de IA:** explicación personal, revisión de diff, tests, ejercicios sin prompts.
- **Seguridad y privacidad:** datos sintéticos en CRM, mínimo privilegio, secretos fuera de repositorios, confirmación para producción.
- **Costo AWS:** budgets, monitoreo y teardown al terminar laboratorios.
- **Sobreingeniería:** empezar con funciones puras y pruebas antes de microservicios o multiagentes.
- **Cambios del ecosistema IA:** evaluar alternativas por requisitos, resultados y mantenimiento; no por modas.
- **Certificaciones versus construcción:** usar exámenes para reforzar arquitectura sin abandonar demos reales.
- **Proyectos múltiples:** distinguir propuesta, prototipo, piloto y producción; no declarar completado lo que es pendiente.

## 10. Calendario de hitos y decisiones

**Día 7:** diagnóstico + laboratorio y primera función.  
**Día 30:** mini-proyecto probado + retrospectiva.  
**Día 90:** fundamentos consolidados con evidencias.  
**Día 180:** API + BD + UI mínima.  
**Día 270:** agente controlado y despliegue de referencia.

Fechas relativas al comienzo real de trabajo, no promesas de terminación.

## 11. Gobernanza de los artefactos

**GitHub Big School:** material técnico, plan, ejercicios, métricas, prompts y registro de avance.  
**Obsidian:** dashboard, vínculos, notas de comprensión, decisiones, estado y retrospectivas.  
**Repositorios de productos:** código de producción específico en su respectivo repo; jamás duplicarlo indiscriminadamente en Big School.

La sincronización de GitHub a la copia local del vault de Obsidian depende del mecanismo Git/sync configurado: un commit remoto no equivale necesariamente a que la app local ya hizo pull.

## 12. Próximas decisiones pendientes

- [ ] Confirmar disponibilidad semanal real para estudiar.
- [ ] Confirmar si el primer laboratorio será conciliación en Python (recomendado) o ingesta MarketMirrorAI.
- [ ] Hacer evaluación inicial autónoma.
- [ ] Establecer el primer bloque de 30 días con inicio efectivo.
- [ ] Revisar la carga paralela AWS / Big School / maestría y ajustar.
- [ ] Cerrar cada ciclo con una demo, pruebas, explicación personal y retrospectiva.

## 13. Respuesta breve para el ejercicio de Big School

> Mi objetivo es convertirme en desarrollador y arquitecto de soluciones de IA, capaz de crear productos empresariales reales con autonomía técnica y empleando asistentes inteligentes de forma supervisada. Mi experiencia con byDebut, MarketMirrorAI, Gas Station Operations, AI Health Agent CRM, AWS-Onion, JetImage y Nubelai demuestra que quiero concentrarme en AI Software Engineering, backend, datos, agentes y cloud. Aprenderé Python como primer lenguaje y TypeScript como segundo, con SQL, Git, FastAPI, React/Next.js, Supabase, n8n y AWS como herramientas relevantes. Mi método será aprender construyendo: ejercicios pequeños, requisitos explícitos, pruebas, revisión del código, GitHub y reflexión en Obsidian. Trabajaré por ciclos, mediré mi capacidad de explicar y depurar sin depender ciegamente de la IA y convertiré cada proyecto en un laboratorio de competencias reutilizables.
