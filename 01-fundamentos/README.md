# Ejercicio 1 — Fundamentos: add, commit, status

## Objetivo
Aprender el ciclo básico de Git: modificar archivos, prepararlos y guardar los cambios.

## Conceptos clave

- **Working directory**: donde editas tus archivos.
- **Staging area**: zona de preparación antes del commit.
- **Commit**: instantánea guardada del proyecto.

```
[Working Directory] → git add → [Staging Area] → git commit → [Repositorio]
```

---

## Ejercicio paso a paso

### Paso 1 — Ver el estado actual
Ejecuta este comando y observa qué te dice:
```bash
git status
```

### Paso 2 — Editar un archivo
Abre el archivo `notas.txt` que está en esta carpeta y agrega una línea con tu nombre.

### Paso 3 — Ver qué cambió
```bash
git status
git diff
```
Observa la diferencia entre ambos comandos.

### Paso 4 — Preparar el cambio
```bash
git add 01-fundamentos/notas.txt
```
Ejecuta `git status` de nuevo. ¿Qué cambió?

### Paso 5 — Hacer el commit
```bash
git commit -m "feat: agrego mi nombre a notas.txt"
```

### Paso 6 — Ver el historial
```bash
git log --oneline
```

---

## Desafio extra
Crea un archivo nuevo llamado `mi-primer-archivo.txt` dentro de esta carpeta, escribe algo en él y haz un commit.

## Pistas
<details>
<summary>Ver pista</summary>

- `git status` muestra archivos modificados (rojo = sin preparar, verde = preparado).
- `git add .` agrega TODOS los archivos modificados al staging.
- Un buen mensaje de commit describe QUÉ cambiaste y POR QUÉ.

</details>
