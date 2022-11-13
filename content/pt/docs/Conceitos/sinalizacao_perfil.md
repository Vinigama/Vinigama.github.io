---
title: "Sinalização de perfil - Administrador"
date: 2022-10-13
weight: 1
description: >
  Sobre a funcionalidade de sinalizar perfil 
---

{{% pageinfo %}}
Esta página visa trazer com detalhes a implementação das funcionalidades de sinalizar e apurar perfil
{{% /pageinfo %}}

# Fluxo

## Sinalizar perfil

![](/pt/docs/Conceitos/images/fluxo_sinalizacao_perfil.png)

## Perfil notificado

![](/pt/docs/Conceitos/images/fluxo_perfil_notificado.png)

## Histórico de sinalizações

![](/pt/docs/Conceitos/images/fluxo_historico_sinalizacoes_perfis.png)


# Utilização
O Model `SinalizacaoPerfil` é o componente responsável pela sinalização de perfil. Quando o usuário sinaliza um perfil o sistema verifica se o perfil possui mais de 10 sinalizações, se sim, a sinalização fica com a classificação negativa, assim, aparecendo para o administrador apurar.

O Administrador fica responsável de escolher as seguintes opções para apurar a sinalização:

 - **Excluir:** deleta o perfil do usuário e também a sinalização
 - **Parece ok:** deleta apenas a sinalização
 - **Enviar notificação:** envia notificação com as modificações necessárias para o usuário alterar
 - **Silenciar:** silencia usuário por 15 ou 30 dias, impedindo dele comentar nos conteúdos