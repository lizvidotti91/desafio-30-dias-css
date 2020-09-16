# Dia 11 - Botão com Efeito Hover

![Botão com Efeito Hover](./botao.gif?raw=true "Botão com Efeito Hover")

-   [Codepen](https://codepen.io/lizvidotti91/pen/qBZywZz);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS Psdeudo-Elements](https://www.w3schools.com/css/css_pseudo_elements.asp);
-   [CSS ::after Selector](https://www.w3schools.com/cssref/sel_after.asp);
-   [CSS ::before Selector](https://www.w3schools.com/cssref/sel_before.asp);
-   [CSS Text-transform Propoerty](https://www.w3schools.com/cssref/pr_text_text-transform.asp);
-   [CSS :hover Selector](https://www.w3schools.com/cssref/sel_hover.asp);
-   [CSS z-index Property](https://www.w3schools.com/cssref/pr_pos_z-index.asp);

## Passo a passo

Na minha estrutura HTML, fiz vários botões, para aplicar cores diferentes em cada botão. Então, a estrutura ficou assim.

```html
<div class="container">
    <button class="search"><span class="fas fa-search"></span> search</button>
    <button class="setting"><span class="fas fa-cogs"></span> setting</button>
    <button class="menu"><span class="fas fa-bars"></span> menu</button>
    <button class="chat"><span class="far fa-comment-dots"></span> chat</button>
    <button class="message">
        <span class="far fa-envelope"></span> message
    </button>
</div>
```

Dentro de cada elemento `<button></button>`, tenho um elemento `<span></span>`, que recebem o conteúdo do ícone, ao lado do texto de cada botão. Para usar os mesmos botões que usei, visite o site do [Font Awesome](https://fontawesome.com/icons?m=free) e crie sua conta grátis. Existem muitos ícones legais por lá!

Para o arquivo CSS, vamos começar com o reset CSS. Vamos deixar o tamanho das caixas a partir das bordas do elemento (se eu aplicar paddings, por exemplo, eles vão se ajustar ao tamanho de largura e altura que eu defini para ele); aplicar uma fonte padrão para todo o documento, `margin:` e `padding:` no valor zero. O `*` serve para que eu aplique essas propriedades em todo o documento.

```css
* {
    box-sizing: border-box;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    margin: 0;
    padding: 0;
}
```

Agora, vamos centralizar o conteúdo em nossa tela. Usaremos o trio `align-items: center; display: flex; justify-content: center;`. Para que o conteúdo fique em colunas, vamos aplicar `flex-direction: column;` e uma altura, que deixarei no tamanho da tela `height: 100vh`. A unidade de medida vh (Viewport Height) faz com que o conteúdo se ajuste aos diversos tamanhos de tela. Por último, vou aplicar uma cor de fundo.

```css
body {
    align-items: center;
    background-color: #233329;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

Para a configuração dos botões, vamos aplicar uma configuração geral, e aplicar as cores para os diferentes botões. Para deixar o botão com bordas arredondadas, usei o `border-radius: 10px`. Não vou deixar o botão com o fundo branco, padrão, então usei o `background: none;`; passando o mouse sobre o botão, para mudar o cursor da setinha para a mãozinha, usei o `cursor: pointer`. Estou separando os botões uns dos outros através do `margin: 0 1vw;`, onde o primeiro valor define as margens superior e inferior e o segundo valor, as margens direita e esquerda. Aumentei a largura do botão com o `padding-right: 3vw;`, deixo a posição do elemento `position: relative`, para que eu possa desenhar um peseudo-elemento depois. Para deixar todo o texto HTML em caixa alta, é só aplicar o `text-transform: uppercase`. Para aplicar o `:hover` no botão, e deixar a transição mais fluida, vamos aplicar o `transition: 0.9s`. Mudando esses valores, você terá transições mais lentas ou mais rápidas. Por último, apliquei o `overflow: hidden;`, para que meu pseudo-elemento não apareça enquanto eu não passe o mouse sobre o botão.

```css
button {
    border-radius: 10px;
    background: none;
    cursor: pointer;
    font-size: 20px;
    margin: 0 1vw;
    padding-right: 3vw;
    overflow: hidden;
    position: relative;
    text-transform: uppercase;
    transition: 0.9s;
}
```

Agora, vamos definir as cores das bordas e dos textos, para cada botão. Para isso, vamos usar o nome da classe de cada botão. No CSS, a classe é selecionada com `.nomeDaClasse`.

```css
button.search {
    border: 1px solid #d62246;
    color: #d62246;
}

button.setting {
    border: 1px solid #fca311;
    color: #fca311;
}

button.menu {
    border: 1px solid #006d77;
    color: #006d77;
}

button.chat {
    border: 1px solid #06d6a0;
    color: #06d6a0;
}

button.message {
    border: 1px solid #f20089;
    color: #f20089;
}
```

Quando passar o mouse sobre o botão, mudarei a cor das letras para branco. Para isso, vou aplicar o `button:hover`.

```css
button:hover {
    color: #d4f4dd;
}
```

Agora, vamos desenhar o pseudo-elemento `::hover`, que desenha um elemento antes do elemento-pai; no caso, o `<button></button>`. Esse novo elemento não terá conteúdo `content: " ";`, terá altura igual ao elemento-pai `height: 100%` e não terá uma largura definida nesse primeiro momento `width: 0%;`. É importante usar o `position:absolute;`, e ele ficará acima do elemento-pai; porém, eu não quero que o elemento cubra o meu botão, então usei `z-index: -1;`, para que o pseudo-elemento fiquei por baixo do botão. Então, fixei o elemento no topo e à esquerda `left: 0; top: 0;`, e arredondei as bordas superior e inferior direita `border-radius: 0% 60% 60% 0%;`. Para a animação, quando vou aplicar o `:hover` no pseudo-elemento, deixarei o `transition:` igual o `<button></button>`.

```css
button::before {
    content: "";
    border-radius: 0% 60% 60% 0%;
    height: 100%;
    left: 0;
    position: absolute;
    top: 0;
    transition: 0.9s;
    width: 0%;
    z-index: -1;
}
```

Agora, vou aplicar uma cor diferente para cada botão. Estou usando as mesmas cores da borda do botão. Novamente, estou estilizando cada elemento pelo seu nome da classe.

```css
button.search::before {
    background-color: #d62246;
}

button.setting::before {
    background-color: #fca311;
}

button.menu::before {
    background-color: #006d77;
}

button.chat::before {
    background-color: #06d6a0;
}

button.message::before {
    background-color: #f20089;
}
```

Agora, quando passar o mouse sobre o botão, quero que o meu pseudo-elemento aumente sua largura em 190%. O que vai deixar essa transição gradual será o `transition: 0.9s` que apliquei no `button:hover`.

```css
button:hover::before {
    width: 190%;
}
```

Aqui, estou estilizando o `<span></span>`, onde estão os ícones dos botões. Aplicando o `padding: 20px;` para afastar o ícones das bordas superior, inferior, esquerda e direita da caixa. Para dar um espaço entre a caixa e o texto, usei o `margin-right: 5px`. Por último, apliquei uma cor para o ícone `color: #d4f4dd`.

```css
span {
    color: #d4f4dd;
    margin-right: 5px;
    padding: 20px;
}
```

E, para cada botão, deixarei a cor de fundo do `<span></span>` igual a cor da borda de cada botão.

```css
button.search span {
    background-color: #d62246;
}

button.setting span {
    background-color: #fca311;
}

button.menu span {
    background-color: #006d77;
}

button.chat span {
    background-color: #06d6a0;
}

button.message span {
    background-color: #f20089;
}
```
