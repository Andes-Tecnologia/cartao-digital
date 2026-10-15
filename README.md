# Cartão digital · Andes Tecnologia

Cartão de apresentação responsivo com links de contato, exportação para a agenda e compartilhamento. Construído com HTML, CSS e JavaScript, sem backend, banco de dados ou etapa de build.

A implementação usa os dados de João Carlos Almeida, da Andes Tecnologia. Para adaptar o cartão, revise os dados e os materiais visuais antes de publicar.

## Funcionalidades

- Acesso a e-mail, WhatsApp, site e formulário de contato.
- Download de contato no formato vCard (`.vcf`).
- Compartilhamento nativo quando disponível, com alternativa de QR Code e cópia de link.
- Capa com fundo, logo e retrato em camadas independentes; detalhe vermelho em CSS.
- Layout ajustado à altura disponível, permitindo rolagem em telas baixas ou com texto ampliado.
- Indicação de foco para navegação por teclado e respeito à preferência de movimento reduzido.

## Executar localmente

Clone o repositório e entre na pasta:

```bash
git clone https://github.com/Andes-Tecnologia/cartao-digital.git
cd cartao-digital
```

Não é necessário instalar pacotes. Com PHP disponível, inicie um servidor estático:

```bash
php -S localhost:8000
```

Abra **http://localhost:8000**. Para encerrar, pressione `Ctrl+C`.

Também é possível abrir `index.html` diretamente, mas usar um servidor HTTP facilita a conferência dos recursos e dos links.

### Acessar pelo celular

Inicie o servidor aceitando conexões da rede local:

```bash
php -S 0.0.0.0:8000
```

Com o computador e o celular na mesma rede, abra `http://IP-DO-COMPUTADOR:8000` no celular. No macOS, você pode consultar o IP da interface Wi-Fi com:

```bash
ipconfig getifaddr en0
```

O nome da interface pode variar. Se necessário, consulte o endereço nas configurações de rede e permita conexões de entrada para o servidor no firewall. Esse servidor é destinado ao desenvolvimento local.

## Estrutura

```text
.
├── index.html                     # HTML, estilos e lógica do cartão
├── assets/
│   ├── andes-tecnologia-logo.png   # Logo
│   ├── bg-code.jpg                # Fundo da capa
│   ├── joao-carlos-almeida.png     # Retrato sem fundo
│   ├── rocket.png                 # Ícone da chamada de projeto
│   ├── compartilhamento-v2.jpg    # Prévia de compartilhamento
│   ├── qrcode-cartao-joao-carlos.jpg # QR Code personalizado
│   ├── capa-andes.webp            # Referência visual original
│   └── capa-andes-sem-mock.webp    # Composição anterior, preservada
└── README.md
```

## Personalizar

Em `index.html`, procure `const CONFIG`:

| Campo | Uso |
|---|---|
| `name` | Nome exibido e exportado no contato. |
| `role` | Cargo exibido e exportado no contato. |
| `company` | Empresa usada no contato e no compartilhamento. |
| `phone` | Número de WhatsApp com DDI e DDD, somente dígitos. |
| `email` | Endereço de e-mail. |
| `website` | Site do botão principal e do contato exportado. |
| `publicUrl` | Endereço do cartão para compartilhar e copiar; vazio usa a URL atual, sem parâmetros ou fragmento. Não altera a imagem do QR Code. |
| `shareDescription` | Texto enviado ao compartilhamento nativo. |
| `whatsappMessage` | Mensagem inicial da conversa. |

Alguns dados estão no HTML ou no JavaScript fora de `CONFIG`. Revise também:

- `<title>`, descrição, metadados Open Graph e textos alternativos das imagens.
- Links iniciais dos elementos `#email`, `#whatsapp` e `#website`, e o link do site no rodapé.
- Destino da chamada `#cta`, atualmente `https://andestecnologia.com.br/#contato`.
- Nome do arquivo `.vcf` em `a.download` e texto da mensagem de compartilhamento.
- Imagens em `assets/` e suas referências, dimensões e posições no CSS.

Use materiais próprios ou que você tenha autorização para publicar. Alterar `CONFIG` não substitui automaticamente todos os textos e links estáticos.

## Salvar contato

O botão gera `joao-carlos-almeida.vcf` no próprio navegador, em vCard 3.0, com nome, empresa, cargo, telefone, e-mail e site. Telefone e e-mail vazios são omitidos. Não há envio desses dados a um backend para gerar o arquivo.

Para conferir no celular, toque em **Salvar contato**, abra o arquivo caso seja baixado e confirme a importação na agenda. Verifique os dados antes de salvar. O site não adiciona contatos automaticamente; a tela de importação depende do sistema e do navegador.

## Compartilhamento e serviços externos

Quando o navegador disponibiliza o compartilhamento nativo, o botão abre essa interface. Caso contrário, ou se ela falhar, abre uma janela com QR Code e opção de copiar o link. Cancelar o compartilhamento nativo encerra a ação.

O QR Code é a imagem local `assets/qrcode-cartao-joao-carlos.jpg`, exibida inteira e sem geração por serviço externo. O conteúdo codificado foi conferido e aponta para:

```text
https://andestecnologia.com.br/cartao-de-visita/joao-carlos-almeida/
```

A imagem usa o domínio sem `www`; `CONFIG.publicUrl` usa o domínio com `www`. Na verificação da integração, os dois endereços retornaram o mesmo conteúdo. Mantenha ambos acessíveis ou configure um redirecionamento ao alterar a hospedagem.

Mudar `CONFIG.publicUrl` não atualiza esse QR Code. Se o endereço de destino mudar, forneça uma nova imagem, confira seu conteúdo com um leitor e substitua o arquivo. Preserve as margens de leitura, o contraste e a proporção. O QR é estático: o projeto não oferece redirecionamento editável ou métricas de leitura.

A cópia de link usa a API de área de transferência e pode depender de HTTPS e das permissões do navegador. Se falhar, a página orienta a copiar o endereço exibido.

A fonte Montserrat é carregada pelo Google Fonts; Arial e a fonte sem serifa do sistema são alternativas. Os links de WhatsApp usam `wa.me`. Não são necessárias chaves de API para a configuração atual.

## Publicar

O projeto pode ser hospedado em um servidor de arquivos estáticos. Envie `index.html` e `assets/` juntos, mantendo os caminhos relativos.

**URL configurada para esta instalação:**

```text
https://www.andestecnologia.com.br/cartao-de-visita/joao-carlos-almeida/
```

Esse endereço está configurado no cartão; isso não confirma que a página já foi publicada. Para usá-lo, coloque os arquivos nessa pasta do servidor e ajuste:

1. `CONFIG.publicUrl` para a URL definitiva.
2. `og:url` para o mesmo endereço.
3. `og:image` para a URL HTTPS absoluta da imagem de compartilhamento.
4. Título, descrição, contatos e links para os dados que serão publicados.

A URL canônica, os metadados de compartilhamento e `CONFIG.publicUrl` usam esse endereço. A prévia dedicada está em `assets/compartilhamento-v2.jpg` (1200 × 630 pixels). Publique a imagem junto com a página. Mesmo no ambiente local, o compartilhamento usa `CONFIG.publicUrl`; o QR Code mantém o endereço gravado na imagem. Publique também o arquivo do QR personalizado.

Depois da publicação em HTTPS, confira os contatos, a importação do vCard, o compartilhamento e a leitura do QR Code por outro aparelho. Aplicativos podem manter a prévia de compartilhamento em cache.

## Contribuir

Sugestões e correções são bem-vindas pelo [rastreador de issues](https://github.com/Andes-Tecnologia/cartao-digital/issues) e por pull requests.

Para reportar um problema, descreva o comportamento esperado e o observado, os passos para reproduzir, o dispositivo e o navegador. Inclua capturas quando ajudarem, sem dados privados.

Para propor uma alteração, explique o problema resolvido e como verificou o resultado. Mantenha o escopo focado e confira o layout em telas estreitas, telas baixas e com texto ampliado. Evite incluir arquivos de editor ou dados pessoais adicionais.

Não há uma suíte automatizada de testes configurada. Uma revisão pode conferir os caminhos dos arquivos, links, geração do contato e comportamento responsivo. Para verificar problemas de espaçamento no diff:

```bash
git diff --check
```

## Licença e materiais visuais

A licença do código ainda não foi definida. Este repositório não contém um arquivo `LICENSE`; sua publicação não concede, por si só, uma licença de reutilização.

A logo, o retrato e os demais materiais visuais não são oferecidos como recursos de uso livre. Consulte os respectivos titulares antes de reutilizá-los. Ao personalizar o cartão, substitua esses arquivos por materiais autorizados.
