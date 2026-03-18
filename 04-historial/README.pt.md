🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Módulo 04 — Histórico

> Este módulo é **opcional mas recomendado**. Ele cobre as ferramentas que você vai usar quando algo der errado no trabalho colaborativo real.

## Objetivo
Aprender a navegar pelo histórico de mudanças, ver exatamente o que mudou e quando, desfazer commits de forma segura e guardar trabalho temporariamente.

## Conceitos-chave

- **git log**: ver todos os commits do projeto.
- **git diff**: ver exatamente quais linhas mudaram.
- **git revert**: criar um novo commit que desfaz um anterior — o histórico fica intacto.
- **git reset**: mover o ponteiro do histórico para trás. Use com cuidado.
- **git stash**: guardar temporariamente mudanças não commitadas para trabalhar em outra coisa.

---

## Passo a passo

### Passo 1 — Explorar o histórico

```bash
# Visão compacta
git log --oneline

# Visão com branches e merges
git log --oneline --graph --all

# Visão detalhada de um commit específico
git show <hash-do-commit>
```

### Passo 2 — Ver diferenças

```bash
# Diferença entre seu working directory e o último commit
git diff

# Diferença entre dois commits
git diff <hash-1> <hash-2>

# Diferença entre uma branch e a main
git diff main..feature/minha-branch
```

### Passo 3 — Fazer uma mudança para praticar o revert

Edite `experimento.txt` nesta pasta, adicione algo e faça commit:
```bash
git add 04-historial/experimento.txt
git commit -m "test: mudança de prática para exercício de revert"
```

### Passo 4 — Desfazer o commit com revert

Primeiro, obtenha o hash do commit que você quer desfazer:
```bash
git log --oneline
```
Então reverta-o:
```bash
git revert <hash-do-commit>
```
O Git abrirá um editor de texto para confirmar a mensagem do commit — salve e feche. O Git cria um novo commit que desfaz o anterior. O histórico fica intacto.

### Passo 5 — Observar o resultado

```bash
git log --oneline
```
Você verá os dois commits: o original e o que o reverte.

---

## revert vs reset

| Comando | O que faz | Quando usar |
|---|---|---|
| `git revert` | Cria um novo commit que desfaz mudanças | Quando já fez push (trabalho compartilhado) |
| `git reset --soft` | Desfaz o commit, mantém mudanças no staging | Apenas localmente, antes do push |
| `git reset --hard` | Desfaz o commit E descarta as mudanças | Com cuidado — as mudanças são perdidas |

> **Regra geral:** se o commit já está no remote, sempre use `git revert`. Nunca use `git reset --hard` em histórico compartilhado.

---

## Bônus: git stash

Imagine que você está editando um arquivo e precisa mudar rapidamente para outra branch (por exemplo, para ajudar um colega). Você não quer fazer commit de uma mudança incompleta.

```bash
# Guarda suas mudanças não commitadas temporariamente
git stash

# Mude de branch, faça o que precisar, volte
git checkout main
# ... fazer algo ...
git checkout feature/sua-branch

# Recupere suas mudanças guardadas
git stash pop
```

`git stash` é o seu botão de "salvar para depois".

---

## Desafio extra
Use `git blame experimento.txt` para ver quem modificou cada linha do arquivo e em qual commit.

## Dicas
<details>
<summary>Ver dicas</summary>

- Nunca use `git reset --hard` em commits que já estão no remote — vai afetar seus colegas.
- `git revert` é a opção segura para desfazer em um projeto compartilhado.
- Os primeiros 7 caracteres do hash são suficientes para identificar um commit.
- `git stash pop` recupera as mudanças guardadas mais recentemente. Se você fez stash várias vezes, use `git stash list` para ver todas.

</details>
