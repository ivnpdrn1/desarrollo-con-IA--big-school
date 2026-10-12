# Buscadores e inteligencias artificiales — investigación y desarrollo crítico

**Fecha:** 2026-10-11. **Fuente:** MoureDev Pro, lección «Buscadores e inteligencias artificiales» (cuatro puntos de las capturas).  
**Estado:** guía preparada, ejercicios no ejecutados.  
**Relacionado con:** [Fuentes y verificación](./2026-10-11-Fuentes-Informacion-y-Verificacion.md), [Learning by Doing](./2026-10-11-Practica-Learning-by-Doing.md), [IDE VS Code](./2026-10-11-IDE-VSCode-Debugging.md), [Pseudocódigo](../02-Concepts/Pseudocodigo-Guia-Conceptual-y-Ejemplos.md).

## Objetivo
Investigar y resolver problemas de programación mediante buscadores, documentación y asistentes de IA sin delegar el criterio técnico. Separar **recuperar evidencia**, **razonar y especificar**, **implementar**, **probar** y **aprobar**.

## 1. Buscar eficientemente en Google

### Construir una pregunta diagnóstica
Antes de buscar, identificar: lenguaje/framework y versión, error literal, comportamiento esperado y real, entorno (Windows/Linux/AWS), intento realizado y restricción.

**Consultas de ejemplo:**
```text
site:docs.python.org/3/tutorial/ control flow for statements
site:code.visualstudio.com/docs/python/ debugging breakpoints Python
site:docs.aws.amazon.com IAM role trust policy assume role
"ModuleNotFoundError" "python" "venv" windows
site:docs.github.com git pull fetch difference
```

### Operadores útiles (comportamiento sujeto al buscador)
- `"frase exacta"`: localizar mensajes de error literales.
- `site:dominio`: restringir al proveedor oficial.
- `-palabra`: excluir término irrelevante.
- `OR`: variantes en una consulta.
- `filetype:pdf`: cuando realmente se busca un documento PDF.
- Fechas/filtros: controlar obsolescencia de herramientas rápidas.

**No asumir** que el primer resultado, fragmento generado o publicación de un foro es correcto para la versión instalada. Consultar documentación original, versiones y changelog.

### Protocolo de búsqueda
1. Pregunta concreta.
2. Búsqueda restringida a documento primario.
3. Revisar fecha, edición, versión, condiciones.
4. Contrastar con otra fuente pertinente.
5. Construir prueba mínima reproducible.
6. Guardar referencia y decisión en Obsidian, evidencia de código en GitHub.

## 2. Usos apropiados de ChatGPT en programación

- Explicar conceptos con analogías y contrastar alternativas.
- Traducir requisitos de negocio a criterios de aceptación.
- Diseñar pseudocódigo y contratos de funciones.
- Revisar errores y proponer hipótesis, no afirmar una causa sin datos.
- Generar casos de prueba (normal, borde, inválido).
- Revisar arquitectura, seguridad y cambios sugeridos por otros agentes.
- Acompañar estudio de Git, Python, AWS, APIs y Harness.

### Plantilla de pregunta
```text
Contexto: [proyecto y objetivo]
Entorno: [lenguaje, versiones, sistema operativo]
Problema: [error o comportamiento concreto]
Esperado: [...]
Observado: [...]
Intentado: [...]
Restricciones: [sin acceso producción, permisos, costo, datos sintéticos]
Responde en esta secuencia:
1. hipótesis y qué comprobar;
2. pseudocódigo/explicación;
3. cambio mínimo sugerido;
4. pruebas y riesgos;
5. fuentes oficiales relevantes;
6. qué debo comprender por mí mismo.
No inventes ejecuciones ni resultados.
```

**Reglas:** no subir secretos, tokens, datos de salud de personas, credenciales, información bancaria ni código privado sin autorización. Una respuesta fluida no garantiza precisión.

## 3. GitHub Copilot: posibilidades y límites

**Copilot** es un asistente de desarrollo integrado en entornos compatibles: según producto, versión y plan puede ofrecer sugerencias inline, chat, ayuda contextual, edición y funciones de agente. Se diferencia de GitHub (plataforma de repositorios) y de Git (control de versiones).

Flujo crítico:
1. escribir intención/comentario o función pequeña;
2. leer sugerencia antes de aceptarla;
3. comprobar tipos, dependencias, seguridad y licencias/políticas relevantes;
4. ejecutar tests y analizar diff;
5. aceptar, ajustar o rechazar.

No afirmar que Copilot está instalado o conectado. **No necesitamos agregarlo obligatoriamente:** nuestra combinación ya operativa conceptualmente ChatGPT → Claude Code → VS Code puede cubrir la necesidad principal. Evaluar Copilot solo por utilidad medible, costo y fricción adicional, sin duplicación innecesaria.

## 4. Balance aprendizaje versus asistencia

| Práctica | Riesgo | Control |
| --- | --- | --- |
| Copiar código generado | comprender solo la apariencia | explicar cada función y trazar variables |
| Dejar que agente modifique múltiples archivos | efectos y regresiones invisibles | alcance por cambio, revisar diff, tests |
| Confiar en una API inventada | fallos por incompatibilidad | docs/versiones y ejecución |
| Repetir búsquedas sin aplicar | sobrecarga informativa | regla: pregunta → prueba → nota corta |
| Aprobar herramientas con privilegios amplios | seguridad/costos/producción | mínimos permisos y aprobación humana |

**Escalera de ayuda:** intento propio (5–10 min) → pista conceptual → pseudocódigo → ejemplo mínimo → implementación guiada → solución completa únicamente cuando sea justificada, seguida de revisión y prueba. No convertir este tiempo orientativo en barrera si existe bloqueo real.

## 5. Aplicación a nuestros proyectos

| Proyecto | Búsqueda/verificación | Uso prudente IA |
| --- | --- | --- |
| AWS-Onion | AWS docs de IAM, SSM, VPC y EC2 por versión/región | explicación de flujo y diseño de laboratorio sin costos no autorizados |
| MarketMirrorAI | docs del proveedor de datos, latencia y formatos | clasificar eventos sintéticos sin órdenes reales |
| Gas Station Operations | reglas acordadas de estación + docs framework | escribir pseudocódigo y tests de conciliación fuera de producción |
| AI Health Agent CRM | políticas de autorización, datos y requisitos aplicables | construir pruebas con datos ficticios; revisión de privacidad y cumplimiento |
| byDebut | Next.js/Supabase/API de modelos y changelogs | revisar auth y trazabilidad de historias |
| JetImage | JetPack/CUDA/TensorRT y compatibilidad | prototipos y medición reproducible |
| Agents/Harness | especificación MCP, SDK, permisos y evals | agentes limitados, logs y gates de aprobación |

## 6. Ejercicio integrado (60 min, incluido en las 5 horas)

**Problema:** una función Python acumula mal galones y devuelve último elemento en vez de suma; datos ficticios `[10,15,20]`.

- **5 min:** escribir resultado esperado (45) y explicación intuitiva.
- **10 min:** buscar cómo funciona `for` en documentación oficial.
- **10 min:** solicitar a ChatGPT pistas sobre acumulador y pseudocódigo, no solución completa.
- **5 min:** pausa.
- **20 min:** depurar en VS Code, corregir y probar caso normal/vacío/negativo.
- **10 min:** explicar propia solución, registrar fuente y tests.

**Código intencionalmente incorrecto:**
```python
def sumar(despachos):
    total = 0
    for cantidad in despachos:
        total = cantidad  # error: reemplaza acumulado
    return total
```

**Pseudocódigo esperado:** iniciar total = 0; para cada cantidad válida sumar al total; devolver. Corrección conceptual: `total += cantidad`. Antes de declarar éxito, ejecutar realmente el programa y registrar resultados.

## 7. Registro y métricas

Registro mínimo por ejercicio: pregunta original; consulta; URL/versiones; pista de IA recibida; predicción; implementación; tests ejecutados; fallo corregido; explicación sin IA; commit/nota.

Métricas: porcentaje de problemas donde identifico fallo sin solución completa, capacidad para explicar un cambio, casos de prueba verificados, decisiones técnicas con fuente, y reducción de búsquedas repetidas. **No inventar línea base ni progreso.**

## 8. Criterio de aceptación
- [ ] Usar al menos un operador de búsqueda y localizar documentación primaria.
- [ ] Contrastar versión y alcance.
- [ ] Solicitar una pista estructurada a ChatGPT.
- [ ] Entender utilidad y límites de Copilot, aunque no se instale.
- [ ] Depurar y comprobar una solución.
- [ ] Explicar resultado en propias palabras.
- [ ] Guardar referencia, fuente y evidencia.

## Fuentes primarias
- Google Search Help: https://support.google.com/websearch/
- Python docs: https://docs.python.org/3/
- GitHub Copilot docs: https://docs.github.com/en/copilot
- VS Code docs: https://code.visualstudio.com/docs
- GitHub docs: https://docs.github.com/

*Las funciones exactas de asistentes cambian con producto y versión; confirmar documentación actual al utilizarlas.*
