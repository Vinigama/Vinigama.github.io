---
title: "Admin Editable - Itens Editáveis por Administrador"
date: 2022-03-21
weight: 1
description: >
  Sobre a funcionalidade de Admin Editable e como ela pode ser utilizada no projeto.
---

{{% pageinfo %}}
A funcionalidade do **Admin Editable** foi criada para facilitar o trabalho com itens que devem ser editáveis para o **Administrador do sistema**.
{{% /pageinfo %}}

# Conceito Geral

A ideia do **Admin Editable** é abstrair o máximo possível a criação de elementos editáveis pelo administrador. A solução alcança este objetivo ao vincular este elemento, representado na tela, ao seu equivalente na tela de administração do Django.

Por padrão, a solução criará automaticamente um botão no canto superior direito do componente onde ele é aplicado. Este comportamento padrão é possível com a criação de uma `div` wrapper que será pai do componente, logo o botão criado e o componente são irmãos na árvore do DOM.

Este comportamento padrão pode ser sobrescrito ao utilizar o atributo HTML: `data-editable-custom-button="true"`. Todavia o comportamento ainda não se encontra implementado e deve ser implementado no arquivo **admin-editable.js** do projeto.


# Utilização

Para ativação da solução, é necessária a importação do modulo onde ela está presente por meio da linha:
```
{% load admin_utils %}
```


Então dentro da tag HTML que possui o componente editável, deve ser adicionada a linha com o seguinte esquema:
```
{% admin_editable user.is_superuser "<nome do app>" "<nome do model>" <id no model> %}
```
Segue um exemplo de implementação utilizado no arquivo **secoes.html** do projeto:
```
{% admin_editable user.is_superuser "conteudos" "secao" secao.id %}
```


# Sobrescrevendo o comportamento padrão

É possível sobrescrever o comportamento relacionado ao posicionamento do botão no elemento. Os atributos utilizados para isso são:
* **`data-edit-button-right`** - Equivalente à propriedade right do CSS. Deve ser uma valor inteiro. Ex: `data-edit-button-right="15"`
* **`data-edit-button-left`** - Equivalente à propriedade left do CSS. Deve ser uma valor inteiro. Ex: `data-edit-button-left="15"`
* **`data-edit-button-top`** - Equivalente à propriedade top do CSS. Deve ser uma valor inteiro. Ex: `data-edit-button-top="15"`
* **`data-edit-button-bottom`** - Equivalente à propriedade bottom do CSS. Deve ser uma valor inteiro. Ex: `data-edit-button-bottom="15"`

Também é possível utilizar o atributo `data-editable-custom-button="true"` para cancelar o comportamento padrão e tornar possível a implementação de um botão personalizado. Para isso, um botão com a classe `button-editable` deve ser colocado dentro deste componente com `display: none` no CSS.