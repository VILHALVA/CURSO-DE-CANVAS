# FUNCAO ARC
A função `arc()` do contexto 2D do `<canvas>` é usada para desenhar arcos e círculos. É uma das funções mais versáteis para criar formas circulares e curvas no canvas.

## Sintaxe do Método `arc()`
```javascript
ctx.arc(x, y, raio, inicio, fim, sentidoAntiHorario);
```

- **x**: A coordenada X do centro do arco ou círculo.
- **y**: A coordenada Y do centro do arco ou círculo.
- **raio**: O raio do arco ou círculo.
- **inicio**: O ângulo inicial do arco, em radianos. 0 radianos é o ponto mais à direita do círculo.
- **fim**: O ângulo final do arco, em radianos. Define o ponto final do arco.
- **sentidoAntiHorario**: Um valor booleano que indica se o arco deve ser desenhado no sentido anti-horário (true) ou no sentido horário (false). O padrão é false.

## Exemplos Práticos
Vamos ver alguns exemplos de como usar o `arc()` para desenhar diferentes tipos de formas no canvas.

### 1. **Desenhar um Círculo Completo**
Para desenhar um círculo completo, você deve definir o ângulo inicial como 0 e o ângulo final como `2 * Math.PI`, que representa uma volta completa.

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Desenhando Círculo com arc()</title>
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
    <canvas id="meuCanvas" width="400" height="400"></canvas>
    <script>
        const canvas = document.getElementById('meuCanvas');
        const ctx = canvas.getContext('2d');

        // Desenha um círculo completo
        ctx.beginPath();
        ctx.arc(200, 200, 100, 0, 2 * Math.PI); // Centro (200, 200), raio 100
        ctx.strokeStyle = 'blue'; // Cor do contorno
        ctx.lineWidth = 5; // Largura do contorno
        ctx.stroke(); // Desenha o contorno
    </script>
</body>
</html>
```

### 2. **Desenhar um Arco**
Para desenhar um arco, defina o ângulo inicial e o ângulo final para criar um segmento de círculo.

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Desenhando Arco com arc()</title>
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
    <canvas id="meuCanvas" width="400" height="400"></canvas>
    <script>
        const canvas = document.getElementById('meuCanvas');
        const ctx = canvas.getContext('2d');

        // Desenha um arco
        ctx.beginPath();
        ctx.arc(200, 200, 100, Math.PI / 4, 3 * Math.PI / 4); // Arco de 45° a 135°
        ctx.strokeStyle = 'red'; // Cor do contorno
        ctx.lineWidth = 5; // Largura do contorno
        ctx.stroke(); // Desenha o contorno
    </script>
</body>
</html>
```

### 3. **Desenhar um Arco com Preenchimento**
Para preencher um arco com uma cor, use `fill()` após `arc()` e `beginPath()`.

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Desenhando Arco com Preenchimento</title>
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
    <canvas id="meuCanvas" width="400" height="400"></canvas>
    <script>
        const canvas = document.getElementById('meuCanvas');
        const ctx = canvas.getContext('2d');

        // Desenha um arco preenchido
        ctx.beginPath();
        ctx.arc(200, 200, 100, Math.PI / 4, 3 * Math.PI / 4); // Arco de 45° a 135°
        ctx.lineTo(200, 200); // Conecta o final do arco ao centro
        ctx.closePath(); // Fecha o caminho para completar o arco
        ctx.fillStyle = 'green'; // Cor do preenchimento
        ctx.fill(); // Preenche o arco com a cor
        ctx.strokeStyle = 'black'; // Cor do contorno
        ctx.lineWidth = 2; // Largura do contorno
        ctx.stroke(); // Desenha o contorno
    </script>
</body>
</html>
```

## Notas Adicionais
- **Unidades de Ângulo**: O ângulo é especificado em radianos, onde `2 * Math.PI` representa uma volta completa (360 graus) e `Math.PI` representa 180 graus. Use `Math.PI / 2` para 90 graus e assim por diante.
- **Sentido Anti-Horário**: Por padrão, os arcos são desenhados no sentido anti-horário. Para desenhar no sentido horário, defina o último parâmetro como `true`.

