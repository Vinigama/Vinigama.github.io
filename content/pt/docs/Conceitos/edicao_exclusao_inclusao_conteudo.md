---
title: "Telas para edição, inclusão e exclusão de conteúdo - Administrador"
date: 2022-03-21
weight: 1
description: >
  Sobre a funcionalidade de edição, inclusão e exclusão feitas por meio de solicitação de usuário
---

{{% pageinfo %}}
Esta página visa trazer maior clareza sobre a implementação de funções chave da aplicação, referentes aos processos de aceitação de conteúdo postado, aceitação de edição em conteúdo postado e aceitação de exclusão de conteúdo postado.
{{% /pageinfo %}}

# Fluxo

## Inclusão

![](/pt/docs/Conceitos/images/fluxo_inclusao_conteudo.png)

## Edição

![](/pt/docs/Conceitos/images/fluxo_edicao_conteudo.png)

## Exclusão

![](/pt/docs/Conceitos/images/fluxo_exclusao_conteudo.png)

# Utilização

O Model `RequisicaoFormulario` é o componente resposável pela administração destas requisições. Por meio do método `aceita_requisicao`, é possível permitir que o fluxo ocorra por completo, sendo assim, quando a o método `aceita_requisicao` é chamado, o fluxo de aceitação da requisição é seguido.

As requisições feitas pelo Aluno Tutor ficam centralizadas no painel de administração do Django. Estas requisições podem ser aceita pela Action personalizada `Aceitar solicitação`, ou podem ser visualizadas de maneira mais detalhada ao ativar o botão `Verificar solicitação`.

O botão `Verificar solicitação` leva a uma View responsável pelo roteamento da requisição. Para mais detalhes, verificar a view `router_requisicao` presente do Django App `requisicoes`.