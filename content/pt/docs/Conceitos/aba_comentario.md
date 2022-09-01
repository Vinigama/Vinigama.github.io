---
title: "Seção Comentário"
date: 2022-08-31
weight: 1
description: >
  Sobre a funcionalidade de comentários na exibição do conteúdo.
---
{{% pageinfo %}}
A seção **Comentário** na exibição do conteúdo foi criada para que o criador do conteúdo e os alunos possam utilizar esse meio como uma interação.
{{% /pageinfo %}}

# Conceito Geral
O objetivo da aba comentários na exibição do conteúdo é trazer uma interação relacionado ao conteúdo. Todos os espectadores podem fazer comentários e também responder outros comentários. O espectador que criar comentário pode apagar o seu próprio comentário e também pode sinalizar e atribuir `like/dislike` nos outros comentários.

Logo abaixo da exibição do conteúdo, irá ter uma barra de comentários e um botão enviar desativado, quando o espectador digitar algo na barra de comentários o botão ficará ativado. O comentário digitado precisa possuir no mínimo 1 caractere e no máximo 255 caractere, se o comentário não atingir o tamanho proposto é exibido um alerta.

# Benefícios
Benefícios de deixar comentários em outros vídeos:
-   **Você se estabelece como um especialista.** Se seus comentários forem bem escritos  e cheios de informações úteis, outras pessoas tomarão nota do seu conhecimento e talvez pedirão mais conselhos.
-   **Você se conecta com novas pessoas.** Comentar vídeos é uma maneira gratuita e rápida de fazer com que sua voz seja ouvida por um novo público.
-   **Você aumentará suas visualizações de vídeo e visualizações de perfil.** Se você disser algo interessante e único, outros espectadores clicarão em seu perfil, consumirão seus conteúdos.

# Funções 
Para construir a seção comentário, foi necessário as seguintes funções:
 - **$("#input-comentario").keyup(function()})** - Funcionalidade para ativar o botão enviar quando um caractere for digitado no `input text` comentário;
 - **function  adicionarComentario(comentario, usuario, comentarioId)}** - Função para adicionar um card comentário contendo o nome do usuário e comentário dinamicamente dentro da `div secao-comentario`;
 - **function  alertaComentario(text)** - Exibi um modal de alerta com text de acordo que passar como parâmetro;
 - **$( "#enviar_comentario" ).click(function()});** - Funcionalidade que envia para o banco de dados o comentário via `AJAX`. Essa funcionalidade possui restrições de caracteres, o tamanho de caracteres que ser maior que 1 e menor que 255, se não atingir encaixar no tamanho proposto é chamado a `function  alertaComentario(text)`;
- **function  likeComentario(elem)** - Função para vincular o usuário que clicou no `button like` com o comentário via AJAX;
- **function  dislikeComentario(elem)** - Função para vincular o usuário que clicou no `button dislike` com o comentário via AJAX;
- **function  dinamicoDislike(botaoLike, botaoDislike, quantidadeLike, quantidadeDislike)** - Funcionalidade para alterar o visual do botão `dislike` quando for clicado, para sinalizar que o usuário está vinculado com o botão. Outra funcionalidade da função é a quantidade de `dislike` que é alterado quando houver contato com o `button`
- **function  dinamicoLike(botaoLike, botaoDislike, quantidadeLike, quantidadeDislike)** - Funcionalidade para alterar o visual do botão `like` quando for clicado, para sinalizar que o usuário está vinculado com o botão. Outra funcionalidade da função é a quantidade de `like` que é alterado quando houver contato com o `button`;
- **function  enviarResposta(elem)** - Função para adicionar resposta ao comentário;
- **function  adicionarResposta(elem, comentario, usuario, comentarioId)** - Função para adicionar um card resposta contendo o nome do usuário e a resposta;
- **function  responder(elem)** -  Quando o usuário clicar no `responder` em um comentário é exibido  o `input text resposta` 
- **function  ajaxSend(data, url)** - Requisição AJAX. Essa funcionalidade é composta pela função AJAX do Jquery para fazer requisições assíncronas;
- **function  deletarComentario(elem, id)** - Função para deletar o comentário. Quando o usuário clicar no botão deletar é exibido um `modal`, confirmando se realmente ele quer deletar, quando ele clicar em sim, o `card` comentário é removido dinamicamente;
- **function  accordionResposta(elem)** - Função que atualiza a quantidade de respostas que está atrelado com o comentário;
- **function  htmlEncode(str)** - Funcionalidade que transforma um script para text, evitando ataque XSS;