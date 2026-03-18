🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Módulo 02 — Trabajo en equipo

## Objetivo
Aprender el flujo cotidiano de colaborar en un repositorio compartido: cómo sincronizar tu trabajo con el de tus compañeros y qué hacer cuando dos personas cambian lo mismo.

## Conceptos clave

- **origin**: nombre por defecto del repositorio remoto (en GitHub/GitLab).
- **push**: subir tus commits al remoto.
- **pull**: bajar los commits de tus compañeros a tu máquina.
- **Conflicto**: cuando dos personas cambian la misma línea del mismo archivo. Git no puede decidir qué versión mantener — necesita que tú lo resuelvas.

---

## Parte A — El flujo del día a día

### El escenario
Hiciste cambios en tu local y los commiteaste. Mientras tanto, un compañero también hizo cambios y los subió antes que tú. Cuando intentas hacer push, Git lo rechaza — tu copia local está desactualizada respecto al remoto.

```
Remoto:  A --- B --- C   ← tu compañero subió C
Local:   A --- B --- D   ← tu commit D
                    ↑
          ¡rechazado! primero hay que hacer pull
```

### Paso 1 — Todos editan equipo.txt
Abre `equipo.txt` y agrega una línea con tu nombre, rol y la fecha de hoy.

### Paso 2 — Preparar y hacer commit
```bash
git add 02-trabajo-en-equipo/equipo.txt
git commit -m "feat: agrego [tu nombre] al archivo del equipo"
```

### Paso 3 — Intentar hacer push
```bash
git push origin main
```

**Si fuiste la primera persona en hacer push:** funcionará. Espera a que tus compañeros lo intenten.

**Si alguien hizo push antes que tú:** verás un error así:
```
! [rejected] main -> main (fetch first)
error: failed to push some refs
```
Esto no es un error tuyo — Git está protegiendo el trabajo de todos. Continúa al Paso 4.

### Paso 4 — Bajar los cambios de tu compañero
```bash
git pull origin main
```

Si tus cambios y los de tu compañero están en **líneas distintas**, Git los integrará automáticamente. Verás un mensaje como `Merge made by the 'ort' strategy` — eso es un éxito.

Si están en la **misma línea**, habrá un conflicto. Ve a la Parte B.

### Paso 5 — Hacer push de nuevo
```bash
git push origin main
```

### Paso 6 — Verificar
```bash
git log --oneline
```
Deberías ver tanto tu commit como el de tu compañero en el historial.

---

### La regla de oro

> **Pull → Trabaja → Add → Commit → Pull → Push**

Siempre haz pull antes de empezar a trabajar, y pull de nuevo antes de hacer push. Esto minimiza los conflictos.

---

## Parte B — Resolver un conflicto

### El escenario
Dos personas editaron la misma línea. Git te muestra las dos versiones y te pide que decidas.

### Cómo se ve un conflicto

Cuando haces `git pull` y hay un conflicto, Git te indica qué archivo tiene el problema. Al abrirlo, verás:

```
<<<<<<< HEAD
Tu versión de la línea
=======
La versión de tu compañero
>>>>>>> origin/main
```

### Cómo resolverlo

1. Abre el archivo con el conflicto (`conciliar.txt`).
2. Decide cuál es la versión final — la tuya, la de tu compañero, o una combinación de ambas.
3. Elimina las marcas de conflicto: `<<<<<<<`, `=======`, `>>>>>>>`.
4. Guarda el archivo.
5. Prepara y haz commit:
```bash
git add 02-trabajo-en-equipo/conciliar.txt
git commit -m "fix: resuelvo conflicto en conciliar.txt"
```
6. Haz push:
```bash
git push origin main
```

### Para practicarlo con tu equipo

- **Persona A:** edita la línea 8 de `conciliar.txt`, hace commit y push.
- **Persona B:** edita la misma línea 8 de `conciliar.txt` (sin hacer pull primero), hace commit e intenta hacer push.
- **Persona B:** verá el rechazo. Hace pull, resuelve el conflicto y vuelve a hacer push.

> Consejo: antes de resolver, habla con la Persona A. Un conflicto es una invitación a conversar, no solo un problema técnico.

---

## 🙋 ¿Haciendo esto solo?

**Para la Parte A:** haz tu cambio en local, haz commit y push. Luego abre el repositorio en el navegador (GitHub o GitLab), navega a `equipo.txt`, haz clic en el ícono de editar (lápiz), agrega una segunda línea y haz commit directamente desde la interfaz web. Ahora tu local está desactualizado respecto al remoto — ejecuta `git pull` para ver la sincronización en acción.

**Para la Parte B:** repite lo mismo pero edita **la misma línea** desde la interfaz web. Cuando hagas pull en local, obtendrás un conflicto para resolver.

> Esto funciona porque aceptaste la invitación de colaborador en `00-setup`. Tienes acceso de escritura al repositorio, incluyendo desde la interfaz web.

---

## Pistas
<details>
<summary>Ver pistas</summary>

- Siempre haz `git pull` antes de empezar a trabajar cada día.
- Si `git push` falla con "rejected", significa que primero debes hacer pull — no que hayas hecho algo mal.
- En un conflicto, la sección `HEAD` es lo que tienes en tu local, y la sección debajo de `=======` es lo que vino del remoto.
- Después de resolver un conflicto, `git status` debe mostrar el archivo como preparado (verde) antes de hacer commit.

</details>

---

Siguiente: [03-ramas](../03-ramas/README.es.md)
