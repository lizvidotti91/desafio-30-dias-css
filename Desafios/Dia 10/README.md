# Dia 10 - Animação Texto alternando

![Animação Texto alternando](./slide.gif?raw=true "Animação Texto alternando")

-   [Codepen](https://codepen.io/lizvidotti91/pen/vYGayJj?editors=0100);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS Psdeudo-Elements](https://www.w3schools.com/css/css_pseudo_elements.asp);
-   [CSS ::after Selector](https://www.w3schools.com/cssref/sel_after.asp);
-   [CSS ::before Selector](https://www.w3schools.com/cssref/sel_before.asp);
-   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp);
-   [CSS Content Property](https://www.w3schools.com/cssref/pr_gen_content.asp);

## Passo a passo

Para a estrutura HTML, teremos um elemento `<div></div>` com dois conteúdos: um texto e um elemento `<span></span>`. Nossa animação acontecerá em nosso elemento `<span></span>`.

```html
<div class="text">I love <span></span></div>
```

Em nosso arquivo CSS, vamos usar o Reset CSS. Definimos que o tamanho das caixas serão definidos a partir da bordas, a fonte que será usada em todo o documento, `margin:` e `padding:` com valor zero.

```css
* {
    box-sizing: border-box;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    margin: 0;
    padding: 0;
}
```

Agora, vamos centralizar nosso conteúdo na página. Usaremos as propriedades `align-items: center; display: flex; flex-direction: column; justify-content: center;`. É importante definir a altura do elemento, que deixei em `height: 100vh`. A unidade de medida vh (Viewport Height), quer dizer que o conteúdo ocupará a altura da tela, podendo se ajustar aos diversos tamanhos de tela. Por fim, definimos uma cor de fundo `background-color:`.

```css
body {
    align-items: center;
    background-color: #a44a3f;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

Agora vamos estilizar nossa `<div class="text"></div>`; o elemento `<span></span>` já deixa nosso conteúdo na mesma linha, e não teríamos a necessidade de aplicar o `display: flex;`, mas estarei usando para garantir que o texto e as imagens que irei usar estejam alinhadas.

```css
div.text {
    align-items: center;
    color: #94a89a;
    display: flex;
    font-size: 10vh;
    justify-content: space-around;
    width: 30vw;
}
```

Agora, vamos criar um pseudo-elemento. Aqui, utilizarei o `::before`. Será neste pseudo-elemento onde irei inserir as imagens. Num primeiro momento, deixarei seu conteúdo vazio `content: " ";`. Aqui vamos definir a animação, que possui quadro-chave de nome `slide`, onde a animação irá durar 5 segundos, e irá ocorrer de forma linear e em looping (quando a animação acabar, ela voltará ao início).

```css
span::before {
    animation: slide 5s linear infinite;
    content: "";
}
```

Agora, na definição dos `@keyframes`, vamos alterar o conteúdo `content:`. A cada momento, vamos inserir uma imagem diferente. Para inserir uma imagem na propriedade `content:`, vamos precisar inserir uma URL `content: url()`, e dentro dos parênteses, vamos inserir o caminho da imagem. Como as imagens estão salvas nesse repositório, colocarei o caminho relativo da imagem. Se você inserir uma imagem da web, basta substituir pela url da imagem. Assim:

```css
@keyframes slide {
    0% {
        content: url(./img/book.png);
    }
    20% {
        content: url(./img/coffe.png);
    }
    40% {
        content: url(./img/music.png);
    }
    60% {
        content: url(./img/netflix.png);
    }
    80% {
        content: url(./img/paint.png);
    }
    100% {
        content: url(./img/travel.png);
    }
}
```

Pronto! Agora você verá as imagens trocando de posição, como uma apresentação de slides.
