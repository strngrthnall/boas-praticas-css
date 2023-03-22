# SMACS

## Scalable and Modular Architeture for CSS
*Arquiterua Escalável e Modular para CSS*

### O que é?
O SMACS é uma forma de organizar e escrever os arquivos CSS de um projeto para que se tenha um facil compreensão por todos aqueles que irão ler ou participar da produção do projeto.

### Modulação:
O SMACS se propõe a dividirmos o código CSS em 5 categorias a `base`, o `layout`, os `módulos`, o `estado` e o `tema`.

---

**Base**

A Base seriam as regras quer serveriam de padrão para os elementos, como por exemplo um reset do CSS.

Dentro da regra base, não usamos Id's nem Classes, apenas as Tags.

---

**Layout**

O layout seriam as regras estruturais das seções de um site, como o cabeçalho, uma barra lateral e assim por diante.

---

**Modulos**

Os modulos são componentes mais discretos da página, como por exemplo a barra de navegação, os carrosséis, dialogos, textos, widgets e por aí vai.

Os módulos ficam dentro dos componentes do Layout, e as vezes pode se encontrar dentro de outros Modulos também.

Cada Módulo deve ser designado para esistir como um componente por si só. Desta maneira a página será mais flexivel. Se feito da maneira certa, os Modulos podem ser facilmente movidas para diferentes partes do layout sem quebrar.

Quando definimos as regras de um modulo, devemos evitar usar ID's e seletores de elemntos, nos prendendo apenas às Classes. Provavelmente um modulo poderá ter uma certa quantidade de elementos, e é preferível que usemos os seletores de descendencia e parentesco para mirarmos nos elementos desejados.

---

**Temas**

Geralment temos apenas um tema por site, mas podemos encontrar grandes sites que tem o mesmo layout com temas diferentes pra suas páginas, como por exemplo o site da Globo.com

Se prestarmos atenção, o site G1 e o site do Globo Esporte tem o layout muito parecido, mas com algumas mudanças no tema.

---

Para mais informações sobre o [SMACCS](http://smacss.com/) acessar o site oficial.

