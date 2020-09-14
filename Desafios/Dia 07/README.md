# Dia 07 - Preloader Animado

![Preloader Animado](./preloader.gif?raw=true "Preloader Animado")

-   [Codepen](https://codepen.io/lizvidotti91/pen/LYNmBvV);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS :nth-child()](https://www.w3schools.com/cssref/sel_nth-child.asp);
-   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp);
-   [CSS Positions](https://www.w3schools.com/css/css_positioning.asp);

## Passo a passo

No arquivo HTML, estarei trabalhando com duas div's; `<div class="loader"></div>` e `<div class="text"></div>`. O primeiro elemento irá armazenar nossos elementos `<span></span>`, onde faremos a animação dos quadradinhos, e a segunda div irá armazenar nosso texto.

```html
<div class="loader">
    <span></span>
    <span></span>
    <span></span>
</div>
<div class="text">Carregando...</div>
```

Em nosso arquivo CSS, vamos usar o reset do CSS. O símbolo `*` quer dizer que estou aplicando a todos os elementos do meu conteúdo HTML:

```css
* {
    box-sizing: border-box;
    font-family: "Roboto", sans-serif;
    margin: 0;
    padding: 0;
}
```

Para centralizar todo o conteúdo do HTML na tela, vamos usar o trio `align-items: center; display: flex; justify-content: center;`. Como o `display: flex` deixa todo o conteúdo em uma única linha, e queremos que o conteúdo fique em colunas, usamos o `flex-direction: column`. É importante também definir uma altura para o corpo da página, que deixei em `height: 100vh;`, ou seja, que ele ocupe toda a altura da tela. Isso faz com que ele se ajuste para diversos tamanhos de tela.

```css
body {
    align-items: center;
    background-color: #3d5a80;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

Agora, vamos focar na construção da animação. Primeiro, vamos estilizar o `<div class="loader"></div>`. Definimos altura e largura, e `position: relative`, onde ele estará posicionado em relação à sua posição normal.

```css
.loader {
    height: 15vh;
    position: relative;
    width: 15vh;
}
```

Para a estilização de cada `<span><span>`:

```css
span {
    animation: loading 1.5s linear infinite;
    background-color: #ee6c4d;
    height: 5vh;
    position: absolute;
    width: 5vh;
}
```

Definimos altura, largura e cor de cada elemento. Também usamos o `position: absolute;`, onde ele estará posicionado em relação ao elemento-pai, no caso, a `<div class="loader"></div>`. Assim, todos os elementos `<span></span>` estarão empilhados na nossa tela. Definimos também o `animation: loading 1.5s linear infinite;`, onde nosso quadro-chave se chama loading, com duaração de 1s e meio, e ocorre de forma linear e em looping. Assim que a animação termina, ela retorna ao início.

Definindo nosso `@keyframes`, para que nosso `<span></span>` deslize da esquerda para a direita, em metade do tamanho do elemento-pai; desça em 100% do tamanho do elemento-pai; deslize da direita para esquerda em 50% relação ao elemento-pai; e termine retornando à sua posição inicial.

```css
@keyframes loading {
    0% {
        left: 0;
        top: 0;
    }
    25% {
        left: 50%;
        top: 0;
    }
    50% {
        left: 50%;
        top: 100%;
    }
    75% {
        left: 0;
        top: 100%;
    }
    100% {
        left: 0;
        top: 0;
    }
}
```

Para a animação ocorrer de forma mais suave, acrescentamos tempos intermediários:

```css
@keyframes loading {
    0% {
        left: 0;
        top: 0;
    }
    12.5% {
        left: 50%;
        top: 0;
    }
    25% {
        left: 50%;
        top: 0;
    }
    37.5% {
        left: 50%;
        top: 100%;
    }
    50% {
        left: 50%;
        top: 100%;
    }
    67.5% {
        left: 0;
        top: 100%;
    }
    75% {
        left: 0;
        top: 100%;
    }
    87.5% {
        left: 0;
        top: 0;
    }
    100% {
        left: 0;
        top: 0;
    }
}
```

Agora, os três `<span></span>` estarão percorrendo o retângulo ao mesmo tempo, empilhados. Para vermos o três elementos, vamos usar a propriedade `animation-delay:`, que atrasa o ínicio da animação de cada elemento. Também iremos usar a propriedade `:nth-child()`, para se referir a cada elemento,individualmente:

```css
span:nth-child(1) {
    animation-delay: 0s;
}

span:nth-child(2) {
    animation-delay: 0.5s;
}

span:nth-child(3) {
    animation-delay: 1s;
}
```

Também usei a animação no texto `Carregando...`, onde ele dá a impressão de estar piscando. Definindo a `<div class="text"></div>`:

```css
.text {
    animation: texting 1s linear infinite;
    color: #293241;
    position: absolute;
    top: 65vh;
}
```

Para dar a impressão de que o texto está piscando, vamos usar a propriedade `opacity:`, que varia de 0 a 1; onde 0 deixa o elemento totalmente transparente; e 1, o deixa totalmente opaco.

```css
@keyframes texting {
    0% {
        opacity: 0;
    }
    10% {
        opacity: 0.2;
    }
    50% {
        opacity: 0.5;
    }
    100% {
        opacity: 1;
    }
}
```
