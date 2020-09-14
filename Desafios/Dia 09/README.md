# Dia 09 - Pêndulo de Newton

![Pêndulo de Newton](./pendulo.gif?raw=true "Pêndulo de Newton")

-   [Codepen](https://codepen.io/lizvidotti91/pen/qBZKoge);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS Psdeudo-Elements](https://www.w3schools.com/css/css_pseudo_elements.asp);
-   [CSS ::after Selector](https://www.w3schools.com/cssref/sel_after.asp);
-   [CSS ::before Selector](https://www.w3schools.com/cssref/sel_before.asp);
-   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp);
-   [CSS Positions](https://www.w3schools.com/css/css_positioning.asp);
-   [CSS Transitions](https://www.w3schools.com/css/css3_transitions.asp);
-   [CSS Transform-origin](https://www.w3schools.com/cssref/css3_pr_transform-origin.asp);

## Passo a passo

Para a estrutura HTML, iremos usar uma `<div></div>`, que contém cinco elementos `<span></span>`. Cada `<span></span>` representa um pêndulo.

```html
<div class="pendulo">
    <span></span>
    <span></span>
    <span></span>
    <span></span>
    <span></span>
</div>
```

Em nosso arquivo CSS, começamos com o reset CSS. O tamanho da caixa será definido a partir das bordas (se um elemento tem 20px de altura, o `padding:` e conteúdo do elemento se adequarão em 20px. Sem usar o `:border-box`, a altura da caixa pode aumentar de 20px).

```css
* {
    box-sizing: border-box;
    font-family: monospace;
    margin: 0;
    padding: 0;
}
```

Para o corpo do documento, vamos centralizar seu conteúdo na tela.

```css
body {
    align-items: center;
    background-color: #5e574d;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

Na nossa `<div class="pendulo"></div>`, vamos aplicar o `display:flex;`, para que todo o conteúdo fique lado a lado. Para fazer a linha horizontal do desenho, vamos usar o `border-top:`, que cria uma bordar apenas na parte superior da caixa.

```css
.pendulo {
    display: flex;
    border-top: 1vh solid #c3dfe0;
}
```

Para desenhar cada pêndulo, vamos agora desenhar uma linha vertical em nosso `<span></span>`, e, para desenhar a bolinha, vamos usar o pseudo-elemento `::after`. Para o span, definimos altura, largura e cor de fundo. Mas ainda não conseguimos ver nosso elemento na tela. Para torná-lo visível, usamos o `display: block`. Agora veremos apenas uma linha na tela, pois nossos elementos estarão juntos. Para descolá-los, vamos aplicar uma margem `margin: 0 2vw;`: o primeiro valor representa as margens superior e inferior, e o segundo valor, as margens esquerda e direita.

Na hora de animar o pêndulo, fazendo ele girar para a esquerda ou para a direita, precisamos mudar o ponto de origem da animação. Normalmente quando aplicamos o `transform: rotate()`, o CSS pega o ponto central do elemento. Mas, queremos usar o ponto superior. Então, vamos usar o `transform-origin: top;`.

```css
.pendulo span {
    background-color: #c3dfe0;
    display: block;
    height: 50vh;
    margin: 0 2vw;
    position: relative;
    transform-origin: top;
    width: 0.2vw;
}
```

Agora, vamos desenhar a bolinha, usando o pseudo-elemento `::after`. Nosso elemento não terá conteúdo `content: " ";`, e terá posição absoluta em relação ao elemento-pai, que, no caso, é o elemento `<span></span>`. Então, deixamos o elemento `<span></span>` com `position: relative;`, e o pseudo-elemento `::after`, com `position: absolute;`.

Então definimos altura, largura e cor de fundo. Para deixar no formato circular, usamos o `border-radius: 50%;`. Agora, a bolinha estará junto à margem superior da barra vertical. Então, fixamos o `bottom: 0;` e `left:0;`. Agora, a bolinha estará posicionada junto à margem inferior e à margem esquerda. Para deixar a bolinha exatamente no meio da margem inferior, usamos o `transform: translateX(-50%);`.

```css
.pendulo span::after {
    background-color: #c3dfe0;
    border-radius: 50%;
    bottom: 0;
    content: "";
    height: 4vw;
    position: absolute;
    left: 0;
    transform: translateX(-50%);
    width: 4vw;
}
```

Nosso desenho está pronto! Para animá-lo, vamos aplicar a propriedade `animation:` no primeiro e último elemento `<span></span>`. Vamos usar o `span:nth-child(1)` e `span:nth-child(5)`, que se referem ao primeiro e quinto (e último) filho da nossa `<div></div>`.

```css
.pendulo span:nth-child(1) {
    animation: left-rotate 2s ease-in infinite;
}
.pendulo span:nth-child(5) {
    animation: right-rotate 2s ease-in infinite 1s;
}
```

O primeiro valor se refere ao nosso quadro-chave, onde aplicaremos os `@keyframes`. As animações terão duração de 2s, começarão de forma mais lenta e vão acelerando `ease-in` e ficarão em looping `infinite`. No `span:nth-child(5)`, usamos o valor de 1 segundo no final do `animation`, para que ele comece depois de 1 segundo do início da animação.

Na definição dos nossos `@keyframes`, os pêndulos irão rotacionar para a esquerda (o `rotate()` terá valor positivo) e para a direita (o `rotate()` terá valor negativo); e depois retornarão para a sua posição inicial.

```css
@keyframes left-rotate {
    0% {
        transform: rotate(0deg);
    }
    25% {
        transform: rotate(30deg);
    }
    50% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(0deg);
    }
}

@keyframes right-rotate {
    0% {
        transform: rotate(0deg);
    }
    25% {
        transform: rotate(-30deg);
    }
    50% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(0deg);
    }
}
```

Aqui, a animação começa em 0 graus. No momento de 25% da animação, apliquei uma rotação de 30 graus radianos, para a esquerda e para a direita. Em 50% e 100%, o pêndulo retorna à posição inicial (0deg). Assim, o pêndulo da esquerda irá subir, e quando ele retornar à posição inicial, será a vez do pêndulo direito subir.
