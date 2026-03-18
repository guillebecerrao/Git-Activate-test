🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Módulo 03 — Ramas

## Objetivo
Aprender a trabajar en paralelo en ramas separadas para que el trabajo de cada persona esté aislado hasta que esté listo para integrarse a main.

## Conceptos clave

- **Branch (rama)**: una línea de trabajo independiente. Los cambios que hagas aquí no afectan `main` hasta que hagas merge.
- **main**: la rama principal — siempre debe estar en un estado funcional.
- **Merge**: integrar los cambios de una rama en otra.

```
main:      A --------- B ----------- E (merge)
                        \           /
feature/ana:             C --- D ---
```

---

## Paso a paso

### Paso 1 — Ver las ramas existentes
```bash
git branch
```
El asterisco (*) marca la rama en la que estás actualmente. Deberías estar en `main`.

### Paso 2 — Asegurarte de que tu main está actualizado
```bash
git pull origin main
```

### Paso 3 — Crear tu propia rama
Reemplaza `tu-nombre` con tu nombre real (sin espacios, usa guiones):
```bash
git checkout -b feature/tu-nombre
```

Verifica en qué rama estás:
```bash
git branch
```

### Paso 4 — Hacer tu cambio
Abre `ideas.txt` y agrega tu idea en una nueva línea.

### Paso 5 — Commit en tu rama
```bash
git add 03-ramas/ideas.txt
git commit -m "feat: agrego idea de [tu nombre]"
```

### Paso 6 — Subir tu rama al remoto
```bash
git push origin feature/tu-nombre
```

### Paso 7 — Volver a main y actualizarlo
```bash
git checkout main
git pull origin main
```

### Paso 8 — Hacer merge de tu rama a main
```bash
git merge feature/tu-nombre
```

Si nadie más editó las mismas líneas, Git hará el merge automáticamente.

### Paso 9 — Hacer push del main actualizado
```bash
git push origin main
```

### Paso 10 — Ver el historial completo con ramas
```bash
git log --oneline --graph --all
```

---

## Desafío extra
Una vez que todos hayan hecho merge de sus ramas, hagan que dos personas editen la **misma línea** de `ideas.txt` en sus respectivas ramas. Hagan merge de la primera normalmente. Luego intenten hacer merge de la segunda — tendrán un conflicto. Resuélvanlo como aprendieron en el Módulo 02.

---

## 🙋 ¿Haciendo esto solo?

Crea dos ramas en secuencia: `feature/version-a` y `feature/version-b`. Haz un cambio diferente en cada una. Mergea la primera, luego la segunda. Observa el historial con `git log --oneline --graph --all` para ver cómo se ven las ramas.

Para el desafío extra: haz que ambas ramas editen la misma línea de `ideas.txt`, luego intenta hacer merge de las dos. Producirás un conflicto para resolver solo.

---

## Pistas
<details>
<summary>Ver pistas</summary>

- Nombra tus ramas de forma descriptiva: `feature/login`, `fix/link-roto`, `draft/spec-v2`.
- Asegúrate siempre de estar en la rama destino (ej: `main`) antes de ejecutar `git merge`.
- Si el merge no tiene conflictos, Git lo hace automáticamente (fast-forward o merge automático).
- Después del merge, puedes eliminar la rama si ya no la necesitas: `git branch -d feature/tu-nombre`

</details>

---

Siguiente: [04-historial](../04-historial/README.es.md)
