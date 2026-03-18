🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Módulo 04 — Historial

> Este módulo es **opcional pero recomendado**. Cubre las herramientas a las que recurrirás cuando algo salga mal en el trabajo colaborativo real.

## Objetivo
Aprender a navegar el historial de cambios, ver exactamente qué cambió y cuándo, deshacer commits de forma segura y apartar trabajo temporalmente.

## Conceptos clave

- **git log**: ver todos los commits del proyecto.
- **git diff**: ver exactamente qué líneas cambiaron.
- **git revert**: crear un nuevo commit que deshace uno anterior — el historial queda intacto.
- **git reset**: mover el puntero del historial hacia atrás. Usar con cuidado.
- **git stash**: apartar temporalmente cambios sin commitear para poder trabajar en otra cosa.

---

## Paso a paso

### Paso 1 — Explorar el historial

```bash
# Vista compacta
git log --oneline

# Vista con ramas y merges
git log --oneline --graph --all

# Vista detallada de un commit específico
git show <hash-del-commit>
```

### Paso 2 — Ver diferencias

```bash
# Diferencia entre tu working directory y el último commit
git diff

# Diferencia entre dos commits
git diff <hash-1> <hash-2>

# Diferencia entre una rama y main
git diff main..feature/mi-rama
```

### Paso 3 — Hacer un cambio para practicar revert

Edita `experimento.txt` en esta carpeta, agrega algo y haz commit:
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
Git abrirá un editor de texto para que confirmes el mensaje del commit — guarda y ciérralo. Git crea un nuevo commit que deshace el anterior. El historial queda intacto.

### Paso 5 — Observa el resultado

```bash
git log --oneline
```
Verás ambos commits: el original y el que lo revierte.

---

## revert vs reset

| Comando | Qué hace | Cuándo usarlo |
|---|---|---|
| `git revert` | Crea un nuevo commit que deshace cambios | Cuando ya hiciste push (trabajo compartido) |
| `git reset --soft` | Deshace el commit, mantiene cambios en staging | Solo en local, antes de push |
| `git reset --hard` | Deshace el commit Y descarta los cambios | Con cuidado — los cambios se pierden |

> **Regla general:** si el commit ya está en el remoto, siempre usa `git revert`. Nunca uses `git reset --hard` en historial compartido.

---

## Bonus: git stash

Imagina que estás editando un archivo y necesitas cambiar rápidamente a otra rama (por ejemplo, para ayudar a un compañero). No quieres hacer commit de un cambio a medias.

```bash
# Guarda tus cambios sin commitear temporalmente
git stash

# Cambia de rama, haz lo que necesitas, vuelve
git checkout main
# ... hacer algo ...
git checkout feature/tu-rama

# Recupera tus cambios guardados
git stash pop
```

`git stash` es tu botón de "guardar para después".

---

## Desafío extra
Usa `git blame experimento.txt` para ver quién modificó cada línea del archivo y en qué commit.

## Pistas
<details>
<summary>Ver pistas</summary>

- Nunca uses `git reset --hard` en commits que ya están en el remoto: afectarás a tus compañeros.
- `git revert` es la opción segura para deshacer en un proyecto compartido.
- Los primeros 7 caracteres del hash son suficientes para identificar un commit.
- `git stash pop` recupera los últimos cambios guardados. Si hiciste stash varias veces, usa `git stash list` para verlos todos.

</details>
