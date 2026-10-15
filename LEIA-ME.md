# Cartão digital — Andes Tecnologia

## Publicação

1. Abra `index.html` e procure `const CONFIG`. Confira `phone` e `email`, já preenchidos com os contatos fornecidos.
2. Faça o upload da pasta `c/joao` para o domínio, mantendo `index.html` e a pasta `assets` juntos. Endereço sugerido: `https://www.andestecnologia.com.br/c/joao/`.
3. Caso escolha outra URL, ajuste as tags `og:image`, `og:url` no `<head>` e `CONFIG.publicUrl`.
4. Abra o endereço **https** em um celular, teste WhatsApp, e-mail, salvar contato e compartilhar.
5. Teste a prévia de compartilhamento usando o depurador de compartilhamento do Facebook e uma conversa do WhatsApp. Alguns aplicativos guardam prévias em cache.
6. Crie o QR Code após a URL definitiva estar publicada; o botão Compartilhar / QR gera a imagem a partir da URL da página (necessita acesso ao serviço de QR externo).

## Conteúdo

- `index.html`: página completa (HTML, CSS e JavaScript num único arquivo).
- `assets/bg-code.jpg`: fundo da capa, com camada clara aplicada em CSS.
- `assets/joao-carlos-almeida.png`: retrato transparente, posicionado independentemente do fundo.
- `assets/rocket.png`: ícone da chamada para orçamento.
- `assets/capa-andes-sem-mock.webp`: versão anterior da capa (ANDES-499), preservada.
- `assets/andes-tecnologia-logo.png`: logo original, exibida como camada independente na capa.
- `assets/capa-andes.webp`: referência original, preservada.
- `assets/compartilhamento.jpg`: imagem para prévia WhatsApp/LinkedIn (Open Graph).

## Observações

- Contatos configurados: WhatsApp +55 (11) 4420-1267 e e-mail joaocarlos@andestecnologia.com.br. A chamada de projeto abre https://andestecnologia.com.br/#contato.
- A página estática não exige backend.
- Os links de WhatsApp usam a API pública `wa.me` e o vCard é gerado diretamente no navegador.
- O QR Code é requisitado a `api.qrserver.com`. A URL pública é enviada ao serviço para gerar a imagem. Se quiser evitar serviço externo, substitua por gerador local ou biblioteca hospedada no próprio domínio.
- A capa usa fundo e retrato separados, com detalhe vermelho em CSS (`clip-path`). A logo original também é exibida separadamente, mantendo sua proporção.

## Layout responsivo (ANDES-500)

- A altura da capa acompanha a altura útil do navegador (`svh`), com limites mínimo e máximo. A foto mantém sua proporção e fica posicionada independentemente do fundo.
- Espaçamentos, ícones e botões foram compactados para priorizar o cartão inteiro na tela.
- Em telas muito baixas, no modo horizontal ou com texto ampliado, a página permite rolagem para preservar o acesso ao conteúdo. Não há bloqueio de rolagem nem escala global da página.
