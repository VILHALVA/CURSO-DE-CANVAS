# SPRITE SHEET
Um **sprite sheet** é uma única imagem que contém várias imagens menores (sprites) organizadas em uma grade. Essa técnica é amplamente utilizada em desenvolvimento de jogos e animações para otimizar a renderização e gerenciar melhor os recursos gráficos. Com um sprite sheet, você pode carregar uma única imagem e, em seguida, exibir apenas as partes necessárias dela.

## Como Funciona um Sprite Sheet
1. **Organização**: Um sprite sheet organiza várias imagens (ou frames) em uma única imagem grande. Cada sprite é uma parte dessa imagem, e a posição e o tamanho de cada sprite são conhecidos.
2. **Desenho**: Para desenhar um sprite do sprite sheet, você usa o método `drawImage()` do `<canvas>`, especificando a parte da imagem a ser desenhada.

## Exemplo de Uso de Sprite Sheet
Vamos criar um exemplo simples para ilustrar como usar um sprite sheet para animar um personagem.

### 1. **Preparar o Sprite Sheet**
Suponha que você tenha um sprite sheet com 4 frames de animação dispostos horizontalmente. Cada frame tem 64x64 pixels e o sprite sheet completo tem 256x64 pixels.

### 2. **Código HTML e JavaScript**
Vamos usar o sprite sheet para animar um personagem que caminha para a direita. O código abaixo carrega o sprite sheet e anima o personagem alterando o frame exibido.

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sprite Sheet no Canvas</title>
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
    <canvas id="meuCanvas" width="800" height="400"></canvas>
    <script>
        const canvas = document.getElementById('meuCanvas');
        const ctx = canvas.getContext('2d');

        const img = new Image();
        img.src = 'https://via.placeholder.com/256x64'; // URL do sprite sheet

        const frameWidth = 64;  // Largura de cada frame
        const frameHeight = 64; // Altura de cada frame
        const totalFrames = 4;  // Número total de frames
        let currentFrame = 0;   // Frame atual para animação

        function atualizar() {
            ctx.clearRect(0, 0, canvas.width, canvas.height); // Limpa o canvas

            // Desenha o frame atual do sprite sheet
            ctx.drawImage(
                img,
                currentFrame * frameWidth, 0, frameWidth, frameHeight, // Parte da imagem a ser desenhada
                100, 100, frameWidth, frameHeight // Posição e tamanho no canvas
            );

            // Atualiza o frame para a próxima animação
            currentFrame = (currentFrame + 1) % totalFrames;

            // Solicita o próximo frame de animação
            requestAnimationFrame(atualizar);
        }

        img.onload = function() {
            atualizar(); // Inicia a animação quando a imagem é carregada
        };
    </script>
</body>
</html>
```

### Explicação do Código
1. **Definir as Dimensões e Propriedades**:
   ```javascript
   const frameWidth = 64;
   const frameHeight = 64;
   const totalFrames = 4;
   let currentFrame = 0;
   ```
   Define as dimensões de cada frame no sprite sheet e o número total de frames.

2. **Desenhar o Frame Atual**:
   ```javascript
   ctx.drawImage(
       img,
       currentFrame * frameWidth, 0, frameWidth, frameHeight,
       100, 100, frameWidth, frameHeight
   );
   ```
   Desenha o frame atual no canvas. O `currentFrame * frameWidth` calcula a posição horizontal do frame atual no sprite sheet.

3. **Atualizar o Frame**:
   ```javascript
   currentFrame = (currentFrame + 1) % totalFrames;
   ```
   Atualiza o frame atual para a próxima animação. Usa o operador `%` para voltar ao primeiro frame após o último.

4. **Iniciar a Animação**:
   ```javascript
   img.onload = function() {
       atualizar();
   };
   ```
   Inicia a animação quando a imagem do sprite sheet é carregada.

## Notas Adicionais
- **Frames Verticalmente Alinhados**: Se os frames estão dispostos verticalmente em vez de horizontalmente, ajuste o código para refletir a posição vertical no sprite sheet.
- **Animação com Sprite Sheet**: Para animações mais complexas, você pode ter vários sprite sheets para diferentes animações (correr, pular, etc.) e alternar entre eles conforme necessário.
- **Performance**: Ao lidar com animações, considere o desempenho e otimize a renderização, especialmente em dispositivos móveis.

