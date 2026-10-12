# IDE — Entorno de Desarrollo Integrado: VS Code y depuración

**Fecha:** 2026-10-11. **Origen:** MoureDev Pro, lección «Entorno de desarrollo integrado (IDE)», seis puntos de las capturas proporcionadas.  
**Estado:** guía y práctica propuestas; no se afirma instalación o ejecución verificada en equipo local.  
**Conexiones:** [Learning by Doing](./2026-10-11-Practica-Learning-by-Doing.md), [Pseudocódigo](../02-Concepts/Pseudocodigo-Guia-Conceptual-y-Ejemplos.md), [Plan de estudio 5×60](../03-Exercises/2026-10-11-Plan-de-Estudio-Personalizado.md).

## Objetivo

Dominar **VS Code** como entorno de trabajo para Python, TypeScript y Claude Code: editar, navegar, ejecutar, depurar, probar y versionar código explicando el flujo del programa. IDE es el conjunto integrado de editor, ejecución, diagnósticos, depurador y herramientas auxiliares; VS Code es un editor extensible que ofrece capacidades de IDE mediante extensiones. Un IDE no reemplaza la comprensión del algoritmo.

## 1. Las seis capacidades de la lección

### A. Qué es un IDE
- Editor: escritura de archivos.
- Language Server/extensiones: reconocimiento del lenguaje, diagnósticos, autocompletado y navegación.
- Terminal integrada: procesos y comandos reproducibles.
- Depurador: inspeccionar estados, llamadas y ejecución.
- Test runner: ejecutar y localizar fallos.
- Control de código fuente: Git, diff, commits.
- No confundir editor, intérprete de Python, entorno virtual, terminal, Git y Claude Code: son herramientas distintas que interoperan.

### B. Atajos VS Code (Windows, configuración predeterminada)
| Operación | Atajo | Motivo |
| --- | --- | --- |
| Command Palette | Ctrl+Shift+P | encontrar cualquier comando |
| Buscar archivo | Ctrl+P | navegar sin árbol |
| Buscar texto en proyecto | Ctrl+Shift+F | localizar usos |
| Ir a definición | F12 | comprender dependencia |
| Volver | Alt+Left | recorrer navegación |
| Renombrar símbolo | F2 | refactorización asistida |
| Comentar/descomentar | Ctrl+/ | probar variaciones |
| Formatear documento | Shift+Alt+F | legibilidad |
| Terminal integrada | Ctrl+` | ejecutar código/pruebas |
| Panel de depuración | Ctrl+Shift+D | ver variables y pila |
| Iniciar/continuar debugging | F5 | reproducir falla |
| Paso por encima | F10 | siguiente línea sin entrar |
| Entrar a función | F11 | inspeccionar llamada |
| Salir de función | Shift+F11 | volver a caller |
| Alternar breakpoint | F9 | detener ejecución |
| Panel de extensiones | Ctrl+Shift+X | herramientas instaladas |

Atajos sujetos a distribución de teclado, personalizaciones, sistema y keybindings vigentes. Revisar en `File > Preferences > Keyboard Shortcuts`.

### C. Autocompletado e IntelliSense
Sugerencias de atributos, tipos, firmas y nombres. Para Python, usar extensión Python y soporte Pylance según configuración; para TS, soporte integrado de lenguaje. Confirmar versión y entorno virtual antes de fiarse de tipos. Un autocompletado no prueba que la lógica sea correcta.

### D. Depuración
**Breakpoint** detiene una ejecución para inspeccionar valores.  
**Step Over (F10):** avanza sobre llamada sin entrar; **Step Into (F11):** entra; **Step Out (Shift+F11):** termina función actual; **Continue (F5):** prosigue hasta próximo punto.  
**Locals / Watch / Call Stack:** observar variables, expresiones y cadena de llamadas.  
Preguntas: ¿cuál era el valor esperado?, ¿cuál es el real?, ¿en qué línea divergen?, ¿qué entrada lo provoca?

### E. Funciones adicionales
Refactorizar con `F2` después de revisar referencias; usar **Git diff** antes de aceptar cambios asistidos por IA; terminal para `python --version`, `python -m pytest`, `git status`; extensiones mínimas, confiables y actualizadas. Seleccionar intérprete correcto (`Python: Select Interpreter`), configurar `.venv` en cada proyecto y excluir secretos/entornos de Git. No ejecutar propuestas de Claude sin revisar permisos, archivos afectados y pruebas.

### F. Comparación razonada
| Herramienta | Enfoque | Elección para nuestros proyectos |
| --- | --- | --- |
| VS Code | editor extensible, Python, TS, Git, terminal, extensiones, Claude Code | **principal**, por continuidad del flujo actual |
| IntelliJ IDEA | IDE potente orientado al ecosistema JVM | considerar si aparece trabajo Java/Kotlin |
| PyCharm | IDE dedicado al desarrollo Python | alternativa si el proyecto Python necesita funciones integradas específicas |
| Android Studio | IDE de Android, emuladores y SDK | solo si construimos app nativa Android |
| Visual Studio | IDE completo especialmente .NET/C++ | solo si se demanda ese ecosistema |

No migrar herramientas por moda. Evaluar facilidad de depuración, lenguajes, hardware, licencias/costo, integración con Git/Claude y complejidad operativa.

## 2. Arquitectura mental del trabajo

```text
Requisito de negocio
  ↓
Pseudocódigo y criterios
  ↓
VS Code: archivos y editor
  ↔ lenguaje / intérprete / dependencias
  ↔ Claude Code para asistencia supervisada
  ↓
Terminal → ejecución y tests
  ↓
Debugger → breakpoints / valores / stack
  ↓
Git diff → revisión → commit
  ↓
GitHub → trazabilidad
  ↓
Obsidian → conocimiento, decisiones, progreso
```

## 3. Práctica guiada: rastrear un error

Ejemplo independiente, datos ficticios; crear `galonaje_debug.py`:
```python
def sumar_galones(despachos):
    total = 0
    for galones in despachos:
        total = galones  # ERROR INTENCIONAL: reemplaza, no acumula
    return total

if __name__ == "__main__":
    datos = [10, 15, 20]
    print(sumar_galones(datos))  # obtiene 20, se esperaba 45
```

**Pseudocódigo esperado:**
```text
INICIAR total = 0
PARA CADA galones EN despachos:
    SUMAR galones AL total
DEVOLVER total
```

**Pasos para depurar en VS Code**
1. Abrir una carpeta de práctica aislada; confirmar el intérprete Python instalado y seleccionado.
2. Crear el archivo y predecir el resultado correcto (45).
3. Colocar breakpoint en la asignación dentro de `for` con F9.
4. Iniciar depuración (F5), elegir configuración Python si se solicita.
5. Ver `total` en Locals antes y después de cada vuelta; usar F10 para avanzar.
6. Identificar que `total = galones` pierde el acumulado de iteraciones anteriores.
7. Corregir a `total += galones`.
8. Ejecutar y comprobar 45. Probar `[]` → 0 y `[7]` → 7.
9. Revisar el diff, registrar qué cambió y por qué.

**Importante:** no declarar ejecutado el ejercicio sin observar el entorno local. Como evolución, crear pruebas pytest automatizadas y entradas inválidas.

## 4. Checklist de configuración VS Code
- [ ] `code --version` si CLI disponible.
- [ ] Python instalado y verificable con `python --version` o `py --version` (Windows).
- [ ] Extensión Python confiable y depuración según versión.
- [ ] Intérprete del proyecto seleccionado; entorno virtual cuando corresponda.
- [ ] Terminal integrada abre el directorio correcto.
- [ ] Git reconoce repo, usuario y cambios; no versionar `.env`, credenciales ni `.venv`.
- [ ] Puedo usar breakpoint, Step Over, Watch y Call Stack.
- [ ] Puedo ejecutar tests y revisar Git diff.
- [ ] Asistencia Claude Code bajo revisión humana y permisos acotados.

## 5. Aplicación por proyecto
- **Gas Station Operations:** recorrer función de conciliación, validar reglas y tests antes de cambios de producción.
- **MarketMirrorAI:** depurar transformaciones de eventos con datos simulados, sin ejecución bursátil.
- **byDebut:** navegación TS/Next.js, red de llamadas frontend/backend y errores de tipos.
- **AI Health Agent CRM:** depurar con datos sintéticos; no imprimir secretos o información personal en logs.
- **JetImage:** Python, paquetes compatibles y profiling cuando haya hardware.
- **AWS-Onion:** VS Code + terminal Git + infraestructura como código y revisión de configuraciones.
- **Agents/Harness:** inspeccionar herramientas permitidas, inputs, outputs, logs y approval gates.

## 6. Plan de estudio y evaluación
Dentro de una sesión de 60 minutos: 10 min reconocer interfaz/atajos; 15 min predecir y leer código; 5 min pausa; 20 min depurar; 10 min explicar y registrar. No agregar horas al plan confirmado.

**Criterios observables:** detectar la línea errónea, explicar el estado esperado y real, arreglarlo, repetir casos y registrar diff. Autonomía 0–4 con la rúbrica general y sin inventar avance.

## 7. Recursos recomendados
- VS Code: https://code.visualstudio.com/docs
- Python en VS Code: https://code.visualstudio.com/docs/python/python-tutorial
- Debugging: https://code.visualstudio.com/docs/debugtest/debugging
- Keyboard shortcuts: https://code.visualstudio.com/docs/getstarted/keybindings
- Python: https://docs.python.org/3/
- Git: https://git-scm.com/docs

Son enlaces de referencia; verificar interfaz y versiones vigentes cuando se aplique el laboratorio.

## Próximo paso
Ejecutar la práctica de debugging en VS Code, documentar capturas o traza, tests y errores antes de marcarla completada.

## 8. Profundización práctica — configuración y seguridad del entorno

**Separación de responsabilidades:**
- VS Code gestiona edición, navegación e integración.
- Python instalado ejecuta los programas; `.venv` aísla dependencias por proyecto.
- Git registra versiones locales; GitHub hospeda el repositorio remoto.
- Claude Code asiste mediante su propia integración y permisos; no equivale al depurador.
- Obsidian conserva decisiones, mapas conceptuales y reflexiones.

**Secuencia reproducible en Windows (PowerShell, proyecto aislado):**
```powershell
py --version
mkdir ide-debug-lab
cd ide-debug-lab
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python --version
code .
```
Si PowerShell impide activar scripts, seleccionar el intérprete `.venv\Scripts\python.exe` desde VS Code y ejecutarlo directamente; no cambiar políticas de seguridad globales innecesariamente. `code .` requiere el comando de VS Code disponible en PATH.

**Antes de ejecutar una sugerencia de IA:**
1. Revisar archivos que pretende cambiar y el diff.
2. Comprobar que no incluye secretos, información personal ni cambios de producción.
3. Entender qué espera conseguir y cuál es el criterio de aceptación.
4. Ejecutar pruebas en ambiente local aislado.
5. Aprobar despliegue/operación externa solamente después de revisión.

**Diferencia entre herramientas de depuración:**
- Breakpoint: detiene ejecución en una línea concreta.
- Breakpoint condicional: detiene solo cuando se cumple una expresión.
- Watch: sigue una expresión mientras avanza el programa.
- Call Stack: revela la cadena de funciones que produjo el punto actual.
- Debug Console: evalúa expresiones durante la pausa, sujeto al depurador.
- Logs: registran eventos, pero no sustituyen una inspección controlada del estado.

**Ejercicio de comprensión adicional:** tras corregir `total = galones`, agregar pruebas para `[]`, `[10]` y `[10,15,20]`. Explicar por qué un test del último elemento aislado no detecta el error del acumulador.

### Referencias cruzadas
El ejercicio de IDE se integra con el pseudocódigo, los bucles Python/JavaScript y el plan de práctica semanal. Se considera realizado únicamente con evidencia de ejecución, breakpoint, diagnóstico, corrección y comprobación.
