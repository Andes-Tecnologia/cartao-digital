# Cartão digital — Andes Tecnologia

## Publicação

1. Abra `index.html` e procure `const CONFIG`. Preencha `phone` e `email` com seus dados reais.
2. Faça o upload da pasta `c/joao` para o domínio, mantendo `index.html` e a pasta `assets` juntos. Endereço sugerido: `https://www.andestecnologia.com.br/c/joao/`.
3. Caso escolha outra URL, ajuste as tags `og:image`, `og:url` no `<head>` e `CONFIG.publicUrl`.
4. Abra o endereço **https** em um celular, teste WhatsApp, e-mail, salvar contato e compartilhar.
5. Teste a prévia de compartilhamento usando o depurador de compartilhamento do Facebook e uma conversa do WhatsApp. Alguns aplicativos guardam prévias em cache.
6. Crie o QR Code após a URL definitiva estar publicada; o botão Compartilhar / QR gera a imagem a partir da URL da página (necessita acesso ao serviço de QR externo).

## Conteúdo

- `index.html`: página completa (HTML, CSS e JavaScript num único arquivo).
- `assets/capa-andes-sem-mock.webp`: capa usada na página, editada para remover bordas e recorte superior do celular (ANDES-499).
- `assets/capa-andes.webp`: imagem original de referência, preservada.
- `assets/compartilhamento.jpg`: imagem para prévia WhatsApp/LinkedIn (Open Graph).

## Observações

- Nenhum telefone ou e-mail foi inventado. Campos vazios mostram aviso até serem configurados.
- A página estática não exige backend.
- Os links de WhatsApp usam a API pública `wa.me` e o vCard é gerado diretamente no navegador.
- O QR Code é requisitado a `api.qrserver.com`. A URL pública é enviada ao serviço para gerar a imagem. Se quiser evitar serviço externo, substitua por gerador local ou biblioteca hospedada no próprio domínio.
- A imagem de capa é derivada de uma captura de tela. Para um resultado de produção ideal, exporte separadamente o fundo, a foto de perfil e a logo em boa resolução.
