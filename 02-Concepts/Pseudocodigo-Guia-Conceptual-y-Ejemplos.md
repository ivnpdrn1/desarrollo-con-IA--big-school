# Pseudocódigo — De los problemas a algoritmos verificables

**Fecha:** 2026-10-11  
**Nivel:** fundamentos; concepto transversal  
**Relacionado con:** [Mecánicas de aprendizaje](../01-Class-Notes/2026-10-11-Mecanicas-de-Aprendizaje.md), [Bucles Python vs JavaScript](../03-Exercises/2026-10-11-Fundamentos-Bucles-Python-vs-JavaScript.md).

## 1. Definición

El pseudocódigo describe un algoritmo mediante instrucciones legibles, sin depender de la sintaxis de un lenguaje. No es código ejecutable, no tiene una gramática universal y no sustituye las pruebas. Su función es aclarar **entradas → transformaciones → decisiones/repeticiones → salidas → validaciones**, antes de implementar.

**Diferencias:**
- Requisito: **qué** quiere el usuario.
- Algoritmo: **cómo** se resolverá mediante pasos finitos y definidos.
- Pseudocódigo: representación textual del algoritmo.
- Diagrama de flujo: representación gráfica de la secuencia y decisiones.
- Código: implementación bajo reglas estrictas de un lenguaje.
- Pruebas: evidencia de comportamiento ante entradas específicas.

## 2. Construcción en siete pasos

1. Formular problema y resultado esperado.
2. Delimitar alcance, precondiciones y supuestos.
3. Identificar entradas, tipos, unidades y fuentes.
4. Identificar salidas y criterios de aceptación.
5. Dividir el problema en funciones pequeñas con responsabilidad única.
6. Escribir secuencias, condiciones y ciclos, incluyendo casos vacíos, errores y terminación.
7. Hacer un trazado manual con casos normal, límite y error; entonces traducir a código y probar.

## 3. Vocabulario recomendado

| Operación | Convención didáctica | Implementación habitual |
| --- | --- | --- |
| Inicio y fin | INICIO / FIN | función o bloque |
| Entrada | RECIBIR / LEER | argumento/input/API |
| Asignación | ASIGNAR x = valor | = |
| Condición | SI / SINO / FIN SI | if / else |
| Recorrido | PARA CADA / FIN PARA | for |
| Repetición condicional | MIENTRAS / FIN MIENTRAS | while |
| Operación | CALCULAR / SUMAR | expresión |
| Subrutina | FUNCIÓN / FIN FUNCIÓN | def / function |
| Retorno | DEVOLVER | return |
| Salida de usuario | MOSTRAR | print/UI/log |
| Rechazo | RECHAZAR / ERROR | excepción o resultado de error |

Convenciones claras importan más que la palabra elegida. Nunca depender de variables sin inicializar o de condiciones que no terminen.

## 4. Ejemplo A — Suma de galones (secuencia + bucle)

**Entrada:** [10, 15, 20] galones. **Salida:** 45 galones.

```text
INICIO
  RECIBIR despachos
  ASIGNAR total = 0
  PARA CADA cantidad EN despachos
    SUMAR cantidad AL total
  FIN PARA
  DEVOLVER total
FIN
```

Python:
```python
def sumar_galones(despachos):
    total = 0
    for cantidad in despachos:
        total += cantidad
    return total

assert sumar_galones([10, 15, 20]) == 45
assert sumar_galones([]) == 0
```

JavaScript:
```javascript
function sumarGalones(despachos) {
  let total = 0;
  for (const cantidad of despachos) {
    total += cantidad;
  }
  return total;
}
console.assert(sumarGalones([10, 15, 20]) === 45);
console.assert(sumarGalones([]) === 0);
```

El ejemplo presupone cantidades válidas; la validación se añade al pasar del ejemplo didáctico a un contrato más robusto.

## 5. Ejemplo B — Condicional

**Entradas:** venta = 500000 COP; pagos = 490000 COP.  
**Convención:** diferencia = pagos - ventas; negativo = faltante; positivo = sobrante.

```text
INICIO
  RECIBIR venta_calculada, pagos_recibidos
  diferencia = pagos_recibidos - venta_calculada
  SI diferencia = 0 ENTONCES
    estado = "CUADRADO"
  SINO SI diferencia < 0 ENTONCES
    estado = "FALTANTE"
  SINO
    estado = "SOBRANTE"
  FIN SI
  DEVOLVER diferencia, estado
FIN
```

Python:
```python
def estado_cuadre(venta, pagos):
    diferencia = pagos - venta
    if diferencia == 0:
        estado = "CUADRADO"
    elif diferencia < 0:
        estado = "FALTANTE"
    else:
        estado = "SOBRANTE"
    return diferencia, estado

assert estado_cuadre(500000, 490000) == (-10000, "FALTANTE")
```

Para importes reales, definir tipo `Decimal` o unidades enteras mínimas, reglas de redondeo, tolerancia configurable y validación de valores; no trasladar este ejemplo directamente a producción.

## 6. Ejemplo C — Divide y vencerás: conciliación

**Contrato de entrada:** despachos con producto, volumen y precio; pagos con medio e importe. Todos sintéticos en prácticas; catálogos válidos definidos por configuración.  
**Contrato de salida:** venta total, pagos totales, diferencia, estado y errores de validación, sin efectos externos.

```text
FUNCIÓN conciliar_turno(despachos, pagos, configuración)
  errores = VALIDAR_ENTRADAS(despachos, pagos, configuración)
  SI errores NO ESTÁ VACÍO
    DEVOLVER resultado_de_error(errores)
  FIN SI

  ventas = CALCULAR_VENTAS(despachos, configuración)
  recibido = SUMAR_PAGOS(pagos)
  diferencia = recibido - ventas
  estado = CLASIFICAR_DIFERENCIA(diferencia, configuración.tolerancia)

  DEVOLVER { ventas, recibido, diferencia, estado }
FIN FUNCIÓN
```

**Subfunciones:** validar, calcular venta, sumar pagos, clasificar diferencia, construir resultado.  
**No incluir:** escrituras en base de datos, acciones productivas o acceso a datos reales en la versión pedagógica.

### Trazado de ejemplo
| Paso | Valor |
| --- | --- |
| Total venta calculada | 500000 COP |
| Pagos | 490000 COP |
| Diferencia | -10000 COP |
| Estado con tolerancia 0 | FALTANTE |

## 7. Ejemplo D — MarketMirrorAI: eventos sin operación financiera

```text
RECIBIR lista de eventos simulados
PARA CADA evento
  SI evento NO ES VÁLIDO
    REGISTRAR error de validación
    CONTINUAR CON siguiente evento
  FIN SI
  NORMALIZAR evento
  CALCULAR indicadores según reglas versionadas
  CLASIFICAR señal
  REGISTRAR resultado en memoria de prueba
FIN PARA
DEVOLVER registros y errores
```

Detallar reglas e indicadores antes de implementar. No enviar órdenes, ni conectar con ejecución real. El pseudocódigo ilustra la estructura, no define una estrategia comercial o de inversión.

## 8. Ejemplo E — Agentes/Harness: permisos y aprobación

```text
RECIBIR solicitud
IDENTIFICAR objetivo y herramientas permitidas
SI la solicitud supera el alcance permitido
  RECHAZAR y registrar motivo
FIN SI

PREPARAR plan y criterios de evaluación
PARA CADA paso del plan
  VALIDAR parámetros y permisos
  SI el paso produce un efecto externo sensible
    SOLICITAR aprobación humana
    SI aprobación NO otorgada
      DETENER o SALTAR el paso según política
    FIN SI
  FIN SI
  EJECUTAR herramienta autorizada
  VALIDAR resultado y registrar evidencia
FIN PARA
DEVOLVER informe verificable
```

La revisión/aprobación es una condición de control, no solo una frase en un prompt; en la implementación debe hacerse cumplir por los límites de herramientas y permisos.

## 9. Ejemplo F — CRM de salud: autorización

```text
RECIBIR usuario_autenticado y solicitud
VALIDAR identidad y permisos para el recurso
SI falta autorización
  RECHAZAR acceso y registrar evento de seguridad
SINO
  ACCEDER solo a campos necesarios
  PROCESAR solicitud conforme a reglas aplicables
  DEVOLVER resultado permitido
FIN SI
```

Usar datos sintéticos en ejercicios, sin información protegida de personas. El pseudocódigo no demuestra cumplimiento normativo: eso requiere arquitectura y controles adicionales.

## 10. Errores comunes

- Describir el objetivo sin especificar pasos.
- Hacer un solo bloque gigantesco.
- Omitir unidades, supuestos, permisos y entradas inválidas.
- Confundir `MOSTRAR` (presentación) con `DEVOLVER` (resultado de una función).
- Utilizar variables antes de inicializarlas.
- Diseñar `MIENTRAS` sin condición de finalización garantizada.
- No probar casos vacíos, de frontera o errores.
- Tratar el pseudocódigo como evidencia de que el software funciona.

## 11. Técnica de examen mental

Ante cualquier solución, preguntar:
1. ¿Qué problema exacto resuelve?
2. ¿Qué información recibe y en qué unidades?
3. ¿Cuáles son sus transformaciones?
4. ¿Qué decisiones y repeticiones existen?
5. ¿Cuándo termina?
6. ¿Qué devuelve si todo funciona?
7. ¿Qué ocurre si falla una validación?
8. ¿Qué efectos externos pueden producirse y quién los autoriza?
9. ¿Qué casos de prueba demuestran el resultado?

## 12. Ejercicios de práctica

1. Escribir pseudocódigo de promedio de 5 calificaciones y manejar lista vacía.
2. Traducir el acumulador de galones a Python y JavaScript.
3. Crear pseudocódigo de máximos y mínimos de una colección.
4. Refactorizar la conciliación en las cinco funciones propuestas.
5. Incorporar pagos por efectivo, transferencia y vales configurables.
6. Transformar el ejemplo de MarketMirrorAI en diagrama de flujo sin conectarlo a órdenes reales.
7. Construir un algoritmo de permisos por rol en CRM usando registros ficticios.
8. Diseñar la aprobación de una herramienta de agente que modifica datos.

**Rúbrica:** 0 sin evidencia; 1 distingue entrada/salida; 2 estructura secuencia y condición guiado; 3 diseña y prueba por sí mismo; 4 separa funciones, controla errores y justifica decisiones. No asignar puntuación sin práctica real.

## 13. Checklist antes de pasar a código

- [ ] Alcance y objetivo expresados con claridad.
- [ ] Entradas y salidas identificadas.
- [ ] Unidades, tipos y validaciones definidos.
- [ ] Secuencia, decisiones y bucles trazables.
- [ ] Terminación garantizada.
- [ ] Funciones con responsabilidades delimitadas.
- [ ] Casos normales, frontera y error definidos.
- [ ] Efectos externos y autorizaciones identificados.
- [ ] Traducción a un lenguaje y pruebas pendientes o verificadas de forma explícita.

## 14. Secuencia pedagógica

**Problema real → requisitos → pseudocódigo → traza de escritorio → implementación → pruebas → GitHub → explicación propia en Obsidian → retrospectiva.**

El pseudocódigo es una herramienta para razonar, no para reemplazar ingeniería de requisitos, pruebas ni revisión humana.
