# Site FiberXpress Telecom

Esta pasta é do site da empresa. Não tem relação com o radar da raiz do repositório (o `index.html` da raiz é a página do radar).

## Estado

**Esboço navegável:** `esboco.html`. Abre direto no navegador, é um arquivo único (logos e fontes embutidos). Prévias em `esboco-previa-desktop.jpg` e `esboco-previa-mobile.jpg`.

Os arquivos originais dos logos estão em `assets/img/` (`logo-colorido.png`, `logo-branco.png`). A imagem de fundo `6.png` não foi usada, como combinado.

## Como funciona o esboço

- Na primeira visita aparece o banner "Em qual cidade você está?". A escolha fica salva no navegador.
- A cidade escolhida muda: a página de planos, o botão de WhatsApp (topo, botão flutuante, contato), o endereço/horário e o texto do título.
- Links por cidade: `?cidade=ribeirao-pires`, `?cidade=ilha-comprida`, `?cidade=iguape` (úteis para Instagram e anúncios).
- Cada botão "Quero este plano" abre o WhatsApp da cidade com a mensagem já escrita (plano, valor, cidade).
- Abas: Início, Planos, Cobertura, Contratos, Contato.

## Pendências (etiqueta amarela "confirmar" no esboço)

1. **Iguape:** o endereço é igual ao de Ribeirão Pires; o telefone fixo é igual ao de Ilha Comprida; o WhatsApp tem DDD 11.
2. **Ilha Comprida e Iguape:** dois planos de 500 Mega (R$ 199,90 e R$ 249,90). Qual é a velocidade do segundo?
3. **Ribeirão Pires:** horário lido como "todos os dias 09:00–17:50, quinta até 20:00".
4. **Cobertura:** lista de bairros/ruas (ou mapa) de cada cidade.
5. **Contratos:** os PDFs (contrato de prestação, plano de serviço por cidade, termos dos SVA, política de privacidade).
6. Os quadrados dos planos mostram só "N apps à sua escolha" (a soma de Standard + Advanced + Premium, lida como apps que o cliente escolhe). Os nomes das categorias não aparecem no site.
7. **Ícones dos apps:** vêm do kit oficial no Canva ("Cópia de Ícones Aplicativos", design `DAG6dnO4yD4`). Os 17 recortes estão em `assets/img/apps/` (108 px, cantos arredondados): Smart Content, Ubook, HotGo, QNutri, Hub Vantagens, Social Comics, Fluid, Curta!On, Docway, Zen, Estuda+, Pequenos Leitores, Kiddle Pass, HBO Max, Disney+, SKY+ e Playkids+. Deezer usa a marca vetorial. **São recortes de miniatura:** para o site final, baixar os arquivos em alta resolução do Canva. Sem ícone no kit: Kaspersky, Looke, Noping, Playlist, Hube Revistas, O Jornalista, Queima Diária. Falta confirmar com o fornecedor dos SVA que os ícones podem aparecer no site.
8. **Foto no início (provisória):** a imagem do hero é uma foto de três pessoas usando notebook e celular, feita no Canva (design `DAHXMUZZV0Y`, "Foto aconchegante de pessoas usando a internet"). O arquivo usado no esboço é a miniatura de 387×516 px, que fica levemente suave em telas grandes e de alta densidade. Falta baixar a versão em alta resolução no Canva (Compartilhar > Baixar > JPG) e conferir se a licença do plano permite uso comercial no site. A ilustração vetorial anterior continua no histórico do git.
9. A faixa "Velocidade de até X Mega / Valores a partir de R$ 99,90" calcula o X pela cidade escolhida (600 em Ribeirão Pires, 500 nas outras duas).
10. **Modo claro (azul):** o botão (sol/lua) fica no canto superior direito e lembra a escolha no navegador (`localStorage`, chave `fx-tema`). O modo escuro (preto fosco e verde) é o padrão da marca; o modo claro usa azuis (fundo azul-gelo, cartões brancos, texto azul-marinho, botões e títulos em azul) para se diferenciar. Para abrir no modo do aparelho do visitante, basta usar `prefers-color-scheme` quando não houver escolha salva. As cores ficam em variáveis no início do CSS (`:root` e `:root[data-theme="light"]`); "Aberto agora" continua verde nos dois modos. Prévias: `esboco-previa-claro-desktop.jpg` e `esboco-previa-claro-mobile.jpg`.
11. **Galeria de apps:** no "Catálogo de apps" os 18 ícones (17 do kit + Deezer) flutuam dentro do quadrado, com o nome ao passar o mouse ou tocar; os apps sem ícone (Playlist, Kaspersky, Looke, Noping, Hube Revistas, O Jornalista, Kaspersky Plus, Queima Diária) ficam numa linha de texto abaixo. Os ícones (61 px no desktop, 36–54 px no celular) formam um bloco compacto e centralizado, com cerca de 20 px de vão, e o quadrado se ajusta à altura do bloco; as posições são calculadas pela largura, sem sobreposição. Com "reduzir movimento" ativado no aparelho, os ícones ficam parados. Prévia: `esboco-previa-galeria.jpg`.
12. **Topo:** o nome "FiberXpress" fica ao lado da logo (o "X" usa a cor de destaque do tema). O menu de três risquinhas passa a valer a partir de 1120 px de largura (antes 900 px), porque abaixo disso a barra completa não cabia com o nome. Em telas de até 540 px o nome some e fica só a logo, para sobrar espaço ao seletor de cidade, ao botão de tema e ao menu.
13. **Galeria de banners ("Promoções e novidades"):** faixa horizontal entre o início e os planos. Cada banner fica cerca de 10 segundos na tela (`TROCA_MS = 10000` no script) e a lista volta ao primeiro depois do último. A troca automática para ao passar o mouse, ao focar um botão, ao tocar, com a aba em segundo plano ou fora da tela, e o botão play/pausa no canto liga e desliga. Com "reduzir movimento" ativado no aparelho a troca automática fica desligada. Há setas, pontos e arrasto com o dedo. São 7 banners: benefício "Ubook Go grátis", "Escolha seus apps", dois de plano (o maior e o de entrada da cidade escolhida, com botão de WhatsApp da cidade), Instagram, Facebook e um espaço de promoção marcado "confirmar".
    - **Imagens provisórias:** os fundos são imagens aleatórias de fibras luminosas nas cores da marca, geradas só para o esboço (`assets/img/banners/banner-1.webp` a `banner-7.webp`, 1000×500 px). Para a arte final, usar 1000×500 px (2:1), com o lado esquerdo mais limpo, onde fica o texto. Se a arte já trouxer texto e botão, o banner pode ser de imagem inteira (opção `soImagem: true` na lista `montarBanners()`, com `src`, `alt` e `cta.href`).
    - **Pendente:** texto e arte reais das promoções (o banner "Sua promoção aqui" é só um espaço reservado), e se o Instagram e o Facebook terão arte própria. Os textos dos banners ficam na função `montarBanners()` do script.
    - Prévia: `esboco-previa-banners.jpg`.
