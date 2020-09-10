# Dia 4 - Efeito Pulsar

-   [Codepen](https://codepen.io/lizvidotti91/pen/wvGmQdq);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS Box-shadow](https://www.w3schools.com/cssref/css3_pr_box-shadow.asp);
-   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp);
-   [CSS RGBA()](https://www.w3schools.com/cssref/func_rgba.asp);

## Passo a passo

No arquivo HTML, usaremos uma tag `<button></button`, com o conteúdo do nosso botão.

```html
<header>
    <h1>Desafio #4: Botão com efeito</h1>
</header>
<button>OK</button>
<footer>
    <p>#30DiasDeCSS</p>
    <p>&copy; Liz</p>
</footer>
```

Em nosso arquivo CSS, vamos usar o reset do CSS:

```html
* { box-sizing: border-box; font-family: monospace; margin: 0; padding: 0; }
```

Para centralizar todo o conteúdo do HTML na tela, vamos usar o trio `align-items: center; display: flex; justify-content: center;`. Como o `display: flex` deixa todo o conteúdo em uma única linha, e queremos que o conteúdo fique em colunas, usamos o `flex-direction: column`. É importante também definir uma altura para o corpo da página, que deixei em `height: 100vh;`, ou seja, que ele ocupe toda a altura da tela. Isso faz com que ele se ajuste para diversos tamanhos de tela.

```html
body { align-items: center; background-color: #6d6875; display: flex;
flex-direction: column; height: 100vh; justify-content: center; }
```

Agora, vamos focar na construção do botão.

```html
button { animation: animate 1s linear infinite; background-color: #b5838d;
border: none; border-radius: 50%; color: whitesmoke; cursor: pointer; font-size:
4vw; font-weight: lighter; height: 8vw; width: 8vw; }
```

Essa é uma construção simples. Defini altura e largura `height: 8vw; width: 8vw;`, deixando o botão quadrado. Observe a unidade de medida que usei: vw(Viewport Width), que quer dizer que o tamanho do botão vai se ajustar às diversas larguras de tela. Para deixá-lo redondo, apliquei o `border-radius: 50%;`, e para deixar sem a marcação do contorno, usei o `border: none;`. Apliquei a cor de fundo do botão `background-color: #b5838d;`, a mudança do ícone da seta do mouse para a mão, quando passo o mouse sobre o botão `cursor: pointer;`. Também estilizei o texto, ajustando sua altura, peso da fonte e cor `color: whitesmoke; font-size: 4vw; font-weight: lighter;`.

Para criar o efeito de pulsar, vamos usar a propriedade `animation: animate 1s linear infinite;`. Nosso quadro-chave (keyframe) se chama `animate`, a animação vai durar 1 segundo, e voltará ao início, graças ao `infinite`.

Na definição do nosso `@keyframes`, vamos aplicar a propriedade `box-shadow:`, que adiciona sombras ao nosso elemento `<button></button>`.

```html
@keyframes animate { 0% { box-shadow: none; } 25% { box-shadow: 0px 0px 0px 10px
rgba(181, 131, 141, 1); } 50% { box-shadow: 0px 0px 0px 20px rgba(181, 131, 141,
0.8); } 75% { box-shadow: 0px 0px 0px 30px rgba(181, 131, 141, 0.5); } 100% {
box-shadow: 0px 0px 0px 40px rgba(181, 131, 141, 0.3); } }
```

Vamos entender os valores que são aplicados no `box-shadow: 0px 0px 0px 40px rgba(181, 131, 141, 0.3)`. O primeiro valor desloca a sombra para baixo; o segundo valor, para a direita; o terceiro valor define o desfoque de cor (quanto maior o valor, maior será o seu desfoque); o quarto valor define o raio da sombra; o quinto valor, a cor da sombra. Em todos os momentos da animação, deixei a sombra sem desfoque e fui aumentando o seu raio. Para o efeito de transparência de cor, usei o rgba(), onde temos o sistema de cores RGB (Red, Green, Blue), acrescidos da propriedade de transparência (o A da sigla RGBA quer dizer alpha). A transparência varia de 0 a 1, onde 0 é totalmente transparente e 1, totalmente opaco.

Quando defino `rgba(181, 131, 141, 0.3)`, estou pegando o código RGB(181,131,141) e acrescentando o valor de opacidade, ou transparência (0.3). Então, em 25%, a cor é totalmente opaca `rgba(181, 131, 141, 1)`, e vou diminuindo seu valor até 100% `rgba(181, 131, 141, 0.3)`. Em 0%, o botão não terá sombra `box-shadow: none;`.
