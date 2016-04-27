---
layout: post
title: "Composer Install"
description: "Instalando o Composer no Linux"
headline: "Instale e deixe o Composer pronto para ser utilizado em seu linux."
category: Desenvolvimento
tags: [Symfony, Composer]
modified: 2016-03-13
featured: yes
imagefeature: postagens/composerInstall/composerInstall.svg
comments: true
share: true
---

Hoje mostrarei como é simples instalar e deixar o composer disponivel para suas aplicações no linux.

Já aprendemos o básico sobre git, e logo iniciaremos algumas postagens sobre Symfony, e o composer que é nosso gerenciador de dependencias é necessário para rodar perfeitamente nossos projetos.

Eis então o Composer:

<figure>
	<img src="{{ site.url }}/images/bancoPostagens/composerInstall/composerLogo.png">
	<figcaption><a href="https://getcomposer.org/download/" data-toggle="tooltip" title="Eis o Maestro">Clique aqui para Download !</a></figcaption>
</figure>

A instalação do Composer muda frequentemente, então siga a partir do link acima.

Porém eles não dão algumas informações importantes.

Quando você faz este procedimento de Download, você tem na pasta em que executou os comandos um arquivo chamado *composer.phar* , e para executá-lo você necessita de chamar o php logo assim ficará o comando:
{% highlight ruby %}
    php composer.phar
{% endhighlight %}

Ao chamar este comando verá a lista de opções que ele te trará:

<figure>
	<img src="{{ site.url }}/images/bancoPostagens/composerInstall/chamadaComposer.png">
	<figcaption><a data-toggle="tooltip" title="Chamada do Composer">Lista de Possiveis Comandos</a></figcaption>
</figure>

Você tem este arquivo numa pasta e tem que chama-lo diretamente, o que é uma chatice, então como proceder para ele estar disponivel em qualquer lugar na sua máquina, em qualquer pasta, bom tornaremos este comando possível Globalmente.

Para isso execute os seguintes passos na pasta onde está localizado seu *composer.phar*:
{% highlight ruby %}
    sudo chmod +x composer.phar
{% endhighlight %}

Assim estamos tornando executável o composer.phar .
Logo após precisamos move-lo para ser chamado globalmente, execute:
{% highlight ruby %}
    sudo mv composer.phar /bin/
{% endhighlight %}

Logo após move-lo para a pasta /bin/ poderemos fazer sua chamada.
Já não é mais necessário colocar o php antes, podendo ser chamado diretamente.

{% highlight ruby %}
    composer.phar
{% endhighlight %}

Sendo assim temos nosso composer disponivel para qualquer projeto em qualquer pasta e momento.
Então se você tem vários projetos não é necessário baixar 1 composer para cada !

Espero ter ajudado ! Até a próxima !
