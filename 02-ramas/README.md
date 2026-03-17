# Ejercicio 2 — Ramas: branch, checkout, merge

## Objetivo
Entender cómo trabajar en ramas para desarrollar features o correcciones sin afectar el código principal.

## Conceptos clave

- **Branch (rama)**: línea de trabajo independiente.
- **main**: rama principal, siempre debe estar estable.
- **Merge**: integrar los cambios de una rama a otra.

```
main:     A --- B ----------- E (merge)
                 \           /
feature:          C --- D ---
```

---

## Ejercicio paso a paso

### Paso 1 — Ver las ramas existentes
```bash
git branch
```
El asterisco (*) marca la rama en la que estás.

### Paso 2 — Crear y cambiar a una nueva rama
Reemplaza `tu-nombre` con tu nombre real (sin espacios, usa guiones):
```bash
git checkout -b feature/tu-nombre
```

Verifica en qué rama estás:
```bash
git branch
```

### Paso 3 — Hacer cambios en tu rama
Abre el archivo `ideas.txt` y agrega una idea de mejora para el equipo.

### Paso 4 — Commit en tu rama
```bash
git add 02-ramas/ideas.txt
git commit -m "feat: agrego idea de [tu nombre]"
```

### Paso 5 — Volver a main y hacer merge
```bash
git checkout main
git merge feature/tu-nombre
```

### Paso 6 — Ver el historial con ramas
```bash
git log --oneline --graph --all
```

---

## Desafio extra
Crea dos ramas distintas, haz un commit diferente en cada una, y luego haz merge de ambas a main. Observa cómo queda el historial.

## Pistas
<details>
<summary>Ver pista</summary>

- Nombra tus ramas de forma descriptiva: `feature/login`, `fix/bug-carrito`, `hotfix/typo-home`.
- Antes de hacer merge, asegúrate de estar en la rama destino (ej: `main`).
- Si el merge no tiene conflictos, Git lo hace automáticamente (fast-forward).

</details>
