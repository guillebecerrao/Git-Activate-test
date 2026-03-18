🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Módulo 00 — Setup

> Complete este checklist **antes da sessão do workshop**. Cada participante deve fazer isso individualmente na sua própria máquina.
>
> Se travar em algum passo, entre em contato com o facilitador antes que a sessão comece.

---

## Checklist

### ✅ Passo 1 — Criar uma conta

Se você ainda não tem uma, crie uma conta na plataforma onde este repositório está:

- **GitHub:** https://github.com/signup
- **GitLab:** https://gitlab.com/users/sign_up

### ✅ Passo 2 — Aceitar o convite de colaborador

O facilitador enviará um convite para você colaborar no repositório. Verifique seu e-mail ou as notificações da plataforma e **aceite o convite**.

> Sem este passo, você conseguirá clonar e trabalhar localmente, mas não conseguirá fazer push das suas mudanças para o repositório compartilhado.

### ✅ Passo 3 — Instalar o Git

Verifique se o Git já está instalado:
```bash
git --version
```

Se você ver um número de versão (ex: `git version 2.43.0`), está pronto. Caso contrário:

- **macOS:** `brew install git` ou baixe em https://git-scm.com
- **Windows:** Baixe o Git for Windows em https://git-scm.com — ele inclui o **Git Bash**, que você deve usar para todos os comandos neste workshop.
- **Linux:** `sudo apt install git` (Ubuntu/Debian) ou `sudo dnf install git` (Fedora)

### ✅ Passo 4 — Configurar sua identidade

O Git precisa saber quem você é para assinar seus commits:
```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```

Verifique se funcionou:
```bash
git config --list
```
Você deve ver seu nome e e-mail na saída.

### ✅ Passo 5 — Criar uma chave SSH

SSH é uma forma segura de se autenticar com GitHub/GitLab sem digitar sua senha a cada push.

> **Usuários Windows:** execute os comandos a seguir no **Git Bash**, não no Command Prompt ou PowerShell.

```bash
ssh-keygen -t ed25519 -C "seu@email.com"
```

- Pressione **Enter** para aceitar o local padrão do arquivo (`~/.ssh/id_ed25519`)
- Você pode definir uma senha para maior segurança, ou pressionar **Enter** duas vezes para pular

### ✅ Passo 6 — Adicionar sua chave SSH ao GitHub ou GitLab

Primeiro, exiba sua chave pública e copie toda a saída:
```bash
cat ~/.ssh/id_ed25519.pub
```
A saída começa com `ssh-ed25519`. Selecione e copie a linha inteira.

Em seguida, adicione-a à sua conta:

**GitHub:**
1. Vá ao seu perfil → **Settings** → **SSH and GPG keys** → **New SSH key**
2. Dê um título (ex: "Meu notebook")
3. Cole a chave e clique em **Add SSH key**

**GitLab:**
1. Clique no seu avatar (canto superior direito) → **Preferences** → **SSH Keys**
2. Cole a chave, dê um título e clique em **Add key**

### ✅ Passo 7 — Testar a conexão SSH

```bash
# GitHub
ssh -T git@github.com

# GitLab
ssh -T git@gitlab.com
```

Respostas esperadas:
- **GitHub:** `Hi username! You've successfully authenticated, but GitHub does not provide shell access.`
- **GitLab:** `Welcome to GitLab, @username!`

> Se aparecer um aviso como `The authenticity of host ... can't be established`, digite `yes` e pressione Enter. Isso é normal na primeira conexão.

### ✅ Passo 8 — Clonar o repositório

Obtenha a **URL SSH** na página do repositório (procure o botão **Clone** e selecione a opção **SSH**). Depois execute:

```bash
git clone git@github.com:OWNER/Git-Activate-test.git
# ou
git clone git@gitlab.com:OWNER/Git-Activate-test.git
```

Substitua `OWNER` pelo nome de usuário ou grupo de quem é dono do repositório. O facilitador fornecerá a URL exata.

### ✅ Passo 9 — Verificação final

Entre na pasta clonada e verifique o histórico:
```bash
cd Git-Activate-test
git log --oneline
```

Você deve ver uma lista de commits anteriores. Se conseguir — está tudo pronto! 🎉

---

## Problemas comuns

| Problema | Causa provável | Solução |
|---|---|---|
| `Permission denied (publickey)` | Chave SSH não adicionada ou chave errada | Refaça os Passos 5–7 |
| `Repository not found` | URL errada ou convite não aceito | Verifique o Passo 2 e a URL do clone |
| `git: command not found` | Git não instalado | Refaça o Passo 3 |
| Aviso SSH na primeira conexão | Comportamento normal | Digite `yes` e pressione Enter |
| `git push` falha com "rejected" | Convite não aceito | Verifique o Passo 2 |

---

Pronto? Vá para [01-primer-commit](../01-primer-commit/README.pt.md) — até a sessão!
