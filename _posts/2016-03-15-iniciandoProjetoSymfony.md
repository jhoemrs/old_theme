---
layout: post
title: "Iniciando Projeto Symfony"
description: "Começando um Projeto Symfony"
headline: "Aprenda a iniciar o Projeto Symfony !"
category: Desenvolvimento
tags: [Symfony]
modified: 2016-03-15
featured: yes
imagefeature: postagens/iniciandoProjetoSymfony/topBar.png
comments: true
share: true
---

Como Iniciar um Projeto em Symfony
==================================

Já temos nosso **[SYMFONY](http://jhoemrs.github.io/desenvolvimento/symfonyInstall)** instalado com nosso **[COMPOSER](http://jhoemrs.github.io/desenvolvimento/composerInstall)** configurado, bom vamos lá.

Sempre utilizei desde que comecei a aprender o Symfony a versão 2.* porém para acompanhar a evolução estarei aprendendo e buscando com vocês as mudanças do Symfony 3 !

Escolha uma pasta que será alocado o seu projeto, e vamos chamar o seguinte comando :
{% highlight ruby %}
symfony new blog
{% endhighlight %}

Com este comando estaremos iniciando uma pasta chamada blog contendo um projeto Symfony.

<figure>
	<img src="{{ site.url }}/images/postagens/iniciandoProjetoSymfony/setTimeZone.png">
	<figcaption><a data-toggle="tooltip" title="Precisamos setar o TimeZone">Opa, algo não está certo !</a></figcaption>
</figure>

Repare que ao fim da instalação do projeto, ele nos reclama falando que nosso sistema não atende aos requisitos técnicos !
E que o date.timezone precisa ser setado em nosso **php.ini** !

Precisamos corrigir isso, e depois realizar esta verificação novamente.
Temos 2 possíveis php.ini que são mais comuns, alteraremos os por via das dúvidas.

Estarei usando o gedit no meu comando que é o meu editor de texto, caso use o VIM ( Que também uso mas não tinha instalado no momento ), ou outro editor, substitua onde está escrito gedit pela chamada do seu editor.

<figure>
	<img src="{{ site.url }}/images/postagens/iniciandoProjetoSymfony/sudoGeditPhpIni.png">
	<figcaption><a data-toggle="tooltip" title="Primeiro Possível php.ini">Apache2 php.ini!</a></figcaption>
</figure>

Logo após a execução deste comando abrirá a tela para edição do php.ini:
Busque ( Normalmente CTRL+F ) por date.timezone e lá que faremos a edição, onde se encontra ;date.timezone = , será necessário retirar o comentário da linha que é este ponto e vírgula inicial, e em sequencia adicionar o seu código de DateTime que está disponivel para consulta na documentação do **[PHP](http://php.net/manual/pt_BR/timezones.php)**.

Logo seu arquivo ficará assim ou similar:

<figure>
	<img src="{{ site.url }}/images/postagens/iniciandoProjetoSymfony/phpIni.png">
	<figcaption><a data-toggle="tooltip" title="php.ini">Arquivo php.ini!</a></figcaption>
</figure>

Precisamos também nos certificar que o php.ini estará configurado na pasta cli que é de comum uso pelo Symfony.
Então execute:

<figure>
	<img src="{{ site.url }}/images/postagens/iniciandoProjetoSymfony/sudoGeditPhpIni2.png">
	<figcaption><a data-toggle="tooltip" title="Segundo Possível php.ini">CLI php.ini!</a></figcaption>
</figure>

Abrirá mais uma vez o arquivo PHP.INI execute o passo de alteração do arquivo acima e vamos para o próximo passo.

Sempre após uma alteração em nosso arquivo de configuração do PHP, para nosso servidor tomar conhecimento dessas alterações precisamos dar um reboot !

Normalmente em nosso Linux executaremos o seguinte comando para reiniciar o apache:
{% highlight ruby %}
sudo /etc/init.d/apache2 restart
{% endhighlight %}

Após tudo isto, podemos verificar se nosso Symfony está agora atendendo aos requisitos técnicos para rodar em nosso sistema:
<figure>
 <img src="{{ site.url }}/images/postagens/iniciandoProjetoSymfony/checkSymfonyOk.png">
 <figcaption><a data-toggle="tooltip" title="Aleluia !">Symfony Requisitos Checkup</a></figcaption>
</figure>

Agora podemos entrar em nossa pasta **blog** que contém nosso projeto.
E teremos a seguinte estrutura de pastas:
<figure>
 <img src="{{ site.url }}/images/postagens/iniciandoProjetoSymfony/estruturaPastas.png">
 <figcaption><a data-toggle="tooltip" title="Repare no Composer !">Pastas e Arquivos</a></figcaption>
</figure>

Temos o detalhe do **Composer.json** neste JSON contém todas as dependências que são necessárias para rodar este projeto, como já temos nosso **[COMPOSER](http://jhoemrs.github.io/desenvolvimento/composerInstall)** configurado , só precisamos executá-lo com o comando **install** para instalarmos as dependências!
<figure>
 <img src="{{ site.url }}/images/postagens/iniciandoProjetoSymfony/composerInstall.png">
 <figcaption><a data-toggle="tooltip" title="Composer em Ação !">Composer Install</a></figcaption>
</figure>

Temos tudo instaladinho agora, podemos chamar um comando que será **EXTREMAMENTE UTILIZADO** em nossos projetos Symfony que é o **bin/console** na versão 2.* poderia ser encontrado sob o comando **app/console** .

Ao executá-lo puramente teremos a lista de comandos disponíveis:
<figure>
 <img src="{{ site.url }}/images/postagens/iniciandoProjetoSymfony/binConsole.png">
 <figcaption><a data-toggle="tooltip" title="Bin/Console Wins!">Symfony em Ação</a></figcaption>
</figure>

Tudo OK ! **Bin/Console** Rodando Liso ! Dependências instaladas ! Agora é só alegria, vamos rodar nosso servidor:

Execute o comando bin/console abaixo:
<figure>
 <img src="{{ site.url }}/images/postagens/iniciandoProjetoSymfony/binConsoleServerRun.png">
 <figcaption><a data-toggle="tooltip" title="Bin/Console Wins!">Rodando Servidor com Symfony</a></figcaption>
</figure>

Só precisamos acessar agora o caminho nos dado ( no meu caso http://127.0.0.1:8000 ) e finalmente teremos a linda tela de boas-vindas do Symfony !
<figure>
 <img src="{{ site.url }}/images/postagens/iniciandoProjetoSymfony/projectStarted.png">
 <figcaption><a data-toggle="tooltip" title="Symfony Wins!">Welcome To Symfony</a></figcaption>
</figure>

Obrigado Pessoal , por hoje é só, espero que tenham gostado! Um abraço !
