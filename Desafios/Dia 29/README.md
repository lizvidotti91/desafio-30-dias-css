# Dia 29 - Menu Responsivo com Media Queries

![Menu Responsivo com Media Queries](./captured.gif?raw=true "Menu Responsivo com Media Queries")

*   [Codepen](https://codepen.io/lizvidotti91/pen/oNLWaVN?editors=1100); 

## Tecnologias Usadas

*   HTML
*   CSS

## O que eu aprendi

*   [CSS Media Queries](https://www.w3schools.com/css/css_rwd_mediaqueries.asp); 

## Passo a passo

 
 Nesse passo-a-passo, vou focar apenas na construção do menu. No arquivo HTML, ele fica da seguinte maneira: 

``` html
 <nav>
     <label for="icon"><i class="fas fa-bars"></i></label>
     <input type="checkbox" name="icon" id="icon">
     <ul>
         <li> <a href="#home"> Home </a></li>
         <li> <a href="#about"> About </a></li>
         <li> <a href="#tour"> Tour </a></li>
         <li> <a href="#contact"> Contact </a></li>
     </ul>
 </nav>
```

E, no arquivo CSS, vamos estilizar nossa barra de navegação. Vamos aplicar uma cor de fundo em `background-color: #EA3546;` , tamanho dos textos em `font-size: 1em;` e largura da barra em `width: 100%;` . Alinhando os textos à direita da tela em `text-align: right;` . Aqui, vamos deixar a posição fixa, e deixar a barra de navegação junto à margem superior e esquerda `position: fixed; top: 0; left: 0;` .

``` css
nav {
    background-color: #EA3546;
    font-size: 1.5em;
    left: 0;
    position: fixed;
    text-align: right;
    top: 0;
    width: 100%;
}
```

Agora, vamos esconder o ícone e o `input` aplicando o `display:none;` .

``` css
nav label {
    display: none;
    line-height: 2em;
}

nav input {
    display: none;
}
```

A ideia é que apenas a lista de itens apareça na barra de menu. Vamos deixar os itens lado a lado `display: flex;` , e distribuí-los à direita da tela `justify-content: flex-end;` . Para que as bolinhas que representam cada item da lista sumam, basta aplicar `list-style-type: none;` .

``` css
nav ul {
    display: flex;
    list-style-type: none;
    justify-content: flex-end;
}
```

Para espaçar cada item da lista, vamos aplicar uma margem na borda direita de cada elemento.

``` css
nav ul li {
    margin-right: 3vw;
}
```

Vamos estilizar os elementos âncora `<a></a>` . Definindo a cor da letra em `color: #F4F2F3;` e aplicando espaçamento entre o texto e as bordas superior e inferior da barra `line-height: 2em;` . Vamos retirar também o efeito sublinhado do texto `text-decoration: none;` , e deixá-lo sublinhado apenas quando passar o mouse sobre o elemento. Para isso, vamos usar o `:hover` , logo depois. Para que a animação ocorra de maneira fluida, vamos utilizar o `transition: 0.3s;` .

``` css
nav ul li a {
    color: #F4F2F3;
    line-height: 2em;
    text-decoration: none;
    transition: 0.3s;
}
```

Aplicando o `:hover` , e deixando o texto sublinhado.

``` css
nav ul li a:hover {
    text-decoration: underline;
}
```

Agora, vamos alterar algumas estilizações para tamanhos diferentes de tela, e para isso estarei usando o Media Queries do CSS `@media (max-width: 600px){}` . Aqui, quero dizer que, para uma largura máxima da tela de 600 pixels, estarei modificando alguns estilos. Todo o conteúdo estará dentro das chaves `{}` .

Vamos começar alterando o tamanho do texto da barra de navegação.

``` css
 nav {
     font-size: 1.2em;
 }
```

Queremos que, para essa largura de tela, o ícone do menu apareça, e os itens da lista fiquem escondidos, e só apareçam quando clicarmos no ícone. Para que o elemento apareça, vamos usar o `display: block;` , e afastar o elemento da borda direita da tela usando o `margin-right: 10vw;` .

``` css
nav label {
    display: block;
    margin-right: 10vw;
}
```

Agora, vamos esconder os itens da lista. Para isso, utilizaremos o `display: none;` . Vamos também alterar a largura da caixa em `width: 100vw;` e deixar os textos centralizados `text-align: center;` .

``` css
nav ul {
    display: none;
    text-align: center;
    width: 100vw;
}
```

Deixarei os itens da lista sublinhados novamente em: 

``` css
nav ul li {
    text-decoration: underline;
}
```

E, ao passar o mouse ou clicar em um item da lista, vamos mudar a cor do texto. Para isso, estarei utilizando o `:hover` (passando o mouse sobre o elemento) e o `:focus` (clique no elemento).

``` css
nav ul li a:hover,
nav ul li a:focus {
    color: #171312;
}
```

Mas, nossos itens da lista ainda estão escondidos. Temos que clicar no ícone para que ele apareçam. Para isso, vamos utilizar o seletor `:checked` , que confirma quando o `input` foi clicado, ou ativado. Ao clicarmos no ícone, o elemento `<ul></ul>` torna a ficar visível.

``` css
nav input:checked+ul {
    display: block;
}
```

Seu `@media` deve ficar assim:

``` css
@media (max-width: 600px) {
    nav {
        font-size: 1.2em;
    }

    nav label {
        display: block;
        margin-right: 10vw;
    }

    nav ul {
        display: none;
        text-align: center;
        width: 100vw;
    }

    nav ul li {
        text-decoration: underline;
    }

    nav ul li a:hover,
    nav ul li a:focus {
        color: #171312;
    }

    nav input:checked+ul {
        display: block;
    }
}
```
