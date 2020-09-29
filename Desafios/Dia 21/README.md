# Dia 21 - Esferas Quicando

![Esferas Quicando](./captured.gif?raw=true "Esferas Quicando")

-   [Codepen](https://codepen.io/lizvidotti91/pen/KKzLzKP?editors=1100);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS Transitions](https://www.w3schools.com/css/css3_transitions.asp);
-   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp);
-   [CSS :nth-child()](https://www.w3schools.com/cssref/sel_nth-child.asp);

## Passo a passo

No arquivo HTML, vamos trabalhar com uma `<div class="box"></div>` principal, que guarda cinco elementos, as `<div class="ball"></div>`. Vamos usar a propriedade `animation:` para aplicar a animação nas bolinhas, fazendo com que elas subam e desçam, na tela.

```html
<div class="box">
    <div class="ball"></div>
    <div class="ball"></div>
    <div class="ball"></div>
    <div class="ball"></div>
    <div class="ball"></div>
</div>
```

Vamos aplicar algumas estilizações gerais, para todo o documento. No arquivo CSS, vamos usar o `*`. Deixamos os tamanhos das caixas serem definidos a partir de suas bordas, margem e preenchimento `padding:` com valores zero.

```css
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
```

Centralizando os elementos na tela. Vamos usar as três propriedades juntas `align-items: center; display: flex; justify-content: center;`, para centralizar o conteúdo nos sentidos horizontal e vertical. Para garantir a centralização no sentido vertical, vamos aplicar uma altura `height: 100vh;` igual à altura da tela. Meu arquivo possui ainda cabeçalho e rodapé, então, o `display: flex;` deixou estes três elementos ocupando uma única linha. Para deixá-los em coluna novamente, apliquei o `flex-direction: column;`. Por fim, aplicamos uma cor de fundo `background-color: #53131E;`. Note que as cores, no CSS, podem ser definidas pelo nome da cor, código hexadecimal, sistema RGB e RGBA. Aqui, usei o código hexadecimal.

```css
body {
    align-items: center;
    background-color: #53131E;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

Estilizando a caixa. Apenas apliquei uma borda inferior, para ser a base da nossa caixa `border-bottom: 10px solid #A8BCA1;`. Para deixar as bolinhas lado a lado, apliquei o `display: flex;`; e para distanciá-las uniformemente na base da caixa, usei o `justify-content: space-around;`.  Deixei uma largura definida para a caixa `width: 20vw;`. A unidade de medida vw (Viewport Width) se refere a largura da tela. Vamos aplicar margens superior `margin-top: 35vh` e inferior `margin-bottom: 10vh;` para afastar a caixa dos elementos do cabeçalho e rodapé.

```css
div.box {
    border-bottom: 10px solid #A8BCA1;
    display: flex;
    justify-content: space-around;
    margin-bottom: 10vh;
    margin-top: 35vh;
    width: 20vw;
}
```

Agora, estilizando as bolinhas. Vamos definir uma cor para o elemento `background-color: #A8BCA1;` e altura e largura `height:` e `width:` de mesmo valor, para deixar o elemento quadrado. Arredondando as bordas da caixa `border-radius: 50%;`, deixaremos os elementos redondos. Por fim, vamos aplicar uma animação `animation: jump 1s ease-in infinite;`. Nosso `@keyframes` terá o nome `jump`, com duração da animação em 1 segundo; o valor `ease-in` deixa a animação com início lento e final rápido; `infinite` fará com que a animação repita indefinidamente, até que se feche a janela do navegador.

```css
div.ball {
    animation: jump 1s ease-in infinite;
    background-color: #A8BCA1;
    border-radius: 50%;
    height: 4vh;
    width: 4vh;
}
```

Agora vamos à definição dos `@keyframes`. Nossa bolinha inicia em sua posição original, sobe uma altura de 30vh, e retorna à posição original. Para isso, usaremos a propriedade `transform: translateY()`, que trabalha a posição do elemento apenas no sentido vertical (eixo Y). Valores negativos farão com que a bolinha desloque para cima, e valores positivos, a bolinha desloca para baixo. O valor zero deixa a bolinha em sua posição original.

```css
@keyframes jump {
    0% {
        transform: translateY(0vh);
    }

    60% {
        transform: translateY(-30vh);
    }

    100% {
        transform: translateY(0vh);
    }
}
```

Agora, todas as bolinhas estarão se movendo ao mesmo tempo. Para que cada bolinha se movimente em tempos diferentes, vamos usar a propriedade `animation-delay:` em cada bolinha. Essa propriedade causa um atraso para o começo da animação. Para aplicar valores diferentes para cada bolinha, usaremos o seletor `:nth-child()`. Em nosso HTML, temos uma `<div></div>` principal que guarda outras cinco `<div></div>`. Dizemos que as `<div class="ball"></div>` são "filhas" da `<div class="box"></div>`. Para nos referirmos a cada filho, usamos, no CSS, `.ball:nth-child(1)` para nos referirmos ao primeiro elemento, `.ball:nth-child(2)`, para nos referirmos ao segundo, e assim por diante.

```css
div.ball:nth-child(1) {
    animation-delay: 0s;
}

div.ball:nth-child(2) {
    animation-delay: 0.2s;
}

div.ball:nth-child(3) {
    animation-delay: 0.4s;
}

div.ball:nth-child(4) {
    animation-delay: 0.6s;
}

div.ball:nth-child(5) {
    animation-delay: 0.8s;
}
```