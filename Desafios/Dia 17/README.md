# Dia 17 - Loader Animado #2

![Loader Animado #2](./loading.gif?raw=true "Loader Animado #2")

-   [Codepen](https://codepen.io/lizvidotti91/pen/OJNdPPr);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS 3D Transforms](https://www.w3schools.com/css/css3_3dtransforms.asp);
-   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp);

## Passo a passo

A base do nosso arquivo HTML será uma `<div></div>`, que será nosso quadrado animado, e um `<h2></h2>`, com o texto que fica mudando de cor.

```html
<div class="loader"></div>
<h2>carregando...</h2>
```

Em nosso arquivo CSS, vamos começar usando algumas propriedades comuns a todo o documento, por isso usaremos o `*{}`.

```css
* {
    box-sizing: border-box;
    font-family: monospace;
    margin: 0;
    padding: 0;
}
```

O tamanho das caixas será medido a partir de suas bordas, ou seja, mesmo que eu aplique um `padding:`, por exemplo, o meu conteúdo ainda estará ocupando a medida que eu defini para a altura e largura dessa caixa. Por padrão do CSS, o tamanho das caixas é medido a partir do conteúdo; então, mesmo que eu defina altura e largura, elas serão alteradas dependendo do tamanho do `padding:` que eu aplicar.

Agora, vamos centralizar nosso conteúdo na tela:

```css
body {
    align-items: center;
    background-color: #61707d;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

Para centralizar o conteúdo nos sentidos horizontal e vertical, usamos as três propriedades juntas: `align-items: center; display: flex; justify-content: center;`. Para que o conteúdo fique centralizado no sentido vertical, vamos completar aplicando uma altura `height: 100vh;`. A unidade de medida vh (Viewport Height) equivale ao tamanho da tela; assim, nosso `body` terá a altura igual a altura da tela. Essa medida faz com que o conteúdo se ajuste aos diversos tamanhos de tela. Agora, nosso conteúdo estará `in-line` (na mesma linha), e vamos deixá-lo novamente em colunas, usando o `flex-direction: column;`. Por fim, apliquei uma cor de fundo `background-color: #61707d;`.

Agora, vamos estilizar nossa `<div></div>`:

```css
div.loader {
    animation: 3s loading linear infinite;
    background-color: #e85d75;
    border-radius: 5vh;
    height: 30vh;
    margin: 5vh 0;
    width: 30vh;
}
```

Definimos mesma altura e largura, para que ela fique no formato quadrado (30vh). Para arredondar suas bordas, vamos usar o `border-radius: 5vh;`. Apliquei uma cor para a caixa em `background-color: #e85d75;`, e apliquei uma margem apenas nas bordas superior e inferior `margin: 5vh 0;`. Para animar nossa caixa, vamos usar o `animation: 3s loading linear infinite;`. Nossa animação tem duração de 3 segundos, com `@keyframes` de nome `loading`, e a animação ocorre de forma linear e infinita.

Agora, na definição dos `@keyframes`, vamos usar a propriedade `transform:` e rotacionar nosso objeto. Quando usamos apenas `rotate()`, estamos apenas rotacionando o objeto num plano; porém, queremos que esse objeto tenha visualização 3D. Para isso, usaremos o `rotateX()` e `rotateY()`; o primeiro, rotaciona o objeto no sentido horizontal (eixo X), e o segundo, no sentido vertical (eixo Y).

```css
@keyframes loading {
    0% {
        transform: rotateX(0deg) rotateY(0deg);
    }
    50% {
        transform: rotateX(180deg) rotateY(0deg);
    }
    100% {
        transform: rotateX(180deg) rotateY(180deg);
    }
}
```

Agora, vamos estilizar nosso texto `<h2> carregando... </h2>`:

```css
h2 {
    animation: 2s change linear infinite;
    animation-direction: alternate;
    margin-bottom: 10vh;
    text-transform: uppercase;
}
```

Aqui, estou deixando as letras em caixa alta `text-transform: uppercase;`, aplicando uma margem na borda inferior `margin-bottom: 10vh;`, e aplicando uma animação `animation: 2s change linear infinite;`. A animação terá duração de 2 segundos, seu `@keyframes` se chama `change`, e ocorre de forma linear e infinita.

Agora, para a estilização dos `@ketframes`, vamos apenas mudar a cor da letra, que começa do rosa e vai mudando até terminar em verde. O `animation-direction: alternate;` que aplicamos no `<h2></h2>` faz com que a animação comece do ponto em que ela terminou, ou seja, ela roda para a frente e para trás.

```css
@keyframes change {
    0% {
        color: #e85d75;
    }
    100% {
        color: #40f99b;
    }
}
```
