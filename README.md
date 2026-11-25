# Meu mês de entregas — pacote para instalar no celular e gerar o APK

## O que tem aqui
- `index.html` — o app (mesmo conteúdo publicado no chat, com as tags do PWA já inseridas)
- `manifest.webmanifest` — nome, cores e ícones do app
- `sw.js` — service worker: deixa o app abrir mesmo sem internet, usando a última versão salva
- `icons/` — ícones em vários tamanhos, incluindo os "maskable" (Android recorta em círculo, quadrado etc.)

## Passo 1 — Colocar no ar com o GitHub Pages (grátis)
1. Crie uma conta em https://github.com (se não tiver).
2. Crie um repositório novo, por exemplo `app-entregador`. Pode ser público.
3. Suba estes arquivos para a raiz do repositório, mantendo a pasta `icons/`:
   - pelo site do GitHub: abra o repositório → "Add file" → "Upload files" → arraste todos os arquivos e a pasta `icons`
4. No repositório, vá em Settings → Pages.
5. Em "Source", escolha a branch `main` e a pasta `/root`, depois Save.
6. Em 1 a 2 minutos o GitHub mostra o link, algo como:
   `https://SEU-USUARIO.github.io/app-entregador/`
7. Abra esse link no celular. Ele é o novo link do app (pode substituir o link do chat).

Importante: o app usa o armazenamento do navegador (localStorage) para guardar seus dados.
Isso é por site. Se você trocar de link (do chat para o GitHub Pages), os dados não se
copiam sozinhos — comece a usar o link novo do zero, ou veja no fim deste arquivo como
exportar e importar.

## Passo 2 — Gerar o APK com o PWABuilder
1. Acesse https://www.pwabuilder.com
2. Cole o link do GitHub Pages (passo 1) e clique em "Start".
3. O PWABuilder vai ler o `manifest.webmanifest` e o `sw.js` sozinho. Se ele pedir para
   corrigir algo, normalmente é só clicar em "Fix" ou seguir a sugestão na tela.
4. Vá até a seção "Package for stores" → escolha "Android".
5. Preencha o nome do pacote (algo como `com.seunome.entregas`) e baixe o pacote gerado.
6. Dentro do pacote baixado tem um arquivo `.apk` (ou `.aab`, que é o formato para a Play Store).
   O `.apk` é o que você distribui direto (GitHub, Mediafire etc.).
   O `.aab` é o que a Google Play pede, se for publicar lá.

Esta etapa eu não testei, porque não tenho acesso a esses sites aqui. Se der erro,
me mande a mensagem exata que eu ajudo a resolver.

## Quando quiser atualizar o app depois
1. Edite o `index.html` com a versão nova.
2. Abra o `sw.js` e troque `entregas-v1` para `entregas-v2` (sempre subir o número).
   Sem isso, o celular de quem já instalou continua vendo a versão antiga.
3. Suba os arquivos de novo no GitHub (mesmo processo do passo 1.3).
4. Quem usa como PWA (sem ser pelo APK) recebe a atualização sozinho, na próxima vez
   que abrir com internet. Quem instalou o APK precisa gerar e instalar um novo APK.

## Se quiser publicar na Google Play
- Taxa única de US$ 25 na conta de desenvolvedor.
- Contas pessoais novas (criadas depois de 13/11/2023) passam por um teste fechado:
  pelo menos 12 pessoas testando por 14 dias seguidos, antes de liberar ao público.
- Depois disso, é pelo arquivo `.aab` que o PWABuilder gera.

## Observações importantes
- Não testei o site no seu celular nem o processo completo no GitHub Pages e no PWABuilder.
- As informações sobre a Google Play e a verificação de desenvolvedor do Android foram
  conferidas por busca em novembro de 2026 e podem mudar.
- Eu não sou advogada nem contadora. Para CNPJ, nota fiscal e venda de assinatura,
  procure um contador.
