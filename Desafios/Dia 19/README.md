# Dia 19 - Fundo de Partículas

![Fundo de Partículas](./captured.gif?raw=true "Fundo de Partículas")

-   [Codepen](https://codepen.io/lizvidotti91/pen/yLOwaqe);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS 2D Transforms](https://www.w3schools.com/css/css3_2dtransforms.asp);
-   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp);
-   [CSS Filter](https://www.w3schools.com/cssref/css3_pr_filter.asp);
-   [CSS Gradient](https://www.w3schools.com/css/css3_gradients.asp);

## Passo a passo

Para este desafio, usei como referência o blog do [TreinaWeb](https://www.treinaweb.com.br/blog/como-fazer-animacao-infinita-de-fundo-com-css/). Eles fizeram um tutorial muito legal que me ajudou muito a entender a construção do projeto.

No arquivo HTML, teremos uma `<div></div>` principal, onde desenharemos nossa animação.

```html
<div class="sky">
    <header>
        <h1>Desafio #19 Fundo de partículas</h1>
    </header>
    <div class="stars"></div>
    <div class="stars2"></div>
    <div class="stars3"></div>
    <footer>
        <p>#30DiasDeCSS</p>
        <p>&copy; Liz</p>
    </footer>
</div>
```

Estilizando nossa `<div class="sky"></div>`:

```css
div.sky {
    align-items: center;
    background-image: linear-gradient(#0d0d1f, #6c6ce4);
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
    width: 100vw;
}
```

Vamos alinhar nossos elementos na tela, usando as três propriedades juntas `align-items: center; display: flex; justify-content: center;`; elas centralizam os elementos nos sentidos horizontal e vertical. Agora precisamos estabelecer uma altura e largura, que defini com `height: 100vh; width: 100vw;`; as unidades de medida vh (Viewport Height) e vw (Viewport Width) fazem com que o elemento se ajuste aos diversos tamanhos de tela. A cor do elemento, defini como um gradiente, onde a cor varia de um azul mais escuro até um azul mais claro `background-image: linear-gradient(#0d0d1f, #6c6ce4);`.

Estilizando cabeçalho e rodapé:

```css
header,
footer {
    color: #e2e1e1b0;
    font-family: monospace;
    position: absolute;
    text-align: center;
}

header {
    font-size: 4vh;
    top: 10vh;
}

footer {
    font-size: 3vh;
    bottom: 10vh;
}
```

Primeiro, defini as mesmas cores, estilo de fonte alinhamento de texto para os dois elementos. Também deixei a posição deles como absluta, onde o elemento fica numa camada acima do elemento-pai. Depois, apliquei tamanhos diferentes de fonte para cada um, e fixei o `<header></header>` na margem superior, e o `<footer></footer>` na margem inferior.

Agora, para desenhar as bolinhas, ao invés de criar várias `<div></div>`, vamos usar a propriedade `box-shadow:` para criar as sombras do elemento. O primeiro valor será o deslocamento para a direita, o segundo valor, deslocamento para baixo, e o terceiro valor, a cor do elemento.

```css
div.stars {
    animation: anima 6s linear infinite;
    border-radius: 50%;
    box-shadow: 0vh 30vh #c1292e, -10vh 0vh #c1292e, 20vh 50vh #c1292e, -30vh
            30vh #c1292e, 40vh 70vh #c1292e, -50vh 80vh #c1292e,
        60vh 50vh #c1292e, -70vh 20vh #c1292e, 80vh 10vh #c1292e, -90vh 30vh
            #c1292e, 100vh 50vh #c1292e;
    height: 2vh;
    position: relative;
    width: 2vh;
}
```

Aplicamos altura e largura para o elemento principal, e o `border-radius: 50%;` para deixar o objeto na forma circular. Ele terá posição relativa, pois vamos criar pseudo-elementos para ele. Aqui também estamos aplicando a animação, que fará com que as bolinhas se desloquem para cima. Essa animação tem duração de 6 segundos, e ocorre de maneira linear e infinita.

Para que a animação aconteça de maneira mais suave, sem que você perceba o ponto que ela começa e termina, vamos criar o pseudo-elemento `::after`. Ele cria um elemento após o elemento principal. Vamos aplicar as mesmas propriedades da nossa `<div></div>` acima, retirando a animação. Também mudaremos a posição de relativa para absoluta, e aplicamos como conteúdo uma string vazia `content: " " ;`.

```css
div.stars::after {
    border-radius: 50%;
    box-shadow: 0vh 30vh #c1292e, -10vh 0vh #c1292e, 20vh 50vh #c1292e, -30vh
            30vh #c1292e, 40vh 70vh #c1292e, -50vh 80vh #c1292e,
        60vh 50vh #c1292e, -70vh 20vh #c1292e, 80vh 10vh #c1292e, -90vh 30vh
            #c1292e, 100vh 50vh #c1292e;
    content: "";
    height: 2vh;
    position: absolute;
    top: 100vh;
    width: 2vh;
}
```

Usei os mesmos estilos para as `<div class="stars2"></div>` e `<div class="stars3"></div>`, mudando a cor dos elementos no `box-shadow:` e a duração da animação. Eu deixei uma diferença de 6 segundos entre as animações. Agora para animá-las, usarei o `@keyframes`

```css
@keyframes anima {
    0% {
        filter: hue-rotate(0deg);
        transform: translate(0vh, 0vh);
    }
    100% {
        filter: hue-rotate(360deg);
        transform: translate(0vh, -100vh);
    }
}
```

O filtro `hue-rotate()` causa uma mudança de cor nas bolinhas, e o `transform: translate()` faz com que as bolinhas se desloquem para cima. Ele começa na posição inicial (0vh, 0vh) e termina em (0vh, -100vh): o primeiro valor é quanto o elemento se desloca para a direita, e o segundo valor, o quanto o elemento se desloca para baixo (valores negativos fazem com o que o elemento desloque para cima).
