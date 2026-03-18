🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Módulo 02 — Trabalho em equipe

## Objetivo
Aprender o fluxo do dia a dia para colaborar em um repositório compartilhado: como sincronizar seu trabalho com o dos seus colegas e o que fazer quando duas pessoas mudam a mesma coisa.

## Conceitos-chave

- **origin**: nome padrão do repositório remoto (no GitHub/GitLab).
- **push**: enviar seus commits para o remote.
- **pull**: baixar os commits dos seus colegas para a sua máquina.
- **Conflito**: quando duas pessoas mudam a mesma linha do mesmo arquivo. O Git não consegue decidir qual versão manter — ele precisa que você resolva.

---

## Parte A — O fluxo do dia a dia

### O cenário
Você fez mudanças localmente e as commitou. Enquanto isso, um colega também fez mudanças e enviou antes de você. Quando você tenta fazer push, o Git rejeita — sua cópia local está desatualizada em relação ao remote.

```
Remote:  A --- B --- C   ← seu colega enviou C
Local:   A --- B --- D   ← seu commit D
                    ↑
          rejeitado! precisa fazer pull primeiro
```

### Passo 1 — Todos editam equipo.txt
Abra `equipo.txt` e adicione uma linha com seu nome, função e a data de hoje.

### Passo 2 — Preparar e fazer commit
```bash
git add 02-trabajo-en-equipo/equipo.txt
git commit -m "feat: adiciono [seu nome] ao arquivo do time"
```

### Passo 3 — Tentar fazer push
```bash
git push origin main
```

**Se você foi a primeira pessoa a fazer push:** vai funcionar. Aguarde seus colegas tentarem.

**Se alguém fez push antes de você:** você verá um erro assim:
```
! [rejected] main -> main (fetch first)
error: failed to push some refs
```
Isso não é um erro seu — o Git está protegendo o trabalho de todos. Continue para o Passo 4.

### Passo 4 — Baixar as mudanças do seu colega
```bash
git pull origin main
```

Se as suas mudanças e as do seu colega estão em **linhas diferentes**, o Git as integrará automaticamente. Você verá uma mensagem como `Merge made by the 'ort' strategy` — isso é sucesso.

Se estiverem na **mesma linha**, haverá um conflito. Veja a Parte B.

### Passo 5 — Fazer push novamente
```bash
git push origin main
```

### Passo 6 — Verificar
```bash
git log --oneline
```
Você deve ver tanto o seu commit quanto o do seu colega no histórico.

---

### A regra de ouro

> **Pull → Trabalhe → Add → Commit → Pull → Push**

Sempre faça pull antes de começar a trabalhar e faça pull novamente antes de enviar. Isso minimiza conflitos.

---

## Parte B — Resolvendo um conflito

### O cenário
Duas pessoas editaram a mesma linha. O Git mostra as duas versões e pede que você decida.

### Como um conflito aparece

Quando você faz `git pull` e há um conflito, o Git indica qual arquivo tem o problema. Ao abri-lo, você verá:

```
<<<<<<< HEAD
Sua versão da linha
=======
A versão do seu colega
>>>>>>> origin/main
```

### Como resolver

1. Abra o arquivo com o conflito (`conciliar.txt`).
2. Decida qual é a versão final — a sua, a do seu colega, ou uma combinação das duas.
3. Delete os marcadores de conflito: `<<<<<<<`, `=======`, `>>>>>>>`.
4. Salve o arquivo.
5. Prepare e faça commit:
```bash
git add 02-trabajo-en-equipo/conciliar.txt
git commit -m "fix: resolvo conflito em conciliar.txt"
```
6. Faça push:
```bash
git push origin main
```

### Para praticar com seu time

- **Pessoa A:** edita a linha 8 de `conciliar.txt`, faz commit e push.
- **Pessoa B:** edita a mesma linha 8 de `conciliar.txt` (sem fazer pull primeiro), faz commit e tenta fazer push.
- **Pessoa B:** verá a rejeição. Faz pull, resolve o conflito e faz push novamente.

> Dica: antes de resolver, converse com a Pessoa A. Um conflito é um ponto de partida para uma conversa, não apenas um problema técnico.

---

## 🙋 Fazendo isso sozinho?

**Para a Parte A:** faça sua mudança localmente, commit e push. Em seguida, abra o repositório no navegador (GitHub ou GitLab), navegue até `equipo.txt`, clique no ícone de edição (lápis), adicione uma segunda linha e faça commit diretamente pela interface web. Agora sua cópia local está desatualizada — execute `git pull` para ver a sincronização em ação.

**Para a Parte B:** repita o mesmo processo, mas edite **a mesma linha** pela interface web. Quando fizer pull localmente, você terá um conflito para resolver.

> Isso funciona porque você aceitou o convite de colaborador no `00-setup`. Você tem acesso de escrita ao repositório, inclusive pela interface web.

---

## Dicas
<details>
<summary>Ver dicas</summary>

- Sempre faça `git pull` antes de começar a trabalhar a cada dia.
- Se `git push` falhar com "rejected", significa que você precisa fazer pull primeiro — não que você fez algo errado.
- Em um conflito, a seção `HEAD` é o que você tem localmente, e a seção abaixo de `=======` é o que veio do remote.
- Após resolver um conflito, `git status` deve mostrar o arquivo como preparado (verde) antes de fazer commit.

</details>

---

Próximo: [03-ramas](../03-ramas/README.pt.md)
