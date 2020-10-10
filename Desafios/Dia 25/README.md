# Dia 25 - Checkbox Animado

![Checkbox Animado](./captured.gif?raw=true "Checkbox Animado")

*   [Codepen](https://codepen.io/lizvidotti91/pen/pobvGYO); 

## Tecnologias Usadas

*   HTML
*   CSS

## O que eu aprendi

*   [CSS :checked Selector](https://www.w3schools.com/cssref/sel_checked.asp); 
*   [CSS Positions](https://www.w3schools.com/css/css_positioning.asp); 
*   [CSS Transform](https://www.w3schools.com/cssref/css3_pr_transform.asp); 

## Passo a passo

No arquivo HTML, teremos uma lista desordenada `<ul></ul>` , onde cada item `<li></li>` é composto de um elemento `<input>` do tipo `checkbox` , e de um elemento `<label></label>` , com um ícone.

``` html
<ul>
    <li>
        <input type="checkbox" id="happy">
        <label for="happy"><i class="far fa-smile"></i></label>
    </li>
    <li>
        <input type="checkbox" id="super">
        <label for="super"><i class="far fa-grin"></i></label>
    </li>
    <li>
        <input type="checkbox" id="star">
        <label for="star"><i class="far fa-grin-stars"></i></label>
    </li>
    <li>
        <input type="checkbox" id="love">
        <label for="love"><i class="far fa-grin-hearts"></i></label>
    </li>
</ul>
```

Em nosso arquivo CSS, vamos estilizar nossa tag `<ul></ul>` . Deixaremos o `display: flex;` , para que os itens da lista fiquem numa mesma linha; vamos aplicar uma largura de `width: 90vw;` , onde vw (Viewport Width), se refere ao tamanho da largura da tela. Agora, vamos distribuir igualmente os itens da lista nesta largura `justify-content: center;` . Para que as bolinhas de cada elemento `<li></li>` não apareçam, vamos aplicar `list-style-type: none;` em nossa `<ul></ul>` . Por fim, dando uma margem para afastar o conteúdo do cabeçalho e rodapé que coloquei em meu projeto, usei `margin: 20vh 0;` , onde o primeiro valor se refere às bordas superior e inferior, e o segundo valor, se refere às bordas esquerda e direita. Aqui também vamos definir o tamanho de cada ícone, em `font-size: 15vh;` .

``` css
ul {
    display: flex;
    font-size: 15vh;
    justify-content: space-around;
    list-style-type: none;
    margin: 20vh 0;
    width: 90vw;
}
```

Agora, vamos esconder a caixinha de marcação do nosso `<input>` .

``` css
input {
    display: none;
}
```

E aplicar algumas estilizações em nosso `<label></label>` . Vamos deixar sua posição relativa, pois iremos criar um pseudo-elemento logo mais. Quando passarmos o mouse sobre cada ícone, vamos mudar o cursor do mouse da setinha para a mãozinha em `cursor: pointer;` . Por fim, iremos aplicar algumas novas estilizações quando clicarmos em determinado ícone. Para deixar essa transição mais suave, usaremos `transition: 0.5s;` .

``` css
label {
    cursor: pointer;
    position: relative;
    transition: 0.5s;
}
```

Vamos aplicar uma cor para nossos ícones. 

``` css
i {
    color: #724E91;
}
```

Agora, ao clicarmos em determinado ícone, iremos mudar algumas estilizações de cada `<label></label>` . Vamos criar uma borda `border: 0.5px solid #724E91;` , onde o primeiro valor se refere à espessura da linha, o segundo valor se refere ao estilo da linha (que no caso, é contínua), e por último, à cor da linha. Vamos também alterar o tamanho do ícone, em `font-size: 13vh;` , e deixar o ícone afastado da borda, aplicando um preenchimento `padding: 1vh;` .

``` css
input:checked+label {
    border: 0.5px solid #724E91;
    font-size: 13vh;
    padding: 1vh;
}
```

Agora, quero trocar a cor do ícone, deixando cores diferentes para cada um, ao clicar nele. Para isso, ao invés de me referir ao elemento `<label></label>` , vou me referir a cada elemento `<i></i>` , que é filho da `<label></label>` , chamando pelo nome de sua classe.

``` css
input:checked+label .fa-smile {
    color: #F2AF29;
}

input:checked+label .fa-grin {
    color: #85FFC7;
}

input:checked+label .fa-grin-stars {
    color: #F3FFB9;
}

input:checked+label .fa-grin-hearts {
    color: #E54F6D;
}
```

Agora, criaremos um pseudo-elemento `::before;` , que será um círculo. Deixaremos ele escondido, e, ao clicar em um ícone, esse círculo irá aparecer. Deixaremos seu conteúdo vazio `content: "";` , com altura e largura iguais `height: 5vh; width: 5vh;` . Para deixá-lo no formato circular, aplicaremos `border-radius: 50%;` , e deixamos sua posição absoluta. Fixamos ele nas margens superior e esquerda `top: -1vw; left: -1vw;` , e aplicamos uma cor `background-color: #E54F6D;` . Vamos deixar ele escondido, modificando seu tamanho em `transform: scale(0);` . Ao clicar no ícone, esse círculo retorna ao seu tamanho original (scale(1)). Para deixar essa transição mais suave, aplicaremos `transition: 0.2s;` .

``` css
label::before {
    background-color: #E54F6D;
    border-radius: 50%;
    content: "";
    display: block;
    height: 5vh;
    left: -1vw;
    position: absolute;
    top: -1vw;
    transform: scale(0);
    transition: 0.2s;
    width: 5vh;
}
```

Agora, aplicamos novas propriedades quando clicarmos no ícone. Vamos aplicar um conteúdo para o pseudo-elemento em `content: "✓";` , definimos seu tamanho e deixaremos ele em negrito `font-size: 3vh; font-weight: bold;` . Para centralizar o símbolo na bolinha, usaremos as três propriedade juntas `align-items: center; display: flex; justify-content: center;` . Agora, deixaremos a bolinha em seu tamanho original em `transform: scale(1);` .

``` css
input:checked+label::before {
    align-items: center;
    color: white;
    content: "✓";
    display: flex;
    font-size: 3vh;
    font-weight: bold;
    justify-content: center;
    transform: scale(1);
}
```
