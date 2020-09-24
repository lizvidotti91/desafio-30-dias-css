# Dia 18 - Texto Esfumaçado

![Texto Esfumaçado](./captured.gif?raw=true "Texto Esfumaçado")

-   [Codepen](https://codepen.io/lizvidotti91/pen/zYqeRGW?editors=1100);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS 2D Transforms](https://www.w3schools.com/css/css3_2dtransforms.asp);
-   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp);
-   [CSS Animation-delay](https://www.w3schools.com/cssref/css3_pr_animation-delay.asp);
-   [CSS :nth-child()](https://www.w3schools.com/cssref/sel_nth-child.asp);

## Passo a passo

No nosso arquivo HTML, teremos um elemento `<div></div>` com uma frase, onde cada letra estará dentro de um elemento `<span></span>`.

```html
<div class="smoke">
    <span>T</span>
    <span>r</span>
    <span>e</span>
    <span>m</span>
    <span>D</span>
    <span>a</span>
    <span>s</span>
    <span>O</span>
    <span>n</span>
    <span>z</span>
    <span>e</span>
</div>
```

Em nosso arquivo CSS, vamos aplicar algumas estilizações em todo o documento. Para isso, usaremos o `*`.

```css
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
```

Aqui, o tamanho das caixas serão definidas a partir de suas bordas (por exemplo, quando aplico o `padding:` em um elemento, por padrão, o tamanho final da caixa se altera tal o tamanho do conteúdo. Com o `border-box`, o valor definido para altura e largura permanecerá o mesmo). Também deixamos os valores de `margin:` e `padding:` em zero.

Centralizando os elementos na tela:

```css
body {
    align-items: center;
    background-color: #293f14;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

Para centralizar, usamos as três propriedades `align-items: center; display: flex; justify-content: center;`. Dessa forma os elementos ficam centralizados nos sentidos horizontal e vertical. Vamos completar definindo uma altura `height: 100vh;`, para que os elementos centralizem no sentido vertical. Como meu documento também tem cabeçalho e rodapé, quando aplico o `display: flex;`, estes três elementos estarão ocupando uma única linha. Aplicando o `flex-direction: column;`, os elementos voltam a ficar dispostos em colunas.

Agora, vamos estilizar nossa `<div></div>`:

```css
div.smoke {
    color: whitesmoke;
    display: flex;
    font-family: Arial, Helvetica, sans-serif;
    font-size: 20vh;
    margin: 20vh 0;
}
```

Aplicamos uma cor para as letras `color: whitesmoke;`, estilo e tamanho da letra `font-family: Arial, Helvetica, sans-serif; font-size: 20vh;`, e margem nas bordas superior e inferior, para separar o texto principal do cabeçalho e rodapé `margin: 20vh 0;`. Para que a animação nos elementos `<span></span>` funcione, vamos aplicar o `display: flex;` na nossa `<div></div>`.

Agora, vamos aplicar a animação em nossos elementos `<span></span>`:

```css
div.smoke span {
    animation: fog 4.5s linear infinite;
    animation-direction: alternate;
}
```

Aqui, vamos usar `animation: fog 4.5s linear infinite;`, onde nossa animação tem `@keyframes` de nome `fog`, com animação durando 4.5 segundos, e ocorre de forma linear e infinita. Quando a animação termina, ela recomeça do ponto inicial. Para dar o efeito de que as letras somem e retornam da fumaça, vamos usar `animation-direction: alternate;`; quando a animação terminar, ela recomeça de seu ponto final, ou seja, alterna para a frente e para trás.

Definindo os `@keyframes`:

```css
@keyframes fog {
    0% {
        opacity: 1;
        filter: blur(0px);
        transform: translate(0px, 0px) rotate(0deg);
    }
    20% {
        opacity: 1;
        filter: blur(0px);
        transform: translate(0px, 0px) rotate(0deg);
    }
    100% {
        filter: blur(20px);
        opacity: 0;
        transform: translate(2vw, -20vh) rotate(45deg);
    }
}
```

Aqui, do começo da animação até 20%, nosso texto permanece opaco `opacity: 1;`, sem desfoque de cor `filter: blur(0px);` e em sua posição original `transform: translate(0px, 0px) rotate(0deg);`. Entre os 20% e o final da animação, ocorre uma transição na opacidade da cor, até que ela se torne completamente transparente `opacity: 0;`; para o efeito de fumaça, vamos aumentar o desfoque de cor `filter: blur(20px);` e mover os elementos `transform: translate(2vw, -20vh) rotate(45deg);`. A propriedade `translate()` define o quanto o elemento desloca para a direita e para baixo (como usei valor negativo, a letra se desloca para cima). A propriedade `rotate()` rotaciona o elemento no plano 2D.

Agora todas as nossas letras estarão sumindo e entrando na tela ao mesmo tempo. Para que as letras vão sumindo gradativamente, vamos aplicar a propriedade `animation-delay:` em cada elemento `<span></span>`; essa propriedade causa um atraso para o início da animação. Para nos refirmos a um único elemento por vez, vamos usar o seletor `:nth-child()`: nossa `<div></div>` principal "guarda" 11 elementos `<span></span>` (11 "filhos"); então, para me referir ao primeiro filho da nossa caixa, uso o `span:nth-child(1)`, e assim por diante, até o `span:nth-child(11)`.

```css
div.smoke span:nth-child(1) {
    animation-delay: 0s;
}

div.smoke span:nth-child(2) {
    animation-delay: 0.4s;
}

div.smoke span:nth-child(3) {
    animation-delay: 0.8s;
}
```

Continuo na mesma lógica, dando um espaço de 0.4 segundos de um elemento para o outro, até o elemento número 11.
