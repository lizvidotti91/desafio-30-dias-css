# Dia 01 - Ícones de mídias sociais em camadas

-   [Codepen](https://codepen.io/lizvidotti91/pen/JjXMLvE);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS :nth-child()](https://www.w3schools.com/cssref/sel_nth-child.asp);
-   [CSS Positions](https://www.w3schools.com/css/css_positioning.asp);
-   [CSS Transitions](https://www.w3schools.com/cssref/css3_pr_transform.asp);
-   [CSS Hover](https://www.w3schools.com/cssref/sel_hover.asp);
-   [CSS Opacity](https://www.w3schools.com/css/css_image_transparency.asp);

## Passo a passo

No HTML, temos que organizar da seguinte maneira: dentro da tag `<body></body>`, inserimos uma lista sem ordenação, a `<ul></ul>`. Cada item na lista, o `<li></li>`, recebe a seguinte estrutura:

```html
<li>
    <a href="#" class="facebook">
        <span class="facebook"></span>
        <span class="facebook"></span>
        <span class="facebook"></span>
        <span class="facebook"></span>
        <span class="fab fa-facebook-f facebook"></span>
    </a>
</li>
```

Cada `<span></span>` será uma camada que iremos animar, e eles não terão conteúdo! Apenas o 5º elemento irá receber o ícone de determinada mídia social.

No arquivo .css, a primeira coisa que iremos fazer será o reset do CSS, deixando na seguinte estrutura:

```css
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
```

Na configuração da `<ul></ul>` e dos `<li></li>`, teremos que a posição destes elementos será `position: relative`, que quer dizer que eles estarão posicionados em relação à sua posição normal. O elemento `<li></li>` receberá o `transform: rotate(-30deg) skew(30deg);`. A `transform:` aplica uma transformação 2D ou 3D a um elemento. O `rotate(-30deg)` define que o elemento irá rotacionar no eixo (x,y) e o `skew(30deg)` define uma transformação de inclinação 2D ao longo do eixo (x,y).

```css
ul {
    align-items: center;
    display: flex;
    height: 100vh;
    justify-content: center;
    position: relative;
}
ul li {
    height: 3vw;
    list-style-type: none;
    margin-right: 5vw;
    position: relative;
    transform: rotate(-30deg) skew(30deg);
    width: 3vw;
}
```

Já as tags `<span></span>` terão `position: absolute`, que quer dizer que elas estarão posicionadas em relação ao elemento-pai (no caso, a tag `<li></li>`).

```css
ul li span {
    align-items: center;
    color: #f5f5f5;
    display: flex !important;
    font-size: 2vw !important;
    height: 100%;
    justify-content: center;
    left: 0;
    position: absolute;
    top: 0;
    transition: 0.3s;
    width: 100%;
}
```

Aí, eu terei todos os `<span></span>` posicionados um sobre o outro, onde o 5º elemento está acima de todos, e o primeiro elemento, está abaixo de todos os elementos. Agora, é onde a mágica acontece! Quando eu passar o mouse sobre o elemento, o chamado `:hover`, cada `<span></span>` irá deslizar nos eixos x e y, graças ao `transform: translate()`. Assim:

```css
ul li:hover span:nth-child(5) {
    transform: translate(5vw, -5vw);
}
ul li:hover span:nth-child(4) {
    opacity: 0.5;
    transform: translate(4vw, -4vw);
}
ul li:hover span:nth-child(3) {
    opacity: 0.4;
    transform: translate(3vw, -3vw);
}
ul li:hover span:nth-child(2) {
    opacity: 0.3;
    transform: translate(2vw, -2vw);
}
ul li:hover span:nth-child(1) {
    opacity: 0.2;
    transform: translate(1vw, -1vw);
}
```

O que quero dizer aí, é que quando o mouse passar sobre o elemento `<li></li>` `li:hover`, cada elemento `<span></span>` irá se comportar de uma forma. Aí que entra o `span:nth-child()`: essa propriedade :nht-child quer dizer que estou me referenciando a um elemento filho específico. Mas, o que são elementos pai e filho? Na estrutura HTML, temos o `<li></li>`, que contém quatro elementos `<span></span>`. Quer dizer que ele é pai de cada elemento `<span></span>`. A ordem em que eles estão dispostos na estrutura HTML, é a ordem de descendência (Filho 1, filho 2...). Assim, quando escrevo `li:hover span:nth-child(1)`, estou querendo dizer que, quando o mouse passar sobre o elemento `<li></li>`, estarei passando as propriedades de seu primeiro filho.

Como todos os elementos `<span></span>` têm a mesma cor de fundo `span.facebook {background-color: #3b5998;}`, apliquei um valor específico de transparência `opacity: 0.2`, para dar o efeito do degradê.
