---
layout: post
title: "Python - Criar Relatório"
description: "Criando um Relatório em Arquivo Texto com Python"
headline: "Aprenda a Manipular Dados em Arquivos Texto com Python"
category: Desenvolvimento
tags: [Python, Exercicios]
modified: 2016-08-22
featured: false
imagefeature: postagens/listapython1/listapython1.svg
comments: true
share: true
---

Olá amigos, na antiga postagem sobre exercicios resolvidos em Python, surgiu uma questão nos comentários para se resolver.

Confira a postagem **[Aqui Neste Link](https://guiaprogramador.com.br/desenvolvimento/exerciciospython1)**.

Tivemos a Seguinte Questão:

<figure>
	<img src="{{ site.url }}/images/bancoPostagens/criarRelatorioPython/sugestaoQuestao.png">
	<figcaption><a data-toggle="tooltip" title="Preservei os Dados para privacidade do Nosso amigo com Dúvidas"></a></figcaption>
</figure>

Algumas Observações que não podem Passar em Branco:

- O arquivo deve estar conter nos primeiros 15 espaços apenas o nome do Usuario ( Se esta Condição não for Cumprida o Código não funcionara Perfeitamente, terão então que ser feitos ajustes no código para limitar ou diferenciar os separadores )
- A questão não deixa tão claro o item acima, pq no texto enviado a lista aparece com os nomes sem espaços em branco, o que deveria ter para completar os 15 caracteres de nome

Sem Mais enrolação o nosso arquivo ficou assim:

usuarios.txt
{% highlight ruby %}
alexandre      456123789
anderson       1245698456
antonio        123456456
carlos         91257581
cesar          987458
rosemary       789456125
{% endhighlight %}


Nosso Código ficou assim:
{% highlight python %}
__author__ = 'Jhonatan Mark'
#Exercicio Sugestão/Dúvida Questão

with open('usuarios.txt') as arquivo:
    linhas = arquivo.read().splitlines()
    arquivo.close()

def organizaNomes(lista):
    listaNome = []
    for i in range(len(lista)):
       listaNome.append(lista[i][0:14].rstrip())
    return listaNome

def organizaTamanhoConsumido(lista):
    listaConsumo = []
    for i in range(len(lista)):
        listaConsumo.append(int(lista[i][15:len(lista[i])]))
    return listaConsumo

def transformaByteEmMega(lista):
    listaEmMega = []
    for i in range(len(lista)):
        listaEmMega.append(round(int(lista[i])/1048576,2))
    return listaEmMega

def calculaPercentuais(lista):
    percentuais = []
    valorTotal = sum(lista)
    for i in range(len(lista)):
       percentuais.append(round((lista[i]/valorTotal)*100,2))
    return percentuais

def calculaEspacoMedio(lista):
    espacoMedio = round(sum(lista)/len(lista),2)
    return espacoMedio

def criaRelatorio(nomes, consumosMega, percentuais):
    if (len(nomes) == len(consumosMega) == len(percentuais)):
        open('relatorio.txt','a')
        arquivo = open('relatorio.txt','w')
        for i in range(len(nomes)):
            arquivo.write(str(i)+' '+str(nomes[i])+' '+str(consumosMega[i])+'MB '+str(percentuais[i])+'%'+'\n')
        arquivo.close()
    else:
       print('Quantidade de Usuarios e Dados Não Conferem.')

nomes = organizaNomes(linhas)
consumos = organizaTamanhoConsumido(linhas)
consumosMega = transformaByteEmMega(consumos)
percentuais = calculaPercentuais(consumosMega)
criaRelatorio(nomes,consumosMega,percentuais)

{% endhighlight %}
