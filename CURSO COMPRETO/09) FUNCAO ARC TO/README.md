# FUNCAO ARC TO
A função `arcTo()` no contexto 2D do `<canvas>` é usada para desenhar um arco entre dois pontos, criando uma transição suave através de uma curva. Ela é especialmente útil para criar curvas que se conectam suavemente a outros segmentos de linha.

## Sintaxe do Método `arcTo()`
```javascript
ctx.arcTo(x1, y1, x2, y2, raio);
```

- **x1, y1**: Coordenadas do ponto de controle anterior (ou seja, o ponto até onde a linha anterior foi desenhada).
- **x2, y2**: Coordenadas do ponto de controle próximo (ou seja, o ponto onde a curva deve terminar).
- **raio**: O raio da curva. Define o quão suave ou apertada a curva será.

## Como Funciona
A função `arcTo()` desenha uma linha do ponto atual para (x1, y1) e então desenha um arco com o raio especificado, de (x1, y1) a (x2, y2). O arco é desenhado de maneira que a transição entre os segmentos de linha seja suave.

## Exemplo Prático
Vamos ver um exemplo de como usar `arcTo()` para desenhar uma curva suave no canvas.

### Código HTML e JavaScript
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Desenhando Curvas com arcTo()</title>
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

        ctx.beginPath();
        ctx.moveTo(50, 50); // Move para o ponto inicial

        // Desenha uma linha para (150, 50)
        ctx.lineTo(150, 50);

        // Desenha uma curva de (150, 50) até (250, 150) com raio 50
        ctx.arcTo(200, 0, 250, 150, 50);

        // Desenha uma linha de (250, 150) para (350, 50)
        ctx.lineTo(350, 50);

        ctx.strokeStyle = 'blue'; // Cor do contorno
        ctx.lineWidth = 5; // Largura do contorno
        ctx.stroke(); // Aplica o contorno
    </script>
</body>
</html>
```

### Explicação do Código
1. **Iniciar o Caminho**:
   ```javascript
   ctx.beginPath();
   ctx.moveTo(50, 50);
   ```
   Inicia um novo caminho e move o "cursor" de desenho para o ponto inicial (50, 50).

2. **Desenhar uma Linha**:
   ```javascript
   ctx.lineTo(150, 50);
   ```
   Desenha uma linha até o ponto (150, 50).

3. **Desenhar a Curva**:
   ```javascript
   ctx.arcTo(200, 0, 250, 150, 50);
   ```
   Desenha um arco com raio 50 que conecta o ponto (150, 50) ao ponto (250, 150), passando por (200, 0) como ponto de controle.

4. **Desenhar Outra Linha**:
   ```javascript
   ctx.lineTo(350, 50);
   ```
   Desenha uma linha até (350, 50), completando o desenho.

5. **Aplicar Estilo e Desenho**:
   ```javascript
   ctx.strokeStyle = 'blue';
   ctx.lineWidth = 5;
   ctx.stroke();
   ```
   Define a cor e a largura do contorno e aplica o estilo ao caminho.

## Notas Adicionais
- **Raio da Curva**: O raio influencia a suavidade da curva. Um raio maior resulta em uma curva mais suave, enquanto um raio menor resulta em uma curva mais apertada.
- **Ponto de Controle**: O ponto (x1, y1) é utilizado para criar uma transição suave entre a linha anterior e o arco. Certifique-se de que esse ponto está em uma posição que cria a curva desejada.

