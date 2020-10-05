# Dia 24 - Loader Animado #3

![Loader Animado #3](./captured.gif?raw=true "Loader Animado #3")

-   [Codepen](https://codepen.io/lizvidotti91/pen/eYzOvNy);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp);
-   [CSS Positions](https://www.w3schools.com/css/css_positioning.asp);
-   [CSS Transform](https://www.w3schools.com/cssref/css3_pr_transform.asp);
-   [CSS :nth-child()](https://www.w3schools.com/cssref/sel_nth-child.asp);


## Passo a passo

No arquivo HTML, vamos usar uma `<div></div>` principal, que contém três elementos `<span></span>`.

```html
<div class="loader">
    <span></span>
    <span></span>
    <span></span>
    <span></span>
</div>
```

No arquivo CSS, vamos usar algumas propriedades comuns a todos os elementos. Para isso, vamos usar o `*`. O tamanho das caixas será determinado a partir de suas bordas (por padrão, esse tamanho é dado a partir do conteúdo). Vamos deixar os valores de `magrgin:` e `padding:` iguais à zero.

```css
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
```

Vamos, agora, centralizar nossa `<div></div>` na tela. Para isso, vamos usar as três propriedades juntas `align-items: center; display: flex; justify-content: center;`. Isso fará com que o elemento fique centralizado nos sentidos horizontal e vertical. Vamos agora definir um altura `height: 100vh;`, para garantir que o elemento centralize no sentido vertical. Por fim, vamos definir uma cor de fundo `background-color: #e07a5f;`.

```css
body {
    align-items: center;
    background-color: #e07a5f;
    display: flex;
    height: 100vh;
    justify-content: center;
}
```

Vamos, agora, estilizar a nossa `<div></div>`. Vamos definir um tamanho para a caixa `height: 20vh; width: 20vh;` e posição relativa. Vamos rotacionar a caixa em `transform: rotate(45deg);`, e aplicar uma animação `animation: loader 2s linear infinite;`, que usaremos mais tarde.

```css
div.loader {
    animation: loader 2s linear infinite;
    height: 20vh;
    position: relative;
    transform: rotate(45deg);
    width: 20vh;
}
```

Agora, vamos estilizar nossos elementos `<span></span>`. Vamos começar definindo um tamanho `height: 10vh; width: 10vh;`, posição absoluta (onde os elementos `<span></span>` numa camada acima da nossa `<div></div>`). Vamos definir uma animação `animation: box 2s linear infinite;`.

```css
span {
    animation: box 2s linear infinite;
    height: 10vh;
    position: absolute;
    width: 10vh;
}
```

Vamos definir alguns estilos próprios para cada `<span></span>`. Cada elemento terá uma cor de fundo e posições diferentes. Queremos que as caixas fiquem posicionadas lado a lado, formando um novo quadrado. Para isso, fixaremos cada elemento em um canto das bordas da nossa `<div></div>`.

```css
span:nth-child(1) {
    background-color: #81b29a;
    left: 0;
    top: 0;
}

span:nth-child(2) {
    background-color: #3d405b;
    bottom: 0vh;
    left: 0;
}

span:nth-child(3) {
    background-color: #f2cc8f;
    right: 0;
    top: 0;
}

span:nth-child(4) {
    background-color: #f4f1de;
    bottom: 0;
    right: 0;
}
```

Vamos agora animar a nossa `<div></div>`; vamos fazer com que ela aumente e volte à sua posição inicial. Como cada `<span></span>` está fixada em um canto da `<div></div>`, teremos a impressão que as caixas estão se mexendo.

```css
@keyframes loader {
    0% {
        height: 20vh;
        width: 20vh;
    }

    10% {
        height: 20vh;
        width: 20vh;
    }

    50% {
        height: 30vh;
        width: 30vh;
    }

    90% {
        height: 20vh;
        width: 20vh;
    }

    100% {
        height: 20vh;
        width: 20vh;
    }
}
```

Agora, vamos fazer com que cada elemento `<span></span>` rotacione na tela.

```css
@keyframes box {
    0% {
        transform: rotate(0deg);
    }

    10% {
        transform: rotate(0deg);
    }

    50% {
        transform: rotate(90deg);
    }

    90% {
        transform: rotate(90deg);
    }

    100% {
        transform: rotate(90deg);
    }
}
```