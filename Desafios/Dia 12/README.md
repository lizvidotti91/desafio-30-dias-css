# Dia 12 - Efeito de Preenchimento ao Passar o Mouse

![Efeito de Preenchimento ao Passar o Mouse](./preenche.gif?raw=true "Efeito de Preenchimento ao Passar o Mouse")

-   [Codepen](https://codepen.io/lizvidotti91/pen/mdPGpZm);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS Psdeudo-Elements](https://www.w3schools.com/css/css_pseudo_elements.asp);
-   [CSS ::after Selector](https://www.w3schools.com/cssref/sel_after.asp);
-   [CSS ::before Selector](https://www.w3schools.com/cssref/sel_before.asp);
-   [CSS :hover Selector](https://www.w3schools.com/cssref/sel_hover.asp);
-   [CSS Transitions](https://www.w3schools.com/css/css3_transitions.asp);
-   [CSS Overflow](https://www.w3schools.com/css/css_overflow.asp);

## Passo a passo

Para aplicar o efeito de preenchimento em quatro direções diferentes, usei a seguinte estrutura HTML, onde a animação irá ocorrer no elemento `<h2></h2>`.

```html
<h2 class="viver">ViverÉDesenharSemBorracha</h2>
<h4>Millôr Fernandes</h4>

<h2 class="crescer">CrescerÉUmProcesso</h2>
<h4>Rupi Kaur</h4>

<h2 class="viva">VivaOsDetalhes</h2>
<h4>Autor desconhecido</h4>

<h2 class="eco">aVidaÉUmEco</h2>
<h4>Autor desconhecido</h4>
```

No arquivo CSS, vamos usar o reset CSS: o tamanho das caixas será definido a partir das bordas (se eu aplicar `padding:` para o elemento, por exemplo, ele continuará a ter altura e largura definidos anteriormente. Todo o conteúdo se adequa a esses valores iniciais).

```css
* {
    box-sizing: border-box;
    font-family: Arial;
    margin: 0;
    padding: 0;
}
```

Centralizando nossos elementos na tela:

```css
body {
    align-items: center;
    background-color: #8093f1;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

As três propriedades `align-items: center; display: flex; justify-content: center;` irão centralizar o elemento na linha. Para centralizar no sentido da altura da tela, devemos definir uma altura `height: 100vh;`. A unidade de medida vh (Viewport Height) faz com que o elemento se ajuste em diferentes tamanhos de tela. Nossos elementos ainda ficarão na mesma linha. Para que eles voltem a ficar em colunas, vamos aplicar o `flex:direction: column;`. Por fim, vamos definir uma cor de fundo `background-color:`.

Estilizando cada elemento `<h2></h2>`:

```css
h2 {
    cursor: pointer;
    font-size: 8vh;
    position: relative;
    text-align: center;
}
```

O mais importante, aqui, é aplicar o `position: relative;`, para podermos criar um pseudo-elemento para cada `<h2></h2>`. Deixei também o `cursor: pointer;` para que, ao passar o mouse sobre a frase, o cursor do mouse mude da setinha para a mãozinha.

Agora, estarei definindo a cor do texto, para cada frase. Note que eu estilizo pelo nome da classe de cada elemento `<h2></h2>`. Para chamar uma classe HTML no CSS, usamos o ponto final `.viver`.

```css
h2.viver {
    color: #ff6978;
}

h2.crescer {
    color: #6d435a;
}

h2.viva {
    color: #6d435a;
}

h2.eco {
    color: #ff6978;
}
```

Agora vamos criar um pseudo-elemento para cada frase. Aqui, estarei usando o `::before`, que cria um novo elemento antes do elemento-pai, que, no caso, é o `<h2></h2>`. Deixamos a posição absoluta, para que o elemento fique numa camada acima do elemento-pai, fixamos ele nas margens superior e esquerda do elemento-pai, e aplicamos o `overflow: hidden;` para que todo o conteúdo que fique para fora do pseudo-elemento `::before` fique escondido. Também vamos aplicar o `transition: 0.9s;` para deixar a animação mais fluida. Valores abaixo de 1 deixam a animação mais lenta, e valores acima de 1 deixam a animação mais rápida.

```css
h2::before {
    overflow: hidden;
    position: absolute;
    left: 0%;
    top: 0%;
    transition: 0.9s;
}
```

Agora, vamos colocar um conteúdo diferente para cada pseudo-elemento. Ele será a mesma frase usada no elemento-pai correspondente. Também aplicaremos cores e tamanhos de altura e largura diferentes.

```css
h2.viver::before {
    color: #6d435a;
    content: "ViverÉDesenharSemBorracha";
    height: 100%;
    width: 100%;
}
```

Aqui, o nosso pseudo-elemento irá cobrir o elemento-pai.

```css
h2.crescer::before {
    color: #ff6978;
    content: "CrescerÉUmProcesso";
    height: 0%;
    width: 100%;
}
```

Aqui, o nosso pseudo-elemento será apenas uma linha junto à margem superior do elemento-pai. Ele tem largura igual ao elemento-pai (100%), e não tem altura (por enquanto).

```css
h2.viva::before {
    color: #ff6978;
    content: "VivaOsDetalhes";
    height: 100%;
    width: 0%;
}
```

Aqui, o nosso pseudo-elemento será apenas uma linha junto à margem esquerda do elemento-pai. Ele tem altura igual ao elemento-pai (100%), e não tem largura (por enquanto).

```css
h2.eco::before {
    color: #6d435a;
    content: "aVidaÉUmEco";
    height: 100%;
    width: 100%;
}
```

Aqui, o nosso pseudo-elemento irá cobrir o elemento-pai.

O que faremos agora, será criar nosso efeito de preenchimento. Para isso, ao passar o mouse sobre o elemento `<h2></h2>`, iremos apenas alterar a largura ou altura do nosso pseudo-elemento.

```css
h2.viver:hover::before {
    height: 0%;
}
```

Aqui, nosso pseudo-elemento passará de uma altura de 100% para 0%, fazendo com que a transição do preenchimento de cor ocorra no sentido vertical, de baixo para cima.

```css
h2.crescer:hover::before {
    height: 100%;
}
```

Aqui, nosso pseudo-elemento passará de uma altura de 0% para 100%, fazendo com que a transição do preenchimento de cor ocorra no sentido vertical, de cima para baixo.

```css
h2.viva:hover::before {
    width: 100%;
}
```

Aqui, nosso pseudo-elemento passará de largura 0% para 100%, fazendo com que a transição do preenchimento de cor ocorra no sentido horizontal, da esquerda para a direita.

```css
h2.eco:hover::before {
    width: 0%;
}
```

Aqui, nosso pseudo-elemento pasará de largura 100% para 0%, fazendo com que a transição do preenchimento de cor ocorra no sentido horizontal, da direita para a esquerda.
