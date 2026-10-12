# Plan de estudio personalizado — ejercicio MoureDev Pro

Fecha: 2026-10-11 (lección recibida en conversación). Estado: disponibilidad confirmada (60 minutos por día, 5 días por semana); ejecución de sesiones pendiente. Actualizado: 2026-10-11.
Fuente: captura «Ejercicio práctico: Plan de estudio», cuatro puntos visibles. Complemento del [Plan de Acción Integral](../03-Exercises/2026-10-11-Plan-de-Accion-Integral.md), [Mecánicas de aprendizaje](../01-Class-Notes/2026-10-11-Mecanicas-de-Aprendizaje.md) y [Pseudocódigo](../02-Concepts/Pseudocodigo-Guia-Conceptual-y-Ejemplos.md).

## Objetivo y restricciones

Fortalecer autonomía para **explicar, escribir, depurar y probar** programas, empezando por Python, después TypeScript, y transferir conocimientos a Gas Station Operations, MarketMirrorAI, AI Health Agent CRM, byDebut, AWS-Onion y agentes/Harness. Este plan no representa el temario oficial íntegro del curso y sus horarios son propuestas.

## 1. Disponibilidad confirmada y rutina diaria

**60 minutos por sesión, 5 sesiones por semana = 300 minutos (5 horas) por semana y 20 sesiones (20 horas programadas) por ciclo de cuatro semanas.** Son horas planificadas, no realizadas. Los dos días no programados son para descanso, recuperación o compromisos existentes, sin obligación de estudio. No se ha definido una hora de reloj ni días específicos de la semana.

| Tiempo | Actividad | Evidencia |
| --- | --- | --- |
| 5 min | recuperación activa y objetivo | explicar un concepto anterior sin notas |
| 20 min | estudiar una unidad | resumen conceptual |
| 5 min | pausa | descanso de la tarea |
| 20 min | pseudocódigo, traza o código | modificación concreta |
| 10 min | probar, explicar y registrar | caso probado, dudas y siguiente acción |

Cuando una práctica exige más tiempo, continuará en la siguiente sesión sin extender por defecto el bloque diario.

## 2. Secuencia operativa: cuatro semanas, cinco sesiones por semana

| Sesión | Concepto y actividad (60 min) | Evidencia de cierre |
| --- | --- | --- |
| **S1.1** | Problema, entrada, salida y pseudocódigo de un despacho | tabla entrada/proceso/salida |
| **S1.2** | Variables, tipos y asignación en Python | script corto con valores ficticios |
| **S1.3** | Operadores, expresiones y unidades | calcular galones y explicar resultado |
| **S1.4** | Decisiones if/elif/else | clasificar diferencia de conciliación |
| **S1.5** | Consolidación semana 1; traza a mano y microejercicio | explicar el algoritmo sin consultar IA |
| **S2.1** | Listas, índices y recorrido | colección de despachos |
| **S2.2** | Bucle for, iteraciones y acumuladores | suma de galones con trazado |
| **S2.3** | while y terminación | bucle correcto y explicación de riesgo infinito |
| **S2.4** | Funciones, parámetros y return | función pura total_galones |
| **S2.5** | Python frente a JavaScript; repaso de bucles | describir misma lógica en ambos lenguajes |
| **S3.1** | Diccionarios; representar producto/volumen/precio | estructura de datos sintéticos |
| **S3.2** | Validar tipos, no negativos y valores faltantes | reglas de validación documentadas |
| **S3.3** | Excepciones y manejo explícito de errores | casos inválidos controlados |
| **S3.4** | Casos límite, listas vacías y prueba de escritorio | matriz de casos con resultados previstos |
| **S3.5** | pytest, primeras pruebas automatizadas | ejecución documentada, sin suponer éxito |
| **S4.1** | Requisitos de minilaboratorio de galonaje y conciliación | alcance y criterios de aceptación |
| **S4.2** | Pseudocódigo y funciones separadas | diseño de validar, calcular, comparar |
| **S4.3** | Implementación incremental con Python | módulo independiente de producción |
| **S4.4** | Pruebas normales, límite y error; revisión de diff | reporte de pruebas y correcciones |
| **S4.5** | Demo reproducible, explicación propia y retrospectiva | commit, evidencia y decisión siguiente |

**Laboratorio pedagógico:** datos ficticios, código aislado de Gas Station Operations productivo. Para dinero utilizar Decimal y reglas explícitas de redondeo; nunca asumir que un ejemplo simplificado reproduce toda la conciliación real.

**Si una sesión no se completa:** no marcarla como terminada; mover su unidad a la siguiente jornada disponible y recorrer las posteriores, manteniendo la prioridad de comprensión. No sumar contenido para compensar.

## 3. Pausas y descansos

- La sesión base de 60 minutos incluye una pausa de 5 minutos; 25/5 o 20/5 son alternativas para reestructurar bloques cuando sea útil.
- Enfocar la pausa en desconectarse de la tarea; evitar cambiar de video sin procesar el contenido.
- Registrar la **siguiente acción** antes de pausar.
- Incluir una jornada semanal ligera o libre, según carga.
- Revisar cada semana carga total junto con AWS, certificaciones y otros cursos.

## 4. Pseudocódigo y escritura a mano

Para cada algoritmo:
1. Definir problema y resultado esperado.
2. Escribir entradas y tipos/unidades.
3. Dibujar bloques y decisiones a mano cuando ayude.
4. Redactar pseudocódigo independiente del lenguaje.
5. Trazar con datos ficticios y anticipar resultados.
6. Traducir a Python y ejecutar.
7. Probar normal, límite y error.
8. Explicar sin leer el prompt de IA y registrar el aprendizaje.

### Ejemplo Gas Station, sin producción
```text
RECIBIR despachos_ficticios
INICIAR total EN 0
PARA CADA despacho
  VALIDAR que galones es un número no negativo
  SI inválido, DEVOLVER error
  SUMAR galones AL total
FIN PARA
DEVOLVER total
```
Prueba de escritorio: [10,15,20] -> 45 galones. Extensiones: agrupación por producto y conciliación de pagos, con especificación monetaria adecuada antes de usar datos reales.

### Ejemplo AWS-Onion
```text
RECIBIR escenario de conectividad
VERIFICAR ruta y destino
COMPROBAR reglas NACL y SG
COMPROBAR servicio en instancia y estado
REGISTRAR hipótesis, evidencia y conclusión
```
Es una guía diagnóstica conceptual: no implica que todas las comprobaciones sean relevantes en todo escenario.

## 5. Integración con el flujo de IA
ChatGPT para conceptualizar y especificar → pseudocódigo y explicación propia → Claude Code para desarrollar de forma incremental → lectura y pruebas humanas → GitHub para código y evidencias → Obsidian para notas y relaciones. La IA no sustituye la evaluación personal.

## 6. Registro por jornada (plantilla)

```markdown
# Sesión — YYYY-MM-DD
Tema:
Duración real:
Objetivo:
Conceptos que explico sin apuntes:
Pseudocódigo / trazado:
Implementación / pruebas:
Error encontrado y cómo lo resolví:
Proyecto relacionado:
Evidencia GitHub:
Próxima acción:
Fatiga percibida (1–5, opcional):
```

## 7. Evaluación y seguimiento de 5 horas semanales

- **Por sesión (20 previstas):** registrar duración real, concepto, recuperación activa, pseudocódigo/código y prueba. Estado: pendiente, parcial o completada con evidencia.
- **Por semana (5 sesiones, 5 horas previstas):** al menos un microejercicio revisado; registrar sesiones realmente realizadas, minutos efectivos, dudas y bloqueos.
- **Al completar la sesión 10:** evaluación de recuerdo sin apuntes, corrección de un caso distinto del ejemplo y ajuste de carga.
- **Al completar la sesión 20:** demo reproducible, evaluación 0–4 por competencia con evidencia y selección del ciclo siguiente. Nunca inferir progreso por horas previstas.
- **Criterio de progreso:** explicar qué entra, qué cambia, qué sale, qué falla, cómo se prueba y cómo modificarlo.

## 8. Riesgos y mitigaciones

- Dispersión: un laboratorio principal, estudiar el resto de proyectos como ejemplos.
- Sobrecarga: modalidad mínima y descanso sin penalización.
- Consumo pasivo: práctica breve obligatoria para declarar la clase aplicada.
- Dependencia de IA: explicación propia y revisión de cambios.
- Datos sensibles/producción: usar datos ficticios y autorizaciones explícitas.
- Horarios desconocidos: no fijar una hora diaria sin conocer la agenda real.

## Próximas decisiones
- [x] Confirmar 60 minutos diarios, cinco días por semana (5 horas semanales).
- [x] Adoptar modalidad base de 60 minutos.
- [ ] Confirmar días concretos y hora si se desea calendarización.
- [ ] Confirmar laboratorio inicial (sugerencia: galonaje y conciliación sintéticos).
- [ ] Registrar línea base y primera sesión.
- [ ] Revisar el plan en dos semanas.
