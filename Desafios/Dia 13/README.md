# Dia 13 - Loading com Efeito

![Loading com Efeito](./loading.gif?raw=true "Loading com Efeito")

-   [Codepen](https://codepen.io/lizvidotti91/pen/LYNgRzo);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS @keyframes](https://www.w3schools.com/cssref/css3_pr_animation-keyframes.asp);
-   [CSS Letter-Spacing Property](https://www.w3schools.com/cssref/pr_text_letter-spacing.asp);
-   [CSS Opacity Property](https://www.w3schools.com/cssref/css3_pr_opacity.asp);
-   [CSS :nth-child Selector](https://www.w3schools.com/cssref/sel_nth-child.asp);

## Passo a passo

A base do nosso arquivo HTML será:

```html
<ul>
    <li>.</li>
    <li>.</li>
    <li>.</li>
    <li>.</li>
    <li>.</li>
    <li>.</li>
    <li>.</li>
    <li>.</li>
    <li>.</li>
    <li>.</li>
</ul>
<h2>carregando...</h2>
```

Vamos animar cada item `<li></li>` da nossa lista desordenada `<ul></ul>`, fazendo com que os pontos se desloquem no sentido horizontal. Também faremos o nosso `<h2></h2>` parecer estar se acendendo e apagando.

Primeiro, em nosso arquivo CSS, vamos aplicar algumas configurações para todo o documento. Para isso, usaremos o `*`.

```css
* {
    box-sizing: border-box;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
        Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
    list-style: none;
    margin: 0;
    padding: 0;
}
```

Aqui, o tamanho das caixas será definido a partir das bordas (todo o conteúdo e `padding:`, por exemplo, sempre irá se ajustar para a largura e altura definidos para a caixa). Usaremos uma única família de fonte para todo o documento. Como usamos a tag `<li></li>`, que define os itens de uma lista, estou usando o `list-style: none;` para retirar os pontinhos que antecedem cada item (eu também pode aplicar essa propriedade para a tag `<li></li>`). A `margin:`e `padding:` terão valor zero.

Centralizando os itens na tela:

```css
body {
    align-items: center;
    background-color: #210124;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

Usando as três propriedades `align-items: center; display: flex; justify-content: center;`, estarei deixando os itens centralizados nos eixos horizontal e vertical. Para deixá-los centralizados no eixo vertical, temos que definir a altura, que deixei em 100vh (Viewport Height). Quer dizer que ele tem a altura da tela, e os itens irão se ajustar aos diversos tamanhos de tela. Agora, nossos itens ainda estão ocupando uma mesma linha. Então, usamos o `flex-direction: column;`, para que eles voltem a ficar em colunas. Também apliquei uma cor de fundo `background-color: #210124;`.

Para os itens da nossa lista ficarem lado a lado, usaremos o `display: flex;` na tag `<ul></ul>`.

```css
ul {
    display: flex;
    font-size: 20vh;
}
```

Agora, vamos estilizar cada item da lista, e aplicar uma animação `animation: slide 2.5s linear infinite;`. Nosso quadro-chave se chama slide, a animação dura 2 segundos e meio, e ocorre de maneira linear e infinita (quando a animação acaba, ela retorna ao ponto inicial). Vamos aplicar uma cor para o texto `color: #750d37;` e um espaço entre cada caractere `letter-spacing: 20px;`.

```css
li {
    animation: slide 2.5s linear infinite;
    color: #750d37;
    letter-spacing: 20px;
}
```

Agora vamos cuidar da nossa, animação, definindo os `@keyframes`.

```css
@keyframes slide {
    0% {
        color: #750d37;
        letter-spacing: 20px;
    }
    50% {
        letter-spacing: -50px;
    }
    75% {
        color: #f77f00;
        letter-spacing: 50px;
    }
    100% {
        color: #19535f;
        letter-spacing: 20px;
    }
}
```

Em cada momento da animação, alteramos o espaçamento entre os caracteres `letter-spacing:` e sua cor `color:`. Agora, todos os pontinhos estão se movendo de forma uniforme. Vamos atrasar em 0.2 segundos cada elemento `<li></li>`, usando o `animation-delay:`. Para nos referirmos apenas a um item da lista por vez, usaremos o `:nth-child()`: para nos referimos ao primeiro item, usamos `:nth-child(1)`; o segundo, `:nth-child(2)`, e assim por diante, até o `:nth-child(10)`.

```css
li:nth-child(1) {
    animation-delay: 0s;
}

li:nth-child(2) {
    animation-delay: 0.2s;
}

li:nth-child(3) {
    animation-delay: 0.4s;
}

li:nth-child(4) {
    animation-delay: 0.6s;
}
```

Agora, vamos animar o nosso texto `<h2>carregando...</h2>`. Estilizando nosso elemento:

```css
h2 {
    animation: load 2s linear infinite;
    color: #750d37;
    margin-bottom: 20vh;
}
```

Nossa animação tem quadro-chave de nome `load`, com duração de 2 segundos, e ocorre de forma linear e infinita (quando a animação termina, ela retorna ao seu ponto inicial). Agora, vamos definir os `@keyframes`, apenas modificando sua transparência `opacity:`, que começa em 0 (totalmente transparente) e vai até 1 (totalmente opaca).

```css
@keyframes load {
    0% {
        color: #750d37;
        opacity: 0;
    }
    100% {
        opacity: 1;
    }
}
```
