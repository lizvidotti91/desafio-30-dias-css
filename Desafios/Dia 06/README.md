# Dia 06 - Efeito Lightning Text

![Efeito Lightning Text](./resiliencia.gif?raw=true "Efeito Lightning Text")

-   [Codepen](https://codepen.io/lizvidotti91/pen/KKzRMee);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS Text-shadow](https://www.w3schools.com/cssref/css3_pr_text-shadow.asp);
-   [CSS :nth-child()](https://www.w3schools.com/cssref/sel_nth-child.asp);
-   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp);

## Passo a passo

No arquivo HTML, usaremos uma tag `<article></article`, com o conteúdo que iremos animar. Repare que, ao invés de escrever a palavra inteira, coloquei cada letra em um `<span></span>`. Assim, poderei animar cada letra separadamente, criando o efeito das luzes se acendendo de cada vez.

```html
<article>
    <span>R</span>
    <span>E</span>
    <span>S</span>
    <span>I</span>
    <span>L</span>
    <span>I</span>
    <span>Ê</span>
    <span>N</span>
    <span>C</span>
    <span>I</span>
    <span>A</span>
</article>
```

Em nosso arquivo CSS, vamos usar o reset do CSS. O símbolo `*` quer dizer que estou aplicando a todos os elementos do meu conteúdo HTML:

```css
* {
    box-sizing: border-box;
    font-family: "Roboto", sans-serif;
    margin: 0;
    padding: 0;
}
```

Para centralizar todo o conteúdo do HTML na tela, vamos usar o trio `align-items: center; display: flex; justify-content: center;`. Como o `display: flex` deixa todo o conteúdo em uma única linha, e queremos que o conteúdo fique em colunas, usamos o `flex-direction: column`. É importante também definir uma altura para o corpo da página, que deixei em `height: 100vh;`, ou seja, que ele ocupe toda a altura da tela. Isso faz com que ele se ajuste para diversos tamanhos de tela.

```css
body {
    align-items: center;
    background-color: #081c15;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

Agora, vamos focar na construção da animação. Primeiro, estarei estilizando cada elemento `<span></span>`, onde estão cada uma das letras. Será nessa tag que eu também estou definindo a animação, com quadr-chave de nome `animate`, com duração de 1.1 segundos, de forma linear e infinita, criando o looping.

```css
span {
    animation: animate 1.1s linear infinite;
    color: #1b4332;
    font-family: Arial;
    font-size: 20vh;
}
```

Na definição do meu quadro-chave, estou dividindo a minha animação em três momentos: ela terá cor `color: #1b4332;` e não terá sombra no texto `text-shadow: none;`; então, mudará de cor `color: #d8f3dc;` e passará a ter sombra no texto `text-shadow: 0px 0px 20px #d8f3dc;`. O primeiro valor do `text-shadow` quer dizer que a sombra se desloca para baixo; o segundo valor, para a direita; o terceiro valor é o seu desfoque (quanto maior o valor, maior será o seu desfoque); por último, a cor da sombra. Optei por usar a mesma cor da letra, com um desfoque alto, para dar a impressão que ela está acendendo.

```css
@keyframes animate {
    0% {
        color: #1b4332;
        text-shadow: none;
    }
    90% {
        color: #1b4332;
        text-shadow: none;
    }
    100% {
        color: #d8f3dc;
        text-shadow: 0px 0px 20px #d8f3dc;
    }
}
```

Ok. Mas, até este momento, todas as nossas letras acendem e apagam ao mesmo tempo. Para cada letra se acender em um momento diferente, teremos que usar a propriedade `animation-delay:`, que define um tempo de atraso para que a animação comece. Para que eu possa aplicar tempos diferentes em cada `<span></span>`, usarei o seletor `:nth-child()`. Na estrutura HTML, a tag `<article></article>` contém 11 elementos `<span></span>`, ou 11 filhos. A ordem de descendência acompanha a ordem nos elementos no documento. Assim, quando digo `span:nth-child(5)`, estou me referindo ao quinto elemento, na ordem de apresentação do HTML.

```css
span:nth-child(1) {
    animation-delay: 0s;
}

span:nth-child(2) {
    animation-delay: 0.1s;
}

span:nth-child(3) {
    animation-delay: 0.2s;
}
```

Para cada elemento, estou dando um atraso de 0.1 segundos entre cada uma. Fazendo isso para cada elemento, até o `span:nth-child(11)`, teremos a animação final.
