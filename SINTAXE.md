# SINTAXE
1. **Criação do Elemento**: Você cria um `<canvas>` no seu HTML como qualquer outro elemento. A aparência padrão é um retângulo vazio.

   ```html
   <canvas id="meuCanvas" width="500" height="400"></canvas>
   ```

2. **Contexto de Desenho**: Para desenhar no `<canvas>`, você precisa obter um "contexto de desenho". O contexto é uma interface de programação que fornece métodos e propriedades para desenhar formas, imagens e texto. Para 2D, você usa `getContext('2d')`.

   ```javascript
   const canvas = document.getElementById('meuCanvas');
   const ctx = canvas.getContext('2d');
   ```

3. **Desenhando no Canvas**: Depois de obter o contexto, você pode usar suas APIs para desenhar. Por exemplo, para desenhar um retângulo:

   ```javascript
   ctx.fillStyle = 'blue'; // Cor de preenchimento
   ctx.fillRect(50, 50, 200, 100); // Desenha um retângulo (x, y, largura, altura)
   ```

4. **Animações e Interatividade**: O `<canvas>` é frequentemente usado para criar animações e jogos. Você pode atualizar o conteúdo do canvas em um loop, redibujando-o a cada quadro para criar animações. Para capturar interações do usuário, como cliques e movimentos do mouse, você pode adicionar ouvintes de eventos.

   ```javascript
   function atualizar() {
       // Código para atualizar a animação
       requestAnimationFrame(atualizar);
   }
   atualizar();
   ```

5. **Gráficos Avançados**: Além de formas básicas, o `<canvas>` permite desenhar imagens, gradientes e padrões, e também pode ser usado para gráficos 3D com WebGL.

