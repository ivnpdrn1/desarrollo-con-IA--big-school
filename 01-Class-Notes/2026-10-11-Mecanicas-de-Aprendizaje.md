# Mecánicas de aprendizaje — seis técnicas operativas

**Fecha:** 2026-10-11  
**Fuente:** lección «Mecánicas», MoureDev Pro / Big School (capturas aportadas por el estudiante).  
**Estado:** guía de aplicación propuesta, no resultados ya medidos.  
**Relación:** [Estrategia maestra](../00-Project-Overview/Estrategia-Maestra.md), [Plan de acción integral](../03-Exercises/2026-10-11-Plan-de-Accion-Integral.md), [Bucles Python/JavaScript](../03-Exercises/2026-10-11-Fundamentos-Bucles-Python-vs-JavaScript.md).

## Propósito

Convertir cursos y proyectos en comprensión transferible, capacidad de explicar código y autonomía para depurar, en vez de acumular horas de vídeo o prompts. Adaptar las técnicas a formación paralela en programación, AWS, IA y construcción de productos, sin asumir que todas deben ejecutarse simultáneamente.

## Las seis mecánicas

### 1. Lecciones cortas y pausas regulares
**Qué:** estudiar una unidad acotada (por ejemplo 15–25 minutos) y pausar al descubrir una idea nueva.  
**Cómo:** anotar de memoria (a) una definición propia, (b) por qué importa, (c) un ejemplo, (d) una duda; reanudar solo cuando se pueda explicar la idea esencial.  
**Ejemplo:** después de un bucle `for`, explicar colección, elemento, acumulador y terminación; modificar un dato y anticipar salida.  
**Evidencia:** una nota comprensible y una predicción contrastada, no simplemente “vídeo visto”.  
**Cuidado:** no fragmentar tanto que se pierda el contexto general; al final reconstruir la secuencia completa.

### 2. Descansos y retención: Pomodoro flexible
**Qué:** alternar foco y descanso. Ejemplo inicial **25 minutos de foco + 5 de descanso**, con pausa más larga tras 3–4 ciclos; ajustar a energía y complejidad, no considerarlo prescripción universal.  
**Durante el descanso:** apartarse de la tarea; evitar iniciar nuevas tareas cognitivamente demandantes.  
**Antes del descanso:** escribir la siguiente acción para facilitar volver.  
**Después:** recuperación activa: responder sin notas “¿qué problema resolví y por qué funciona?”.  
**Evidencia:** ciclos y objetivos completados, calidad de comprensión y fatiga percibida (1–5). No confundir número de Pomodoros con competencia.

### 3. Divide y vencerás
**Qué:** transformar un problema grande en unidades independientes con entradas, transformación, salida y pruebas.  
**Ejemplo Gas Station, sin afectar producción:** (1) validar despachos → (2) sumar galones → (3) calcular ventas por producto → (4) sumar pagos → (5) comparar y mostrar diferencia.  
**Ejemplo MarketMirrorAI:** recibir evento sintético → validar → normalizar → calcular señal → registrar → comparar contra resultado esperado; sin órdenes bursátiles.  
**Evidencia:** cada función tiene propósito, casos normales/borde/error y contrato comprobable.  
**Antipatrón:** pedir a Claude “construye todo el sistema” sin comprender ni probar los bloques.

### 4. Pseudocódigo antes de sintaxis
**Qué:** expresar el algoritmo en lenguaje claro y sin dependencia de Python/TypeScript.
```text
RECIBIR despachos y pagos de prueba
VALIDAR que los valores son correctos y no negativos
INICIAR total_ventas y total_pagos en cero
PARA CADA despacho:
    CALCULAR venta según volumen y precio
    AGREGAR venta a total_ventas
PARA CADA pago:
    AGREGAR pago a total_pagos
CALCULAR diferencia = total_pagos - total_ventas
MOSTRAR totales, diferencia y resultado
```
**Luego:** escribir primero una función pura pequeña en Python, probarla y solo después traducirla a JavaScript/TypeScript si el caso lo exige.  
**Evidencia:** poder predecir y explicar el algoritmo antes del código.  
**Cuidado:** precisar reglas de redondeo, validación, excepciones y casos vacíos antes de producción; para dinero usar tipos decimales/unidades mínimas.

### 5. Escritura a mano
**Qué:** dibujar el flujo, trazar variables o escribir una explicación propia en papel cuando sea útil. No es obligación para todas las clases ni reemplaza práctica en editor.  
**Actividad:** trazar `total = 0`, luego iteraciones con despachos 12.5, 18.25, 9.75, 15.5: 12.50 → 30.75 → 40.50 → 56.00. Escribir qué cambia si falta un registro.  
**Transferencia:** fotografiar o sintetizar hallazgo en Obsidian, pero registrar una conclusión, no solo una imagen.  
**Evidencia:** explicar la evolución de variables sin mirar el programa.

### 6. Organización y estructura
**Qué:** calendario razonable + objetivos semanales + trazabilidad.  
**Unidad mínima de clase:** nombre/fecha/fuente; cinco ideas clave; tres relaciones con otros conceptos; un ejemplo aplicado; una pregunta abierta; una práctica verificable.  
**Revisión:** al cierre de sesión, decidir próxima acción; semanalmente revisar bloqueos; mensualmente actualizar prioridades y competencias.  
**Límites:** máximo un laboratorio principal y uno secundario, balanceando Big School, AWS y demás formación.  
**Evidencia:** GitHub conserva ejercicios/código/pruebas; Obsidian conecta conceptos, notas y decisiones. Un commit remoto del vault no garantiza que la aplicación Obsidian local ya haya sincronizado.

## Protocolo de sesión de referencia (60 minutos, adaptable)
| Fase | Duración de referencia | Acción | Resultado |
| --- | ---: | --- | --- |
| Objetivo y recuperación | 5 min | escribir qué aprender y recordar sin notas | pregunta guía |
| Estudio focalizado | 20 min | concepto de la lección | idea anotada |
| Pausa | 5 min | descanso breve | retorno consciente |
| Aplicación | 20 min | pseudocódigo, código o prueba | artefacto |
| Recuperación y registro | 10 min | explicar sin apuntes; documentar duda y próximo paso | nota, evidencia y siguiente acción |

La duración no debe sustituir descansos adicionales si son necesarios.

## Aplicación por proyecto
| Proyecto | Unidad de estudio delimitada |
| --- | --- |
| AWS-Onion | dibujar paso a paso usuario → IAM/SSM → EC2 y justificar permisos |
| MarketMirrorAI | descomponer pipeline y probar un evento sintético |
| Gas Station Operations | pseudocódigo y pruebas para conciliación |
| AI Health Agent CRM | descomponer validación, autorización y auditoría con datos ficticios |
| byDebut | trazado de una solicitud desde interfaz hasta persistencia |
| JetImage | procesar un fotograma de prueba y explicar salida |
| Agentes/Harness | especificar herramienta, entrada, permiso, aprobación y resultado |

## Recuperación espaciada (complemento sugerido)
Tras cada tema: intentar recordar al día siguiente, a los 3–4 días y a la semana; reajustar intervalos según errores. Es una propuesta adicional a las seis técnicas de la lección, no una cita de su contenido.

## Indicadores mensurables
- **Comprensión:** explicar en propias palabras sin copiar el material.
- **Transferencia:** resolver variación del ejercicio en otro proyecto.
- **Calidad:** pruebas de casos normales, borde y error.
- **Autonomía:** diagnosticar una modificación sin delegar todo el razonamiento.
- **Sostenibilidad:** sesiones realizables sin fatiga excesiva.
- **Continuidad:** fecha, enlace de evidencia, bloqueo y siguiente acción.

No registrar mejoras cuantitativas sin observaciones reales.

## Checklist por sesión
- [ ] Objetivo en una oración.
- [ ] Una unidad manejable.
- [ ] Pausa y recuperación activa.
- [ ] Problema descompuesto.
- [ ] Pseudocódigo o trazado propio.
- [ ] Prueba o ejercicio aplicado.
- [ ] Nota en Obsidian y referencia GitHub cuando corresponda.
- [ ] Duda y siguiente acción.

## Revisión después de 2 semanas
¿Puedo explicar conceptos que estudié sin video? ¿Estoy aplicando más y consumiendo menos pasivamente? ¿Qué técnica mejoró la comprensión en ejercicios concretos? ¿Qué duración de bloque resulta sostenible? Conservar lo útil y ajustar lo demás.

**Principio rector:** aprender no equivale a completar lecciones; aprender implica recuperar, aplicar, comprobar y explicar.
