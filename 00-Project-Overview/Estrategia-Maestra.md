# Estrategia maestra de aprendizaje y creación

**Versión:** 1.0 — 2026-10-10  
**Horizonte:** ciclos orientativos de 12 semanas; ritmo ajustable a clases, proyectos y disponibilidad.

## Principio rector
Aprender programación para **comprender, construir y dirigir soluciones**, no para limitarse a producir código. El criterio técnico, las pruebas y la seguridad van por delante de la velocidad.

## Sistema de dos repositorios
- **Repositorio técnico:** https://github.com/ivnpdrn1/desarrollo-con-IA--big-school — temario, conceptos, ejercicios, prompts, ejemplos versionados y evidencias.
- **Knowledge Vault (Obsidian):** `Projects/Desarrollo con IA - Big School/` — navegación, reflexión, progreso, conexiones y decisiones.
- Ambos se actualizan explícitamente. Obsidian Git puede descargar el VAULT localmente; no existe sincronización automática entre los dos repositorios.

## Ruta de competencias
| Fase | Enfoque | Evidencia para avanzar |
| --- | --- | --- |
| 0. Línea base | Identificar fortalezas, vacíos y seleccionar un laboratorio | Autoevaluación y primer objetivo SMART |
| 1. Fundamentos | Variables, estructuras de datos, funciones, control de flujo, Git, terminal y depuración | Programa pequeño comprensible con tests |
| 2. Construcción de aplicaciones | Python/TypeScript según necesidad, HTTP/APIs, persistencia, auth y arquitectura | Servicio o flujo funcional, probado y documentado |
| 3. Desarrollo asistido por IA | Ingeniería de contexto, especificaciones, revisión del código y pruebas | Prompt → implementación → pruebas → revisión con trazabilidad |
| 4. Agentes y Harness | Herramientas, AGENTS.md, permisos, estado, memoria, evaluación y orquestación | Agente limitado, observabilidad y evaluación repetible |
| 5. Producto y operación | Seguridad, AWS, CI/CD, métricas, costos y resiliencia | Despliegue supervisado y rollback ensayado |

**No son períodos rígidos ni una afirmación del currículo de Big School.** Las fases se pueden estudiar en paralelo según requisitos reales.

## Cadencia propuesta
- **Cada clase:** una nota con 5 conceptos, 3 relaciones y al menos 1 ejemplo aplicado.
- **Cada semana:** un ejercicio terminado y un registro de dudas, hallazgos y decisiones.
- **Cada dos semanas:** revisión corta de evidencias y selección del siguiente cuello de botella.
- **Cada cuatro semanas:** demostración funcional, revisión del portafolio y ajuste del plan.
- **Cada trimestre:** revisar la declaración de propósito.

## Criterios de calidad y límites
1. No implementar sin objetivo y criterios de aceptación claros.
2. Proteger secretos, credenciales, datos personales y finanzas; nunca incluirlos en commits.
3. Aislar agentes y conceder permisos mínimos.
4. Separar experimentos de producción; exigir aprobación para despliegues y gastos.
5. Documentar supuestos, errores, resultados y decisiones; verificar la salida de IA.
6. Mantener el trabajo sostenible: pocos objetivos activos y priorización por aprendizaje.

## Indicadores (sin inventar progreso)
| Indicador | Cómo medirlo | Frecuencia |
| --- | --- | --- |
| Comprensión | Explicación propia y preguntas de repaso | Por clase |
| Implementación | Ejercicios funcionales completados | Semanal |
| Calidad | Pruebas aprobadas, regresiones y correcciones | Por entrega |
| Autonomía | Tareas que puedo diagnosticar/ajustar explicando cómo | Quincenal |
| Portafolio | Demos verificables y commits referenciados | Mensual |
| Aplicación | Problema de negocio atendido y retroalimentación | Por hito |

## Próximas acciones
- [ ] Registrar conocimientos de partida y lenguaje de foco inicial.
- [ ] Incorporar el temario real de Big School, sin inferirlo.
- [ ] Elegir UN laboratorio de aprendizaje para el primer ciclo.
- [ ] Definir su primera entrega de alcance reducido y sus pruebas.
- [ ] Crear ficha de la primera clase y primer ejercicio.
- [ ] Efectuar primera retrospectiva al cierre de la semana.

## Gobernanza
La persona mantiene dirección y decisiones. ChatGPT sirve para el análisis, la especificación, la pedagogía y la revisión; Claude Code es un ejecutor asistido; GitHub aporta historial y colaboración; Obsidian facilita aprendizaje y continuidad. **La IA propone; la persona valida.**
