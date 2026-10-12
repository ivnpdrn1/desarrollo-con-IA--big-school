# Ejercicio práctico — Plan de práctica semanal

**Fecha de documentación:** 2026-10-11  
**Fuente:** captura de la lección «Ejercicio práctico: Plan de práctica», MoureDev Pro.  
**Estado:** plan preparado, ejecución por verificar.  
**Compatibilidad:** [Plan de estudio 60 min × 5 días](./2026-10-11-Plan-de-Estudio-Personalizado.md), [Práctica — Learning by Doing](../01-Class-Notes/2026-10-11-Practica-Learning-by-Doing.md), [Pseudocódigo](../02-Concepts/Pseudocodigo-Guia-Conceptual-y-Ejemplos.md).

## 1. Finalidad

Transformar la práctica en una **unidad semanal verificable**: seleccionar dos o tres conceptos, trabajar en ejercicios pequeños en cinco sesiones de 60 minutos y cerrar con una retrospectiva basada en evidencias. El ciclo propuesto de cuatro semanas tiene 20 sesiones (20 horas planificadas, aún no realizadas). No agregar otros 30 minutos diarios: la práctica se incorpora dentro de cada hora existente.

## 2. Compromisos y principios

- **Duración confirmada:** 60 min × 5 días = 5 horas semanales.
- **Práctica directa:** proponer inicialmente **20–30 minutos de código/pseudocódigo en cada sesión**, ajustando la distribución sin superar los 60 minutos; la lección sugiere al menos 30 minutos diarios como ejemplo, pero el tiempo debe ser compatible con comprender y registrar.
- **No fijar fechas ni hora de reloj:** aún no se han especificado los cinco días ni el inicio efectivo.
- **Un laboratorio activo:** módulo educativo de galonaje/conciliación de Gas Station Operations, aislado de producción, con datos ficticios.
- **Aprendizaje:** intentar por cuenta propia, usar pistas graduadas de ChatGPT y luego Claude Code para cambios incrementales, revisar el diff y ejecutar pruebas.
- **Evidencia:** material preparado no equivale a práctica ejecutada.

## 3. Rutina de sesión

| Bloque | Duración | Qué sucede |
| --- | ---: | --- |
| Recuperación y objetivo | 5 min | recordar concepto previo y definir resultado |
| Comprensión y pseudocódigo | 15 min | una idea, predicción y pasos |
| Pausa | 5 min | descanso |
| Práctica activa | 25 min | implementar, variar y probar |
| Cierre | 10 min | explicar sin apuntes y registrar evidencia |
| **Total** | **60 min** | **25 min de práctica directa, más pseudocódigo en preparación** |

Si se desea cumplir una meta de 30 minutos de práctica directa, reducir comprensión a 10 min y cierre a 10 min, manteniendo 5 min recuperación + 5 pausa + 30 práctica + 10 cierre = 60 min. No asumir que más minutos generan mejor comprensión.

## 4. Plan semanal: dos o tres conceptos específicos

| Semana | Conceptos elegidos | Microproducto | Evidencia de aceptación |
| --- | --- | --- | --- |
| **1. Lógica** | variables, condicionales, pseudocódigo | clasificador educativo de cuadre/faltante/sobrante | explicar entradas, regla y tres resultados |
| **2. Bucles** | listas, bucles, funciones | contador/sumador de galones | sumar [10,15,20] = 45, lista vacía = 0, función reutilizable |
| **3. Calidad** | diccionarios, validaciones, pruebas | validador de despachos | rechazar negativos/tipos inválidos, casos de borde y tests |
| **4. Integración** | composición de funciones, pruebas, depuración | mini-conciliador aislado | entrada sintética → total → diferencia → estado; demo y reflexión |

Estos son focos de *práctica* alineados con el temario ya definido, no clases adicionales. Python primero; comparación con JavaScript como transferencia posterior.

## 5. Cinco sesiones tipo por semana

| Sesión | Trabajo práctico | Entregable |
| --- | --- | --- |
| 1 | elegir 2–3 conceptos, expresar problema, entradas, salidas y pseudocódigo | contrato y algoritmo |
| 2 | resolver ejemplo mínimo y ejecutar | función pequeña |
| 3 | modificar requisito o datos sin copiar solución completa | variación funcional |
| 4 | probar normal, borde y error, localizar y corregir un fallo | matriz y resultado real de pruebas |
| 5 | ejercicio de transferencia + explicación sin notas + retrospectiva | evidencia de aprendizaje, próximo bloqueo |

No se declara completada una sesión hasta registrar evidencia; los resultados no se presuponen.

## 6. Catálogo de microproyectos progresivos

| Microproyecto | Conceptos | Proyecto relacionado |
| --- | --- | --- |
| Contador 1..N | bucles, variables | fundamentos |
| Calculadora de dos valores | funciones, operadores, validación | fundamentos |
| Sumador de galones | listas, bucles, acumulador | Gas Station Operations |
| Clasificador de diferencia | condiciones, funciones | Gas Station Operations |
| Totales por producto | diccionarios, bucles | Gas Station Operations |
| Procesador de alertas sintéticas | bucles, condiciones y registro | MarketMirrorAI |
| Filtro de tareas sintéticas | listas, condiciones y autorización simulada | AI Health Agent CRM |
| Revisor de versiones | objetos, iteraciones | byDebut |
| Analizador de resultados de frames | listas y métricas | JetImage |

No alterar repositorios productivos ni exponer información de clientes/pólizas/mercados.

## 7. Ejemplo guiado: clasificador de conciliación

**Requisito:** dadas venta y pagos ficticios, producir diferencia y estado, con tolerancia cero.

```text
FUNCIÓN clasificar(ventas, pagos)
    VALIDAR que ambos sean importes no negativos
    diferencia = pagos - ventas
    SI diferencia = 0
        estado = "CUADRADO"
    SINO SI diferencia < 0
        estado = "FALTANTE"
    SINO
        estado = "SOBRANTE"
    FIN SI
    DEVOLVER diferencia, estado
FIN FUNCIÓN
```

**Python de referencia didáctica:**
```python
from decimal import Decimal

def clasificar(ventas: Decimal, pagos: Decimal):
    if ventas < 0 or pagos < 0:
        raise ValueError("Los importes deben ser no negativos")
    diferencia = pagos - ventas
    if diferencia == 0:
        estado = "CUADRADO"
    elif diferencia < 0:
        estado = "FALTANTE"
    else:
        estado = "SOBRANTE"
    return diferencia, estado

assert clasificar(Decimal("500000"), Decimal("490000")) == (Decimal("-10000"), "FALTANTE")
```

**Casos para verificar:** 500000/500000 → CUADRADO; 500000/490000 → FALTANTE; 500000/510000 → SOBRANTE; entrada negativa → rechazo. Evitar convertir valores monetarios desde `float` sin política explícita; validar tipos en una implementación real.

## 8. Retrospectiva de fin de semana (10–15 min dentro de sesión 5)

Responder con evidencia:
1. ¿Qué 2–3 conceptos pude explicar sin apuntes?
2. ¿Qué programa modifiqué y dónde está el commit?
3. ¿Qué pruebas ejecuté y cuáles fallaron?
4. ¿Qué error tuve y cómo encontré su causa?
5. ¿Qué conseguí sin ayuda y qué necesitó ChatGPT/Claude?
6. ¿Cuál es el cuello de botella para la próxima semana?
7. ¿Mantengo los conceptos o ajusto el nivel/duración?

**Regla de adaptación:** si no puedo explicar y resolver una variación, repetir el concepto antes de avanzar. Si puedo resolver y justificar, pasar a dificultad ligeramente superior. Si hay fatiga, reducir alcance y conservar descanso.

## 9. Métricas semanales sin inventar avance

| Métrica | Meta orientativa | Medición |
| --- | --- | --- |
| Sesiones | 5 previstas | realizadas con fecha y evidencia |
| Tiempo | 300 min previstos | duración real registrada |
| Conceptos | 2–3 | explicación propia de cada uno |
| Microproducto | 1 | ejecución/commit enlazado |
| Pruebas | normal, borde, error | resultados reales, no supuestos |
| Autonomía | progresiva | distinguir pista, código generado y resolución propia |
| Retrospectiva | 1 | decisión para semana siguiente |

Rúbrica 0 sin evidencia, 1 identifica, 2 resuelve guiado, 3 resuelve/depura autónomamente, 4 transfiere y justifica. Evaluar solo si se observó desempeño.

## 10. Plantilla semanal reutilizable

```markdown
# Semana [N] — práctica Big School
Periodo efectivo: [pendiente]
Conceptos (2–3):
Microproyecto:
Entradas/salidas:
Pseudocódigo:
Criterios de aceptación:
- [ ] Caso normal
- [ ] Caso límite
- [ ] Caso de error

| Sesión | Fecha | Minutos reales | Qué intenté | Pruebas/resultado | Evidencia | Estado |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | | | | | | Pendiente |
| 2 | | | | | | Pendiente |
| 3 | | | | | | Pendiente |
| 4 | | | | | | Pendiente |
| 5 | | | | | | Pendiente |

Qué aprendí sin apuntes:
Errores y correcciones:
Ayuda de IA recibida:
Qué puedo modificar de forma autónoma:
Principal bloqueo:
Decisión siguiente semana:
```

## 11. Definición de terminado

- [ ] Seleccionados 2–3 conceptos compatibles con el plan de estudio.
- [ ] Escrito problema, entradas, salidas y algoritmo.
- [ ] Intento personal y ejercicio pequeño.
- [ ] Código ejecutado y pruebas registradas.
- [ ] Explicación y variación propia.
- [ ] Evidencia versionada en GitHub.
- [ ] Retrospectiva y seguimiento en Obsidian.

**Próxima acción:** iniciar la semana 1 cuando se confirme fecha efectiva; no asignar resultados ni marcar casillas sin evidencia.
