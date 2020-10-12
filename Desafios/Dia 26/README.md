# Dia 25 - Fantasminha

![Fantasminha](./captured.gif?raw=true "Fantasminha")

*   [Codepen](https://codepen.io/lizvidotti91/pen/VwjLOqw?editors=1100); 
*   Para esse desafio, usei como referência o desafio do [BrunoSSantana](https://github.com/BrunoSSantana/30diasDeCSS/tree/master/Challenges/challenge04); 

## Tecnologias Usadas

*   HTML
*   CSS

## O que eu aprendi

*   [CSS :first-child Selector](https://www.w3schools.com/cssref/sel_firstchild.asp); 
*   [CSS :last-child Selector](https://www.w3schools.com/cssref/sel_last-child.asp); 
*   [CSS :nth-child() Selector](https://www.w3schools.com/cssref/sel_nth-child.asp); 
*   [CSS :hover Selector](https://www.w3schools.com/cssref/sel_hover.asp); 
*   [CSS Positions](https://www.w3schools.com/css/css_positioning.asp); 
*   [CSS Transform](https://www.w3schools.com/cssref/css3_pr_transform.asp); 

## Passo a passo

Vamos focar na construção do fantasminha. O arquivo HTML fica da seguinte maneira:

``` html
<div class="fantasma">
    <div class="rosto">
        <div class="olhos">
            <span></span>
            <span></span>
        </div>
        <div class="boca"></div>
    </div>
    <div class="maos">
        <span></span>
        <span></span>
    </div>
    <div class="pes">
        <span></span>
        <span></span>
        <span></span>
        <span></span>
    </div>
</div>
```

No arquivo CSS, vamos centralizar o nosso fantasminha na tela. Para centralizar o elemento na tela, usei as três propriedades juntas: `align-items: center; display: flex; justify-content: center;` , onde nosso elemento vai ficar centralizado nos sentidos horizontal e vertical. Para garantir que o elemento fique centralizado no sentido vertical, vamos aplicar uma altura `height: 100vh;` , onde a unidade de medida vh (Viewport Height), se refere a altura da tela, se ajustando aos diversos tamanhos de tela. Por fim, vamos aplicar uma cor de fundo em `background-color: #e4092e;` .

``` css
body {

    align-items: center;
    background-color: #e4092e;
    display: flex;
    height: 100vh;
    justify-content: center;

}
```

Vamos começar deixando nossa `<div class="fantasma"></div>` com a posição relativa.

``` css
div.fantasma {
    position: relative;
}
```

Agora, vamos estilizar o corpinho do fantasma. Vamos colocar a posição relativa `position: relative;` ; altura e largura `height: 40vh; width: 30vh;` , cor do elemento `background-color: whitesmoke;` . Agora vamos arredondar as bordas superiores e deixar as bordas inferiores retas `border-radius: 20vh 20vh 0 0;` ; o primeiro valor se refere à borda superior esquerda; o segundo valor, à borda superior direita; o terceiro valor, à borda inferior esquerda; o quarto valor, à borda inferior direita. Por fim, para mudar o cursor do mouse da setinha para a mãozinha, quando passarmos o mouse sobre o fantasma, vamos usar o `cursor: pointer;` .

``` css
div.fantasma div.rosto {
    background-color: whitesmoke;
    border-radius: 20vh 20vh 0 0;
    cursor: pointer;
    height: 40vh;
    position: relative;
    width: 30vh;
}
```

Agora, para a construção dos olhos, vamos deixar o `display: flex;` , para que as bolinhas do olhos fiquem lado a lado. Deixaremos a posição absoluta `position: absolute;` , e vamos fixar a `<div></div>` nas margens superior e esquerda `top: 8vh; left: 15vh;` . Para deixar o elemento centralizado na horizontal, vamos aplicar o `transform: translateX(-50%);` . Para deixar as bolinhas dos olhos separadas uma da outra, vamos aplicar uma largura para nossa `<div></div>` , `width: 15vh` . Agora, vamos fixar as bolinhas dos olhos nas extremidades deste elemento em `justify-content: space-between;` .

``` css
div.fantasma div.rosto div.olhos {
    display: flex;
    justify-content: space-between;
    left: 15vh;
    position: absolute;
    top: 8vh;
    transform: translateX(-50%);
    width: 15vh;
}
```

Agora, vamos desenhar as bolinhas, estilizando os elementos `<span></span>` . Vamos começar definindo altura e largura `height: 5vh; width: 5vh;` , e cor do elemento `background-color: #e4092e;` . Para deixar o quadrado na forma circular, vamos aplicar o `border-radius: 50%;` . Quando passarmos o mouse sobre o fantasma, seus olhos irão mudar de tamanho. Para deixar essa transição mais fluida, vamos aplicar o `transition: 0.3s;` . Quanto maior esse valor, mais lenta será sua transição.

``` css
div.fantasma div.rosto div.olhos span {
    background-color: #e4092e;
    border-radius: 50%;
    height: 5vh;
    transition: 0.3s;
    width: 5vh;
}
```

Agora, vamos fazer a modificação dos olhos, quando o mouse passa sobre o fantasma. Para isso, utilizarei o seletor `:hover` , que se refere ao evento do mouse quando passa sobre um elemento. Vamos apenas modificar a altura e largura dos elementos `<span></span>` .

``` css
div.fantasma:hover div.rosto div.olhos span {
    height: 6vh;
    width: 4vh;
}
```

Você dá deve ver os olhinhos do fantasma mudando, agora.

Vamos estilizar a boca do fantasma. Vamos começar definindo altura e largura `height: 5vh; width: 10vh;` . Vamos aplicar uma cor para o elemento em `background-color: #e4092e;` . Agora, para fazermos a curva da boca sorrindo, vamos arredondar as boras inferiores, em `border-radius: 0 0 5vh 5vh;` ; o primeiro valor se refere à borda superior esquerda; segundo valor, à borda superior direita; terceiro valor, à borda inferior esquerda; quarto valor, à borda inferior direita. Agora, vamos deixar a posição da boca absoluta `position: absolute;` , e fixar o elemento das margens superior e esquerda do corpo do fantasma `top: 15vh; left: 15vh;` . Para centralizar a boca no sentido horizontal, vamos usar `transform: translateX(-50%);` .

Quando o mouse passar sobre o fantasma, vamos modificar a boca também. Vamos usar o mesmo esquema do `:hover` , que usamos para os olhos. Então, para deixar a transição mais fluida, vamos usar `transition: 0.3s;` . Quanto maior o valor, mais lenta será a transição.

``` css
div.fantasma div.rosto div.boca {
    background-color: #e4092e;
    border-radius: 0 0 5vh 5vh;
    left: 15vh;
    height: 5vh;
    position: absolute;
    top: 15vh;
    transform: translateX(-50%);
    transition: 0.3s;
    width: 10vh;
}
```

Agora, aplicando o `:hover` no corpo do fantasma, vamos modificar sua boca. Para isso, vamos mudar sua altura e largura, e deixar as quatro bordas arredondadas.

``` css
div.fantasma:hover div.rosto div.boca {
    border-radius: 5vh;
    height: 8vh;
    width: 5vh;
}
```

Agora, você já deve ver os olhos e a boca se mexendo.

Vamos agora estilizar os braços do fantasminha. Vamos aplicar uma largura para a `<div><div>` que envolve os dois braços `width: 40vh;` . Depois, vamos deixar os braços lado a lado, e fixá-los nas bordas da nossa `<div></div>` . Para isso, usaremos `display: flex; justify-content: space-between;` . Vamos fixar o elemento nas margens superior e esquerda `top: 20vh; left: 0;` , e deixar os braços encostado junto ao corpo `transform: translateX(-5vh);` .

``` css
div.fantasma div.maos {
    display: flex;
    justify-content: space-between;
    left: 0;
    position: absolute;
    top: 20vh;
    transform: translateX(-5vh);
    width: 40vh;
}
```

Agora, vamos desenhar os braços. Vamos definir altura e largura `height: 5vh; width: 10vh;` e cor do elemento `background-color: whitesmoke;` . Quando passarmos o mouse sobre o fantasma, queremos também que seus braços se movam; para deixar a transição fluida, aplicaremos o `transition: 0.3s;` . Quanto maior for este valor, mais lenta será a transição.

``` css
div.fantasma div.maos span {
    background-color: whitesmoke;
    height: 5vh;
    transition: 0.3s;
    width: 10vh;
}
```

Agora, para arredondar as bordas dos braços, vamos precisar estilizar um elemento `<span></span>` por vez. Usaremos o seletor `:nth-child:` para isso. Sabemos que a `<div class="maos"></div>` possui dois descendentes, ou dois elementos. Para me referir ao primeiro elemento, usarei `span:nth-child(1)` , e, para o segundo `span:nth-child(2)` . A ordem deles segue a ordem do documento HTML.

Para o primeiro elemento, vamos deixar arredondados as duas bordas da esquerda, e girarmos ele no sentido anti-horário.

``` css
div.fantasma div.maos span:nth-child(1) {
    border-radius: 5vh 0 0 5vh;
    transform: rotate(-45deg);
}
```

E, quando aplicarmos o `:hover` no fantasminha, vamos fazer com que o elemento gire no sentido horário.

``` css
div.fantasma:hover div.maos span:nth-child(1) {
    transform: rotate(45deg);
}
```

Para o segundo elemento, vamos deixar arredondados as duas bordas da direitas, e girarmos ele no sentido horário.

``` css
div.fantasma div.maos span:nth-child(2) {
    border-radius: 0vh 5vh 5vh 0vh;
    transform: rotate(45deg);
}
```

E, quando aplicarmos o `:hover` no fantasminha, vamos fazer com que o elemento gire no sentido anti-horário.

``` css
div.fantasma:hover div.maos span:nth-child(2) {
    transform: rotate(-45deg);
}
```

Agora, você verá olhos, boca e braços se movendo, ao passar o mouse sobre o fantasma.

Estilizando seus "pés". Para a `<div class="pes"></div>` , vamos aplicar uma largura igual à largura do corpinho do fantasma `width: 30vh;` . Vamos deixar o `display: flex;` , para que os elementos `<span></span>` fiquem lado a lado, vamos deixar sua posição absoluta `position: absolute;` e fixar o elemento nas margens inferior e esquerda `bottom: -5vh; left: 0;` . Valores negativos para a margem inferior fazem com que o elemento se desloque para baixo.

``` css
div.fantasma div.pes {
    bottom: -5vh;
    display: flex;
    left: 0;
    position: absolute;
    width: 30vh;
}
```

Agora, vamos estilizar os elementos `<span></span>` . Para dividir a largura dos elementos igualmente em relação à altura estabelecida no elemento pai `<div class="pes"></div>` , vamos usar o `flex: 1;` . Isso só serve porque deixamos o elemento pai com `display: flex;` . Aplicamos uma altura `height: 10vh;` e cor dos elementos `background-color: whitesmoke;` . Para deixar apenas as duas bordas inferiores arredondadas, vamos aplicar `border-radius: 0 0 10vh 10vh;` .

``` css
div.fantasma div.pes span {
    background-color: whitesmoke;
    border-radius: 0 0 10vh 10vh;
    flex: 1;
    height: 10vh;
}
```

Porém, o primeiro e o último elemento têm estilização diferentes. No primeiro, queremos que a margem esquerda fique reta, e no último elemento, queremos que a margem esquerda fique reta. Poderíamos nos referir a eles como `span:nth-child(1)` e `span:nth-child(4)` . Aqui, porém, vamos utilizar `span:first-child` e `span:last-child` .

``` css
div.fantasma div.pes span:first-child {
    border-radius: 0vh 0vh 5vh 2.5vh;
}

div.fantasma div.pes span:last-child {
    border-radius: 0vh 0vh 2.5vh 5vh;
}
```
