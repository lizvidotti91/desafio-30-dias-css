# Dia 03 - Mudança de cor quando o texto entra em outra div

-   [Codepen](https://codepen.io/lizvidotti91/pen/JjXppWe?editors=1100);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS overflow](https://www.w3schools.com/css/css_overflow.asp);
-   [CSS position](https://www.w3schools.com/css/css_positioning.asp);
-   [CSS white-space](https://www.w3schools.com/cssref/pr_text_white-space.asp);

## Passo a passo

No arquivo HTML, nossa estrutura básica, dentro do `<body></body`, será:

```html
<section class="home">
    <span class="slide"> Amor é fogo que arde sem se ver </span>
    <div class="box">
        <span class="slide"> Amor é fogo que arde sem se ver </span>
    </div>
</section>
```

Primeiro, em nosso arquivo CSS, vamos usar o reset do CSS:

```css
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
```

No nosso arquivo CSS, vamos deixar a `<div class="box"></div>` por cima da nossa `<section class="home"></section>`. Para isso, vamos usar bastante da propriedade `position: absolute` nos elementos. Lembrando que, o último elemento na sequência do HTML, será o elemento que estará mais acima.

```css
.home {
    bottom: 25vh;
    color: hotpink;
    overflow: hidden;
    position: absolute;
    top: 25vh;
    width: 100%;
}
.box {
    background-color: hotpink;
    color: whitesmoke;
    height: 100%;
    left: 0;
    overflow: hidden;
    position: absolute;
    top: 0;
    width: 50%;
}
.slide {
    animation: animate 10s linear infinite;
    font-size: 9vw;
    line-height: 10vw;
    overflow: visible;
    position: absolute;
    top: 25%;
    white-space: nowrap;
    width: 30vw;
}
```

Uma coisa muito interessante para posicionar o conteúdo de um elemento HTML, é a propriedade `overflow:`. Essa propriedade controla o que acontece com conteúdo, quando ele é muito grande para caber em uma área. Por padrão, ele é `overflow: visible`, o que quer dizer que o conteúdo extrapola os limites da área delimitada por um elemento. No caso, como estou definindo altura e largura da `<section></section` e da `<div></div`, e não quero que a parte do texto que extrapola estes limites apareça, usei a propriedade `overflow: hidden`, que deixa o restante do conteúdo escondido. Somente na `<span class="slide"></span>` deixei o conteúdo visível, pois ela quebrava o texto na hora de fazer a animação.

Mas, mesmo com o `overflow: hidden`, o texto quebrava em duas linhas, se ajustando ao tamanho da caixa que ele ocupa. Então, usei o `white-space: nowrap`, que deixou o texto em linha. Esta propriedade especifica como o espaço em branco dentro de um conteúdo é tratado.

Para fazer a animação do texto, foi aplicado o `animation: animate 10s linear infinite;` no `<span class="slide"></span>`. Vamos fazer uma animação, onde o quadro-chave se chama "animate"; sua animação acontece em 10 segundos, de forma linear e infinita, para que, quando se acabem os 10 segundos, ele recomeça automaticamente. Então, usamos o `@keyframes`

```css
@keyframes animate {
    0% {
        transform: translate(100%, 0);
    }
    100% {
        transform: translate(-200%, 0);
    }
}
```

Nessa animação, o elemento `<span class="slide"></span>` começa na borda direita da caixa, e termina em sua borda esquerda. Usei "200%" para que o conteúdo fosse deslizando até a última letra da frase. Como a propriedade `translate()` determina a posição no eixo x e y, deixei "0" depois da vírgula, já que o texto se move apenas na horizontal.
