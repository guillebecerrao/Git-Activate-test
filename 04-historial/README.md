# Ejercicio 4 — Historial: log, diff, revert

## Objetivo
Aprender a navegar el historial de cambios y a deshacer commits cuando algo sale mal.

## Conceptos clave

- **git log**: ver todos los commits del proyecto.
- **git diff**: ver exactamente qué líneas cambiaron.
- **git revert**: crear un nuevo commit que deshace uno anterior (sin borrar historial).
- **git reset**: mover el puntero del historial (con cuidado).

---

## Ejercicio paso a paso

### Paso 1 — Explorar el historial
```bash
# Vista compacta
git log --oneline

# Vista con ramas y merges
git log --oneline --graph --all

# Vista detallada de un commit específico
git show <hash-del-commit>
```

### Paso 2 — Ver diferencias entre commits
```bash
# Diferencia entre working directory y último commit
git diff

# Diferencia entre dos commits
git diff <hash-1> <hash-2>

# Diferencia entre una rama y main
git diff main..feature/mi-rama
```

### Paso 3 — Hacer cambios para practicar el revert
Edita el archivo `experimento.txt` en esta carpeta, agrega algo y haz commit:
```bash
git add 04-historial/experimento.txt
git commit -m "test: cambio de prueba para practicar revert"
```

### Paso 4 — Deshacer el commit con revert
Primero obtén el hash del commit que quieres deshacer:
```bash
git log --oneline
```
Luego reviértelo:
```bash
git revert <hash-del-commit>
```
Git creará un nuevo commit que deshace el anterior. El historial queda intacto.

### Paso 5 — Observa el resultado
```bash
git log --oneline
```
Verás ambos commits: el original y el que lo revierte.

---

## Diferencia entre revert y reset

| Comando | Qué hace | Cuándo usarlo |
|---|---|---|
| `git revert` | Crea un nuevo commit que deshace cambios | Cuando ya hiciste push (trabajo compartido) |
| `git reset --soft` | Deshace el commit, mantiene cambios en staging | Solo en local, antes de push |
| `git reset --hard` | Deshace el commit Y descarta los cambios | Con cuidado — se pierden los cambios |

---

## Desafio extra
Usa `git blame experimento.txt` para ver quién modificó cada línea del archivo y en qué commit.

## Pistas
<details>
<summary>Ver pista</summary>

- Nunca uses `git reset --hard` en commits que ya están en el remoto: afectarás a tus compañeros.
- `git revert` es la opción segura para deshacer en un proyecto compartido.
- Los primeros 7 caracteres del hash son suficientes para identificar un commit.

</details>
