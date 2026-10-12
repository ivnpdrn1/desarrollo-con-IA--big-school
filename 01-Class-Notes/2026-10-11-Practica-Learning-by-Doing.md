# Práctica en programación — Learning by Doing

**Fecha de incorporación:** 2026-10-11  
**Fuente:** lección «Práctica» de MoureDev Pro aportada en imagen por el estudiante.  
**Estado:** guía de aprendizaje elaborada; no constituye evidencia de prácticas ejecutadas.

Relacionar con: [Mecánicas de aprendizaje](./2026-10-11-Mecanicas-de-Aprendizaje.md), [Pseudocódigo](../02-Concepts/Pseudocodigo-Guia-Conceptual-y-Ejemplos.md), [Plan de estudio 60 min × 5 días](../03-Exercises/2026-10-11-Plan-de-Estudio-Personalizado.md), [Fundamentos: bucles](../03-Exercises/2026-10-11-Fundamentos-Bucles-Python-vs-JavaScript.md).

## 1. ¿Por qué es fundamental practicar?

Leer código o ver a Claude Code implementar una función produce familiaridad, pero **no demuestra que podamos escribirla, cambiarla ni depurarla**. La práctica implica intentar resolver una tarea, observar resultados, comparar con criterios de aceptación, localizar errores y volver a intentar.

Distinguir:
- **Exposición:** ver una explicación o demostración.
- **Comprensión:** explicar qué hace y por qué.
- **Aplicación guiada:** reproducir y modificar con ayuda.
- **Transferencia:** resolver un problema distinto con la misma estructura.
- **Autonomía:** implementar, probar y justificar cambios sin depender de copiar una respuesta.

La habilidad se desarrolla mediante práctica deliberada, retroalimentación, recuperación activa y progresión de dificultad; repetir mecánicamente no basta.

## 2. Beneficios de la práctica constante

| Beneficio | Mecanismo | Evidencia observable |
| --- | --- | --- |
| Consolidar fundamentos | recuperar y usar variables, condicionales, bucles y funciones | explicación sin notas |
| Resolver problemas | descomponer, formular hipótesis y comprobar | algoritmo + casos de prueba |
| Detectar errores | contrastar salidas con resultados esperados | diagnóstico y corrección |
| Transferir conocimientos | aplicar una función conceptual en otra solución | ejercicio nuevo sin copiar |
| Confianza calibrada | acumular pequeñas verificaciones objetivas | prueba reproducible, no sensación subjetiva |
| Productividad responsable con IA | revisar especificación, diff, tests y permisos | entrega con controles |

No presuponer que horas de estudio implican dominio.

## 3. Learning by Doing: ciclo pedagógico

**Problema pequeño → intento propio → pseudocódigo → implementación → ejecución → observación → corrección → explicación → variación → registro.**

1. Establecer un objetivo verificable y datos de entrada.
2. Escribir el resultado esperado **antes de ejecutar**.
3. Construir pseudocódigo o trazar variables.
4. Intentar solución propia (con tiempo acotado para evitar bloqueo excesivo).
5. Solicitar a ChatGPT una pista o explicación antes que una solución completa.
6. Pedir a Claude Code cambios incrementales y revisables si corresponde.
7. Ejecutar pruebas normales, de frontera y de error.
8. Revisar código, entender decisiones y explicar en lenguaje simple.
9. Repetir con una modificación de requisitos o contexto.
10. Documentar evidencia en GitHub, síntesis y preguntas en Obsidian.

**Protocolo si hay bloqueo:** describir entrada/salida, reducir problema a una función, recrear el error mínimo, leer el mensaje de error, formular una hipótesis, probarla, pedir una pista graduada. Evitar copiar soluciones sin explicación.

## 4. Cómo encaja en 60 minutos × 5 días semanales

No alterar las 5 horas semanales confirmadas. Distribución habitual por sesión:
- **5 min:** recordar sin notas y definir tarea.
- **20 min:** un concepto / ejemplo y predicción.
- **5 min:** descanso.
- **20 min:** implementar, probar y corregir.
- **10 min:** explicar sin ayudas y registrar próximo paso.

La práctica no se agrega como sexto día ni como obligación adicional: **es parte de cada sesión**. En días de integración puede dedicarse más del bloque al código y menos a teoría, conservando la duración.

### Ritmo semanal
| Sesión | Énfasis | Evidencia |
| --- | --- | --- |
| 1 | entender un concepto y escribir pseudocódigo | secuencia razonada |
| 2 | primer ejemplo en código | comportamiento observado |
| 3 | variar datos o requisitos | solución modificada |
| 4 | explorar errores y pruebas | casos normal/límite/error |
| 5 | ejercicio de transferencia y explicación propia | entrega semanal y retrospectiva |

Este ritmo es una guía compatible con las 20 sesiones del plan vigente, **no sustituye su temario de cuatro semanas**.

## 5. Progresión de ejercicios (fundamentos Python)

| Nivel | Ejercicio | Criterio de avance |
| --- | --- | --- |
| 1. Observar | explicar un bucle que suma galones [10,15,20] | predecir total 45 |
| 2. Reproducir | escribir la función `sumar_galones` | salida correcta |
| 3. Modificar | agregar un nuevo despacho y probar lista vacía | resultados esperados |
| 4. Robustecer | validar negativos y tipos erróneos | falla controlada |
| 5. Generalizar | agrupar galones por producto | algoritmo y tests de categorías |
| 6. Integrar | cálculo ficticio de ventas y pagos | módulo separado, con Decimal y reglas explícitas |
| 7. Transferir | aplicar bucle a eventos simulados de MarketMirrorAI | explicar correspondencias |

**Restricciones:** datos sintéticos, sin cambios a producción y sin ejecutar órdenes bursátiles.

## 6. Ejemplo de práctica guiada

**Requisito:** sumar galones válidos de una lista.  
**Pseudocódigo:**
```text
RECIBIR lista
ASIGNAR total = 0
PARA CADA cantidad EN lista
  SI cantidad NO ES NUMÉRICA O cantidad < 0
    RECHAZAR entrada
  FIN SI
  total = total + cantidad
FIN PARA
DEVOLVER total
```

**Implementación de referencia en Python:**
```python
def sumar_galones(despachos):
    total = 0
    for cantidad in despachos:
        if isinstance(cantidad, bool) or not isinstance(cantidad, (int, float)):
            raise TypeError("Galones deben ser numéricos")
        if cantidad < 0:
            raise ValueError("Galones no pueden ser negativos")
        total += cantidad
    return total
```

**Pruebas por diseñar y ejecutar:** [10,15,20] → 45; [] → 0; [0] → 0; [-1] → ValueError; ["10"] → TypeError. Para entrada física real, considerar valores no finitos, precisión, unidades y límites de negocio. No afirmar pruebas superadas hasta ejecutarlas.

**Variación de transferencia:** en lugar de sumar galones, sumar importes de pagos por medio y devolver desglose. Antes de hacerlo, elegir representación monetaria adecuada.

## 7. Aplicaciones por proyecto

- **Gas Station Operations:** cálculo separado de galonaje/ventas, validaciones y conciliación.
- **MarketMirrorAI:** procesar eventos sintéticos, probar señales, no operar cuentas.
- **AI Health Agent CRM:** recorrer pólizas/tareas ficticias y verificar permisos.
- **byDebut:** controlar versiones, roles y flujo de una historia.
- **JetImage:** iterar fotogramas de prueba y registrar resultados medibles.
- **AWS-Onion:** diagnosticar un escenario con hipótesis y experimentos de infraestructura autorizados.
- **Agents/Harness:** simular una invocación de herramienta, permiso, aprobación y evidencia.

## 8. Rúbrica de evaluación (0–4)

0: no hay evidencia.  
1: identifica variables y objetivo con apoyo.  
2: reproduce y ajusta un ejemplo guiado.  
3: resuelve caso nuevo, depura y prueba con autonomía.  
4: generaliza la solución, justifica decisiones y enseña el razonamiento.

Registrar nivel solo después de observar ejecución propia. Una respuesta correcta de un asistente de IA no constituye por sí sola evidencia de competencia personal.

## 9. Definición de práctica terminada
- [ ] Requisito y resultado esperado escritos.
- [ ] Intento de solución/pseudocódigo propio.
- [ ] Código ejecutado en un entorno concreto.
- [ ] Al menos caso normal, límite y error comprobados.
- [ ] Diagnóstico de correcciones documentado.
- [ ] Explicación propia sin copiar respuesta de la IA.
- [ ] Evidencia/commit referenciados en GitHub.
- [ ] Lección aprendida y siguiente ejercicio en Obsidian.

**No confundir «material preparado» con «ejercicio completado».**

## 10. Registro mínimo de práctica
```markdown
Fecha:
Sesión del plan (S1.1...S4.5):
Problema y resultado esperado:
Pseudocódigo / hipótesis:
Intento y ayuda solicitada:
Pruebas ejecutadas (con resultados reales):
Error, corrección y causa:
Qué puedo explicar sin notas:
Nueva variación:
Commit/evidencia:
Siguiente acción:
```

## 11. Preguntas de recuperación
1. ¿Qué diferencia hay entre reconocer código y ser capaz de modificarlo?
2. ¿Por qué predecir el resultado antes de ejecutar?
3. ¿Qué valor tiene el caso vacío y el dato inválido?
4. ¿Cuándo conviene dividir un problema?
5. ¿Cómo distingues ayuda de IA de comprensión autónoma?
6. ¿Qué prueba permite afirmar que una función funciona para cierto caso?

## Próximo paso
Aplicar el bucle de práctica a la primera sesión pendiente del plan de cuatro semanas, sin declarar ejecutado ningún ejercicio anticipadamente.
