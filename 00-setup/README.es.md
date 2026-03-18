🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Módulo 00 — Setup

> Completa este checklist **antes de la sesión del taller**. Cada participante debe hacerlo individualmente en su propia máquina.
>
> Si te trabas en algún paso, contacta al facilitador del taller antes de que empiece la sesión.

---

## Checklist

### ✅ Paso 1 — Crear una cuenta

Si todavía no tienes una, crea una cuenta en la plataforma donde vive este repositorio:

- **GitHub:** https://github.com/signup
- **GitLab:** https://gitlab.com/users/sign_up

### ✅ Paso 2 — Aceptar la invitación de colaborador

El facilitador te enviará una invitación para colaborar en el repositorio. Revisa tu email o las notificaciones de la plataforma y **acepta la invitación**.

> Sin este paso, podrás clonar y trabajar en local, pero no podrás hacer push de tus cambios al repositorio compartido.

### ✅ Paso 3 — Instalar Git

Verifica si Git ya está instalado:
```bash
git --version
```

Si ves un número de versión (ej: `git version 2.43.0`), estás listo. Si no:

- **macOS:** `brew install git` o descarga desde https://git-scm.com
- **Windows:** Descarga Git for Windows desde https://git-scm.com — incluye **Git Bash**, que debes usar para todos los comandos en este taller.
- **Linux:** `sudo apt install git` (Ubuntu/Debian) o `sudo dnf install git` (Fedora)

### ✅ Paso 4 — Configurar tu identidad

Git necesita saber quién eres para firmar tus commits:
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

Verifica que funcionó:
```bash
git config --list
```
Deberías ver tu nombre y email en el resultado.

### ✅ Paso 5 — Crear una SSH key

SSH es una forma segura de autenticarte con GitHub/GitLab sin escribir tu contraseña en cada push.

> **Usuarios de Windows:** ejecuta los siguientes comandos en **Git Bash**, no en Command Prompt ni PowerShell.

```bash
ssh-keygen -t ed25519 -C "tu@email.com"
```

- Presiona **Enter** para aceptar la ubicación por defecto del archivo (`~/.ssh/id_ed25519`)
- Puedes agregar una contraseña para mayor seguridad, o presionar **Enter** dos veces para omitirla

### ✅ Paso 6 — Agregar tu SSH key a GitHub o GitLab

Primero, muestra tu clave pública y copia todo el resultado:
```bash
cat ~/.ssh/id_ed25519.pub
```
El resultado empieza con `ssh-ed25519`. Selecciona y copia toda la línea.

Luego agrégala a tu cuenta:

**GitHub:**
1. Ve a tu perfil → **Settings** → **SSH and GPG keys** → **New SSH key**
2. Dale un título (ej: "Mi laptop")
3. Pega la clave y haz clic en **Add SSH key**

**GitLab:**
1. Haz clic en tu avatar (arriba a la derecha) → **Preferences** → **SSH Keys**
2. Pega la clave, dale un título y haz clic en **Add key**

### ✅ Paso 7 — Probar la conexión SSH

```bash
# GitHub
ssh -T git@github.com

# GitLab
ssh -T git@gitlab.com
```

Respuestas esperadas:
- **GitHub:** `Hi username! You've successfully authenticated, but GitHub does not provide shell access.`
- **GitLab:** `Welcome to GitLab, @username!`

> Si ves un aviso como `The authenticity of host ... can't be established`, escribe `yes` y presiona Enter. Esto es normal en la primera conexión.

### ✅ Paso 8 — Clonar el repositorio

Obtén la **URL SSH** desde la página del repositorio (busca el botón **Clone** y selecciona la opción **SSH**). Luego ejecuta:

```bash
git clone git@github.com:OWNER/Git-Activate-test.git
# o
git clone git@gitlab.com:OWNER/Git-Activate-test.git
```

Reemplaza `OWNER` con el nombre de usuario o grupo de quien sea dueño del repositorio. El facilitador te dará la URL exacta.

### ✅ Paso 9 — Verificación final

Entra a la carpeta clonada y revisa el historial:
```bash
cd Git-Activate-test
git log --oneline
```

Deberías ver una lista de commits anteriores. Si la ves — ¡estás listo! 🎉

---

## Problemas comunes

| Problema | Causa probable | Solución |
|---|---|---|
| `Permission denied (publickey)` | SSH key no agregada o key incorrecta | Repite los Pasos 5–7 |
| `Repository not found` | URL incorrecta o invitación no aceptada | Revisa el Paso 2 y la URL del clone |
| `git: command not found` | Git no está instalado | Repite el Paso 3 |
| Aviso SSH en primera conexión | Comportamiento normal | Escribe `yes` y presiona Enter |
| `git push` falla con "rejected" | No aceptaste la invitación | Revisa el Paso 2 |

---

¿Listo? Ve a [01-primer-commit](../01-primer-commit/README.es.md) — ¡nos vemos en la sesión!
