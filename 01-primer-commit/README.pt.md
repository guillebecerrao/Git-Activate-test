🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Módulo 01 — Meu primeiro commit

## Objetivo
Completar o ciclo completo do Git pela primeira vez: editar um arquivo, prepará-lo, fazer commit e enviá-lo para o repositório compartilhado.

## Conceitos-chave

- **Working directory**: onde você edita seus arquivos.
- **Staging area**: zona de preparação — você escolhe o que vai no próximo commit.
- **Commit**: um snapshot salvo do projeto em um momento específico.
- **Remote**: o repositório compartilhado no GitHub/GitLab para o qual todos fazem push e pull.

```
[Working Directory] → git add → [Staging Area] → git commit → [Repo local] → git push → [Remote]
```

---

## Passo a passo

### Passo 1 — Verificar o estado atual
Execute isso e observe o que aparece:
```bash
git status
```
Você deve ver que tudo está em dia — ainda não há mudanças.

### Passo 2 — Editar um arquivo
Abra `notas.txt` nesta pasta e adicione uma linha com seu nome e uma coisa que você quer aprender.

### Passo 3 — Ver o que mudou
```bash
git status
git diff
```
Perceba a diferença: `git status` diz *quais* arquivos mudaram, `git diff` mostra *o que* mudou dentro deles.

### Passo 4 — Preparar a mudança
```bash
git add 01-primer-commit/notas.txt
```
Execute `git status` novamente. Veja como o arquivo foi de "not staged" (vermelho) para "staged" (verde).

### Passo 5 — Fazer o commit
```bash
git commit -m "feat: adiciono [seu nome] às notas"
```
A mensagem deve descrever o que você mudou. Use o presente e seja específico.

### Passo 6 — Enviar para o repositório compartilhado
```bash
git push origin main
```
Isso envia seu commit para o remote para que seus colegas possam vê-lo.

### Passo 7 — Verificar
```bash
git log --oneline
```
Você deve ver seu commit no topo da lista.

---

## Desafio extra
Crie um novo arquivo chamado `meu-primeiro-arquivo.txt` dentro desta pasta, escreva algo nele e faça um commit.

## Dicas
<details>
<summary>Ver dicas</summary>

- `git status` mostra arquivos modificados (vermelho = não preparado, verde = preparado).
- `git add .` prepara TODOS os arquivos modificados de uma vez. Use com cuidado.
- Uma boa mensagem de commit descreve O QUE você mudou e POR QUÊ.
- Na primeira vez que fizer push, o Git pode pedir para confirmar sua identidade — isso é normal.

</details>

---

Próximo: [02-trabajo-en-equipo](../02-trabajo-en-equipo/README.pt.md)
