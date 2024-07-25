# DESENHANDO LINHAS
Desenhar linhas no `<canvas>` é uma tarefa comum e essencial para criar gráficos e desenhos dinâmicos. O contexto 2D do `<canvas>` fornece métodos específicos para desenhar linhas e formas relacionadas. Vamos explorar como fazer isso com detalhes.

## Métodos para Desenhar Linhas
### 1. `beginPath()`
Antes de começar a desenhar uma linha (ou qualquer outra forma), você deve iniciar um novo caminho usando o método `beginPath()`. Isso é necessário para garantir que a linha ou forma que você vai desenhar não seja afetada por caminhos anteriores.

### 2. `moveTo()`
Este método move o "cursor" de desenho para um ponto específico, sem desenhar uma linha. É útil para definir o ponto inicial de uma linha.

### 3. `lineTo()`
Após definir o ponto inicial com `moveTo()`, o método `lineTo()` é usado para desenhar uma linha até um ponto específico. 

### 4. `stroke()`
Após definir o caminho e as linhas desejadas com `lineTo()`, o método `stroke()` é usado para desenhar a linha com a cor e estilo especificados.

## Exemplo Prático
Aqui está um exemplo de como usar esses métodos para desenhar linhas no `<canvas>`:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Desenhando Linhas no Canvas</title>
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

        // Começa um novo caminho
        ctx.beginPath();

        // Define o ponto inicial da linha
        ctx.moveTo(50, 50);

        // Desenha a linha até o ponto final
        ctx.lineTo(200, 50);

        // Desenha a linha com a cor e estilo definidos
        ctx.strokeStyle = 'blue'; // Cor da linha
        ctx.lineWidth = 5; // Largura da linha
        ctx.stroke(); // Aplica o desenho da linha

        // Desenha outra linha
        ctx.beginPath();
        ctx.moveTo(50, 100);
        ctx.lineTo(200, 200);
        ctx.strokeStyle = 'red'; // Cor da linha
        ctx.lineWidth = 3; // Largura da linha
        ctx.stroke(); // Aplica o desenho da linha

        // Desenha uma linha contínua com segmentos
        ctx.beginPath();
        ctx.moveTo(50, 250);
        ctx.lineTo(200, 250);
        ctx.lineTo(200, 300);
        ctx.lineTo(50, 300);
        ctx.closePath(); // Fecha o caminho (opcional)
        ctx.strokeStyle = 'green'; // Cor da linha
        ctx.lineWidth = 2; // Largura da linha
        ctx.stroke(); // Aplica o desenho da linha
    </script>
</body>
</html>
```

## Explicação do Código
1. **Iniciar o Caminho**:
   ```javascript
   ctx.beginPath();
   ```
   Inicia um novo caminho para garantir que o desenho de linhas subsequentes não seja misturado com o que foi desenhado anteriormente.

2. **Definir o Ponto Inicial**:
   ```javascript
   ctx.moveTo(50, 50);
   ```
   Move o cursor de desenho para a posição (50, 50), que será o início da linha.

3. **Desenhar a Linha**:
   ```javascript
   ctx.lineTo(200, 50);
   ```
   Desenha uma linha da posição atual até a posição (200, 50).

4. **Aplicar o Estilo da Linha**:
   ```javascript
   ctx.strokeStyle = 'blue';
   ctx.lineWidth = 5;
   ctx.stroke();
   ```
   Define a cor e a largura da linha e desenha a linha no canvas.

5. **Desenho de Múltiplas Linhas**:
   Repetimos os passos para desenhar linhas adicionais com diferentes cores e larguras.

6. **Desenho de Linhas Contínuas**:
   Utilizamos `lineTo()` para criar múltiplos segmentos de linha e `closePath()` para fechar o caminho, se necessário.

## Dicas Adicionais
- **Linhas Contínuas e Polígonos**: Use `lineTo()` repetidamente para desenhar linhas contínuas ou polígonos. Use `closePath()` para conectar o último ponto ao primeiro, criando uma forma fechada.
  
- **Transformações e Estilo**: Você pode aplicar transformações (como escalas e rotações) e estilos adicionais (como padrões e gradientes) para criar efeitos visuais mais complexos.

Esses métodos fornecem uma base sólida para desenhar linhas e formas básicas no `<canvas>`. 