---
title: "Sinalização de conteúdo - Administrador"
date: 2022-10-25
weight: 1
description: >
  Sobre a funcionalidade de sinalização de conteúdo
---

{{% pageinfo %}}
Esta página visa trazer com detalhes a implementação das funcionalidades de sinalizar e apurar conteúdos
{{% /pageinfo %}}

# Fluxo
## Sinalizar conteúdo

![](/pt/docs/Conceitos/images/fluxo_sinalizacao_conteudo.png)

## Apuração da sinalização

![](/pt/docs/Conceitos/images/fluxo_apuracao_conteudo.png)

## Solicitar edição

![](/pt/docs/Conceitos/images/fluxo_sinalizacao_conteudo_edicao.png)

## Histórico de sinalizações

![](/pt/docs/Conceitos/images/fluxo_historico_sinalizacoes_conteudos.png)

# Utilização
O Model `SinalizacaoConteudo`  é o componente responsável pela sinalização de conteúdo. Quando o usuário faz uma sinalização de conteúdo o sistema faz uma condição para saber se o conteúdo sinalizado possui teor negativo ou não. A condição é realizada através dos percentuais dos dislikes e de sinalizações, se conteúdo possuir um percentual de sinalizações maior que 40 e de dislikes maior que 10, o conteúdo é categorizado como negativo.

O Administrador fica responsável de analisar o conteúdo, se for apontado algum tipo de irregularidade na análise administrador, o próprio enviará uma notificação via email falando com detalhes sobre as irregularidades.