

Compilar o PDO_OCI para acessarmos o banco oracle por nosso PHP, em um ambiente linux.

Esta é, uma das maiores dificuldades que encontramos ao utilizar o PHP com linux no ambiente empresarial, pois não temos nativamente uma configuração fácil para acessar bancos Oracle em nosso ambiente.

Estarei fazendo este tutorial no Debian 8, provavelmente funcione no seu linux também...

É um trabalho um pouco extenso então vamos começar.

Antes de mais nada vamos atualizar nossos pacotes.
{% highlight ruby %}
sudo apt-get update
{% endhighlight %}

Agora vamos instalar o pacote `libaio1`
{% highlight ruby %}
sudo apt-get install libaio1
{% endhighlight %}

Precisamos baixar alguns pacotes extras com do `instantclient`

ARQUIVO 1 , 2

Agora vamos executar...

sudo dpkg -i oracle-instantclient11.2-basic_11.2.0.4.0-2_amd64.deb


E agora o segundo pacote

sudo dpkg -i oracle-instantclient11.2-devel_11.2.0.4.0-2_amd64.deb

Agora vamos criar alguns links simbólicos:

sudo ln -s /usr/include/oracle/11.2/client64 /usr/include/oracle/11.2/client

E mais este...

sudo ln -s /usr/lib/oracle/11.2/client64 /usr/lib/oracle/11.2/client


AGORA FAÇA DOWNLOAD DESTE PDO_OCI

ARQUIVO 3

Agora execute o seguinte comando, ainda na pasta que baixou o arquivo

sudo tar -xvf pdo_oci

Agora entre na pasta que foi descompactada...

cd PDO_OCI-1.0/


sudo touch config.m4.patch

Agora edite este arquivo patch e adicione:

9a10,11
> elif test -f $PDO_OCI_DIR/lib/libclntsh.$SHLIB_SUFFIX_NAME.11.2; then
> PDO_OCI_VERSION=11.2
119a122,124
> PHP_ADD_LIBRARY(clntsh, 1, PDO_OCI_SHARED_LIBADD)
> ;;
> 11.2)


Após isso execute:

sudo patch config.m4 < config.m4.patch

Para rodar o próximo comandos precisamos instalar mais 1 pacote:

sudo apt-get install php5-dev

Agora podemos rodar:

sudo phpize

Agora execute:

sudo ./configure --with-pdo-oci=shared,instantclient,/usr,11.2

Caso esteja no debian verá a seguinte mensagem:

MENSAGEM 1


Agora vamos atualizar a indexação de nossos arquivos para localizar este arquivo que falta.

sudo updatedb

E agora ache ele:

locate php_pdo_driver.h

Após achar execute:

sudo sed -ie 's,include/php/ext/pdo/php_pdo_driver.h,include/php5/ext/pdo/php_pdo_driver.h,g' configure


Agora podemos executar:

sudo ./configure --with-pdo-oci=shared,instantclient,/usr,11.2

Edite o arquivo pdo_oci.c

sudo gedit pdo_oci.c

E adicione `zend_` na `function_entry` conforme imagem abaixo, salve:

IMAGEM

Execute:

sudo ln -s /usr/include/php5/ include/php

E agora:

sudo make && sudo make install


Agora dentro da pasta:

/etc/php5/cli/conf.d

Crie um arquivo

sudo touch pdo_oci.ini]

Edite-o e insira as seguintes informações:

; Enable pdo_oci (oracle) extension module
extension=pdo_oci.so


Agora para verificar crie um arquivo phpinfo :

touch index.php

Depois edite e insira:

<?php

phpinfo();

Para todas as nossas alterações terem efeito, restarte o servidor:

sudo /etc/init.d/apache2 restart

Agora vamos rodar o servidor para acessarmos nosso phpinfo...

php -S localhost:8000

Vá até PDO , se você executou tudo corretamente verá o seguinte:

IMAGEM PHPINFO
