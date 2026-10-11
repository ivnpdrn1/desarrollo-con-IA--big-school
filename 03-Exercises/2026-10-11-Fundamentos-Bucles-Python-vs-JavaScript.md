# Fundamentos: bucles en Python y JavaScript

**Fecha:** 2026-10-11  
**Tipo:** Ejercicio comparativo de Big School  
**Estado:** material y solución de referencia preparados; ejecución personal pendiente.

## Objetivo
Comprender que la lógica de iteración es independiente de la sintaxis. Poder predecir, explicar, ejecutar, cambiar y probar un bucle `for` en Python y JavaScript; reconocer variables, colecciones, acumuladores, condiciones y terminación.

## 1. Modelo conceptual
Un bucle repite instrucciones. El `for` recorre elementos; un `while` repite mientras su condición sea verdadera. En ambos debemos verificar la condición de terminación y evitar mutaciones que produzcan resultados inesperados.

Pseudocódigo:
```text
crear colección de ventas
inicializar total en cero
para cada venta:
    sumar venta al total
mostrar el total
```

| Concepto | Explicación | Ejemplo |
| --- | --- | --- |
| Variable | nombre asociado a un valor | total |
| Colección | valores procesables | ventas |
| Iteración | una pasada por el cuerpo del bucle | procesar una venta |
| Acumulador | conserva resultado parcial | total += venta |
| Condición/terminación | determina cuándo acaba | sin elementos restantes |

## 2. Comparación básica

Python:
```python
ventas = [100, 200, 300]
total = 0
for venta in ventas:
    total += venta
print(total)  # 600
```

JavaScript:
```javascript
const ventas = [100, 200, 300];
let total = 0;
for (const venta of ventas) {
  total += venta;
}
console.log(total); // 600
```

| Decisión lógica | Python | JavaScript |
| --- | --- | --- |
| Declarar colección | ventas = [...] | const ventas = [...] |
| Variable acumuladora | total = 0 | let total = 0 |
| Iterar valores | for venta in ventas: | for (const venta of ventas) { ... } |
| Bloque | indentación obligatoria | llaves |
| Acumular | total += venta | total += venta |
| Salida | print(total) | console.log(total) |

`for...of` en JavaScript recorre valores; `for...in` recorre claves de propiedades, por lo que no es el equivalente apropiado para este arreglo.

## 3. Laboratorio aplicado: galones vendidos

### Problema
El islero registra cuatro despachos sintéticos: 12.5, 18.25, 9.75, 15.5 galones. Calcular el total de galones sin tocar el sistema operativo ni consultar datos reales.

### Python
```python
def total_galones(despachos):
    total = 0.0
    for galones in despachos:
        if not isinstance(galones, (int, float)) or isinstance(galones, bool):
            raise TypeError("Cada despacho debe ser numérico")
        if galones < 0:
            raise ValueError("No se admiten galones negativos")
        total += galones
    return total

if __name__ == "__main__":
    datos = [12.5, 18.25, 9.75, 15.5]
    print(f"Total: {total_galones(datos):.2f} galones")
```

### JavaScript
```javascript
function totalGalones(despachos) {
  let total = 0;
  for (const galones of despachos) {
    if (typeof galones !== "number" || !Number.isFinite(galones)) {
      throw new TypeError("Cada despacho debe ser numérico y finito");
    }
    if (galones < 0) {
      throw new RangeError("No se admiten galones negativos");
    }
    total += galones;
  }
  return total;
}

const datos = [12.5, 18.25, 9.75, 15.5];
console.log(`Total: ${totalGalones(datos).toFixed(2)} galones`);
```

**Resultado esperado:** 56.00 galones. Los datos son ficticios y el ejemplo es pedagógico. Para dinero real usar `decimal.Decimal` en Python o enteros de unidad mínima/biblioteca decimal adecuada en JavaScript, y reglas de redondeo explícitas.

### Trazado paso a paso

| Iteración | Dato | Acumulador antes | Acumulador después |
| --- | ---: | ---: | ---: |
| 1 | 12.50 | 0.00 | 12.50 |
| 2 | 18.25 | 12.50 | 30.75 |
| 3 | 9.75 | 30.75 | 40.50 |
| 4 | 15.50 | 40.50 | 56.00 |

## 4. for vs while

Python:
```python
indice = 0
while indice < len(despachos):
    total += despachos[indice]
    indice += 1
```

JavaScript:
```javascript
let indice = 0;
while (indice < despachos.length) {
  total += despachos[indice];
  indice += 1;
}
```

En estos fragmentos se presupone que `despachos` y `total` ya existen y que `total` fue inicializado a cero. El índice debe avanzar o el bucle podría no terminar.

## 5. Ejercicios graduados (sin resolver automáticamente)

1. Predecir la suma sin ejecutar código.
2. Cambiar el tercer despacho a 10 y explicar la variación.
3. Agregar un quinto despacho.
4. Hallar número de operaciones y promedio; evitar dividir entre cero.
5. Identificar el despacho de mayor volumen; manejar lista vacía.
6. Rechazar entradas negativas y no numéricas.
7. Convertir la solución a `while`.
8. Usar una lista de diccionarios/objetos con `producto` y `galones` y acumular por producto.
9. Extender a ventas en unidades monetarias con tipos adecuados y pruebas.
10. Explicar diferencias entre `for...of` y `for...in` en JavaScript.

## 6. Pruebas recomendadas

| Entrada | Resultado esperado |
| --- | --- |
| [12.5, 18.25, 9.75, 15.5] | 56 |
| [] | 0 |
| [10] | 10 |
| [0, 1] | 1 |
| [-1, 10] | error |
| [5, "3"] | error |
| [2.5, 3.25] | 5.75 |
| [0, 0] | 0 |

Python, ejemplo de pytest:
```python
import pytest
from modulo import total_galones

@pytest.mark.parametrize("datos, esperado", [
    ([12.5, 18.25, 9.75, 15.5], 56),
    ([], 0),
    ([10], 10),
    ([0, 1], 1),
    ([2.5, 3.25], 5.75),
])
def test_totales(datos, esperado):
    assert total_galones(datos) == pytest.approx(esperado)

def test_negativos():
    with pytest.raises(ValueError):
        total_galones([-1])

def test_tipos():
    with pytest.raises(TypeError):
        total_galones([5, "3"])
```

Ejecutar: `python -m pytest`. No afirmar que las pruebas se ejecutaron hasta verificarlo en el entorno.

## 7. Preguntas de comprensión
- ¿Por qué total comienza en cero?
- ¿Qué cambia si `total += galones` se coloca fuera del bucle?
- ¿Qué diferencia existe entre procesar valores e índices?
- ¿Qué sucede con lista vacía?
- ¿Qué problema genera usar `while` sin actualizar el índice?
- ¿En qué fase corresponde validar datos?
- ¿Cómo explicaría un cambio del precio por producto sin reescribir el cálculo de galones?

## 8. Rubrica (0–4)
0 sin evidencia; 1 identifica componentes; 2 explica el trazado con ayuda; 3 implementa y depura por su cuenta; 4 adapta a otra estructura y justifica las pruebas. No asignar nivel sin evidencia.

## 9. Definición de terminado
- [ ] Ejecutar Python y JavaScript.
- [ ] Predecir y comprobar el resultado.
- [ ] Completar tabla de iteraciones sin ayuda.
- [ ] Resolver al menos 4 extensiones.
- [ ] Ejecutar pruebas y documentar resultado.
- [ ] Explicar los fallos corregidos.
- [ ] Registrar aprendizaje en Obsidian y enlazar el commit.

## 10. Conexiones a proyectos
- Gas Station Operations: acumulación de galones y pagos por categoría.
- MarketMirrorAI: procesamiento por iteración de eventos/velas y señales sin operar dinero real.
- AI Health Agent CRM: recorrer tareas o pólizas sintéticas.
- byDebut: recorrer versiones/historias y validarlas.
- JetImage: procesar lotes de frames o detecciones.
- AWS-Onion: recorrer recursos de infraestructura y revisar configuraciones.

**Principio transferible:** lenguaje diferente ≠ lógica diferente; fundamentos de datos, control de flujo y validación permiten razonar sobre cualquier stack.

## 11. Próxima práctica
Funciones y estructuras de datos: agrupar despachos por producto; introducir pruebas de datos faltantes y separar cálculo puro de interfaz y persistencia.
