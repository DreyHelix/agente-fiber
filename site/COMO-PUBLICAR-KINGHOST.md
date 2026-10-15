# Como publicar o site na KingHost

Tempo: uns 15 minutos. Você não precisa saber programar.

## Antes de começar

1. **Confira as pendências 1 a 3 do `LEIA-ME.md`.** Sem os PDFs dos contratos os botões ficam "Em breve", e o site não deveria ser divulgado assim.
2. **Ative o SSL (HTTPS) do domínio** no painel da KingHost: Hospedagem > SSL (Let's Encrypt gratuito) para `www.fiberxpress.com.br` e `fiberxpress.com.br`. Faça isso **antes** de subir o `.htaccess`, senão o redirecionamento para HTTPS derruba o site.
3. Tenha o usuário e a senha de FTP da hospedagem (painel KingHost > FTP) e um programa de FTP, como o FileZilla. O Gerenciador de Arquivos do painel também serve.

## Passo a passo

1. Abra a pasta `site/publicar-kinghost/` (ou descompacte o `fiberxpress-kinghost.zip`).
2. Entre no FTP e abra a pasta pública do domínio (na KingHost costuma ser `public_html` ou `www`).
3. Envie **todos os arquivos de dentro** da pasta, sem criar uma subpasta. Atenção ao arquivo `.htaccess`: ele começa com ponto e pode ficar oculto no seu computador. No FileZilla, ative "Servidor > Forçar exibição de arquivos ocultos".
4. Se já houver um `index.html` ou `index.php` antigo (página padrão da KingHost), apague ou renomeie, senão ele aparece no lugar do site.
5. Os PDFs dos contratos: crie a pasta `docs/` e envie os arquivos. Depois me peça para ligar os botões, e eu gero uma nova pasta.

## Conferindo se deu certo

- `http://fiberxpress.com.br` deve ir sozinho para `https://www.fiberxpress.com.br`.
- Abra no celular e escolha uma cidade. O botão de WhatsApp deve abrir a conversa da cidade certa.
- Cole o endereço no WhatsApp: deve aparecer a prévia com a imagem da FiberXpress.
- `https://www.fiberxpress.com.br/robots.txt` e `.../sitemap.xml` devem abrir.
- Uma página que não existe (`.../teste`) deve mostrar o aviso 404 da FiberXpress.

## Se algo der errado

- **Erro 500 depois de subir o `.htaccess`:** apague o arquivo e me avise. Geralmente é o SSL ainda não ativado ou o servidor ser Nginx, não Apache.
- **O site abre sem o visual (texto puro):** o `index.html` não foi inteiro. Reenvie em modo binário.
- **Continua aparecendo a página antiga:** limpe o cache do navegador (Ctrl+F5) e confira o item 4 acima.

## Depois que o site estiver no ar

1. **Google Search Console** (search.google.com/search-console): adicione o site e envie `https://www.fiberxpress.com.br/sitemap.xml`.
2. **Google Meu Negócio:** crie uma ficha para cada unidade (Ribeirão Pires, Ilha Comprida e Iguape) com endereço, horário, telefone e o link do site com `?cidade=` da cidade (ex.: `https://www.fiberxpress.com.br/?cidade=iguape`).
3. Use os links por cidade na bio do Instagram e nos anúncios.
