# INSERINDO IMAGENS
Inserir imagens no `<canvas>` permite criar gráficos e composições visuais mais complexas. O método principal para desenhar imagens no `<canvas>` é o `drawImage()`. Este método é bastante flexível e pode ser usado para diversas finalidades, como exibir imagens, criar efeitos de máscara, e manipular imagens em tempo real.

## Métodos do `drawImage()`
O método `drawImage()` pode ser usado de várias maneiras, dependendo do que você deseja fazer. Aqui estão as formas mais comuns de usá-lo:

1. **Desenhar a Imagem Completa**:
   ```javascript
   ctx.drawImage(imagem, x, y);
   ```
   - **imagem**: O objeto da imagem.
   - **x**: A coordenada X no canvas onde a imagem será desenhada.
   - **y**: A coordenada Y no canvas onde a imagem será desenhada.

2. **Desenhar uma Parte da Imagem**:
   ```javascript
   ctx.drawImage(imagem, sx, sy, sWidth, sHeight, dx, dy, dWidth, dHeight);
   ```
   - **sx, sy**: Coordenadas no canto superior esquerdo da parte da imagem a ser desenhada.
   - **sWidth, sHeight**: Largura e altura da parte da imagem a ser desenhada.
   - **dx, dy**: Coordenadas no canvas onde a parte da imagem será desenhada.
   - **dWidth, dHeight**: Largura e altura da parte da imagem desenhada no canvas.

## Exemplo Básico de Inserção de Imagem
Vamos criar um exemplo onde uma imagem é carregada e desenhada em um canvas.

### Código HTML e JavaScript
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inserindo Imagens no Canvas</title>
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
    <script>
        const canvas = document.getElementById('meuCanvas');
        const ctx = canvas.getContext('2d');

        // Cria um novo objeto de imagem
        const img = new Image();
        img.src = 'https://via.placeholder.com/150'; // URL da imagem

        // Desenha a imagem quando ela é carregada
        img.onload = function() {
            ctx.drawImage(img, 50, 50); // Desenha a imagem no canvas
        };
    </script>
</body>
</html>
```

## Explicação do Código
1. **Criar um Objeto de Imagem**:
   ```javascript
   const img = new Image();
   img.src = 'https://via.placeholder.com/150';
   ```
   Cria um novo objeto de imagem e define sua fonte (URL).

2. **Desenhar a Imagem Quando Carregada**:
   ```javascript
   img.onload = function() {
       ctx.drawImage(img, 50, 50);
   };
   ```
   Define uma função que será chamada quando a imagem for carregada. Dentro dessa função, desenha a imagem no canvas usando `drawImage()`.

## Exemplo de Desenhar uma Parte da Imagem
Vamos criar um exemplo onde apenas uma parte da imagem é desenhada no canvas.

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Desenhando Parte da Imagem</title>
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
    <script>
        const canvas = document.getElementById('meuCanvas');
        const ctx = canvas.getContext('2d');

        const img = new Image();
        img.src = 'https://via.placeholder.com/300'; // URL da imagem

        img.onload = function() {
            // Desenha uma parte da imagem (50x50 pixels da imagem original)
            ctx.drawImage(img, 50, 50, 100, 100, 200, 100, 150, 150);
            // sx, sy, sWidth, sHeight: Parte da imagem original a ser desenhada
            // dx, dy, dWidth, dHeight: Tamanho e posição no canvas
        };
    </script>
</body>
</html>
```

## Explicação do Código
1. **Desenhar Parte da Imagem**:
   ```javascript
   ctx.drawImage(img, 50, 50, 100, 100, 200, 100, 150, 150);
   ```
   Desenha um retângulo de 100x100 pixels da imagem original, começando nas coordenadas (50, 50) da imagem, e redimensiona esse retângulo para 150x150 pixels no canvas, começando nas coordenadas (200, 100).

## Notas Adicionais
- **Carregamento de Imagem**: Sempre certifique-se de que a imagem está completamente carregada antes de desenhá-la no canvas. Use o evento `onload` para garantir que a imagem está disponível.
- **Manipulação de Imagem**: Depois de desenhar a imagem, você pode aplicar outras operações, como desenhar formas sobre ela ou criar efeitos visuais.
- **Manipulação de Dados da Imagem**: Para modificar os pixels da imagem diretamente, você pode usar o método `getImageData()` e `putImageData()`.

