# Site FiberXpress Telecom

Esta pasta é do site da empresa. Não tem relação com o radar da raiz do repositório (o `index.html` da raiz é a página do radar).

## Arquivos

| O que | Onde |
|---|---|
| Site completo para abrir no navegador (arquivo único, com `noindex`, para testes) | `esboco.html` |
| **Pasta pronta para subir na KingHost** (indexável, ícones, SEO, `.htaccess`) | `publicar-kinghost/` |
| Passo a passo de publicação | `COMO-PUBLICAR-KINGHOST.md` |
| Logos originais, ícones dos apps, artes dos banners | `assets/img/` |
| Prévias em imagem | `esboco-previa-*.jpg` |

`esboco.html` e `publicar-kinghost/index.html` têm o mesmo conteúdo. A diferença é que o segundo pode ser indexado pelo Google e tem as tags de SEO. Eles são gerados a partir de um modelo, então não edite os dois à mão: peça a alteração e eu regenero.

## Como o site funciona

- Na primeira visita aparece o banner "Em qual cidade você está?". A escolha fica salva no navegador.
- A cidade escolhida muda: os planos, o botão de WhatsApp (topo, botão flutuante, contato, banners), o endereço e o horário, e o título.
- Links por cidade: `?cidade=ribeirao-pires`, `?cidade=ilha-comprida`, `?cidade=iguape` (úteis para Instagram e anúncios).
- Cada "Quero este plano" abre o WhatsApp da cidade com a mensagem pronta (plano, valor, cidade).
- Abas: Início, Planos, Cobertura, Contratos, Contato. Botão sol/lua alterna o modo escuro (preto fosco e verde, padrão) e o claro (azul).

## Decisões já tomadas (rodadas de perguntas de 15/10/2026)

- **Iguape:** WhatsApp (13) 99672-6219, endereço Largo Durvalino Vieira, nº 83, telefone fixo igual ao de Ilha Comprida, (13) 3842-7002.
- **Planos:** a contagem de apps (1, 2, 3 e 4) foi confirmada. Os dois planos de 500 Mega de Ilha Comprida e Iguape têm a mesma velocidade e mudam só nos apps. "Ubook Go grátis" vale em todos, sem prazo.
- **Cartões dos planos:** mostram "Roteador Wi-Fi em comodato" e "Envio de até 60% do download". Fidelidade e taxa de instalação ficaram de fora, por decisão do dono.
- **Horário de Ribeirão Pires:** confirmado (todos os dias 09:00–17:50, quinta até 20:00).
- **Cobertura:** sem lista de bairros. Há o formulário "Chega na sua rua?" e um botão que abre o WhatsApp da cidade perguntando sobre o endereço.
- **Banners:** 6 banners (Ubook Go, Escolha seus apps, dois planos da cidade, Instagram, Facebook), troca a cada ~10 s. O espaço "Sua promoção aqui" foi removido. As artes são ilustrações vetoriais feitas para o assunto de cada banner (fones e livro, ladrilhos de apps, velocímetro, casa com Wi-Fi, celular do Instagram, joinha do Facebook). Para trocar por arte própria: imagens de 1000×500 px (2:1), em `assets/img/banners/`.
- **Ícones dos apps:** o kit é do fornecedor dos SVA, uso autorizado pelo dono.
- **Domínio:** `www.fiberxpress.com.br` (hospedagem na KingHost, envio por FTP). O endereço principal é o com "www". Para usar o sem "www", é só pedir.
- **Medição:** nenhuma (sem Google Analytics, sem pixel, sem cookies, sem aviso de cookies). Se for adicionar depois, a política de privacidade e o aviso de cookies precisam mudar junto.

## Pendências (nada disso é visível ao visitante, mas precisa ser resolvido antes de divulgar)

1. **Contratos (bloqueia o lançamento):** hoje os botões dizem "Em breve". [Provável] A Anatel exige contrato e plano de serviço publicados no site. Enviar os PDFs (contrato de prestação, plano de serviço de cada cidade, termos dos apps/SVA) e eu ligo cada botão. No código, é o bloco `DOCS` no início do script: troque `null` pelo caminho do arquivo (ex.: `'docs/contrato.pdf'`) e coloque os PDFs na pasta `docs/` ao lado do `index.html`.
2. **Política de privacidade:** o texto no site é um **rascunho** escrito por mim, com uma nota "Texto em revisão jurídica". Ele só vale enquanto o site não guardar dados nem usar ferramentas de análise. Peça a revisão de um advogado e, depois de aprovada, troque `POLITICA_REVISADA` para `true` no script (a nota some). Se o advogado preferir um PDF próprio, é só enviar.
3. **"Envio de até 60% do download":** o número veio de "uns 60%". Confirme com a parte técnica antes de publicar, porque vira promessa comercial.
4. **Linha da Anatel (1331)** na aba Contratos: fui eu que acrescentei, não veio do arquivo da empresa. O número 1331 é o da central da Anatel. Apague se não quiser.
5. **Foto do início (provisória):** miniatura de 387×516 px feita no Canva (design `DAHXMUZZV0Y`), fica levemente suave em telas grandes. Trocar por foto real da equipe ou de instalação, ou baixar a versão grande no Canva e conferir a licença para uso comercial.
6. **Ícones em alta resolução:** os 17 ícones são recortes de miniatura do kit (design `DAG6dnO4yD4`, 108 px). Pedir os arquivos originais ao fornecedor. Sem ícone no kit (aparecem só como texto): Kaspersky, Looke, Noping, Playlist, Hube Revistas, O Jornalista, Queima Diária.
7. **Promoções:** quando houver uma promoção real, enviar texto, valor, prazo e cidades, e eu incluo o banner.
8. **Teste em aparelho real:** os testes automáticos rodaram em Chromium (Chrome/Edge). Falta abrir em iPhone (Safari) e em Android. Os horários de "Aberto agora" usam o fuso de Brasília.
9. **Depois de publicar:** cadastrar o site no Google Search Console, enviar o `sitemap.xml` e criar o Google Meu Negócio das 3 unidades. [Provável] Para provedor local, o Meu Negócio costuma trazer mais contatos que o próprio site.

## Notas técnicas

- **Etiquetas "confirmar":** o código ainda tem o mecanismo das etiquetas amarelas. Estão desligadas (`REVISAO = false`). Ligue para ver de novo onde há dado em dúvida.
- **Temas:** as cores ficam em variáveis no início do CSS (`:root` e `:root[data-theme="light"]`). A escolha é lembrada no navegador (`localStorage`, chave `fx-tema`).
- **Galeria de apps:** 18 ícones flutuando no "Catálogo de apps", com o nome ao passar o mouse ou tocar. Com "reduzir movimento" ativado no aparelho, ficam parados.
- **Banners:** o texto de cada banner fica na função `montarBanners()` do script; o tempo de troca é `TROCA_MS` (10000 ms). A troca é automática e **em círculo**: depois do último volta ao primeiro, para sempre. Não há botão de play/pausa nem setas (removidos a pedido do dono); a navegação manual é pelos pontos, pelo arrasto com o dedo ou pelo mouse. A troca para sozinha enquanto o mouse está sobre os banners, enquanto há foco ou toque neles, com a aba em segundo plano ou fora da tela. Com "reduzir movimento" ativado no sistema a troca continua, mas sem animação (o banner muda de uma vez). [Atenção] Sem botão de pausa, quem não consegue parar o movimento só tem o mouse parado em cima; as diretrizes de acessibilidade (WCAG 2.2.2) pedem um controle de pausa para conteúdo que se move sozinho por mais de 5 s. Se isso importar, o botão pode voltar discreto. Em telas de 1366 px aparecem 2 banners por vez, então os dois últimos (Instagram e Facebook) aparecem juntos no fim e o ponto 5 não chega a acender. No celular e até 1100 px a arte fica em cima e o texto embaixo.
- **Topo:** o nome "FiberXpress" fica ao lado da logo. O menu de três risquinhas vale a partir de 1120 px de largura. Até 540 px o nome some e fica só a logo.
