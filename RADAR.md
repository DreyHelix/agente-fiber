# RADAR — Fibra óptica e telecom para provedores

Definição do radar no formato CLARO. O time de agentes lê este arquivo antes de cada execução.

---

## C — Contexto e fontes

**Assunto:** produtos de telecom para redes de acesso de provedores no Brasil, com foco em fibra óptica/FTTH: materiais, equipamentos e ferramental.

- **Primeiro plano — fibra/FTTH:** cabos (drop, autossustentado), caixas (CTO, CEO), splitters, conectores e cordões, OLT/ONU, máquinas de fusão, OTDR, power meter, clivadores e ferramentas de instalação.
- **Segundo plano — demais produtos de provedor:** rádios, switches, roteadores, nobreaks, torres.

**Por que importa:** decidir **onde comprar**. Preço e confiança têm o mesmo peso. Um bom lugar para comprar precisa ser **barato e seguro**: fornecedor sério, produto homologado pela Anatel, garantia, estoque e prazo de entrega.

**Fontes:**
- **Principais:** Abrint, Fiberflex, FiberHome.
- **Outras:** todas as que o time encontrar, mas cada item mostra a origem. Se a fonte for fraca, o item vai para a **aba de baixa confiabilidade**, não para o briefing (ver Resultado).

---

## L — Limites

**Interessa:** qualquer informação sobre os produtos do escopo, nesta ordem de prioridade:
1. promoções;
2. lançamentos;
3. o resto: estoque, alta ou queda de preço, homologação Anatel, recall, produto pirata ou sem homologação.

**Não interessa (fica fora):**
- celular e produto de consumidor final;
- notícias corporativas (fusões, balanços);
- leilões e política de telecom;
- vagas de emprego.

**O radar nunca:**
- apresenta opinião como se fosse fato;
- traz preço sem link ou sem data;
- cita rede social ou grupo de WhatsApp sem fonte;
- fala de pessoas (fofoca, bastidores);
- recomenda loja sem mostrar de onde veio a informação.

---

## A — Ação (o que o time faz todo dia)

Os agentes estão em `.claude/agents/` e rodam nesta ordem:

1. **Pesquisador** (`pesquisador`): varre as fontes principais e o resto da internet atrás de promoções, lançamentos e novidades do escopo, começando por fibra/FTTH. Grava de 5 a 10 itens brutos em `fontes/AAAA-MM-DD.md`.
2. **Rastreador de preços** (`rastreador-precos`), ao mesmo tempo que o pesquisador: para cada produto de `precos/produtos-marcados.md`, busca o preço atual e acrescenta linhas em `precos/historico.csv`. Compara com o histórico e grava o resumo das mudanças em `precos/AAAA-MM-DD.md`.
3. **Verificador** (`verificador`): reabre cada link e confere se a página diz o que o item afirma (CONFERE, NÃO CONFERE ou NÃO ABRIU). Anota os sinais de confiança (CNPJ visível, homologação Anatel, garantia, estoque e prazo) e classifica cada item como **CONFIÁVEL** ou **BAIXA** (critérios em Resultado). Grava em `verificacao/AAAA-MM-DD.md`.
4. **Auxiliar Telecom** (`auxiliartelecom`): com os itens que conferiram e os preços, escreve uma seção curta e descontraída, **marcada como opinião**, com a dica de preço baixo, as promoções à vista e o que ele faria na compra. Grava a seção em `auxiliar/AAAA-MM-DD.md` e a entrega em texto puro em `auxiliar/AAAA-MM-DD.txt`.
5. **Redator** (`redator`): usa só os itens que conferiram. Ordena fibra antes do resto, e promoções e lançamentos antes do resto. Escreve os três arquivos do dia em `diario/`, com a seção do Auxiliar Telecom no fim do briefing, e gera o `index.html` a partir do `modelo-index.html`.
6. **Guarda** (`guarda`): lê tudo o que vai ser publicado e termina com **PODE PUBLICAR** ou **NÃO PUBLIQUE**. Qualquer achado bloqueia a publicação.

---

## R — Resultado

**Três arquivos por dia, mais a página:**
- `diario/AAAA-MM-DD.md`: o briefing, direto, cabe em uma página. Só traz itens CONFERE e CONFIÁVEL.
- `diario/AAAA-MM-DD-detalhes.md`: os detalhes de cada item, **com a mesma numeração** (o item 4 do briefing é o item 4 dos detalhes).
- `diario/AAAA-MM-DD-baixa-confianca.md`: a **aba de baixa confiabilidade**. Reúne até 10 itens que batem com a fonte, mas cuja fonte é fraca. Cada item traz link, data e **o motivo** de estar ali.
- `index.html`: a página do dia, gerada a partir do `modelo-index.html`, com links para os dias anteriores.

**Um item vai para a aba de baixa confiabilidade quando:**
- a loja ou o site é desconhecido, ou não mostra CNPJ;
- o preço está suspeito: mais de 30% abaixo do menor preço do histórico ou das outras lojas;
- o produto exige homologação Anatel e ela não foi encontrada;
- o lançamento foi anunciado só por revendedor, sem confirmação do fabricante;
- a página não tem data, ou as fontes se contradizem.

Na aba, as regras do "nunca" continuam valendo: sem link e data o item não entra, e rede social ou WhatsApp sem fonte continua fora.

**Topo (os primeiros cinco segundos):** três linhas, nesta ordem:
1. **Melhor promoção do dia**
2. **Produtos marcados que mudaram de preço**
3. **O que exige ação hoje** (promoção que acaba hoje, estoque acabando, preço abaixo do menor já registrado)

Se uma das linhas não tiver novidade, ela diz "nada hoje".

**Corpo:** até **10 itens**, numerados. Cada item traz título, duas ou três linhas diretas e o link. Todo preço vai com loja e data. Se o dia estiver fraco, o briefing sai com menos itens. O time nunca completa com item fraco para chegar a dez.

**O que não conferiu:** só os títulos dos itens que não bateram com a fonte ou não abriram.

**Tom:** direto. Especificações, sinais de confiança e comparação de preço ficam só no arquivo de detalhes.

**Modelo do briefing:**

```markdown
# Radar — AAAA-MM-DD

**Promoção do dia:** <produto> por R$ <valor> na <loja> (<data>) — <link>
**Marcados que mudaram:** <produto> R$ <antes> → R$ <agora> (<loja>) — <link> | nada hoje
**Ação hoje:** <o que fazer e até quando> — <link> | nada hoje

## Itens

1. **<título>**
   <linha 1>. <linha 2>.
   <link>

## O que não conferiu

- <título>

[Detalhes do dia](AAAA-MM-DD-detalhes.md) · [Baixa confiabilidade](AAAA-MM-DD-baixa-confianca.md)

Gerado em AAAA-MM-DD às HH:MM (horário de Brasília)
```

---

## O — Observáveis (como sei que o briefing de hoje está bom)

- [ ] Toda afirmação tem link, e todo preço tem loja e data.
- [ ] Nada fora do tema: tudo está no escopo e respeita os limites.
- [ ] Cabe em uma página.
- [ ] O topo tem as três linhas, na ordem certa.
- [ ] São no máximo 10 itens, e a numeração bate com o arquivo de detalhes.
- [ ] Todo produto marcado ganhou uma linha nova no histórico de preços (mesmo que seja "não encontrado").
- [ ] Toda loja fora das fontes principais mostra de onde veio.
- [ ] Nenhum item de baixa confiabilidade aparece no briefing principal, e todo item da aba de baixa confiabilidade diz por que está ali.
- [ ] O guarda terminou com PODE PUBLICAR.
