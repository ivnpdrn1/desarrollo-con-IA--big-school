# Fuentes de información — política de aprendizaje y verificación

**Lección:** Fuentes — MoureDev Pro / Big School. **Fecha:** 2026-10-11.  
**Estado:** referencia y metodología propuesta. Relacionada con [Mecánicas](./2026-10-11-Mecanicas-de-Aprendizaje.md), [Learning by Doing](./2026-10-11-Practica-Learning-by-Doing.md) y [Plan de práctica semanal](../03-Exercises/2026-10-11-Plan-de-Practica-Semanal.md).

## Objetivo
Seleccionar información técnica fiable, vigente y relevante, contrastarla con otras fuentes y experimentos, y mantenerse al día sin convertirse en consumidor permanente de contenido. **Conocimiento válido = afirmación respaldada por fuente apropiada + alcance/versión + comprobación práctica cuando sea posible.**

## 1. Jerarquía funcional de fuentes

| Prioridad | Tipo | Uso | Limitaciones |
| --- | --- | --- | --- |
| 1 | Documentación oficial versionada, especificaciones y referencias de API | contratos, comportamientos, límites y soporte | requiere verificar versión, excepciones y fecha |
| 2 | Repositorio fuente, release notes, changelogs, issues oficiales | cambios, implementaciones y problemas conocidos | código en desarrollo puede no representar la versión desplegada |
| 3 | Laboratorios y pruebas reproducibles | validar comportamiento en nuestro entorno | una prueba no demuestra universalidad |
| 4 | Cursos estructurados (MoureDev Pro, AWS, formación específica) | pedagogía, secuencia y contexto | ejemplos pueden simplificar o estar desactualizados |
| 5 | Artículos y blogs de especialistas, comunidad técnica | casos reales y alternativas | opiniones, sesgos, versiones y condiciones pueden variar |
| 6 | Respuestas ChatGPT, Claude u otros asistentes | hipótesis, explicación, borradores y búsqueda orientada | pueden equivocarse o inventar APIs; verificar antes de aplicar |

No hay jerarquía absoluta: una especificación oficial no prueba el desempeño real bajo una carga particular, mientras que un laboratorio no sustituye una norma de seguridad.

## 2. Fuentes iniciales por área

| Área | Documentación primaria | Complementos |
| --- | --- | --- |
| Python | https://docs.python.org/3/ | guías prácticas y ejercicios |
| JavaScript | https://developer.mozilla.org/en-US/docs/Web/JavaScript y https://tc39.es/ecma262/ | cursos y ejemplos contrastados |
| TypeScript | https://www.typescriptlang.org/docs/ | repositorios y pruebas |
| React / Next.js | https://react.dev/ y https://nextjs.org/docs | changelogs y demos |
| FastAPI | https://fastapi.tiangolo.com/ | pruebas con APIs simples |
| PostgreSQL | https://www.postgresql.org/docs/ | EXPLAIN y ejercicios SQL |
| Supabase | https://supabase.com/docs | comprobación de Auth/RLS |
| AWS | https://docs.aws.amazon.com/ | AWS Well-Architected, workshops y registros de cambios |
| n8n | https://docs.n8n.io/ | integraciones y prueba aislada |
| Git | https://git-scm.com/docs | práctica local |
| GitHub | https://docs.github.com/ | ejemplos en repositorios |
| MCP | https://modelcontextprotocol.io/ | especificación, SDKs y actualizaciones |
| PyTorch | https://docs.pytorch.org/ | ejemplos y benchmarks |
| NVIDIA Jetson | https://docs.nvidia.com/jetson/ | compatibilidad hardware/JetPack |

Estas son rutas de referencia recomendadas, no una afirmación de que todas se verificaron en vivo en esta sesión.

## 3. Protocolo de contrastación

**Pregunta → fuente primaria → versión/fecha → fuente complementaria independiente → prueba mínima → conclusión y evidencia.**

Para cada respuesta técnica:
1. Formular pregunta verificable: «¿Por qué Lambda necesita determinado permiso IAM?».
2. Verificar fuente oficial y compatibilidad de la versión.
3. Localizar limitaciones, notas de seguridad, cambios recientes.
4. Contrastar con implementación o demostración fiable, no solo repetir blogs.
5. Ejecutar experimento controlado (datos ficticios, permisos mínimos, sin afectar producción).
6. Documentar resultado, ambiente, fecha, URL y grado de certeza.
7. Señalar lo que permanece sin comprobar.

**Conflictos entre fuentes:** priorizar documentación del proveedor para contratos y versiones; pruebas para comportamiento observado; regulaciones y normas vigentes para obligaciones. Escalar desacuerdos que afectan seguridad, cumplimiento o costos.

## 4. Calidad de fuentes: checklist SCORE

- **S — Source/autoría:** ¿quién publica y con qué responsabilidad?
- **C — Contexto:** ¿se aplica a nuestro caso, región, versión y configuración?
- **O — Oportunidad:** ¿qué fecha y actualización tiene?
- **R — Reproducibilidad:** ¿hay ejemplos y evidencia verificables?
- **E — Exactitud:** ¿coincide con otras fuentes y pruebas independientes?

No convertir la puntuación en verdad matemática: usar las preguntas para decidir qué verificar.

## 5. Casos aplicados a proyectos

**AWS-Onion:** diferenciar documentación de VPC/route tables/NACL/security groups y observación de un laboratorio EC2. Registrar región, recursos, hora y configuración sin secretos.

**MarketMirrorAI:** separar documentación oficial del proveedor de datos, características de temporalidad y comportamiento demostrado en simulación; nunca confundir datos retrasados con realtime ni activar trading por una afirmación de IA.

**Gas Station Operations:** validar requisitos de negocio y configuración de productos/medios de pago contra decisiones del propietario, además de la documentación técnica del framework; el código no determina por sí solo las reglas correctas.

**AI Health Agent CRM:** documentación de API, seguridad, privacidad y requisitos estatales/federales aplicables; verificar con asesoría pertinente antes de operar información real, no confiar en blogs o respuestas generativas para conformidad regulatoria.

**byDebut:** documentación Next.js/Supabase/Gemini y pruebas de permisos y propiedad intelectual.

**JetImage:** compatibilidad JetPack, drivers, frameworks, modelos y benchmarks propios antes de elegir hardware/software.

**Agents/Harness:** especificación MCP/SDK real, límites de herramientas, políticas de permiso, tests de denegación y aprobación humana antes de acciones externas.

## 6. Control de sobrecarga: presupuesto de información

El plan confirmado es 60 minutos diarios × 5 días por semana, con estudio y práctica incluidos. Propuesta: **reservar 15–20 minutos de una de esas sesiones semanales** para revisar novedades relevantes; no adicionar obligaciones fuera de las 5 horas ni reemplazar la práctica sostenida.

Regla de tres:
- **Fuente base:** una documentación primaria por tema.
- **Complemento:** una fuente pedagógica útil.
- **Verificación:** un ejemplo, laboratorio o prueba.

Mantener una lista de espera «investigar después» para novedades sin relación con el siguiente entregable. No seguir todas las redes/noticias; escoger uno o dos canales o newsletters por áreas activas y revisar a intervalos definidos.

## 7. Flujo GitHub/Obsidian

**GitHub (repositorio técnico):** documentación de arquitectura, referencias versionadas, experimentos, tests, decisiones técnicas y cambios de dependencias.

**Obsidian (knowledge vault):** notas de conceptos, referencias, mapas de relaciones, lista de espera de novedades y pregunta pendiente.

Metadatos mínimos para nota de fuente:
```yaml
tema: 
pregunta: 
url: 
autor_o_editor: 
fecha_consulta: 
fecha_publicacion_o_revision: 
version_aplicable: 
confianza: pendiente
verificacion: pendiente
proyecto: 
```

Estados recomendados: **por verificar / contrastado / probado en entorno / obsoleto**. Citar fecha y versión; una URL sin contexto no es prueba suficiente.

## 8. Ejercicio práctico semanal

Seleccionar una pregunta técnica relacionada con la sesión actual. Registrar:
- [ ] pregunta específica y expectativa;
- [ ] fuente oficial identificada;
- [ ] versión y alcance;
- [ ] una fuente complementaria contrastada;
- [ ] prueba mínima (si corresponde);
- [ ] conclusión y límites;
- [ ] nota en Obsidian y enlace a evidencia GitHub.

**Ejemplo:** «¿Cómo recorre Python una lista?». Fuente Python oficial + curso MoureDev + prueba con `for` y `[]`. Resultado esperado: lista vacía produce cero iteraciones. Confirmarlo mediante ejecución y no declararlo realizado antes de probar.

## 9. Criterios de aceptación de la lección

Poder justificar qué fuente consultar, reconocer versión y alcance, diferenciar contrato de opinión, realizar contraste, señalar incertidumbre y detener búsquedas irrelevantes. El aprendizaje no se mide por enlaces guardados sino por decisiones y pruebas mejor fundamentadas.
