# Dia 09 - Pêndulo de Newton

! [] (pendulo.gif)

-   [Codepen](https://codepen.io/lizvidotti91/pen/vYGrYeE);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS Psdeudo-Elements](https://www.w3schools.com/css/css_pseudo_elements.asp);
-   [CSS ::after Selector](https://www.w3schools.com/cssref/sel_after.asp);
-   [CSS ::before Selector](https://www.w3schools.com/cssref/sel_before.asp);
-   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp);
-   [CSS Positions](https://www.w3schools.com/css/css_positioning.asp);

## Passo a passo

Nossa estrutura do HTML terá apenas uma `<div class="heart"></div>`, onde vamos desenhar e animar o coração. Em nosso arquivo CSS, vamos definir um quadrado, com altura, largura e cor de fundo. Também é importante que deixemos o `position: relative`, pois iremos desenhar outros elementos que terão `position: absolute` em relação à ela. Estamos definindo também o `animation: pulse 1s linear infinite;`: pulse é o meu quadro-chave, a animação terá duração de 1 segundo, e ocorrerá de forma linear e infinita (quando a animação termina, ela retorna ao início).

```css
.heart {
    animation: pulse 1s linear infinite;
    background-color: #dd1c1a;
    height: 20vh;
    position: relative;
    width: 20vh;
}
```

Agora, vamos trabalhar com pseudo-elementos, onde iremos inserir um conteúdo antes e depois da nossa `<div class="heart"></div>`. Vamos usar os pseudo-elementos `::after` e `::before`, que inserem elementos após e antes da nossa div. Vamos desenhar dois círculos, que ficarão por cima do elemento principal, formando a parte de cima do coração.

```css
.heart::after {
    background-color: #dd1c1a;
    border-radius: 50%;
    content: "";
    height: 20vh;
    left: 0;
    position: absolute;
    top: -10vh;
    width: 20vh;
}

.heart::before {
    background-color: #dd1c1a;
    border-radius: 50%;
    content: "";
    height: 20vh;
    left: 10vh;
    position: absolute;
    top: 0vh;
    width: 20vh;
}
```

Definimos altura, largura e cor de fundo, posição absoluta (para que os pseudo-elementos fiquem por cima). É importante que a `<div class="heart"></div>` tenha a posição relativa, para que os pseudo-elementos sejam posicionados em relação à ela. Para deixar a forma circular, deixamos o `border-radius: 50%`. Como os pseudo-elementos não terão conteúdo, deixamos o `content: " ";`.

Agora, vamos posicionar o pseudo-elemento `::after` com `top: -10vh`, para que ele se posicione acima do elemento principal, e o pseudo-elemento `::before` terá `left: 10vh`, para que ele se posicione à direita do elemento principal. Agora, nosso coração estará "deitado", com as bordas redondas viradas para a direita. Mas vamos consertar isso em nosso `@keyframes`.

```css
@keyframes pulse {
    0% {
        transform: rotate(-45deg) scale(1);
    }
    40% {
        transform: rotate(-45deg) scale(1.2);
    }
    60% {
        transform: rotate(-45deg) scale(0.9);
    }
    100% {
        transform: rotate(-45deg) scale(1.2);
    }
}
```

Graças ao `transform: rotate(-45deg)`, nosso coração estará na posição certa. Agora, para que ele possa dar a impressão de que está pulsando, vamos aplicar outra propriedade `transform: scale()`. O `scale()` aumenta ou diminui o elemento em quantas vezes definirmos. O valor 1 quer dizer que ele permanece em seu tamanho normal; valores abaixo de 1, estaremos diminuindo o elemento em relação ao seu tamanho original; valores acima de 1, estaremos aumentando o elemento em relação ao seu tamanho original.
