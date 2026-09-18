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

1. **Pesquisador:** varre as fontes principais e o resto da internet atrás de promoções, lançamentos e novidades do escopo. Começa por fibra/FTTH.
2. **Rastreador de preços:** para cada produto listado em `precos/produtos-marcados.md`, busca o preço atual nas lojas e acrescenta uma linha em `precos/historico.csv`. Compara com o histórico e aponta o que mudou.
3. **Verificador:** abre cada link e confere se a página diz o que o item afirma. Registra loja e data e checa os sinais de confiança: CNPJ visível, homologação Anatel quando se aplica, garantia, estoque e prazo. Depois classifica cada item como **confiável** ou **baixa confiabilidade** (critérios em Resultado).
4. **Editor:** corta o que está fora do escopo ou fere os limites, ordena os itens (fibra antes do resto, promoções e lançamentos antes do resto) e escreve os três arquivos do dia: briefing, detalhes e baixa confiabilidade.

---

## R — Resultado

**Três arquivos por dia:**
- `briefings/AAAA-MM-DD.md`: o briefing, direto, cabe em uma página. Só traz itens confiáveis.
- `briefings/AAAA-MM-DD-detalhes.md`: os detalhes de cada item, **com a mesma numeração** (o item 4 do briefing é o item 4 dos detalhes).
- `briefings/AAAA-MM-DD-baixa-confianca.md`: a **aba de baixa confiabilidade**. Reúne até 10 itens que podem valer uma olhada mas não passaram na verificação. Cada item traz link, data e **o motivo** de estar ali.

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

**Corpo:** até **10 itens**, numerados. Cada item ocupa uma linha: tipo, o que é, preço (se houver), loja ou fonte e link. Se o dia estiver fraco, o briefing sai com menos itens. O time nunca completa com item fraco para chegar a dez.

**Tom:** direto. Especificações, contexto, comparação de preço e sinais de confiança ficam só no arquivo de detalhes.

**Modelo do briefing:**

```markdown
# Radar — AAAA-MM-DD

**Promoção do dia:** <produto> por R$ <valor> na <loja> — <link>
**Marcados que mudaram:** <produto> R$ <antes> → R$ <agora> (<loja>) — <link> | nada hoje
**Ação hoje:** <o que fazer e até quando> — <link> | nada hoje

1. [Fibra · Promoção] <produto> — R$ <valor> · <loja> · <link>
2. [Fibra · Lançamento] <produto> — <fabricante> · <link>
3. [Telecom · Alerta] <fato> — <fonte> · <link>
...
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
