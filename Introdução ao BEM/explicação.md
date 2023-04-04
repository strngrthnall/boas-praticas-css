# BEM - Block Element Modifier

O [BEM](https://getbem.com/) é uma metodologia para escrever blocos de estilo, ou seja, CSS.



## Block

O Bloco é um container, como por exemplo um `<form>` ou uma `<div>`, ou seja são blocos que contenham *elementos* em seu conteúdo.

O Bloco encapsula uma entidade independente que é significativa por si só. 
Embora os blocos possam ser aninhados e interagir entre si, semanticamente eles permanecem iguais; não há precedência ou hierarquia. 
Entidades holísticas sem representação DOM (como controladores ou modelos) também podem ser blocos.

### Nomeando

Os nomes de bloco podem consistir em letras latinas, dígitos e traços. 
Para formar uma classe CSS, adicione um prefixo curto para "namespacing".
Ex.: `.block`

### HTML

Qualquer node do DOM pode ser um bloco se ele aceitar um nome de classe.
Ex.: `<div class="block">...</div>`

### CSS

Use apenas o seletor de nome de classe. Sem nome de tag ou IDs. 
Sem dependência de outros blocos/elementos em uma página.
Ex.: `.block { color: #042; }`

---

## Element

Um elemento seriam itens que estejam dentro de um bloco, como por exemplo um `<input>` dentro do `<form>`

### Nomeando

Nomes de elementos podem consistir em letras latinas, dígitos, hífens e sublinhados. 
A classe CSS é formada pelo nome do bloco mais dois sublinhados e o nome do elemento.
Ex.: `.block__elem`

### HTML

Qualquer node do DOM dentro de um bloco pode ser um elemento. 
Dentro de um determinado bloco, todos os elementos são semanticamente iguais.

### CSS

`<div class="block"><span class="block__elem"></span></div>`

**Bom**
```
.block__elem { color: #042; }
```

**Ruim**
```
.block .block__elem { color: #042; }
div.block__elem { color: #042; }
```

---

## Modifier

Um modificador seria uma classe que adcionaria uma modificação à algum item

### Nomeando

Os nomes de modificadores podem consistir em letras latinas, dígitos, hífens e sublinhados. 
A classe CSS é formada pelo nome do bloco ou do elemento mais dois hífens.
Ex.: `.block--mod` ou `.block__elem--mod` e `.block--color-black`. 
Espaços em modificadores complicados são substituidos por traços.

### HTML

O modificador é um nome de classe adicional que você adiciona a um node do DOM de bloco/elemento. Adicione classes de modificadores apenas aos blocos/elementos que eles modificam e mantenha a classe original.

### CSS

Use o nome da classe de modificador como seletor.
Ex.: `.block--hidden { }`

Para alterar elementos com base em um modificador de nível de bloco.
Ex.: `.block--mod .block__elem { }`

Modificador de elemento.
Ex.: `.block__elem--mod { }`

**Bom**
```
<div class="block block--mod">...</div>
<div class="block block--size-big block--shadow-yes">...</div>
```

**Ruim**
```
<div class="block--mod">...</div>
```
## Exemplo

Suponha que você tenha um bloco de formulário com modificadores `theme: "xmas"` e `simple: true` e com os elementos `input` e `submit`, e o elemento `submit` com seu proprio modificador `disabled: true` para não enviar o formulário enquanto ele não estiver preenchido:


**HTML**
```
<form class="form form--theme-xmas form--simple">
  <input class="form__input" type="text" />
  <input
    class="form__submit form__submit--disabled"
    type="submit" />
</form>
```

**CSS**
```
.form { }
.form--theme-xmas { }
.form--simple { }
.form__input { }
.form__submit { }
.form__submit--disabled { }
```


---

**Obs.: A maior parte desta página foi retirada do site oficial do [BEM](https://getbem.com/).**