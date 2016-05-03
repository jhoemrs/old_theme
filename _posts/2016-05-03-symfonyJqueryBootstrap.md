---
layout: post
title: "Symfony 3 jQuery BootStrap Install"
description: "Instalando via Composer Bootstrap e Jquery em um projeto Symfony 3"
headline: "Utilizando Assetic para Instalar Dependencias JQuery e Bootstrap em um projeto Symfony3"
category: Desenvolvimento
tags: [Symfony, Bootstrap, Jquery]
modified: 2016-05-03
featured: yes
imagefeature: postagens/symfonyJqueryBootstrap/symfonyJqueryBootstrap.svg
comments: true
share: true
---

Utilizar os Assets para instalar o `Bootstrap` e o `jQuery` (entre outros) pode ser um desafio muito grande para os iniciantes no Symfony.

Se você assim como eu, deseja utilizar o composer para gerenciar suas dependências e não gostaria de colocar diretamente estes Assets genéricos na pasta web, bom existe uma excelente forma de utilizar os mesmos.

Hoje irei demonstrar um dos métodos de Instalação com grande embasamento na documentação do **[SYMFONY](http://symfony.com/doc/current/cookbook/assetic/asset_management.html)** que você pode conferir mais detalhes se desejar direto na documentação.

Necessito maiores buscas para dizer se o método que demonstrarei é uma boa prática ou se segue os `Design Patterns` indicados, então que sirva mais como estudo ou base se você necessita fazer o mesmo.
E se você tiver uma opinião ou um material que possa vir aprimorar o que aqui descrevo, fique à vontade para comentar, até agradeço !

Vamos lá, mãos à obra!

O Primeiro passo foi dizer ao meu composer quais dependências eu vou instalar, a primeira de todas é o `assetic/bundle` então entre na pasta do seu projeto e execute o seguinte comando:
{% highlight ruby %}
composer.phar require symfony/assetic-bundle
{% endhighlight %}

Então agora habilite este `Bundle` no seu `AppKernel.php` da sua aplicação Symfony:
{% highlight php %}
// app/AppKernel.php

// ...
class AppKernel extends Kernel
{
    // ...

    public function registerBundles()
    {
        $bundles = array(
            // ...
            new Symfony\Bundle\AsseticBundle\AsseticBundle(),
        );

        // ...
    }
}
{% endhighlight %}

Agora vamos no nosso arquivo `config.yml` e colocar estas configurações mínimas do bundle:
{% highlight yaml %}
# app/config/config.yml

# Assetic Configuration
assetic:
    debug:          '%kernel.debug%'
    use_controller: '%kernel.debug%'
    filters:
        cssrewrite: ~
# ...
{% endhighlight %}

Agora que já temos nosso gerenciador de `assets` instalado, precisamos do `jQuery` e do `Bootstrap`.  

Vamos dizer diretamente ao composer os componentes que precisamos.

Primeiro `jQuery`:
{% highlight ruby %}
composer.phar require components/jquery
{% endhighlight %}

Agora o `Bootstrap`:
{% highlight ruby %}
composer.phar require twbs/bootstrap
{% endhighlight %}

Ao terminar a Instalação dos dois voltaremos ao nosso Arquivo `config.yml` e adicionaremos estes `assets` da seguinte forma:
{% highlight yaml %}
# Assetic Configuration
assetic:
    debug:          '%kernel.debug%'
    use_controller: '%kernel.debug%'
    filters:
        cssrewrite: ~
    assets:
        jquery:
            inputs:
                - '%kernel.root_dir%/../vendor/components/jquery/jquery.min.js'
        bootstrap_css:
            inputs:
                - '%kernel.root_dir%/../vendor/twbs/bootstrap/dist/css/bootstrap.min.css'
        bootstrap_js:
            inputs:
                - '%kernel.root_dir%/../vendor/twbs/bootstrap/dist/js/bootstrap.min.js'
{% endhighlight %}

Após isto nossos `assets` já estarão prontos para serem acessados por nossas views, porém para deixar a coisa ainda mais legal, vamos deduzir que o bootstrap e o jquery será um asset padrão, e então vamos alterar o nosso arquivo `base`.

Este arquivo pode ser localizado dentro da pasta do projeto seguido de `Resources/views/default/base.html.twig` lá então teremos nosso arquivo base, e vamos deixá-lo desta seguinte maneira:
{% highlight twig %}
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1">

        <title>{% block title %}Welcome!{% endblock %}</title>


        {% block stylesheets %}
            {% stylesheets
                '@bootstrap_css' %}
            <link rel="stylesheet" href="{{ asset_url }}" />
            {% endstylesheets %}
        {% endblock %}

        <link rel="icon" type="image/x-icon" href="{{ asset('favicon.ico') }}" />

    </head>
    <body>
        {% block body %}{% endblock %}
        {% block javascripts %}
            {% javascripts
                '@jquery'
                '@bootstrap_js' %}
            <script src="{{ asset_url }}"></script>
            {% endjavascripts %}
        {% endblock %}
    </body>
</html>
{% endhighlight %}

Agora só precisamos extender nossas futuras `views` apontando para `base` e teremos já o bootstrap disponível.

Para exemplificar e testar faça uma view deste forma:
{% highlight twig %}
{% extends 'base.html.twig' %}
{% block body %}
<button class="btn btn-primary">Botão Bootstrap</button>
{% endblock %}
{% endhighlight %}

Se você ver o resultado do botão semelhante à esta imagem:
<figure>
	<img src="{{ site.url }}/images/bancoPostagens/symfonyJqueryBootstrap/botaoBootstrap.png">
	<figcaption><a data-toggle="tooltip" title="Botão Bootstrap!">Botão deve ser similar a este.</a></figcaption>
</figure>

Você fez tudo corretamente!

Obrigado e Abraços !
