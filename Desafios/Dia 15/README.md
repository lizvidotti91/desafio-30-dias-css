# Dia 15 - Texto Flutuante

![Texto Flutuante](./flutua.gif?raw=true "Texto Flutuante")

-   [Codepen](https://codepen.io/lizvidotti91/pen/poyQdbM);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS Text-Shadow](https://www.w3schools.com/cssref/css3_pr_text-shadow.asp);
-   [CSS Animation-Direction](https://www.w3schools.com/cssref/css3_pr_animation-direction.asp);
-   [Cores RBG e RGBA](https://www.w3schools.com/css/css_colors_rgb.asp);
-   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp);

## Passo a passo

No nosso arquivo HTML, vamos aplicar nossa animação na tag `<h2></h2>`:

```html
<h2>Consideramos justa toda forma de amor</h2>
```

Em nosso arquivo CSS, vamos começar aplicando algumas estilizações comuns a todo o documento. Para isso, usaremos o `*`. O tamanho das caixas serão calculados a partir de suas bordas, temos um tipo de fonte comum a todo o projeto, `margin:` e `padding:` iguais a zero.

```css
* {
    box-sizing: border-box;
    font-family: Arial;
    margin: 0;
    padding: 0;
}
```

Centralizando o conteúdo na tela:

```css
body {
    align-items: center;
    background-color: #5e565a;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

As três propriedades juntas `align-items: center; display: flex; justify-content: center;` centralizam o conteúdo nos sentidos horizontal e vertical. Vamos completar aplicando uma altura para o nosso `body`, para deixar o conteúdo centralizado na vertical. Além da tag `<h2></h2>`, estou usando um cabeçalho e rodapé na página. Quando aplico o `display: flex;`, esses três elementos estarão ocupando a mesma linha. Para voltar a deixá-los em coluna, estou usando o `flex-direction: column;`. Por último, apliquei uma cor de fundo `background-color: #5e565a;`.

Agora vamos estilizar nosso texto:

```css
h2 {
    animation: floating 2s linear infinite;
    animation-direction: alternate;
    color: #ff4e00;
    font-size: 8vh;
    letter-spacing: 10px;
    line-height: 15vh;
    margin: 20vh 10vw;
    text-align: center;
    text-shadow: 0px 10px 2px rgba(169, 203, 183, 0.1);
    text-transform: uppercase;
}
```

Para deixar o texto em caixa alta, usei o `text-transform: uppercase;`. Estou separando o texto do meu cabeçalho, rodapé e bordas laterais com uma margem `margin: 20vh 10vw;` (o primeiro valor determina as margens superior e inferior, e o segundo valor, as margens esquerda e direita). Para aumentar o espaço entre as linhas do texto, usei o `line-height: 15vh;`, e para centralizar o texto na tela, o `text-align: center;`. Para separar um pouco a distância entre as letras, estou usando o `letter-spacing: 10px`, e aplicando um tamanho de fonte e cor em `font-size:` e `color:`.

Vamos aplicar uma sombra nas letras usando `text-shadow: 0px 10px 2px rgba(169, 203, 183, 0.1);`. O primeiro valor determina o quanto a sombra se desloca para a direita; o segundo valor, seu deslocamento para baixo; o terceiro valor, o desfoque da sombra. Por último, estou aplicando uma cor RGBA (Red-Green-Blue-Alpha), para dar transparência na cor.

Agora, vamos determinar os quadros-chaves: `animation: floating 2s linear infinite;`. Nossos `@keyframes` se chamam floating, a animação tem duração de 2 segundos, e ocorre de forma linear e infinita.

```css
@keyframes floating {
    0% {
        transform: rotate(-3deg);
    }
    100% {
        transform: rotate(3deg);
    }
}
```

Aqui acontece nossa animação: o texto rotaciona da esquerda para a direita, e volta para a posição inicial. Para deixar a animação de forma mais fluida, apliquei o `animation-direction: alternate;`, que reproduz a animação para a frente e para trás.
