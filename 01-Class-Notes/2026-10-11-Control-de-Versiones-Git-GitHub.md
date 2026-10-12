# Control de versiones — Git y GitHub

**Fecha de incorporación:** 2026-10-11. **Fuente:** MoureDev Pro, lección «Control de versiones» aportada en capturas.  
**Estado:** guía conceptual preparada; ejercicio local pendiente.  
**Relaciones:** [IDE y debugging](./2026-10-11-IDE-VSCode-Debugging.md), [Learning by Doing](./2026-10-11-Practica-Learning-by-Doing.md), [Plan 5×60](../03-Exercises/2026-10-11-Plan-de-Estudio-Personalizado.md).

## 1. Qué es el control de versiones

Un sistema de control de versiones registra **estados y cambios** de archivos a lo largo del tiempo, con autoría y mensajes que explican decisiones. Git es un sistema distribuido: permite trabajar y crear commits localmente, aun sin conexión. Permite comparar diferencias, revertir de forma controlada, crear ramas y combinar trabajo. **No es un sistema de respaldo completo** ni reemplaza tests, backups, gestión de secretos y revisión de código.

**Problema sin Git:** archivos como `programa_final_3_ahora_si.py`, dificultad para identificar la razón del cambio, restaurar un comportamiento o integrar aportes.

**Con Git:** se identifica el diff, autor, commit y secuencia de decisiones, con posibilidad de recuperar versiones anteriores.

## 2. Ventajas en proyectos individuales y colaborativos

| Necesidad | Beneficio | Precaución |
| --- | --- | --- |
| Historia | ver qué cambió y por qué | mensajes claros |
| Experimentación | ramas para cambios aislados | no confundir rama con backup |
| Recuperación | consultar/restaurar estados | entender `restore`, `revert` y `reset` |
| Colaboración | integrar trabajo con revisión | conflictos pueden requerir resolución humana |
| Calidad | diffs, PR y CI | commit no prueba que funcione |
| Portafolio | evidencias verificables | no divulgar proyectos privados o secretos |

## 3. Modelo Git — cuatro espacios principales

```text
WORKING TREE (archivos editados)
     | git add
     v
STAGING AREA (cambios elegidos)
     | git commit
     v
LOCAL REPOSITORY (.git: historial, ramas)
     | git push
     v
REMOTE (GitHub: repositorio remoto)
     | git fetch / git pull
     v
LOCAL REPOSITORY / WORKING TREE
```

- `git status`: estado de la copia de trabajo.
- `git diff`: cambios sin stage; `git diff --staged`: cambios que entrarán al commit.
- `git add`: seleccionar cambios.
- `git commit`: registrar snapshot con mensaje e identificador SHA.
- `git log --oneline`: historial resumido.
- `git branch` y `git switch`: ramas y navegación.
- `git merge`: combinar historiales; puede dar conflictos.
- `git fetch`: descargar referencias y objetos sin integrar por sí solo.
- `git pull`: fetch + integración (merge/rebase/ff según configuración).
- `git push`: enviar commits locales al remoto.

**No confundir:** Save en VS Code guarda archivo, `commit` guarda historial Git local, `push` publica commits en remoto y `pull` incorpora cambios remotos en una copia local.

## 4. Conceptos: repositorio, commit, rama y merge

**Repositorio:** carpeta versionada y su historial `.git`.  
**Commit:** snapshot de los archivos versionados seleccionados, con autor, fecha, mensaje y relación con commits anteriores.  
**Rama:** referencia móvil a una línea de commits; sirve para trabajar sin modificar de inmediato `main`.  
**Merge:** integra cambios/historial de otra rama; cuando hay cambios incompatibles en la misma región, requiere resolver conflictos.

Ejemplo:
```text
main:      A --- B -------- M
                  \       /
feature:           C --- D
```
`M` puede ser un commit de merge; algunas integraciones son fast-forward y no crean uno nuevo.

## 5. Git y GitHub: responsabilidades distintas

| Git | GitHub |
| --- | --- |
| herramienta distribuida de control de versiones | servicio de alojamiento y colaboración sobre repositorios Git |
| funciona localmente sin internet | requiere acceso de red para sincronizar |
| commits, branches, diffs, merges | pull requests, reviews, Issues, Actions, permisos y visualización |
| la rama local no es la remota | la rama remota se actualiza con push/API |

El portafolio público debe incluir README, propósito, demo/evidencias no sensibles, instalación, arquitectura y licencia cuando proceda. No abrir código privado automáticamente.

## 6. Caso real: Big School y Obsidian

Repositorio técnico: https://github.com/ivnpdrn1/desarrollo-con-IA--big-school  
Vault: repositorio https://github.com/ivnpdrn1/ivan-knowledge-vault, carpeta `Projects/Desarrollo con IA - Big School/`.

**Son dos repositorios diferentes.** Publicar una guía en GitHub no la copia por sí mismo a Obsidian. Los documentos se mantienen enlazados y, cuando corresponde, se actualizan en ambos. Tras un commit remoto del Vault, la copia local de Obsidian requiere fetch/pull o sincronización configurada. El botón/estado de sincronización de otros proyectos no garantiza que este haya hecho pull.

Diagnóstico no destructivo si un documento no aparece localmente:
1. Confirmar que existe en GitHub en `main`.
2. Verificar carpeta local del Vault y rama remota correctas.
3. En terminal situada **dentro del repositorio correcto**: `git status`, `git remote -v`, `git branch --show-current`.
4. Si hay cambios locales sin guardar/commit, no hacer acciones destructivas; revisar primero.
5. `git fetch origin` y `git log --oneline --decorate --all -10` para comparar.
6. Solo si el estado permite integrar cambios con seguridad, `git pull --ff-only` en la rama correspondiente. Si falla, estudiar divergencia en lugar de forzar.
7. Revisar que Obsidian indexa la carpeta correcta.

**Importante:** nunca ejecutar `git reset --hard`, `git clean -fd` o `git push --force` como solución genérica a sincronización.

## 7. Git con Claude Code y VS Code

**Antes del cambio:** definir requisito, confirmar rama y `git status`, proteger secretos.  
**Durante:** trabajar con cambios pequeños, revisar archivos afectados, evitar commits automáticos sin revisión.  
**Antes de commit:** `git diff`, tests, secret scanning cuando sea aplicable, mensajes claros.  
**Antes de push/merge:** evaluar conflictos, impacto, despliegue, posibles datos sensibles y permisos.  
**Después:** registrar commit y evidencia en Obsidian; mantener separados material educativo y código de producción de cada proyecto.

## 8. Taller de 60 minutos — repositorio local de práctica

Hacer en carpeta nueva, NO dentro del Vault ni de ningún repositorio de producción.

**A. Iniciar (10 min)**
```powershell
mkdir git-lab
cd git-lab
git init
git branch -M main
git status
```
Si `git commit` reclama identidad, configurar `user.name` y `user.email` con valores que correspondan al usuario; evitar compartir datos personales en capturas.

**B. Primer commit (15 min)**
Crear `README.md` con objetivo, y `galones.py` con función de suma de una lista de tres despachos ficticios.
```bash
git status
git add README.md galones.py
git diff --staged
git commit -m "Add initial gallons practice"
git log --oneline
```
Guardar en el editor NO equivale a commit.

**C. Rama y experimento (15 min)**
```bash
git switch -c feature/validacion
```
Agregar validación de galones no negativos, probar y registrar:
```bash
git add galones.py
git diff --staged
git commit -m "Validate non-negative gallons"
git switch main
git merge feature/validacion
git log --oneline --graph --decorate --all
```
No hacer `push` a un repositorio remoto a menos que se haya creado deliberadamente uno para el laboratorio y se compruebe que no contiene secretos.

**D. Recuperación y reflexión (20 min)**
```bash
git show --stat HEAD
git status
git diff HEAD~1 HEAD
```
Si el historial no tiene dos commits, `HEAD~1` no existirá; comprobar con `git log`. Explicar la diferencia entre working tree, stage, commit, rama y merge y guardar la prueba en notas.

## 9. Precauciones y casos frecuentes

- `.gitignore` debe excluir `.env`, `.venv/`, caches y archivos temporales (pero `.gitignore` no borra secretos ya committeados).
- Conflicto: inspeccionar marcadores `<<<<<<<`, `=======`, `>>>>>>>`, decidir contenido, ejecutar tests, hacer stage y finalizar merge.
- `git revert <sha>` crea commit inverso y suele ser preferible en ramas compartidas frente a reescribir historia.
- PR no es commit; es propuesta de integrar cambios con discusión y revisión.
- `git pull` puede modificar archivos locales; `fetch` permite inspeccionar primero.
- GitHub no despliega código por defecto, aunque workflows integrados sí pueden hacerlo; verificar Actions y permisos.

## 10. Rúbrica y evidencia

0 sin evidencia; 1 reconoce términos; 2 puede seguir flujo guiado; 3 crea ramas, revisa diffs y resuelve cambios con autonomía; 4 explica/diagnostica divergencias y diseña una estrategia segura de colaboración.

**Checklist (pendiente):**
- [ ] Crear repositorio local aislado.
- [ ] Distinguir Save, add, commit, push y pull.
- [ ] Registrar dos commits.
- [ ] Crear rama y combinarla.
- [ ] Consultar diff y log.
- [ ] Explicar por qué un commit remoto del Vault no equivale a actualización en Obsidian local.
- [ ] Registrar experiencia y capturas sin datos sensibles.

## 11. Fuentes
- Git: https://git-scm.com/docs
- GitHub: https://docs.github.com/
- Git branching: https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell
- Pull requests: https://docs.github.com/en/pull-requests
