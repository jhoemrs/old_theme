---
layout: post
title: "Symfony Install"
description: "Instalando o Symfony no Linux"
headline: "Instale e deixe o Symfony pronto para ser utilizado em seu linux."
category: Desenvolvimento
tags: [Symfony]
modified: 2016-03-14
featured: yes
imagefeature: postagens/symfonyInstall/SymfonyTopBar.jpg
comments: true
share: true
---

Hoje mostrarei como é simples instalar e deixar o Symfony disponivel para o linux.

Assim como o composer o Symfony tem algumas instruções para instalar e deixa-lo funcionando:

<figure>
	<img src="{{ site.url }}/images/postagens/symfonyInstall/comoInstalar.png">
	<figcaption><a href="https://symfony.com/download" data-toggle="tooltip" title="Symfony Download">Clique aqui para Download !</a></figcaption>
</figure>

Já vi algumas maneiras diferentes de instalar o Symfony então caso haja alguma alteração clique no link acima para obter maiores informações de como instalar.

Logo que executamos o primeiro comando listado acima podemos nos deparar com a seguinte mensagem:

<figure>
	<img src="{{ site.url }}/images/postagens/symfonyInstall/curlNotFound.png">
	<figcaption><a data-toggle="tooltip" title="Cadê o Curl?">Curl Not Found</a></figcaption>
</figure>

Sendo assim precisamos instalar o curl, um erro comum é se instalar o php5-curl esperando que este seja o problema, bom não se trata do php5-curl o pacote que não está instalado é do próprio curl.
Para isso apenas execute:
<figure>
	<img src="{{ site.url }}/images/postagens/symfonyInstall/instalarCurl.png">
	<figcaption><a data-toggle="tooltip" title="Eis o Curl">Curl Install</a></figcaption>
</figure>

Após o curl instalado e tudo corretamente setado:

Execute aqueles primeiros dois comandos de instalação do Symfony:
{% highlight ruby %}
sudo curl -LsS https://symfony.com/installer -o /usr/local/bin/symfony
{% endhighlight %}

Este primeiro comando baixará o Symfony e o Alocará na pasta /usr/local/bin/ pois foi passado o parametro -o de OutPut .

{% highlight ruby %}
sudo chmod a+x /usr/local/bin/symfony
{% endhighlight %}

Este segundo comando tornará o symfony Executável.

Sendo assim só executar **symfony** de qualquer lugar no console que chamará o instalador do symfony, como mostrado abaixo:
<figure>
	<img src="{{ site.url }}/images/postagens/symfonyInstall/chamadaSymfony.png">
	<figcaption><a data-toggle="tooltip" title=Symfony Installer">Comandos Symfony</a></figcaption>
</figure>

Sendo assim já temos o Symfony pronto para iniciarmos um novo projeto !

Obrigado e até a próxima !
