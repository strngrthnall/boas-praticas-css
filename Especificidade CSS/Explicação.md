# Especificidade CSS

### A especificidade em CSS é uma forma de entendermos quais regras tem "maior força" na hora de serem aplicadas.

## Código:

    <!DOCTYPE html>
    <html lang="pt-br">
    <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width initial-scale=1.0">
      <title>Document</title>
      <style>
        button {
          background-color: blue;
        }

        .btn-sucesso {
          background-color: green;
        }
      </style>
    </head>
    <body>
      <button class="btn-sucesso" style="background-color: red;">Enviar Mensagem
      </button>
    </body>
    </html>
**Exemplo1.html**

## Explicação:
Usando o código acima como refrência, podemos observar que temos três diferentes formas de escrever a mudnça de cor de fundo do botão.

A primeira forma é utilizando a tag `<style>` e referenciando dentro dela, da mesma forma que em um arquivo CSS, a tag `<button>` e nesta refenrencia mudamos a cor para azul.

    <style>
      button {
        background-color: blue;
      }
    ...
    </style>

Este tipo de referenciação é o tipo 'mais fraco' assim sendo facilmente sobreposto por outrar regras, como por exemplo quando referenciamos um classe.

*A especificidade deste seletor é 0, 0, 1*

No nosso exemplo a classe usada foi o `.btn-successo`, e nesta referencia mudamos a cor do botão para verde. Todos os botões com esta classe devem ter esta regra aplicada, a menos que tenham uma regra mais especifica.

    <style>
    ...
      .btn-sucesso {
        background-color: green;
      }
    </style>

Este tipo de referenciação só perde para o a estilização em linha.

*A especificidade deste seletor é 0, 1, 0*

A estilização em linha é feita diretamente na tag HTML. Esta é a regra mais específica do CSS.

    <button ... style="background-color: red;">...</button>

Neste caso a refenreciação muda a cor de fundo do botão para vermelho.

*A especificidade deste seletor é 1, 0, 0*

## Numerando a especificidade do seletor:

Como pode ser observado acima, podemos usar uma certa matemática para entender qual é a especificidade do seletor.

Um seletor com a especificidade (0, 1, 0) é maior que um com (0, 0, 1). Mas em certos casos essas especificidades podem ser somadas, o que causa uma mudança no calculo.

Por exemplo:

    <style>
      button {
        background-color: blue;
      }
    </style>

*A especificidade deste seletor é 0, 0, 1*

    <style>
      .btn-sucesso {
        background-color: green;
      }
    </style>

Este tipo de referenciação só perde para o a estilização em linha.

*A especificidade deste seletor é 0, 1, 0*

Mas quando adcionamos a classe no seletor button:

    <style>
      button.btn-sucesso {
        background-color: blue;
      }
    </style

*A especificidade deste seletor é 0, 1, 1*

Acontece uma soma entre as duas especificidades, e agora esta é a mais forte.

No caso do código abaixo: 

    <!DOCTYPE html>
    <html lang="pt-br">
    <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Document</title>
      <style>
        button.btn-sucesso {
          background-color: blue;
        }

        .btn-sucesso {
          background-color: green;
        }
      </style>
    </head>
    <body>
      <button class="btn-sucesso" >Enviar Mensagem
      </button>
    </body>
    </html>
**Exemplo2.html**

A cor de fundo do botão seria azul, mas caso adcionasse a estelização em linha:

    <!DOCTYPE html>
    <html lang="pt-br">
    <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Document</title>
      <style>
        button.btn-sucesso {
          background-color: blue;
        }

        .btn-sucesso {
          background-color: green;
        }
      </style>
    </head>
    <body>
      <button class="btn-sucesso" style="background-color: red" >Enviar Mensagem
      </button>
    </body>
    </html>
**Exemplo3.html**

A cor de fundo voltaria a ser vemelha, pois A especificidade deste seletor é (1, 0, 0)

## !important

Existe uma maneira de contornar toda esta especificidade, e habilitar o menos específico como o mais importante.

Seria justamente com a tag CSS `!important`:

    <!DOCTYPE html>
    <html lang="pt-br">
    <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Document</title>
      <style>
        button {
          background-color: blue;
        }

        .btn-sucesso {
          background-color: green !important;
        }
      </style>
    </head>
    <body>
      <button class="btn-sucesso" style="background-color: red" >Enviar Mensagem
      </button>
    </body>
    </html>
**Exemplo4.html**

Usando-a da forma como é demonstrado acima, o botão voltará a ter a cor verde, pois agora esta regra terá mais peso que todas as outras.

**Importante: Esta forma de especificidade é considerada má prática, por ser mais dificil de ser detectada**

### Links:

[Calculadora de especificidade](https://specificity.keegan.st/)
