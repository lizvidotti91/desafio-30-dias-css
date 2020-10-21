# Dia 28 - Cor do Background Mudando

![Cor do Background Mudando](./captured.gif?raw=true "Cor do Background Mudando")

*   [Codepen](https://codepen.io/lizvidotti91/pen/XWKNXVy?editors=1100); 

## Tecnologias Usadas

*   HTML
*   CSS

## O que eu aprendi

*   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp); 

## Passo a passo

Esta construção é bem simples! Vamos começar com nosso arquivo HTML:

``` html
<body>
    <header>
        <h1>Desafio #28 Cor do Background Mudando</h1>
    </header>
    <section>
        <h1>Amai para entendê-las! </h1>
        <h1>Pois só quem ama pode ter ouvido</h1>
        <h1>Capaz de ouvir e e de entender estrelas</h1>
    </section>
    <footer>
        <p>Olavo Bilac | #30DiasDeCSS</p>
        <p>&copy; Liz</p>
    </footer>
</body>
```

Na nossa tag `<body></body>` , temos cabeçalho `<header></header>` , conteúdo principal `<section></section>` e rodapé `<footer></footer>` .

No arquivo CSS, vamos estilizar algumas propriedades, comuns a todos os elementos do documento. Para isso, usaremos o `*` . O tamanho das caixas é definido a partir de suas bordas (por padrão, o tamanho das caixas é definido a partir do conteúdo. Isso faz com que, ao aplicar preenchimento `padding:` , por exemplo, o tamanho da caixa é alterado, conforme o valor de seu preenchimento). Também deixaremos o valor das margens e preenchimento em zero.

``` css

* {

    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
```

A tag `<body></body>` é que estará recebendo a animação, que faz com que a cor de fundo fique mudando. Vamos aplicar outras estilizações também. Para centralizar seu conteúdo nos eixos vertical e horizontal, vamos usar as propriedades `align-items: center; display: flex; height: 100vh; justify-content: center;` . É importante que seja sempre definida uma altura, para que o conteúdo se ajuste no sentido vertical. Agora, você deve estar vendo todo o conteúdo ocupando uma única linha; vamos usar `flex-direction: column;` para que o conteúdo volte a ficar em colunas. Aplicando uma cor de fundo `background-color: #FF0000;` e a animação `animation: coloring 8s linear infinite;` ; ela tem quadro-chave de nome coloring, tem duração de oito segundos, e ocorre de maneira linear e infinita. Quando a animação terminar, vamos fazer com que ela recomece do final e retorne ao início, e recomece novamente, vamos usar `animation-direction: alternate;` .

``` css
body {
    align-items: center;
    animation: coloring 8s linear infinite;
    animation-direction: alternate;
    background-color: #FF0000;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

Agora, para a definição do `@keyframes` , vamos alterar apenas a cor de fundo `background-color:`

``` css
@keyframes coloring {
    0% {
        background-color: #ef476f
    }

    25% {
        background-color: #ffd166;
    }

    50% {
        background-color: #06d6a0;
    }

    75% {
        background-color: #118ab2;
    }

    100% {
        background-color: #073b4c;
    }
}
```

Agora, você já deve ver a cor de fundo mudando! Vamos estilizar os textos:

``` css
header,
footer {
    color: whitesmoke;
    font-family: monospace;
    font-size: 3vh;
    opacity: 0.8;
    text-align: center;
}

section {
    color: whitesmoke;
    font-family: Arial;
    font-size: 6vh;
    line-height: 12vh;
    margin: 15vh 0;
    text-align: center;
}
```
