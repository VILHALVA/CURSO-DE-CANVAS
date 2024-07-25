# MOVENDO IMAGENS COM O TECLADO
Para mover uma imagem usando o teclado em um `<canvas>`, você pode capturar eventos de teclado e atualizar a posição da imagem com base nas teclas pressionadas. Em seguida, você redesenha a imagem no canvas na nova posição.

Aqui está um exemplo básico de como fazer isso:

## Código HTML e JavaScript
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Movendo Imagem com o Teclado</title>
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
    <canvas id="meuCanvas" width="800" height="600"></canvas>
    <script>
        const canvas = document.getElementById('meuCanvas');
        const ctx = canvas.getContext('2d');

        // Cria um novo objeto de imagem
        const img = new Image();
        img.src = 'https://via.placeholder.com/150'; // URL da imagem
        let x = canvas.width / 2 - 75; // Posição inicial X
        let y = canvas.height / 2 - 75; // Posição inicial Y
        const velocidade = 5; // Velocidade de movimento

        // Função para desenhar a imagem
        function desenharImagem() {
            ctx.clearRect(0, 0, canvas.width, canvas.height); // Limpa o canvas
            ctx.drawImage(img, x, y); // Desenha a imagem na nova posição
        }

        // Função para atualizar a posição com base na tecla pressionada
        function atualizarPosicao(tecla) {
            switch(tecla) {
                case 'ArrowUp':
                    y -= velocidade; // Move para cima
                    break;
                case 'ArrowDown':
                    y += velocidade; // Move para baixo
                    break;
                case 'ArrowLeft':
                    x -= velocidade; // Move para a esquerda
                    break;
                case 'ArrowRight':
                    x += velocidade; // Move para a direita
                    break;
            }
            desenharImagem(); // Redesenha a imagem na nova posição
        }

        // Captura eventos de teclado
        window.addEventListener('keydown', function(event) {
            atualizarPosicao(event.key); // Atualiza a posição com base na tecla pressionada
        });

        // Desenha a imagem quando a imagem é carregada
        img.onload = function() {
            desenharImagem(); // Desenha a imagem na posição inicial
        };
    </script>
</body>
</html>
```

## Explicação do Código
1. **Definir a Imagem e Posições**:
   ```javascript
   const img = new Image();
   img.src = 'https://via.placeholder.com/150';
   let x = canvas.width / 2 - 75; // Posição inicial X
   let y = canvas.height / 2 - 75; // Posição inicial Y
   const velocidade = 5; // Velocidade de movimento
   ```
   Define a imagem e suas posições iniciais. A `velocidade` determina a rapidez com que a imagem se move.

2. **Desenhar a Imagem**:
   ```javascript
   function desenharImagem() {
       ctx.clearRect(0, 0, canvas.width, canvas.height); // Limpa o canvas
       ctx.drawImage(img, x, y); // Desenha a imagem na nova posição
   }
   ```
   Limpa o canvas e desenha a imagem na nova posição.

3. **Atualizar a Posição com Base na Tecla**:
   ```javascript
   function atualizarPosicao(tecla) {
       switch(tecla) {
           case 'ArrowUp':
               y -= velocidade; // Move para cima
               break;
           case 'ArrowDown':
               y += velocidade; // Move para baixo
               break;
           case 'ArrowLeft':
               x -= velocidade; // Move para a esquerda
               break;
           case 'ArrowRight':
               x += velocidade; // Move para a direita
               break;
       }
       desenharImagem(); // Redesenha a imagem na nova posição
   }
   ```
   Atualiza a posição da imagem com base na tecla pressionada e redesenha a imagem.

4. **Capturar Eventos de Teclado**:
   ```javascript
   window.addEventListener('keydown', function(event) {
       atualizarPosicao(event.key); // Atualiza a posição com base na tecla pressionada
   });
   ```
   Adiciona um ouvinte de eventos para capturar as teclas pressionadas e atualizar a posição da imagem.

5. **Desenhar a Imagem Quando Carregada**:
   ```javascript
   img.onload = function() {
       desenharImagem(); // Desenha a imagem na posição inicial
   };
   ```
   Desenha a imagem no canvas quando ela é carregada.

## Notas Adicionais
- **Limites de Movimento**: Se você deseja impedir que a imagem saia dos limites do canvas, adicione verificações para garantir que as coordenadas da imagem permaneçam dentro dos limites.
- **Velocidade de Movimento**: A velocidade pode ser ajustada para aumentar ou diminuir a rapidez com que a imagem se move.
- **Outras Teclas**: Você pode adicionar suporte para outras teclas ou combinações de teclas, se necessário.

