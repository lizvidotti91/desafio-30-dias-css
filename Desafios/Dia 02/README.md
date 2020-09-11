# Dia 02 - Loader Animado

-   [Codepen](https://codepen.io/lizvidotti91/pen/GRZyLrP?editors=1100);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS animations](https://www.w3schools.com/css/css3_animations.asp);

## Passo a passo

No arquivo HTML, nossa estrutura básica, dentro do `<body></body`, será:

```html
<div class="loading">
    <div class="text">Carregando</div>
    <div class="ring"></div>
</div>
```

Aplicaremos algumas propriedades de animação CSS na nossa `<div class="ring"></div>`, que será o círculo que ficará rodando em looping. O texto "Carregando" também receberá a propriedade `animation:`, onde a opacidade do texto ficará variando de 0 a 1, também em looping.

Primeiro, vamos aplicar o reset do CSS, em nosso arquivo .css.

```css
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
```

Então, vamos aplicar a propriedade `position: absolute` em nossa `<div class="loading"></div>`. Ela se posicionará em relação ao elemento-pai, que, no caso, é o `<body></body>`. Vamos colocar os valores de `top:` e `left:` em 50%, que significa que o elemento estará posicionado em 50% da largura e 50% da altura da tela.

```css
div.loading {
    left: 50%;
    position: absolute;
    top: 50%;
    transform: translate(-50%, -50%);
}
```

Nossa `<div class="text"></div>` também seguirá o mesmo raciocínio. Ela terá posição absoluta em relação à `<div class="loading"></div>`, que é o elemento-pai em relação à ela. Para que o texto possa parecer que está "acendendo e apagando", vamos aplicar a propriedade `opacity:` a este elemento. Vamos precisar aplicar o `animation:`:

```css
div.text {
    animation: text 3s linear infinite;
    color: #c204c2;
    font-family: monospace;
    font-size: 10vh;
    font-weight: 100;
    left: 50%;
    position: absolute;
    top: 50%;
    transform: translate(-50%, -50%);
}
```

Mas, afinal, o que quer dizer `animation: text 3s linear infinite;`? Para que eu possa usar a animação no CSS, é preciso especificar alguns quadros-chave. Eles vão mostrar o estado do elemento em alguns momentos, que variam de 0% a 100%. Nesse caso, o quadro chave se chama `text`. Ele tem a duração de 3 segundos, e ocorre de maneira linear e infinita (quando chega em 100%, ela volta pra 0%).

Agora, vamos especificar o quadro-chave "text".

```css
@keyframes text {
    0% {
        display: hidden;
    }
    25% {
        display: block;
        opacity: 0.1;
    }
    50% {
        opacity: 0.3;
    }
    75% {
        opacity: 0.5;
    }
    100% {
        opacity: 1;
    }
}
```

No começo da animação (0%), o elemento estará invisível na tela `display: hidden;`. Nos outros momentos, ele já volta a ficar visível `display: block;`, e vai perdendo sua transparência `opacity: 0.1`. A propriedade de opacidade varia de 0 a 1, onde 0 é completamente transparente, e 1, totalmente opaco.

Para a `<div class="ring"></div>`, vamos aplicar o mesmo raciocínio dos `@keyframes`. Primeiro, vamos definir um tamanho para o nosso círculo, `{height: 40vw; width: 40vw}`. A unidade de menina "vw" quer dizer "Viewport Width", ou largura da tela. Isso garante que a bolinha varie de tamanho conforme a largura da tela aumenta ou diminui. Para deixar na forma circula, vamos aplicar o `border-radius: 50%`, e deixar sem cor de borda ou de fundo. Com a propriedade `box-shadow: 10px 5px 0px #c204c2;`, vamos aplicar um sombreamento no elemento. Cada um destes valores quer dizer que a sombra estará 10px para baixo; 5px para esquerda; 0px quer dizer que a sombra será opaca, com a cor #c204c2 (código hexadecimal).

```css
div.ring {
    animation: animate 2s linear infinite;
    border-radius: 50%;
    box-shadow: 10px 5px 0px #c204c2;
    height: 40vw;
    width: 40vw;
}
```

Como no texto, vamos aplicar o `@keyframe`:

```css
@keyframes animate {
    0% {
        transform: rotate(0deg);
    }

    100% {
        transform: rotate(360deg);
    }
}
```

Isso fará com que a bolinha permaneça girando em looping.
