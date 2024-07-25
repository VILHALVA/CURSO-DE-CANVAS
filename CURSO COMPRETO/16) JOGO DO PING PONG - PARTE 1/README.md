# JOGO DO PING PONG
Criar um jogo simples de ping pong (ou "ping-pong") no `<canvas>` é uma excelente maneira de aplicar conceitos de programação gráfica e lógica de jogo. O jogo de ping pong envolve duas raquetes e uma bola que se movem pelo canvas, e o objetivo é impedir que a bola passe por sua raquete.

Aqui está um exemplo básico de como você pode criar um jogo de ping pong usando JavaScript e `<canvas>`:

## Código HTML e JavaScript
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jogo de Ping Pong</title>
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
            background-color: #000;
        }
    </style>
</head>
<body>
    <canvas id="meuCanvas" width="800" height="400"></canvas>
    <script>
        const canvas = document.getElementById('meuCanvas');
        const ctx = canvas.getContext('2d');

        const raqueteLargura = 10;
        const raqueteAltura = 100;
        const bolaTamanho = 10;

        // Posiciona e define dimensões das raquetes e da bola
        let raqueteEsquerda = { x: 10, y: canvas.height / 2 - raqueteAltura / 2, largura: raqueteLargura, altura: raqueteAltura };
        let raqueteDireita = { x: canvas.width - raqueteLargura - 10, y: canvas.height / 2 - raqueteAltura / 2, largura: raqueteLargura, altura: raqueteAltura };
        let bola = { x: canvas.width / 2, y: canvas.height / 2, raio: bolaTamanho / 2, dx: 5, dy: 3 };

        function desenharRaquete(raquete) {
            ctx.fillStyle = 'white';
            ctx.fillRect(raquete.x, raquete.y, raquete.largura, raquete.altura);
        }

        function desenharBola() {
            ctx.beginPath();
            ctx.arc(bola.x, bola.y, bola.raio, 0, Math.PI * 2);
            ctx.fillStyle = 'white';
            ctx.fill();
            ctx.closePath();
        }

        function moverRaquetes() {
            document.addEventListener('keydown', (event) => {
                switch (event.key) {
                    case 'ArrowUp':
                        if (raqueteDireita.y > 0) raqueteDireita.y -= 10;
                        break;
                    case 'ArrowDown':
                        if (raqueteDireita.y < canvas.height - raqueteAltura) raqueteDireita.y += 10;
                        break;
                    case 'w':
                        if (raqueteEsquerda.y > 0) raqueteEsquerda.y -= 10;
                        break;
                    case 's':
                        if (raqueteEsquerda.y < canvas.height - raqueteAltura) raqueteEsquerda.y += 10;
                        break;
                }
            });
        }

        function atualizarBola() {
            bola.x += bola.dx;
            bola.y += bola.dy;

            // Colisão com o topo e o fundo do canvas
            if (bola.y + bola.raio > canvas.height || bola.y - bola.raio < 0) {
                bola.dy = -bola.dy;
            }

            // Colisão com as raquetes
            if (bola.x - bola.raio < raqueteEsquerda.x + raqueteLargura && bola.y > raqueteEsquerda.y && bola.y < raqueteEsquerda.y + raqueteAltura) {
                bola.dx = -bola.dx;
            }

            if (bola.x + bola.raio > raqueteDireita.x && bola.y > raqueteDireita.y && bola.y < raqueteDireita.y + raqueteAltura) {
                bola.dx = -bola.dx;
            }

            // Checar se a bola saiu do canvas (ponto)
            if (bola.x + bola.raio > canvas.width || bola.x - bola.raio < 0) {
                // Resetar a bola para o centro
                bola.x = canvas.width / 2;
                bola.y = canvas.height / 2;
                bola.dx = -bola.dx; // Inverter a direção da bola
            }
        }

        function atualizar() {
            ctx.clearRect(0, 0, canvas.width, canvas.height); // Limpa o canvas

            desenharRaquete(raqueteEsquerda);
            desenharRaquete(raqueteDireita);
            desenharBola();
            atualizarBola();

            requestAnimationFrame(atualizar); // Solicita o próximo frame
        }

        moverRaquetes();
        atualizar(); // Inicia a atualização do jogo
    </script>
</body>
</html>
```

## Explicação do Código
1. **Definir Propriedades do Jogo**:
   - As raquetes, bola e suas propriedades, como tamanho e posição inicial.
   ```javascript
   const raqueteLargura = 10;
   const raqueteAltura = 100;
   const bolaTamanho = 10;

   let raqueteEsquerda = { x: 10, y: canvas.height / 2 - raqueteAltura / 2, largura: raqueteLargura, altura: raqueteAltura };
   let raqueteDireita = { x: canvas.width - raqueteLargura - 10, y: canvas.height / 2 - raqueteAltura / 2, largura: raqueteLargura, altura: raqueteAltura };
   let bola = { x: canvas.width / 2, y: canvas.height / 2, raio: bolaTamanho / 2, dx: 5, dy: 3 };
   ```

2. **Desenhar Raquetes e Bola**:
   - Funções para desenhar as raquetes e a bola no canvas.
   ```javascript
   function desenharRaquete(raquete) {
       ctx.fillStyle = 'white';
       ctx.fillRect(raquete.x, raquete.y, raquete.largura, raquete.altura);
   }

   function desenharBola() {
       ctx.beginPath();
       ctx.arc(bola.x, bola.y, bola.raio, 0, Math.PI * 2);
       ctx.fillStyle = 'white';
       ctx.fill();
       ctx.closePath();
   }
   ```

3. **Mover Raquetes**:
   - Captura eventos de teclado para mover as raquetes.
   ```javascript
   function moverRaquetes() {
       document.addEventListener('keydown', (event) => {
           switch (event.key) {
               case 'ArrowUp':
                   if (raqueteDireita.y > 0) raqueteDireita.y -= 10;
                   break;
               case 'ArrowDown':
                   if (raqueteDireita.y < canvas.height - raqueteAltura) raqueteDireita.y += 10;
                   break;
               case 'w':
                   if (raqueteEsquerda.y > 0) raqueteEsquerda.y -= 10;
                   break;
               case 's':
                   if (raqueteEsquerda.y < canvas.height - raqueteAltura) raqueteEsquerda.y += 10;
                   break;
           }
       });
   }
   ```

4. **Atualizar a Bola**:
   - Calcula o movimento da bola e verifica colisões com as raquetes e as bordas do canvas.
   ```javascript
   function atualizarBola() {
       bola.x += bola.dx;
       bola.y += bola.dy;

       // Colisão com o topo e o fundo do canvas
       if (bola.y + bola.raio > canvas.height || bola.y - bola.raio < 0) {
           bola.dy = -bola.dy;
       }

       // Colisão com as raquetes
       if (bola.x - bola.raio < raqueteEsquerda.x + raqueteLargura && bola.y > raqueteEsquerda.y && bola.y < raqueteEsquerda.y + raqueteAltura) {
           bola.dx = -bola.dx;
       }

       if (bola.x + bola.raio > raqueteDireita.x && bola.y > raqueteDireita.y && bola.y < raqueteDireita.y + raqueteAltura) {
           bola.dx = -bola.dx;
       }

       // Checar se a bola saiu do canvas (ponto)
       if (bola.x + bola.raio > canvas.width || bola.x - bola.raio < 0) {
           // Resetar a bola para o centro
           bola.x = canvas.width / 2;
           bola.y = canvas.height / 2;
           bola.dx = -bola.dx; // Inverter a direção da bola
       }
   }
   ```

5. **Atualizar o Jogo**:
   - Função principal para limpar o canvas, desenhar os elementos e atualizar o jogo a cada frame.

   ```javascript
   function atualizar() {
       ctx.clearRect(0, 0, canvas.width, canvas.height); // Limpa o canvas

       desenharRaquete(raqueteEsquerda);
       desenharRaquete(

    raqueteDireita);
       desenharBola();
       atualizarBola();

       requestAnimationFrame(atualizar); // Solicita o próximo frame
   }
    ```

## Notas Adicionais
- **Pontuação**: Você pode adicionar um sistema de pontuação para contar quantas vezes a bola passou por uma raquete.
- **Ajustes de Dificuldade**: Ajuste a velocidade da bola ou adicione um nível de dificuldade para tornar o jogo mais interessante.
- **Estilo e Animações**: Personalize o visual e adicione efeitos visuais para melhorar a experiência do jogo.
