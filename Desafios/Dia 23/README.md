# Dia 23 - Texto com Efeito de Máquina de Escrever

![Texto com Efeito de Máquina de Escrever](./captured.gif?raw=true "Texto com Efeito de Máquina de Escrever")

-   [Codepen](https://codepen.io/lizvidotti91/pen/LYNKrge);
- Para esse desafio, usei como referência o desafio do [BrunoSSantana](https://github.com/BrunoSSantana/30diasDeCSS).

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp);
-   [CSS Animation-Timing Function](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-timing-function);
-   [CSS Overflow](https://www.w3schools.com/css/css_overflow.asp);
-   [CSS White-Space Property](https://www.w3schools.com/cssref/pr_text_white-space.asp);


## Passo a passo

Em nosso arquivo HTML, vamos usar uma `<div><div>` principal, que guarda o texto que iremos animar.

```html
<div>Baiano não nasce, baiano estreia!</div>
```

No arquivo CSS, vamos aplicar algumas configurações comuns a todos os elementos. Para isso, usarei o `*`. O tamanho das caixas será medido a partir das bordas (por padrão, essa medida é dada a partir do conteúdo da caixa; então, ao aplicar o preenchimento `padding:`, por exemplo, o tamanho final da caixa é alterado dependendo do tamanho da caixa. Ao usarmos as medidas a partir das bordas, seu tamanho não muda. O preenchimento deve se adequar ao tamanho definido para o elemento). A fonte utilizada em todo o documento é `font-family: monospace;`, e os valores de `margin:`e `padding:` serão iguais a zero.

```css
* {
    box-sizing: border-box;
    font-family: monospace;
    margin: 0;
    padding: 0;
}
```

Centralizando o documento na tela. Para centralizar os elementos nos sentidos horizontal e vertical, vamos usar as três propriedades juntas `align-items: center; display: flex; justify-content: center;`. Para garantir que o conteúdo se ajuste no sentido vertical, vou definir uma altura para o corpo `height: 100vh;`. A unidade de medida vh (Viewport Height), se refere à altura da tela. Como tenho ainda, em meu projeto, cabeçalho e rodapé, verei estes três itens (cabeçalho, conteúdo e rodapé) em uma única linha. Utilizei o `flex-direction: column;` para deixar o conteúdo novamente em colunas. Por fim, vamos aplicar uma cor de fundo `background-color: #283618;`. Aqui, a cor é aplicada com seu código hexadecimal.

```css
body {
    align-items: center;
    background-color: #283618;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

Agora, vamos estilizar a `<div></div>` principal. Vamos definir cor, tamanho e espessura da fonte `color: #bc6c25; font-size: 50px; font-weight: bolder;`; como estou definindo cabeçalho e rodapé, dei uma margem entre os elementos aplicando em `margin: 20vh 0;`; o primeiro valor se refere às margens superior e inferior, e, o segundo valor, às margens esquerda e direita.

Nesse primeiro momento, vamos deixar o conteúdo invisível na tela, e fazer uma animação em que cada letra apareça gradativamente, como se estivéssemos digitando ao vivo. Vamos começar definindo uma largura para a caixa `width: 0vw;`. Agora o conteúdo da caixa continua aparecendo, pois ele extrapola o tamanho da caixa que o envolve. Para deixá-lo invisível, vamos usar `overflow: hidden;`, e para deixá-lo em uma única linha, vamos usar `white-space: nowrap;`. Assim, quando o tamanho da caixa for aumentando, o conteúdo estará sempre ajustado em linha única, ao invés de quebrar linha.

Para a animação, vamos fazer com que o tamanho da caixa aumente gradativamente, como se estivéssemos digitando, vamos usar `animation: type 5s steps(30) infinite normal`; o número dentro dos parênteses, em steps(), representa o número de paradas que ele deve fazer; esse número é ajustado conforme a quantidade de caracteres do seu texto. O quadro-chave da animação é o "type", a animação tem duração de 5 segundos, e ocorre de maneira infinita e linear.

Agora, para criar um cursor, que fica piscando na tela, vou aplicar outra animação, com duração menor que a primeira. Repare que separo as animações por vírgula. `animation: type 5s steps(30) infinite normal, pisc 0.2s infinite normal;`. A segunda animação tem quadro-chave de nome "pisc", com duração de 0.2 segundos, e ocorre de maneira linear e infinita.

Vou atrasar um pouco o início da animação em `animation-delay: 0.5s;`, e vou fazer com que ela, ao terminar, recomece de seu ponto final, como se estivéssemos escrevendo e depois apagando o texto. Para isso, vamos usar `animation-direction: alternate;`.

```css
div {
    animation: type 5s steps(30) infinite normal, pisc 0.2s infinite normal;
    animation-delay: 0.5s;
    animation-direction: alternate;
    color: #bc6c25;
    font-size: 50px;
    font-weight: bolder;
    margin: 20vh 0;
    overflow: hidden;
    width: 0vw;
    white-space: nowrap;
}
```

Agora, vamos definir os quadros-chave. A primeira animação, "type", altera o tamanho da nossa `<div></div>`.

```css
@keyframes type {
    0% {
        width: 0vw;
    }

    100% {
        width: 950px;
    }
}
```

A segunda, "pisc", ddeixa a impressão que temos um cursor piscando na tela, à medida que escrevemos.

```css
@keyframes pisc {
    0% {
        border-right: 5px solid #bc6c25;
    }

    100% {
        border-right: none;
    }
}
```