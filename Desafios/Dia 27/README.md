# Dia 27 - Chamada Celular

![Chamada Celular](./captured.gif?raw=true "Chamada Celular")

*   [Codepen](https://codepen.io/lizvidotti91/pen/gOMMydx?editors=1100); 

## Tecnologias Usadas

*   HTML
*   CSS

## O que eu aprendi

*   [CSS :hover Selector](https://www.w3schools.com/cssref/sel_hover.asp); 
*   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp); 
*   [CSS Positions](https://www.w3schools.com/css/css_positioning.asp); 
*   [CSS Pseudo-Elements](https://www.w3schools.com/css/css_pseudo_elements.asp); 
*   [CSS Transform](https://www.w3schools.com/cssref/css3_pr_transform.asp); 

## Passo a passo

Para a construção da tela do celular, temos o seguinte código HTML:

``` html
<div class="phone">
    <div class="screen">
        <div class="call">
            <h2>chamada recebida</h2>
            <h3><i class="fas fa-user"></i></h3>
            <h4>Mamãe</h4>
            <h5>+55 99 99999-9999</h5>
        </div>
        <div class="container">
            <div class="yes"><i class="fas fa-phone-alt"></i></div>
            <div class="no"><i class="fas fa-phone-slash"></i></div>
        </div>
    </div>
</div>
```

No arquivo CSS, vamos começar aplicando algumas propriedades comuns à todos os elementos. Para isso, vamos usar o `*` .

``` css

* {

    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
```

Vamos aplicar uma cor de fundo para o corpo do projeto, e definir sua altura. Vamos deixar também sua posição relativa.

`

``` css
body {
    background-color: #363535;
    height: 100vh;
    position: relative;
}

`
```

Vamos começar a desenhar o corpo do nosso celular. Primeiro, vamos definir altura, largura e cor de fundo `height: 70vh; width: 40vh; background-color: black;` . Para deixar as bordas do celular arredondadas, vamos aplicar o `border-radius: 5vh;` ; para definição de sua sombra, `box-shadow: 10px 10px 5px #181717;` , onde o primeiro valor define o quanto a sombra se desloca para baixo; o segundo valor, a sombra se desloca para a direita; o terceiro valor serve para dar desfoque à sombra; quando mais alto o valor, maior será o seu desfoque; o último valor é a cor da sombra. Vamos posicionar o elemento no meio da tela; para isso, usei o `position: absolute;` e fixei o elemento nas margens esquerda e superior: `left: 50vw; top: 50vh;` . Repare na unidade de medida que usei: vh (Viewport Height) e vw (Viewport Width), que se referem, respectivamente, à altura e à largura da tela. Para garantir que o elemento fique centralizado nos eixos X e Y, vamos aplicar `transform: translate(-50%, -50%);` . Por fim, para que todo o conteúdo da nossa `<div></div>` fique centralizado, vamos usar as três propriedades `align-items: center; display: flex; justify-content: center;` .

``` css
div.phone {
    align-items: center;
    background-color: black;
    border-radius: 5vh;
    box-shadow: 10px 10px 5px #181717;
    display: flex;
    height: 70vh;
    justify-content: center;
    left: 50vw;
    position: absolute;
    top: 50vh;
    transform: translate(-50%, -50%);
    width: 40vh;
}
```

Agora vamos desenhar a tela do nosso celular. Vamos começar definindo altura e largura da caixa `height: 55vh; width: 35vh;` e cor de fundo `background-color: whitesmoke;` . Para a sombra da tela, vamos inverter a sombra, deixando-a para dentro do elemento, usando o atributo `inset` : `box-shadow: 0px 0px 10px #080808 inset;` .

``` css
div.phone div.screen {
    background-color: whitesmoke;
    box-shadow: 0px 0px 10px #080808 inset;
    height: 55vh;
    width: 35vh;
}
```

Para a parte da tela em que está escrito o nome e número do contato, vamos definir as propriedades:

``` css
div.phone div.screen div.call {
    background-color: #1f741f;
    color: whitesmoke;
    font-family: Arial;
    height: 30vh;
    position: relative;
    width: 100%;
}
```

Vamos definir altura e largura `height: 30vh; width: 100%;` . Repare que, para a largura, usei a unidade de medida `%` ; estou querendo dizer que este elemento tem mesma medida do elemento-pai (no caso, a `<div class="screen"></div>` ). Definição da cor do elemento em `background-color: #1f741f;` e cor e fonte do texto `color: whitesmoke; font-family: Arial;` .

Definindo os textos dentro da nossa `<div class="call"></div>` :

``` css
div.phone div.screen div.call h2 {
    font-size: 2vh;
    left: 1vh;
    position: absolute;
    top: 1vh;
}

div.phone div.screen div.call h3 {
    font-size: 10vh;
    left: 50%;
    position: absolute;
    top: 5vh;
    transform: translateX(-50%);
}

div.phone div.screen div.call h4 {
    font-size: 3vh;
    left: 50%;
    position: absolute;
    top: 18vh;
    transform: translateX(-50%);
}

div.phone div.screen div.call h5 {
    font-size: 2vh;
    left: 50%;
    position: absolute;
    top: 22vh;
    transform: translateX(-50%);
}
```

Cada título tem tamanho de fonte diferentes, definindos em `font-size:` ; todos terão posição absoluta `position: absolute;` e serão fixados nas margens esquerda e superior `left:` e `top:` . Para centralizar os textos no sentido horizontal, usei o `transform: translateX(-50%);` .

Para a definição da caixa que envolve os botões de atender e recusar chamadas, teremos as seguintes configurações. Primeiro, definimos a largura do elemento em `width: 35vh;` e aplicamos o `display: flex;` para deixar os botões lado a lado. Para espaçá-los igualmente nesse espaço de 35vh, usaremos `justify-content: space-around;` . Deixaremos sua posição `position: absolute;` e fixaremos na margem superior `top: 45vh;` .

``` css
div.phone div.screen div.container {
    display: flex;
    justify-content: space-around;
    position: absolute;
    top: 45vh;
    width: 35vh;
}
```

Para a definição dos botões, teremos muitas estilizações comuns, sendo diferente apenas a cor do botão. Para deixar o botão circular, definimos mesma altura e largura, e deixamos as bordas arredondadas `height: 10vh; width: 10vh; border-radius: 50%;` . A cor e tamanho do ícone é definida em `color: whitesmoke; font-size: 5vh;` . Para que o ícone fique centralizado no botão, usaremos as três propriedades `align-items: center; display: flex; justify-content: center;` . Deixamos a posição relativa `position: relative;` , pois iremos desenhar novos círculos sobre o botão de atender a chamada. Vamos também aplicar o `:hover` , que é quando o mouse passa sobre o botão, para modificarmos a cor do elemento. Para deixar essa transição mais fluida, aplicaremos o `transition: 0.3s;` . E, para mudar o cursor do mouse da setinha para a mãozinha, quando passamos o mouse sobre o elemento, vamos usar o `cursor: pointer;` . Em cada botão, aplicamos cores diferentes `div.yes{background-color: #1f741f;}` e `div.no{background-color: #da0b0b;}` .

``` css
div.phone div.screen div.container div.yes,
div.phone div.screen div.container div.no {
    align-items: center;
    border-radius: 50%;
    color: whitesmoke;
    cursor: pointer;
    display: flex;
    font-size: 5vh;
    height: 10vh;
    justify-content: center;
    position: relative;
    transition: 0.3s;
    width: 10vh;
}

div.phone div.screen div.container div.yes {
    background-color: #1f741f;
}

div.phone div.screen div.container div.no {
    background-color: #da0b0b;
}
```

Agora, ao passarmos o mouse sobre o botão, vamos alterar a opacidade, ou transparência, do botão.

``` css
div.phone div.screen div.container div.yes:hover,
div.phone div.screen div.container div.no:hover {
    opacity: 0.8;
}
```

Agora, vamos desenhar dois pseudo-elementos, antes e depois do nosso botão de atender chamada. Eles terão as mesmas estilizações: terão altura e largura iguais ao do botão `height: 10vh; width: 10vh;` , com a borda arredondada `border-radius: 50%;` , sem conteúdo `content: "";` , com posição absoluta `position: absolute;` . Não definiremos cor de fundo, apenas borda `border: 1px solid #1f741f;` ; o primeiro valor será a espessura da linha, o segundo valor, o estilo da linha, e, por último, sua cor. Para o efeito pulsar, vamos aplicar uma animação ` animation: pulse 1.5s linear infinite;` ; a animação tem quadro-chave de nome `pulse` , com duração de 1.5 segundos, e ocorre de forma linear e infinita.

``` css
div.phone div.screen div.container div.yes::after,
div.phone div.screen div.container div.yes::before {
    animation: pulse 1.5s linear infinite;
    border: 1px solid #1f741f;
    border-radius: 50%;
    content: "";
    height: 10vh;
    position: absolute;
    width: 10vh;
}
```

Na definição dos `@keyframes` , vamos alterar o tamanho e opacidade dos círculos; eles aumentam de tamanho, e passam de totalmente opacos para totalmente transparente.

``` css
@keyframes pulse {
    0% {
        opacity: 1;
        transform: scale(1);
    }

    100% {
        opacity: 0;
        transform: scale(1.5);
    }
}
```

Por último, vamos atrasar o início da animação de um dos pseudo-elementos, para que as linhas fiquem aparecendo gradualmente.

``` css
div.phone div.screen div.container div.yes::before {
    animation-delay: 0.5s;
}
```
