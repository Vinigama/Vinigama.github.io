---
title: "Classificador de comentário"
date: 2022-11-13
weight: 1
description: >
  Sobre a funcionalidade de classificar o comentário
---

{{% pageinfo %}}
Esta página visa trazer com detalhes a implementação do classificador de comentário.
{{% /pageinfo %}}

# Classificador
Para medir o sentimento do comentário, foi utilizado as bibliotecas de linguagem de processamento natural e de machine learning. Foi utilizado dois `dataframes` que seria de comentários de filmes e de palavrões.

Passo a passo de como foi criado o classificador:

 1. Leitura dos dois dataframes
 2. Junção dos dataframes
 3. Importação da biblioteca tagger que verifica as classes das palavras. Ex: substantivo, adjetivo etc
 4. Tokenização dos comentários 
 5. Remoção de ruídos dos comentários e lematização
 6. Separação das palavras que tem classificação positiva e negativa
 7. Criação do dataframe verificando se o comentário é positivo ou negativo
 8. Treinamento do modelo com dataframe
 9. Exportação do `Naive Bayer`  treinado
 
 ## Clasificador no projeto

 
Na hora que o usuário sinaliza o comentário, o sistema passar pelas seguintes funções antes de atribuir no modelo:
 

**remove_noise**: remoção de ruídos de comunicação. Exemplo: caracteres especiais.

     def remove_noise(self, tokens, stop_words = ()):
        """ Remoção de ruídos de comunicação """
        cleaned_tokens = []
    
        for token, tag in self.tagger.tag(tokens):
            token = re.sub('http[s]?://(?:[a-zA-Z]|[0-9]|[$-_@.&+#]|[!*\(\),]|'\
                        '(?:%[0-9a-fA-F][0-9a-fA-F]))+','', token)
            token = re.sub("(@[A-Za-z0-9_]+)","", token)
    
            if tag.startswith("N"):
                pos = 'n'
            elif tag.startswith('V'):
                pos = 'v'
            else:
                pos = 'a'
    
            lemmatizer = WordNetLemmatizer()
            token = lemmatizer.lemmatize(token, pos)
    
            if len(token) > 0 and token not in string.punctuation and token.lower() not in stop_words:
                cleaned_tokens.append(token.lower())
    
        return cleaned_tokens

 **lemmatize_sentence**: Lematização das palavras. Função para reduzir uma palavra à sua forma base e agrupar diferentes formas da mesma palavra.
 
    def lemmatize_sentence(self, tokens):
        """ Função para reduzir uma palavra à sua forma base e agrupar diferentes formas da mesma palavra"""
        lemmatizer = WordNetLemmatizer()
        lemmatized_sentence = []
        for word, tag in self.tagger.tag(tokens):
            if tag.startswith('N'):
                pos = 'n'
            elif tag.startswith('V'):
                pos = 'v'
            else:
                pos = 'a'
            lemmatized_sentence.append(lemmatizer.lemmatize(word, pos))
        return lemmatized_sentence
 
Após passar pelos dois processos, o comentário é passado como parâmetro para o modelo, onde verifica se o comentário é positivo ou negativo.