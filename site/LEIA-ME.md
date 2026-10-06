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
7. **Logos dos apps:** só Kaspersky e Deezer estão com a marca real. Os outros (Disney+, Max, Sky+ com Globo, Looke, Ubook, Playkids+) estão como tile tracejado com as iniciais. Falta o logo oficial (SVG ou PNG) de cada um, do kit de marca do fornecedor dos SVA, e a confirmação de que a empresa pode usá-los no site.
