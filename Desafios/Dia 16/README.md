# Dia 16 - Botão com Efeito

![Botão com Efeito](./button.gif?raw=true "Botão com Efeito")

-   [Codepen](https://codepen.io/lizvidotti91/pen/LYNMxzW);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS Hover Selector](https://www.w3schools.com/cssref/sel_hover.asp);
-   [CSS Overflow](https://www.w3schools.com/css/css_overflow.asp);

## Passo a passo

Dessa vez, usei como referência o Desafio 01 do repositório do [BrunoSSantana](https://github.com/BrunoSSantana/30diasDeCSS).

Em nosso arquivo HTML, teremos uma `<div></div>` principal, onde ficarão nossos botões `<button></button>`. Cada botão tem um ícone (no elemento `<span></span>`) e um texto.

```html
<div>
    <button class="instagram">
        <span class="fab fa-instagram"></span>
        instagram
    </button>
    <button class="facebook">
        <span class="fab fa-facebook-f"></span>
        facebook
    </button>
    <button class="twitter">
        <span class="fab fa-twitter"></span>
        twitter
    </button>
    <button class="snapchat">
        <span class="fab fa-snapchat-ghost"></span>
        snapchat
    </button>
</div>
```

Em nosso arquivo CSS, vamos começar aplicando algumas estilizações comuns em todo o documento. Faremos o chamado reset CSS, com o tamanho das caixas definido a partir de suas bordar, uma fonte padrão, `margin:` e `padding:` de valores zero.

```css
* {
    box-sizing: border-box;
    font-family: monospace;
    margin: 0;
    padding: 0;
}
```

Centralizando nossos elementos na tela, vamos começar com as três propriedades juntas `align-items: center; display: flex; justify-content: center;`, que centralizam nossos elementos nos sentidos horizontal e vertical. Completando, vamos definir a altura em 100vh. Isso quer dizer que o corpo do nosso documento tem tamanho igual ao tamanho da tela. Como ainda coloquei cabeçalho e rodapé, além da `<div></div>` principal, estes elementos vão estar ocupando apenas uma linha na tela. Para deixá-los novamente em colunas, apliquei o `flex-direction: column;`. Por fim, apliquei uma cor de fundo `background-color: #070707;`.

```css
body {
    align-items: center;
    background-color: #070707;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

Agora, vamos deixar nossos botões lado a lado em nossa `<div></div>`. Também estarei usando o `display: flex;`, que deixa os elementos na mesma linha. Para separá-los do cabeçalho e do rodapé, apliquei uma margem `margin: 10vh 0;`. O primeiro valor define as margens superior e inferior, e o segundo valor, as margens esquerda e direita.

```css
div {
    display: flex;
    margin: 10vh 0;
}
```

Estilizando os botões:

```css
button {
    align-items: center;
    border: none;
    border-radius: 10vh;
    color: whitesmoke;
    cursor: pointer;
    display: flex;
    font-size: 5vh;
    height: 10vh;
    margin-right: 4vh;
    overflow: hidden;
    position: relative;
    padding-left: 10vh;
    transition: 0.5s;
    width: 10vh;
}
```

Primeiro, defini `height:`e `width:` em 10vh. Para deixar o conteúdo alinhado no botão no sentido vertical, usei o `align-items: center; display: flex;`. Defini tamanho e cor da letra do conteúdo do botão `font-size:` e `color:`. Para deixar o botão na forma circular, apliquei o `border-radius: 10vh;` e deixei a caixa sem borda aparente `border: none;`. Para que o texto do botão não fique aparecendo na tela, usei o `overflow: hidden;` e `padding-left: 10vh;`. Deixaremos a posição do botão relativa, e aplicamos uma transição de 0.5 segundos, para deixar a animação mais fluida, quando aplicarmos o `:hover` (passar o mouse em cima do botão). O `cursor: pointer;` muda o ícone do mouse da setinha para a mãozinha, quando o mouse passa sobre o botão.

Agora, personalizando a cor de fundo de cada botão. Usei as cores oficiais das logos de cada mídia social. Vamos fazer a chamada de cada botão pelo nome da classe. Ao nos referirmos a uma classe no CSS, usamos o .nomeDaClasse (lembre-se: #nomeDoID; .nomeDaClasse).

```css
button.instagram {
    background-color: #833ab4;
}

button.facebook {
    background-color: #4267b2;
}

button.twitter {
    background-color: #00acee;
}

button.snapchat {
    background-color: #fffc00;
}
```

Agora, vamos estilizar nosso `:hover;` nos botões. Quando passarmos o mouse sobre o botão, vamos aumentar sua largura e aumentar um pouco nosso `padding-left:`.

```css
button:hover {
    padding-left: 12vh;
    width: 40vh;
}
```

Estilizando nosso `<span></span>`:

```css
button span {
    background-color: #8f8f8fa6;
    border-radius: 50%;
    color: whitesmoke;
    font-size: 6vh;
    height: 10vh;
    left: 0;
    padding-top: 2vh;
    position: absolute;
    top: 0;
    width: 10vh;
}
```

Aqui, definimos altura e largura iguais aos do nosso botão (10vh). Para deixar-mos na forma circular, aplicamos `border-radius: 50%`. O tamanho do ícone é definido em `font-size:`. Deixamos a posição do nosso `<span></span>` absoluta, e fixá-lo nas bordas superior e esquerda do nosso botão (`top: 0; left: 0;`). Por fim, apliquei uma cor de fundo `background-color: #8f8f8fa6;` e cor do ícone `color: whitesmoke;`.
