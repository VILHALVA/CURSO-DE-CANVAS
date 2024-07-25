# RECT CLEARRECT FILLRECT
Vamos explorar os métodos `rect()`, `clearRect()`, e `fillRect()` que são usados no contexto 2D do `<canvas>`. Esses métodos fazem parte da API de desenho 2D e são essenciais para criar e manipular formas retangulares no canvas.

## 1. `rect()`
### Descrição
O método `rect()` é usado para definir um retângulo em um contexto de desenho 2D, mas não o desenha imediatamente. Ele é frequentemente usado em conjunto com métodos como `stroke()` e `fill()` para aplicar um contorno ou preencher o retângulo.

### Sintaxe
```javascript
ctx.rect(x, y, largura, altura);
```

- **x**: A coordenada X do canto superior esquerdo do retângulo.
- **y**: A coordenada Y do canto superior esquerdo do retângulo.
- **largura**: A largura do retângulo.
- **altura**: A altura do retângulo.

### Exemplo
```javascript
const canvas = document.getElementById('meuCanvas');
const ctx = canvas.getContext('2d');

ctx.beginPath(); // Começa um novo caminho
ctx.rect(50, 50, 150, 100); // Define o retângulo
ctx.stroke(); // Aplica o contorno do retângulo
```

Neste exemplo, `rect()` define o retângulo, mas ele só será visível depois que `stroke()` é chamado para desenhar o contorno do retângulo.

## 2. `clearRect()`
### Descrição
O método `clearRect()` é usado para limpar uma área retangular do canvas, tornando-a transparente. Isso pode ser útil para apagar parte do canvas antes de redesenhar algo ou para criar efeitos de animação.

### Sintaxe
```javascript
ctx.clearRect(x, y, largura, altura);
```

- **x**: A coordenada X do canto superior esquerdo da área a ser limpa.
- **y**: A coordenada Y do canto superior esquerdo da área a ser limpa.
- **largura**: A largura da área a ser limpa.
- **altura**: A altura da área a ser limpa.

### Exemplo
```javascript
const canvas = document.getElementById('meuCanvas');
const ctx = canvas.getContext('2d');

ctx.fillStyle = 'blue';
ctx.fillRect(20, 20, 150, 100); // Desenha um retângulo azul

ctx.clearRect(50, 50, 100, 50); // Limpa a área do retângulo azul
```

Neste exemplo, o `clearRect()` limpa a parte do canvas onde o retângulo azul foi desenhado, criando um "buraco" na área retangular.

## 3. `fillRect()`
### Descrição
O método `fillRect()` é usado para desenhar um retângulo preenchido com a cor ou padrão especificado pela propriedade `fillStyle`.

### Sintaxe
```javascript
ctx.fillRect(x, y, largura, altura);
```

- **x**: A coordenada X do canto superior esquerdo do retângulo.
- **y**: A coordenada Y do canto superior esquerdo do retângulo.
- **largura**: A largura do retângulo.
- **altura**: A altura do retângulo.

### Exemplo
```javascript
const canvas = document.getElementById('meuCanvas');
const ctx = canvas.getContext('2d');

ctx.fillStyle = 'green'; // Define a cor de preenchimento
ctx.fillRect(30, 30, 200, 100); // Desenha um retângulo verde preenchido
```

Neste exemplo, `fillRect()` desenha um retângulo verde preenchido, usando a cor definida por `fillStyle`.

## Resumo
- **`rect()`**: Define um retângulo no contexto de desenho, mas não o desenha imediatamente. Usado com `stroke()` ou `fill()` para aplicar o contorno ou preenchimento.
- **`clearRect()`**: Limpa uma área retangular do canvas, tornando-a transparente.
- **`fillRect()`**: Desenha um retângulo preenchido com a cor ou padrão especificado por `fillStyle`.

Esses métodos são fundamentais para manipular e desenhar retângulos no `<canvas>`, e são frequentemente utilizados em conjunto para criar gráficos e interfaces interativas. 