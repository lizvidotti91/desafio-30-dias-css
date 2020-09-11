# Dia 4 - Botão com efeito

-   [Codepen](https://codepen.io/lizvidotti91/pen/vYGRBoN);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [Pseudo-elementos CSS](https://www.w3schools.com/css/css_pseudo_elements.asp);
-   [CSS ::after](https://www.w3schools.com/cssref/sel_after.asp);
-   [CSS ::before](https://www.w3schools.com/cssref/sel_before.asp);
-   [CSS ::hover](https://www.w3schools.com/cssref/sel_hover.asp);
-   [CSS Positions](https://www.w3schools.com/css/css_positioning.asp);

## Passo a passo

No arquivo HTML, usaremos uma tag `<button></button`, com o conteúdo do nosso botão.

```html
<header>
    <h1>Desafio #4: Botão com efeito</h1>
</header>
<button>Clique em mim</button>
<footer>
    <p>#30DiasDeCSS</p>
    <p>&copy; Liz</p>
</footer>
```

Em nosso arquivo CSS, vamos usar o reset do CSS:

```css
* {
    box-sizing: border-box;
    font-family: monospace;
    margin: 0;
    padding: 0;
}
```

Para centralizar todo o conteúdo do HTML na tela, vamos usar o trio `align-items: center; display: flex; justify-content: center;`. Como o `display: flex` deixa todo o conteúdo em uma única linha, e queremos que o conteúdo fique em colunas, usamos o `flex-direction: collumn`. É importante também definir uma altura para o corpo da página, que deixei em `height: 100vh;`, ou seja, que ele ocupe toda a altura da tela. Isso faz com que ele se ajuste para diversos tamanhos de tela.

```css
body {
    align-items: center;
    background-color: #d62828;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
}
```

Agora, vamos focar na construção do botão.

```css
button {
    background-color: transparent;
    border: 5px solid #003049;
    border-radius: 10px;
    color: #003049;
    cursor: pointer;
    font-size: 5vh;
    height: 12vh;
    position: relative;
    width: 25vw;
}
```

Definimos altura, largura, altura da fonte. Repare que usei as unidades de medida vw (Viewport Width) e vh(Viewport Height), para que o tamanho da caixa se ajuste aos diversos tamanhos de tela. Deixei a borda mais grossa e colorida, e o fundo transparente. `cursor: pointer` quer dizer que, quando passar o mouse sobre o botão, o ícone do mouse irá mudar da seta para a mão. É importante que eu deixe o `position: relative`, para criar os pseudo-elementos.

Os pseudo-elementos são usados para estilizar partes específicas de um documento. Nesse caso, vamos inserir conteúdos antes e depois do conteúdo do botão.

```css
button::after,
button::before {
    background-color: #d62828;
    content: "";
    height: 2vw;
    position: absolute;
    transform: rotate(30deg);
    transition: 0.5s;
    width: 2vw;
}
```

Estou criando dois quadrados antes e depois do nosso `<button></button>`. Como só quero desenhar os quadrados, deixarei seu conteúdo vazio `content: " ";`. É importante também definir altura e largura. Para dar a impressão de que a borda do botão está "quebrada", vamos deixar a cor de fundo igual a cor de fundo da nossa tag `<body></body>`. Também vamos usar o `position: absolute`, para que nossos pseu-elementos fiquem por cima do `<button></button>`.

Agora, vamos posicionar os pseudo-elementos sobre a borda do botão.

```css
button::after {
    right: 2vw;
    top: -1vw;
}
```

```css
button::before {
    bottom: -1vw;
    left: 2vw;
}
```

As propriedades left, top, right e bottom são usadas para posicionar o elemento em relação ao elemento-pai, o `<button></button>`. Como a posição do `<button></button>` é `position: absolute;`, as propriedades left, top, right e bottom definem a posição dos pseudo-elementos em relação às bordas do elemento-pai.

Pronto! Agora parece que a borda de nosso botão está quebrada. Para animar o nosso botão quando passamos o mouse sobre ele, vamos aplicar a pseudo-classe `:hover`.

```css
button:hover::after {
    right: 20vw;
}
```

```css
button:hover::before {
    left: 20vw;
}
```

Assim, nossos pseudo-elementos vão se posicionar mais à esquerda e mais à direita de sua posição inicial, quando passarmos o mouse sobre o botão. Observe que a posição inicial do `button::after` era `right: 2vw;` e, quando passamos o mouse sobre o botão, ele passa a ter posição `right: 20vw`. A mesma lógica acontece com o `button::before`. Para deixar essa transição mais suave, aplicamos o `transition: 0.5s;` em nossos `button::after` e `button::before`.
