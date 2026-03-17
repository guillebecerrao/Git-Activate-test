# Ejercicio 3 — Colaboración: push, pull y conflictos

## Objetivo
Simular trabajo en equipo: subir cambios, bajar los del resto, y resolver conflictos cuando dos personas editan lo mismo.

## Conceptos clave

- **origin**: nombre por defecto del repositorio remoto (en GitHub).
- **push**: subir tus commits al remoto.
- **pull**: bajar los commits del remoto a tu máquina.
- **Conflicto**: cuando dos personas cambian la misma línea del mismo archivo.

---

## Ejercicio A — Push y Pull básico

### Paso 1 — Hacer un cambio y subirlo
Edita el archivo `equipo.txt`, agrega tu nombre y haz commit:
```bash
git add 03-colaboracion/equipo.txt
git commit -m "feat: me uno al equipo - [tu nombre]"
```

### Paso 2 — Subir al repositorio remoto
```bash
git push origin main
```

### Paso 3 — Bajar cambios de tus compañeros
Cuando alguien del equipo haya hecho push, tú ejecutas:
```bash
git pull origin main
```

---

## Ejercicio B — Resolver un conflicto (hazlo con un compañero)

Un conflicto ocurre cuando dos personas editan la misma línea. Así se ve:

```
<<<<<<< HEAD
Tu versión del texto
=======
La versión de tu compañero
>>>>>>> origin/main
```

### Cómo resolverlo:
1. Abre el archivo con el conflicto.
2. Decide qué versión queda (o combina ambas).
3. Elimina las marcas `<<<<<<<`, `=======`, `>>>>>>>`.
4. Guarda el archivo.
5. Haz `git add` y luego `git commit`.

### Para simular el conflicto:
- Persona A: edita la línea 1 de `conflicto.txt`, commit y push.
- Persona B: edita la misma línea 1 de `conflicto.txt` (sin hacer pull primero), commit y push.
- Persona B verá el error. Debe hacer `git pull`, resolver el conflicto y volver a hacer push.

---

## Pistas
<details>
<summary>Ver pista</summary>

- Siempre hacer `git pull` antes de empezar a trabajar cada día.
- Si el push falla con "rejected", necesitas hacer pull primero.
- En un conflicto, comunícate con tu compañero para decidir qué versión mantener.

</details>
