---
name: radar
description: Roda o radar do dia com o time de agentes, na ordem pesquisador, verificador, redator, guarda (e o agente do dono, se existir), e depois grava o dia no repositório com um commit. Use quando alguém pedir para rodar o radar ou quando a rotina das 7h disparar.
---

# Radar do dia

Você coordena o time do radar. Você não pesquisa, não escreve o briefing e não opina. O seu trabalho é acionar cada agente, conferir o que ele gravou e só então passar para a próxima etapa. Faça uma etapa por vez, nesta ordem, sem pular nenhuma.

## Antes da etapa 1

1. Leia `RADAR.md` e `CLAUDE.md`.
2. Pegue a data e a hora de agora no fuso de Brasília (America/Sao_Paulo), no formato `AAAA-MM-DD` e `HH:MM`. Use a mesma data em todas as etapas, mesmo que a rodada passe da meia-noite.
3. Liste `.claude/agents/`. O time tem cinco agentes: `pesquisador`, `rastreador-precos`, `verificador`, `redator` e `guarda`. Qualquer outro agente nessa pasta é um **agente do dono**. Hoje há um: `auxiliartelecom`.
4. Acione cada agente pelo nome que está no cabeçalho dele. Se um agente do time não estiver disponível nesta sessão, pare e diga que é preciso abrir uma sessão nova do Claude Code nesta pasta. Não faça o trabalho dele no lugar.
5. Em todo acionamento, passe no pedido a pasta do projeto e a data. Para o redator, passe também a hora.
6. Conte os agentes que rodarem. O número entra no resumo final.

## Etapa 1: pesquisa

1. Acione o `pesquisador` e, ao mesmo tempo, o `rastreador-precos`. O rastreador roda aqui, e não na etapa 4, porque o redator usa os preços dele na linha "marcados que mudaram" do topo.
2. Confira se `fontes/AAAA-MM-DD.md` existe e conte os itens (os títulos `### N.`).
   - Se tiver três itens ou mais, siga.
   - Se tiver menos de três, ou se não houver nada novo, anote isso para o resumo e siga mesmo assim.
   - Se o arquivo não existir, o pesquisador falhou. Pare, mostre a resposta dele e não faça commit.
3. Confira se `precos/AAAA-MM-DD.md` existe. Se não existir, anote e siga: o redator escreve "sem dados hoje".

## Etapa 2: verificação

1. Acione o `verificador`.
2. Confira se `verificacao/AAAA-MM-DD.md` existe e se tem a tabela e a linha **Contagem**. Se não existir, pare, mostre a resposta dele e não faça commit.

## Etapa 3: redação

1. Acione o `redator`, passando a data e a hora.
2. Confira se existem `diario/AAAA-MM-DD.md`, `diario/AAAA-MM-DD-detalhes.md` e `diario/AAAA-MM-DD-baixa-confianca.md`, e se o `index.html` tem a data de hoje. Se faltar algum desses, pare, mostre a resposta do redator e não faça commit.

## Etapa 4: agente do dono

Se não houver agente além dos cinco do time, pule para a etapa 5. Se houver, acione cada um. Hoje é só o `auxiliartelecom`.

O que o agente devolver entra no fim do briefing, numa seção com o nome dele:

- **O conteúdo:** se o agente gravou a própria seção num arquivo, use o arquivo como está. O `auxiliartelecom` grava em `auxiliar/AAAA-MM-DD.md`, já com o título "## Auxiliar Telecom (opinião)". Se o agente não gravou arquivo, use a resposta dele sob o título `## <nome do agente>`.
- **No `diario/AAAA-MM-DD.md`:** ponha a seção logo antes da linha dos links do dia (`[Detalhes do dia]…`).
- **No `index.html`:** ponha a mesma seção em HTML simples (`<h2>`, `<p>`, `<strong>`, `<a href>`) logo antes de `</article>`, sem tocar no `<footer>`.
- **Sem duplicar:** se a seção já existir, porque a rodada foi repetida no mesmo dia, substitua a antiga.
- **Sem editar:** não mude nenhuma palavra do que o agente escreveu.

## Etapa 5: guarda

1. Acione o `guarda`.
2. Leia a última linha do relatório.
   - Se for **PODE PUBLICAR**, siga para a etapa 6.
   - Se for **NÃO PUBLIQUE**, ou qualquer outra coisa, pare. Mostre o relatório inteiro e não faça commit. Os arquivos do dia ficam na pasta para correção.

## Etapa 6: gravar no repositório (só com PODE PUBLICAR)

1. `git add -A`
2. `git commit -m "radar de AAAA-MM-DD"`
3. Se `git remote` listar um remoto, rode `git push`.
4. Se o push falhar, diga o motivo exato, com a mensagem do git, e pare. Não tente contornar: nada de `--force`, nada de trocar de remoto, nada de pedir ou digitar login, chave ou senha. O commit fica guardado no computador e sobe no próximo push.

## Etapa 7: resumo

Mostre em três linhas:

1. a primeira linha do briefing (a linha "Promoção do dia");
2. quantos itens conferiram, contados na linha **Contagem** do `verificacao/`. Exemplo: "7 de 9 conferiram, 2 foram para a aba de baixa confiabilidade";
3. quantos agentes rodaram, e quais.

Se alguma etapa anotou algo, diga numa linha a mais. Exemplos: menos de três itens, preços faltando, push que falhou.

## Nunca

- Enviar qualquer coisa a alguém além do commit e do push. Nada de e-mail, mensagem, notificação ou formulário.
- Usar, pedir ou digitar chave, senha ou token.
- Pular etapa, mudar a ordem ou fazer o trabalho de um agente no lugar dele.
- Editar o que os agentes escreveram. A única exceção é incluir a seção do agente do dono, na etapa 4.
- Fazer commit sem PODE PUBLICAR.
