# Dia 14 - Fundo de Texto Animado

![Fundo de Texto Animado](./loading.gif?raw=true "Fundo de Texto Animado")

-   [Codepen](https://codepen.io/lizvidotti91/pen/eYZPrMK);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS Background-clip](https://developer.mozilla.org/pt-BR/docs/Web/CSS/background-clip);
-   [CSS Background-Position](https://www.w3schools.com/cssref/pr_background-position.asp);

## Passo a passo

A base do nosso arquivo HTML será:

```html
<div>Como uma onda no mar</div>
```

Em nosso arquivo CSS, vamos começar aplicando algumas estilizações para todo o documento. O tamanhos dos elementos será contado a partir de suas bordas, a fonte padrão será `monospace`, e `margin:` e `padding:` terão valor zero.

```css
* {
    box-sizing: border-box;
    font-family: monospace;
    margin: 0;
    padding: 0;
}
```

Centralizando os elementos na tela:

```css
body {
    align-items: center;
    background-color: #3d5a80;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

As três propriedades juntas `align-items: center; display: flex; justify-content: center;` farão com que os elementos fiquem centralizados na tela, nos sentidos horizontal e vertical. Para garantir a centralização no sentido vertical, vamos aplicar uma altura para o corpo do documento, que deixem em `height: 100vh`. A unidade de medida vh (Viewport Height) é relativa a altura da tela. Assim, os elementos podem se ajustar aos diversos tamanhos de tela. Para deixar os elementos distribuídos em colunas, vamos usar `flex-direction: column;`. Por fim, apliquei uma cor de fundo `background-color:`.

Agora iremos estilizar nossa `<div></div>`:

```css
div {
    animation: slide 5s linear infinite;
    background: url(./img/FreeVector-Waves-Vector-Pattern.jpg);
    background-clip: text;
    -webkit-background-clip: text;
    color: transparent;
    font-family: "Changa One", cursive;
    font-size: 18vh;
    font-weight: bold;
    text-transform: uppercase;
}
```

Para deixar o texto em caixa alta, estou usando o `text-transform: uppercase`. Coloquei um estilo de fonte diferente `font-family:` e deixei a fonte mais grossa `font-weight:` e com altura correspondente a 18vh (Viewport Height), para que a altura do texto se ajuste aos diversos tamanhos de tela. Para que possamos aplicar uma imagem como cor de um texto, usaremos as propriedades `background: url(./img/FreeVector-Waves-Vector-Pattern.jpg); background-clip: text; -webkit-background-clip: text; color: transparent;`. A URL do seu background pode conter um endereço de uma imagem na web. Para isso, você deverá colocar a url entre " ".

Agora, para animar a nossa imagem de fundo, usaremos a propriedade `animation: slide 5s linear infinite;`. Nosso quadro-chave se chamará slide, a animação terá duração de 5 segundos e ocorrerá de forma linear e infinita (quando a animação termina, ela retorna ao ponto inicial).

Vamos definir o `@keyframes`. Aqui, apenas estaremos mudando a posição da nossa imagem de fundo. Para isso,
usaremos a propriedade `background-position:`, que irá variar de 0% a 100%.

```css
@keyframes slide {
    0% {
        background-position: 0%;
    }
    100% {
        background-position: 100%;
    }
}
```
