---
layout: post
title: "Novo Bundle Symfony"
description: "Aprenda a Criar um novo Bundle no Symfony e Limpar o AppBundle()"
headline: "Como Limpar um Bundle e Criar um Novo no Symfony"
category: Desenvolvimento
tags: [Symfony]
modified: 2016-03-17
featured: yes
imagefeature: postagens/novoBundle/symfonytopbar.png
comments: true
share: true
---

Hoje iremos criar nosso Bundle !

Um bundle é algo que pode ser reutilizado como uma peça independente de software, por exemplo, se um Bundle Fatura depende do Bundle Produto para funcionar, então não há sentido dos dois estarem separados.

Esta informação está disponível no **[Symfony Best Practices](http://symfony.com/doc/current/best_practices/creating-the-project.html)** , fiz uma tradução livre e resumida, ainda exerço algumas coisas que devem ser melhoradas neste intuito, já criei bundles que não funcionavam como uma peça sozinha mas funcionavam bem para organização, então é uma espada de 2 gumes, mas seguir as melhores práticas sempre acredito que seja uma boa, mas não é algo de extrema preocupação para quem está aprendendo.

Vamos lá, mão na massa!

Primeiro vamos limpar o Bundle que já veio com nosso projeto.

<figure>
	<img src="{{ site.url }}/images/postagens/novoBundle/limparPastasAppKernel.png">
	<figcaption><a data-toggle="tooltip" title="Limpando a estrutura.">Limpe AppKernel + Apague Pastas</a></figcaption>
</figure>

Para limpar o Bundle antigo apague-o do AppKernel e exclua as duas pastas AppBundle que estão selecionadas também na imagem acima, o próximo passo é limpar nosso routing.yml conforme imagem abaixo.

<figure class="half">
	<a href="{{ site.url }}/images/novoBundle/routingSujo.png"><img src="{{ site.url }}/images/novoBundle/routingSujo.png"></a>
	<a href="{{ site.url }}/images/novoBundle/routingLimpo.png"><img src="{{ site.url }}/images/novoBundle/routingLimpo.png"></a>
</figure>

Agora abrimos o terminal e acessaremos a pasta de nosso projeto.

<figure>
	<img src="{{ site.url }}/images/postagens/novoBundle/pastaProjeto.png">
	<figcaption><a data-toggle="tooltip" title="CD BLOG">Acesse a Pasta do Projeto !</a></figcaption>
</figure>

Após isso executaremos o comando:

{% highlight ruby%}
bin/console generate:bundle
{% endhighlight %}

Nos depararemos agora com a primeira pergunta:
{% highlight ruby%}
Are you planning on sharing this bundle across multiple applications? [no]:
{% endhighlight %}

Ao Pressionar Enter você estará selecionando a **resposta padrão** que se encontra **entre colchetes**.

**IMPORTANTE**, este tipo de resposta padrão poderá ser utilizado e será, em vários comandos bin/console que executaremos daqui para frente.

Logo após isto será questionado o nome do nosso novo Bundle, que deve terminar com Bundle.
{% highlight ruby%}
Bundle name:
{% endhighlight %}
Para dar sequência escolhi o nome de **JornalBundle** para nossa aplicação.

Próximo questionamento será:
{% highlight ruby%}
Target Directory [src/]:
{% endhighlight %}

A não ser que você esteja fazendo algo muito customizado, o costume do bundle é se localizar dentro de src/ .
Pressione Enter para continuar.

Logo será nos dado a próxima questão, qual será o formato de nossa configuração, por padrão é sugerido annotation, é exatamente ele que vamos utilizar em nossos exemplos.
{% highlight ruby%}
Configuration format (annotation, yml, xml, php) [annotation]:
{% endhighlight %}

Ao fim deste passo, terá uma tela similar a esta:
<figure>
	<img src="{{ site.url }}/images/postagens/novoBundle/generateBundle.png">
	<figcaption><a data-toggle="tooltip" title="Bundle Gerado!">Tela Bundle Gerado !</a></figcaption>
</figure>

Agora Rode o Projeto com o Comando:
{% highlight ruby%}
bin/console server:run
{% endhighlight %}

Ao acessarmos o endereço do servidor iniciado, se você executou todos os passos acima, verá a seguinte tela no navegador:

<figure>
	<img src="{{ site.url }}/images/postagens/novoBundle/navegadorHelloWorld.png">
	<figcaption><a data-toggle="tooltip" title="Hello World !">O Hello World Pra dar Sorte !!!</a></figcaption>
</figure>

Oficialmente Seja Bem-Vindo ao seu Bundle no Symfony.

Um abraço, e até a próxima!
