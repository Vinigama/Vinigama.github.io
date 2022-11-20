---
title: "Histórico de conteúdos visualizados"
date: 2022-03-21
weight: 1
description: >
  Sobre a funcionalidade do histórico de conteúdos visualizados
---

{{% pageinfo %}}
Esta página visa trazer maior clareza sobre a implementação do histórico de conteúdos visualizados
{{% /pageinfo %}}


# Fluxo

## Histórico 
![](/pt/docs/Conceitos/images/fluxo_historico_conteudos.png)

# Utilização
Para acessar o histórico dos conteúdos visualizados, basta acessar o menu no canto direito superior e clicar na opção histórico. Após passar por esse processo, será exibido os conteúdos visualizados.

Na tela de exibição de conteúdo contém duas funcionalidades, sendo elas:

 - **Search bar:** campo input para preencher o nome do conteúdo
 - **Limpar histórico:** botão para limpar o histórico

### Model
O componente principal do funcionamento do histórico é o model **Historico**, com ele é possível fazer o relacionamento com o usuário e o conteúdo 

    `class Historico(models.Model):
        visualizador = models.ManyToManyField(Perfil, related_name="+")
        conteudo = models.ForeignKey(
            Conteudo,
            on_delete=models.CASCADE,
            limit_choices_to={"ativo": True},
            related_name="+",
        )
        data = models.DateTimeField(auto_now_add=True)
    
        def __str__(self):
            return f"{self.conteudo}"`