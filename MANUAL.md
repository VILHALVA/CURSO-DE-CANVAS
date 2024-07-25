# MANUAL
## PASSO 1: CONFIGURAÇÃO DO AMBIENTE:
1. **Editor de Código**:
   - **Escolha um Editor**: Você pode usar qualquer editor de código que prefira, como [Visual Studio Code](https://code.visualstudio.com/), [Sublime Text](https://www.sublimetext.com/), [Atom](https://atom.io/), ou qualquer outro editor que suporte HTML e JavaScript.

2. **Instalação do Navegador**:
   - **Escolha um Navegador**: Certifique-se de ter um navegador moderno instalado, como [Google Chrome](https://www.google.com/chrome/), [Mozilla Firefox](https://www.mozilla.org/firefox/), ou [Microsoft Edge](https://www.microsoft.com/edge). O `<canvas>` é suportado pela maioria dos navegadores modernos.

3. **Configuração do Ambiente de Desenvolvimento**:
   - **(Opcional) Ferramentas de Desenvolvimento**: Muitos editores de código vêm com ferramentas integradas de desenvolvimento e depuração. Se preferir, você pode instalar extensões adicionais para HTML, CSS e JavaScript que ajudam a facilitar o desenvolvimento.

## PASSO 2: CRIAR O PROJETO:
1. **Criação da Estrutura de Pastas**:
   - **Crie uma Nova Pasta**: Crie uma nova pasta para o seu projeto. Nomeie-a conforme preferir, por exemplo, `meu-primeiro-projeto-canvas`.

2. **Criar Arquivos**:
   - **Arquivo HTML**: Dentro da pasta do projeto, crie um arquivo chamado `index.html`.
   - **Arquivo JavaScript**: Crie um arquivo chamado `script.js`.

## PASSO 3: CONFIGURAR O ARQUIVO HTML:
Abra o arquivo `index.html` no seu editor de código e adicione o seguinte conteúdo:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Meu Primeiro Projeto Canvas</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }
        canvas {
            border: 1px solid #000;
        }
    </style>
</head>
<body>
    <canvas id="meuCanvas" width="600" height="400"></canvas>
    <script src="script.js"></script>
</body>
</html>
```

## PASSO 4: CONFIGURAR O ARQUIVO JAVASCRIPT:
Abra o arquivo `script.js` e adicione o seguinte código:

```javascript
// Obtém o elemento canvas e o contexto de desenho
const canvas = document.getElementById('meuCanvas');
const ctx = canvas.getContext('2d');

// Define a cor de preenchimento
ctx.fillStyle = 'lightblue';

// Desenha um retângulo preenchido
ctx.fillRect(50, 50, 200, 100);

// Define a cor da borda
ctx.strokeStyle = 'darkblue';

// Desenha a borda do retângulo
ctx.strokeRect(50, 50, 200, 100);

// Define a cor do texto
ctx.fillStyle = 'darkred';

// Desenha o texto no canvas
ctx.font = '30px Arial';
ctx.fillText('Olá Canvas!', 100, 200);
```

## PASSO 5: EXECUTAR O PROJETO:
1. **Abrir o HTML no Navegador**:
   - **Método Simples**: No seu editor de código, você pode clicar com o botão direito no arquivo `index.html` e selecionar "Abrir com" ou "Abrir no navegador" para visualizar seu projeto no navegador.
   - **Servidor Local (Opcional)**: Para desenvolvimento mais avançado, você pode usar um servidor local. Se estiver usando Visual Studio Code, você pode instalar a extensão "Live Server" para executar um servidor local com um clique.

2. **Verifique a Visualização**:
   - Quando você abrir o arquivo `index.html` no navegador, você deve ver um canvas com um retângulo azul claro e uma borda escura, além de um texto vermelho dizendo "Olá Canvas!".
