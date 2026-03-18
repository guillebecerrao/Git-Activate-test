🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Módulo 03 — Branches

## Objetivo
Aprender a trabalhar em paralelo em branches separadas para que o trabalho de cada pessoa fique isolado até estar pronto para ser integrado à main.

## Conceitos-chave

- **Branch (ramo)**: uma linha de trabalho independente. As mudanças que você faz aqui não afetam `main` até o merge.
- **main**: a branch principal — deve sempre estar em um estado funcional.
- **Merge**: integrar as mudanças de uma branch em outra.

```
main:      A --------- B ----------- E (merge)
                        \           /
feature/ana:             C --- D ---
```

---

## Passo a passo

### Passo 1 — Ver as branches existentes
```bash
git branch
```
O asterisco (*) marca a branch em que você está. Você deve estar na `main`.

### Passo 2 — Garantir que sua main está atualizada
```bash
git pull origin main
```

### Passo 3 — Criar sua própria branch
Substitua `seu-nome` pelo seu nome real (sem espaços, use hífens):
```bash
git checkout -b feature/seu-nome
```

Verifique em qual branch você está:
```bash
git branch
```

### Passo 4 — Fazer sua mudança
Abra `ideas.txt` e adicione sua ideia em uma nova linha.

### Passo 5 — Commit na sua branch
```bash
git add 03-ramas/ideas.txt
git commit -m "feat: adiciono ideia de [seu nome]"
```

### Passo 6 — Enviar sua branch para o remote
```bash
git push origin feature/seu-nome
```

### Passo 7 — Voltar para main e atualizá-la
```bash
git checkout main
git pull origin main
```

### Passo 8 — Fazer merge da sua branch na main
```bash
git merge feature/seu-nome
```

Se ninguém mais editou as mesmas linhas, o Git fará o merge automaticamente.

### Passo 9 — Fazer push da main atualizada
```bash
git push origin main
```

### Passo 10 — Ver o histórico completo com branches
```bash
git log --oneline --graph --all
```

---

## Desafio extra
Depois que todos tiverem feito merge de suas branches, faça com que duas pessoas editem a **mesma linha** de `ideas.txt` em suas respectivas branches. Faça merge da primeira normalmente. Em seguida, tente fazer merge da segunda — você terá um conflito. Resolva-o como aprendeu no Módulo 02.

---

## 🙋 Fazendo isso sozinho?

Crie duas branches em sequência: `feature/versao-a` e `feature/versao-b`. Faça uma mudança diferente em cada uma. Faça merge da primeira, depois da segunda. Observe o histórico com `git log --oneline --graph --all` para ver como as branches ficam.

Para o desafio extra: faça as duas branches editarem a mesma linha de `ideas.txt`, depois tente fazer merge das duas. Você vai gerar um conflito para resolver sozinho.

---

## Dicas
<details>
<summary>Ver dicas</summary>

- Nomeie suas branches de forma descritiva: `feature/login`, `fix/link-quebrado`, `draft/spec-v2`.
- Sempre certifique-se de estar na branch de destino (ex: `main`) antes de executar `git merge`.
- Se o merge não tiver conflitos, o Git o faz automaticamente (fast-forward ou merge automático).
- Após o merge, você pode deletar a branch se não precisar mais: `git branch -d feature/seu-nome`

</details>

---

Próximo: [04-historial](../04-historial/README.pt.md)
