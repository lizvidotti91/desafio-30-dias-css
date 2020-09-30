# Dia 22 - Ícones com Efeito

![Ícones com Efeito](./captured.gif?raw=true "Ícones com Efeito")

-   [Codepen](https://codepen.io/lizvidotti91/pen/wvGbNmL);

## Tecnologias Usadas

-   HTML
-   CSS

## O que eu aprendi

-   [CSS Transitions](https://www.w3schools.com/css/css3_transitions.asp);
-   [CSS Animations](https://www.w3schools.com/css/css3_animations.asp);
-   [CSS Pseudo-Elements](https://www.w3schools.com/css/css_pseudo_elements.asp);

## Passo a passo

No arquivo HTML, teremos uma `<div></div>` principal, que guarda quatro botões.

```html
<div class="container">
    <div class="icon">
        <i class="fas fa-arrow-up"></i>
    </div class="icon">
    <div class="icon">
        <i class="fas fa-arrow-down"></i>
    </div class="icon">
    <div class="icon">
        <i class="fas fa-arrow-left"></i>
    </div class="icon">
    <div class="icon">
        <i class="fas fa-arrow-right"></i>
    </div class="icon">
</div>
```

Em nosso arquivo CSS, vamos começar definindo algumas estilizações comuns a todo o documento HTML. Para isso, vamos usar o `*`. Vamos definir o tamanho das caixas a partir de suas bordas (por padrão, essa medida é feita a partir de seu conteúdo. Assim, ao definir um `padding:`, por exemplo, o tamanho final da caixa vai variar com o tamanho definido para o seu preenchimento. Isso não ocorre com o valor `border-box;`). Definimos também o valor zero para `margin:` e `padding:`.

```css
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
```

Centralizando os elementos na tela. Para centralizar os elementos nos sentidos horizontal e vertical, usaremos as três propriedades juntas `align-items: center; display: flex; justify-content: center;`. Como eu ainda tenho cabeçalho e rodapé em meu projeto, eles estarão todos ocupando uma única linha. (cabeçalho, conteúdo e rodapé). Para isso, usei o `fle-direction: column;`, onde o conteúdo torna a ficar em colunas. Para que os elementos fiquem no meio da tela, vamos aplicar uma altura `height: 100vh;`. A unidade de medida vh (Viewport Height), é medida em relação à altura da tela. Assim, seu conteúdo pode se ajustar a diversos tamanhos de tela. Por último, vamos aplicar uma cor de fundo `background-color: #283044;`. No CSS, as cores podem ser definidas com o seu código hexadecimal, que é o que estou usando no projeto.

```css
body {
    align-items: center;
    background-color: #283044;
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
}
```

Nesse momento, os ícones estão dispostos em coluna. Para deixá-los em uma única linha, temos que aplicar o `display: flex;` em nossa `<div class="container"><div>`. Para separar essa caixa do caçalho e rodapé, apliquei uma margem nas bordas superior e inferior do elemento `margin: 20vh 0;`; aqui, o primeiro valor se refere às margens superior e inferior; o segundo valor, se refere às margens esquerda e direita.

```css
div.container {
    display: flex;
    margin: 20vh 0;
}
```

Vamos estilizar agora as `<div class="icon"></div>`. Vamos definir altura e largura iguais, `height: 20vh; width: 20vh;`, e `` border-radius: 50%;`, para que nossa caixa fique na forma circular. Vamos aplicar também uma cor para nossa borda `border: 1px solid #FF5E5B;`; o primeiro valor se refere à espessura da borda, depois o estilo da borda (aqui deixaremos uma linha contínua) e sua cor. Para centralizar nosso ícone, vamos aplicar também as propriedades `align-items: center; display: flex; justify-content: center;`. Para afastar um pouco um botão do outro, vamos aplicar uma margem nas bordas esquerda e direita `margin: 0 3vw;`; o primeiro valor se refere às margens superior e inferior; o segundo valor, às margens esquerda e direita.

Vamos também mudar o ícone do mouse quando passamos ele sobre o botão para a mãozinha `cursor: pointer;`. Queremos também criar um segundo círculo tracejado dentro do nosso botão, que aparece quando passamos o mouse sobre ele. Para isso, usarei o pseudo-elemento ::before. Então, deixarei a posição deste elemento como relativa.

```css
div.container div.icon {
    align-items: center;
    border: 1px solid #FF5E5B;
    border-radius: 50%;
    cursor: pointer;
    display: flex;
    height: 20vh;
    justify-content: center;
    margin: 0 3vw;
    position: relative;
    width: 20vh;
}
```

Agora, vamos criar nosso pseudo-elemento `::before`. Vamos começar deixando o seu conteúdo vazio `conten: "";`, e definindo altura e largura iguais `height: 17vh; width: 17vh;`. Para deixar o elemento no formato circular, aplicamos o `border-radius: 50%;`. Vamos aplicar a borda tracejada em `border: 3px dashed #FF5E5B;`; o primeiro valor se refere à sua espessura; o segundo, seu estilo (que deixaremos com uma linha tracejada); e sua cor.

Usaremos o `position: absolute;` para que esse círculo fique sobre o elemento-pai (no caso, a `<div class="icon"></div>`). Mas não queremos que ela apareça agora, por isso deixaremos `display: none;`. Assim, ela permanece invisível.

```css
div.icon::before {
    content: "";
    border: 3px dashed #FF5E5B;
    border-radius: 50%;
    display: none;
    height: 17vh;
    position: absolute;
    width: 17vh;
}
```

Agora, queremos que, quando o mouse passa sobre o nosso ícone, esse círculo tracejado apareça. Para isso, usaremos o `display: block;`. Também vamos aplicar uma animação, para que nosso círculo tracejado fique girando na tela. Assim, usarei `animation: rotation 10s linear infinite;`; nossa animação tem quadro-chave de nome rotation, tem duração de 10 segundos, e ocorre de maneira linear e infinita. 

```css
div.icon:hover::before {
    animation: rotation 10s linear infinite;
    display: block;
}
```

Agora, para a definição dos quadros-chave, vamos usar a propriedade `transform: rotate();`; o elemento tracejado sai da posição zero para uma rotação de 360 graus (uma volta completa).

```css
@keyframes rotation {
    0% {
        transform: rotate(0deg);
    }

    100% {
        transform: rotate(360deg);
    }
}
```

Pronto, você já deve estar vendo o círculo tracejado se mexendo lentamente. Agora, vamos estilizar nosso ícone `<i></i>`. Vamos definir um tamanho para o nosso ícone em `font-size: 15vh;`, uma cor `color: #FF5D5B;`, vamos deixar a caixa que envolve o ícone redonda `border-radius: 50%;`. Ao passar o mouse sobre o ícone, queremos também alterar a cor dele. Para deixar essa transição mais fluida, vamos aplicar `transition: 0.3s;`.

```css
div.container div.icon i {
    border-radius: 50%;
    color: #FF5E5B;
    font-size: 15vh;
    transition: 0.3s;
}
```

Agora, aplicando o hover na `<div class="icon"></div>`, vamos estilizar nosso `<i></i>`. Vamos definir, primeiro, um novo tamanho para o elemento `height: 15vh; width: 15vh;` e deixá-lo no formato circular `border-radius: 50%;`. Vamos diminuir um pouco o tamanho do ícone em `font-size: 14vh;`. Para deixar o ícone centralizado na caixa, vamos usar `align-items: center; display: flex; justify-content: center;`. Por fim, mudaremos a cor do ícone `color: #EBF5EE;` e a cor de fundo do elemento `<i></i>` em `background-color: #FF5E5B;`.

```css
div.container div.icon:hover i {
    align-items: center;
    background-color: #FF5E5B;
    color: #EBF5EE;
    display: flex;
    font-size: 14vh;
    height: 15vh;
    justify-content: center;
    width: 15vh;
}
```