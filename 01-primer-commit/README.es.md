🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Módulo 01 — Mi primer commit

## Objetivo
Completar el ciclo completo de Git por primera vez: editar un archivo, prepararlo, hacer commit y subirlo al repositorio compartido.

## Conceptos clave

- **Working directory**: donde editas tus archivos.
- **Staging area**: zona de preparación — decides qué va en el próximo commit.
- **Commit**: una instantánea guardada del proyecto en un momento específico.
- **Remote**: el repositorio compartido en GitHub/GitLab al que todos hacen push y pull.

```
[Working Directory] → git add → [Staging Area] → git commit → [Repo local] → git push → [Remote]
```

---

## Paso a paso

### Paso 1 — Ver el estado actual
Ejecuta esto y observa qué te dice:
```bash
git status
```
Deberías ver que todo está al día — todavía no hay cambios.

### Paso 2 — Editar un archivo
Abre `notas.txt` en esta carpeta y agrega una línea con tu nombre y algo que quieres aprender.

### Paso 3 — Ver qué cambió
```bash
git status
git diff
```
Nota la diferencia: `git status` te dice *qué* archivos cambiaron, `git diff` te muestra *qué* cambió dentro de ellos.

### Paso 4 — Preparar el cambio
```bash
git add 01-primer-commit/notas.txt
```
Ejecuta `git status` de nuevo. Observa cómo el archivo pasó de "not staged" (rojo) a "staged" (verde).

### Paso 5 — Hacer el commit
```bash
git commit -m "feat: agrego [tu nombre] a las notas"
```
El mensaje debe describir qué cambiaste. Usa presente e intenta ser específico.

### Paso 6 — Hacer push al repositorio compartido
```bash
git push origin main
```
Esto sube tu commit al remoto para que tus compañeros puedan verlo.

### Paso 7 — Verificar
```bash
git log --oneline
```
Deberías ver tu commit en la parte superior de la lista.

---

## Desafío extra
Crea un archivo nuevo llamado `mi-primer-archivo.txt` dentro de esta carpeta, escribe algo en él y haz un commit.

## Pistas
<details>
<summary>Ver pistas</summary>

- `git status` muestra archivos modificados (rojo = sin preparar, verde = preparado).
- `git add .` prepara TODOS los archivos modificados a la vez. Úsalo con cuidado.
- Un buen mensaje de commit describe QUÉ cambiaste y POR QUÉ.
- La primera vez que hagas push, Git puede pedirte confirmar tu identidad — eso es normal.

</details>

---

Siguiente: [02-trabajo-en-equipo](../02-trabajo-en-equipo/README.es.md)
