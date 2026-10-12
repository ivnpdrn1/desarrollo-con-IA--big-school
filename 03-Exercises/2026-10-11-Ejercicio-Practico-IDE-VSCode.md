# Ejercicio práctico: Familiarízate con tu IDE — VS Code

**Fecha de incorporación:** 2026-10-11  
**Origen:** lección MoureDev Pro «Ejercicio práctico: IDE» (captura suministrada).  
**Estado:** instrucciones y código de referencia preparados; ejecución local del alumno pendiente.  
**Relaciones:** [Lección IDE](../01-Class-Notes/2026-10-11-IDE-VSCode-Debugging.md), [Learning by Doing](../01-Class-Notes/2026-10-11-Practica-Learning-by-Doing.md), [Pseudocódigo](../02-Concepts/Pseudocodigo-Guia-Conceptual-y-Ejemplos.md), [Plan de estudio 5 × 60](./2026-10-11-Plan-de-Estudio-Personalizado.md).

## Propósito y alcance

Usar VS Code en Windows con Python para completar **los cinco objetivos del ejercicio**: proyecto pequeño con variables/condicionales/bucles, atajos, breakpoint y ejecución paso a paso, autocompletado y exploración del entorno. Se trabaja con datos **totalmente ficticios** de despachos de Gas Station Operations, en una carpeta local de práctica, sin conexión a estaciones ni credenciales reales.

## Sesión de 60 minutos (dentro de las 5 horas semanales)

| Minutos | Actividad | Resultado |
| --- | --- | --- |
| 0–5 | objetivo y reconocimiento del editor | carpeta de laboratorio |
| 5–20 | pseudocódigo y pequeño programa Python | archivo `galonaje_ide.py` |
| 20–25 | descanso | pausa |
| 25–35 | atajos, búsqueda, comentarios y autocompletado | funciones localizadas y editadas |
| 35–50 | breakpoint, Locals, Watch y pasos | traza de tres iteraciones |
| 50–60 | pruebas, diff y explicación personal | registro del ejercicio |

Si una fase necesita más tiempo, continúa en otra sesión de 60 minutos sin sobrecargar la agenda.

## 1. Crear un proyecto simple

Abrir VS Code y seleccionar `File > Open Folder...`. Usar una carpeta local separada, por ejemplo `big-school-ide-lab`. Comprobar que Python está instalado desde la terminal integrada (`Terminal > New Terminal`): `py --version` o `python --version`. Usar `Python: Select Interpreter` para elegir el intérprete correcto; crear entorno virtual cuando el proyecto tenga dependencias. Instalar extensión Python desde un editor confiable si aún no existe.

### Requisito
Dado un conjunto ficticio de galones, sumar valores y clasificar el total según un umbral didáctico. Introducimos:
- **variable** `total`;
- **bucle** `for`;
- **condicional** `if/else`;
- **función** con entrada y retorno.

### Pseudocódigo
```text
RECIBIR despachos
INICIAR total EN CERO
PARA CADA cantidad EN despachos
    VALIDAR que cantidad es numérica y no negativa
    ACUMULAR cantidad en total
FIN PARA
SI total >= 40
    estado = "ALTO"
SINO
    estado = "NORMAL"
FIN SI
DEVOLVER total, estado
```

### Código de referencia (`galonaje_ide.py`)
```python
def analizar_galones(despachos):
    total = 0
    for cantidad in despachos:
        if isinstance(cantidad, bool) or not isinstance(cantidad, (int, float)):
            raise TypeError("La cantidad debe ser numérica")
        if cantidad < 0:
            raise ValueError("No se admiten galones negativos")
        total += cantidad

    estado = "ALTO" if total >= 40 else "NORMAL"
    return total, estado


if __name__ == "__main__":
    datos = [10, 15, 20]
    total, estado = analizar_galones(datos)
    print(f"Total: {total} galones; estado: {estado}")
```

**Resultado esperado:** `Total: 45 galones; estado: ALTO`. El umbral de 40 galones es ficticio para enseñar condicionales; no representa regla de la estación. En producción harían falta más controles de valores finitos, precisión y reglas operativas.

## 2. Practicar atajos (Windows, configuración predeterminada)

| Tarea concreta | Atajo habitual |
| --- | --- |
| Guardar el archivo | Ctrl+S |
| Comentar/descomentar línea seleccionada | Ctrl+/ |
| Buscar en archivo | Ctrl+F |
| Buscar en todos los archivos | Ctrl+Shift+F |
| Abrir archivo rápido | Ctrl+P |
| Paleta de comandos | Ctrl+Shift+P |
| Renombrar símbolo | F2 |
| Ir a definición | F12 |
| Abrir terminal integrada | Ctrl+` |
| Colocar/quitar breakpoint | F9 |
| Iniciar/continuar debug | F5 |
| Step Over | F10 |
| Step Into | F11 |

**Microtarea:** buscar `total`; comentar temporalmente `print`, deshacer el comentario, renombrar `estado` mediante F2 y guardar. Los atajos pueden variar según distribución del teclado o asignaciones personales.

## 3. Depurar con breakpoint y seguir el flujo

1. Abrir `galonaje_ide.py` y poner un breakpoint (F9) en `total += cantidad`.
2. Abrir `Run and Debug` (Ctrl+Shift+D) y usar F5; elegir configuración Python si la solicita.
3. Inspeccionar variables `cantidad` y `total` en **Locals**.
4. En **Watch**, agregar `total + cantidad` para anticipar el siguiente acumulado (expresión sin efectos).
5. Avanzar con F10 y continuar con F5 hasta la siguiente iteración.
6. Confirmar el trazado esperado:

| Iteración | cantidad | total antes | total después |
| --- | ---: | ---: | ---: |
| 1 | 10 | 0 | 10 |
| 2 | 15 | 10 | 25 |
| 3 | 20 | 25 | 45 |

**Variación diagnóstica opcional:** cambiar intencionalmente `total += cantidad` por `total = cantidad`, predecir 20, observar la pérdida del acumulado y corregir. No conservar el error en el código final.

## 4. Probar autocompletado

En un nuevo renglón dentro de la función, escribir `despachos.` y examinar las propuestas; luego borrar esa línea de exploración. Teclear `total.` y comparar sugerencias: dependen del tipo inferido, la extensión y la configuración del editor. Utilizar `Ctrl+Space` para invocar sugerencias cuando esté disponible. Verificar que el autocompletado sirve para navegar APIs, no demuestra que una regla de negocio sea correcta.

## 5. Explorar otras áreas del IDE

- **Explorer:** estructura de archivos.
- **Search:** ocurrencias en toda la carpeta.
- **Run and Debug:** breakpoints, variables y Call Stack.
- **Terminal:** ejecución de `python galonaje_ide.py` (o `py galonaje_ide.py` según entorno).
- **Problems:** diagnósticos.
- **Source Control:** cambios y diff Git si la carpeta está versionada.
- **Extensions:** editor, editor responsable, compatibilidad y permisos antes de instalar.

No ejecutar comandos de IA automáticamente sin revisar archivos y efectos externos. Mantener secretos fuera de repositorios y entornos de práctica.

## 6. Pruebas adicionales

| Entrada | Salida esperada |
| --- | --- |
| `[10,15,20]` | `(45, "ALTO")` |
| `[]` | `(0, "NORMAL")` |
| `[20,20]` | `(40, "ALTO")` |
| `[8,10]` | `(18, "NORMAL")` |
| `[-1]` | `ValueError` |
| `["10"]` | `TypeError` |

No afirmar que las pruebas se ejecutaron hasta verificarlas en VS Code. Para el ejercicio basta explicar y comprobar un caso normal, uno de borde y uno inválido.

## 7. Evidencia y criterio de terminado

- [ ] Carpeta y archivo creados localmente.
- [ ] Python e intérprete confirmados.
- [ ] Código ejecutado y resultado explicado.
- [ ] Atajos Guardar, Buscar y Comentar practicados.
- [ ] Breakpoint detuvo la ejecución.
- [ ] Variables inspeccionadas en Locals/Watch.
- [ ] Tres iteraciones trazadas y resultado contrastado.
- [ ] Autocompletado probado.
- [ ] Al menos tres casos probados.
- [ ] Diff revisado, errores corregidos y explicación propia redactada.
- [ ] Evidencia registrada en GitHub/Obsidian.

**Estado inicial:** todo por verificar; el material técnico no demuestra aprendizaje ya realizado.

## 8. Vínculo a competencias y proyectos

El mismo procedimiento sirve para depurar funciones en Gas Station Operations, transformaciones de datos de MarketMirrorAI, backend CRM sintético, rutas de ejecución de byDebut, scripts de AWS-Onion y herramientas de agentes. La disciplina reutilizable es **anticipar → ejecutar → inspeccionar → corregir → probar → documentar**.
