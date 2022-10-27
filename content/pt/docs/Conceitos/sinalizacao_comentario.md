---
title: "Sinalização de comentário - Administrador"
date: 2022-10-25
weight: 1
description: >
  Sobre a funcionalidade de sinalizar comentários nos conteúdos
---

{{% pageinfo %}}
Esta página visa trazer com detalhes a implementação das funcionalidades de sinalizar e apurar comentários
{{% /pageinfo %}}

# Fluxo

## Sinalizar comentário

![](/pt/docs/Conceitos/images/fluxo_sinalizacao_comentario.png)

## Apurar sinalização

![](/pt/docs/Conceitos/images/fluxo_apuracao_comentario.png)

## Histórico de sinalizações

![](/pt/docs/Conceitos/images/fluxo_historico_sinalizacoes_comentarios.png)

# Utilização

O Model `SinalizacaoComentario` é o componente resposável pela sinalização de comentário. Quando o usuário sinaliza um comentário o sistema faz uma média ponderada para saber se o comentário sinalizado possui teor negativo ou não, se o comentário possuir uma classificação diferente de positivo é apresentado para o administrador na página de sinalizações de comentários.

O Administrador fica responsável de escolher as opções de **remover** ou de classificar como **ok**. Se o administrador escolher a opção de **remover**, o comentário será removido e será gerado uma entrada de histórico no `HistoricoSinalizacaoComentario`, caso o administrador escolher a opção **parecer ok**, apenas a sinalização será removida.