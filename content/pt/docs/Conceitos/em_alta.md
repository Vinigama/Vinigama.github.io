---
title: "Em alta"
date: 2022-03-21
weight: 1
description: >
  Sobre a funcionalidade do em alta
---

{{% pageinfo %}}
Esta página visa trazer maior clareza sobre a implementação da funcionalidade em alta 
{{% /pageinfo %}}


# Fluxo

## Histórico 
![](/pt/docs/Conceitos/images/fluxo_em_alta.png)



# Utilização
Para acessar os conteúdos que estão em alta na plataforma, basta clicar na opção "em alta" que está localizado no canto direito superior. Após passar por esse processo, será exibido os conteúdos que estão em alta (os mais visualizados).

### Model
O componente principal do funcionamento do em alta é o model **Visualizacao**, com ele é possível fazer o relacionamento com o usuário e o conteúdo 

    class Visualizacao(models.Model):
        objects = AltaManager()
    
        visualizador = models.ManyToManyField(Perfil, related_name="visualizador")
        conteudo = models.ForeignKey(
            Conteudo,
            on_delete=models.CASCADE,
            related_name="conteudo",
            limit_choices_to={"ativo": True},
        )
        data = models.DateTimeField(auto_now_add=True)
    
        def __str__(self):
            return f"{self.conteudo}"
### Manager
Os conteúdos que estão em alta tem uma validade de 7 dias. Todas as semanas os conteúdos que estão em alta na plataforma são resetados através do manager que possui uma função para filtrar os models que estão mais de 7 dias dentro do banco de dados.

    class AltaManager(models.Manager):
        def select_old(self):
            seven_days_ago = timezone.now() - timedelta(days=7)
            return self.filter(data__lt=seven_days_ago)
Para a função ser executada basta rodar o seguinte código no shell:

    Visualizacao.objects.select_old().delete()