# Plan de estudio personalizado — ejercicio MoureDev Pro

Fecha: 2026-10-11 (lección recibida en conversación). Estado: propuesta pendiente de confirmar disponibilidad y aplicar.
Fuente: captura «Ejercicio práctico: Plan de estudio», cuatro puntos visibles. Complemento del [Plan de Acción Integral](../03-Exercises/2026-10-11-Plan-de-Accion-Integral.md), [Mecánicas de aprendizaje](../01-Class-Notes/2026-10-11-Mecanicas-de-Aprendizaje.md) y [Pseudocódigo](../02-Concepts/Pseudocodigo-Guia-Conceptual-y-Ejemplos.md).

## Objetivo y restricciones

Fortalecer autonomía para **explicar, escribir, depurar y probar** programas, empezando por Python, después TypeScript, y transferir conocimientos a Gas Station Operations, MarketMirrorAI, AI Health Agent CRM, byDebut, AWS-Onion y agentes/Harness. Este plan no representa el temario oficial íntegro del curso y sus horarios son propuestas.

## 1. Tiempo de estudio diario

Elegir de acuerdo con disponibilidad real: **mínimo sostenible 30 min**, **base sugerida 60 min**, **intensivo opcional 90 min**. Priorizar constancia sobre horas acumuladas.

| Modalidad | Bloques de referencia | Entregable |
| --- | --- | --- |
| Mínima (30 min) | 5 recuperar + 15 estudiar + 5 aplicar + 5 cerrar | una explicación y un microejemplo |
| Base (60 min) | 5 objetivo + 20 concepto + 5 pausa + 20 práctica + 10 cierre | código/pseudocódigo y reflexión |
| Extendida (90 min) | 10 recordar + 25 estudiar + 5 pausa + 25 aplicar + 5 pausa + 20 probar/revisar | práctica y pruebas más profundas |

Los intervalos son flexibles; si surge fatiga, descansar y reajustar. No compensar una sesión perdida mediante sobrecarga.

## 2. Temas divididos en unidades pequeñas: primer ciclo de cuatro semanas

**Semana 1 — Razonamiento:** D1 entradas/salidas; D2 variables/tipos; D3 operaciones; D4 decisiones if/else; D5 trazado a mano; D6 práctica aplicada; D7 revisión flexible/descanso.

**Semana 2 — Repetición:** D8 listas; D9 for; D10 acumuladores; D11 while y terminación; D12 funciones; D13 comparación Python/JavaScript; D14 repaso o descanso.

**Semana 3 — Robustez:** D15 diccionarios; D16 validaciones; D17 excepciones; D18 casos vacíos y límite; D19 pytest básico; D20 mejora guiada; D21 repaso/descanso.

**Semana 4 — Mini-laboratorio:** D22 requisitos; D23 pseudocódigo; D24 función validar; D25 función sumar galones; D26 pruebas de casos normales y errores; D27 revisión de diferencias del código y explicación; D28 demo, retrospectiva y próximo ciclo.

La numeración es de jornadas de referencia, no un compromiso de estudio obligatorio cada día. Se puede alargar el ciclo según otros estudios y disponibilidad.

## 3. Pausas y descansos

- Usar Pomodoro 25/5 cuando resulte útil, o 20/5 para conceptos intensos.
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

## 7. Evaluación y revisión

- **Por sesión:** producir explicación propia y microejemplo.
- **Semanal:** un ejercicio revisado, dudas y próximos bloqueos.
- **Quincenal:** evaluación de recuerdo sin apuntes y capacidad de corregir un caso nuevo.
- **Mensual:** una demostración reproducible, evaluación de competencias 0–4 basada en evidencias y ajuste del plan.
- **Criterio de progreso:** explicar qué entra, qué cambia, qué sale, qué falla, cómo se prueba y cómo modificarlo.

## 8. Riesgos y mitigaciones

- Dispersión: un laboratorio principal, estudiar el resto de proyectos como ejemplos.
- Sobrecarga: modalidad mínima y descanso sin penalización.
- Consumo pasivo: práctica breve obligatoria para declarar la clase aplicada.
- Dependencia de IA: explicación propia y revisión de cambios.
- Datos sensibles/producción: usar datos ficticios y autorizaciones explícitas.
- Horarios desconocidos: no fijar una hora diaria sin conocer la agenda real.

## Próximas decisiones
- [ ] Confirmar minutos disponibles los días de estudio.
- [ ] Elegir modalidad por defecto.
- [ ] Confirmar laboratorio inicial (sugerencia: galonaje y conciliación sintéticos).
- [ ] Registrar línea base y primera sesión.
- [ ] Revisar el plan en dos semanas.
