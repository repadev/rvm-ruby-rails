RVM + Ruby + Rails
==================

Instalación y configuración del RVM (Ruby Version Manager), Ruby y el framework RubyOnRails.

<img src="http://tomonrails.files.wordpress.com/2014/02/rvm.png" alt="rvm" width="230" height="220" class="aligncenter size-full wp-image-162" />

<p align="justify">Suele pasar que al tener una versión antigua de Ruby instalada y querer actualizar (ó desinstalar por completo dicha versión antigua e instalar la nueva) la máquina nos da problemas. Bien sea, porque intenta encontrar un paquete que no está, o que instale, y luego la aplicación que estemos desarrollando presente problemas. <a href="http://rvm.io" title="RVM" target="_blank">RVM</a> (ó <strong>Ruby Version Manager</strong>), facilita la vida del desarrollador en ese sentido, ya que es una aplicación que nos permite instalar/manejar dentro de nuestro sistema diferentes versiones de <strong>Ruby</strong> y de <strong>Rails</strong> al mismo tiempo (e incluso de mas aplicaciones en 'gemas') y de una forma muy sencilla. Osea, que por ejemplo, podremos tener Ruby 1.9.3 y 2.1.0, y Rails 3.2.16 y 4.0.2, y trabajar con la combinación que necesitemos. Pero vamos al grano...</p>

<pre><code>$ sudo apt-get update
$ sudo apt-get dist-upgrade</code></pre>

<p align="justify">Como se pueden dar cuenta, este post está orientado en Linux, porque es el mejor ambiente que puede tener un desarrollador de aplicaciones en RubyOnRails y se apunta a optimizar aun mas dicho ambiente. Cabe resaltar que Rails puede ser instalado tanto en Mac como en Windows y tienen sus diferentes formas de instalación en dichos sistemas operativos. Personalmente, recomiendo <strong>GNU/Linux</strong>. Ya para empezar de lleno, con los comandos anteriores actualizamos nuestro sistema para tener al día los paquetes que vayamos a instalar.</p>

<p align="justify">Lo que vamos a hacer después es instalar una dependencia necesaria para RVM llamada <strong>curl</strong>:</p>

<pre><code>$ sudo apt-get install curl</code></pre>

<p align="justify">Luego, ahora si, instalamos RVM ejecutando el siguiente comando en la terminal. (El sitio web de RVM muestra las diferentes maneras de hacer éste paso, ésta que se detalla a continuación es la forma mas sencilla)</p>

<pre><code>$ curl -L get.rvm.io | bash -s stable</code></pre>

<p align="justify">Ahora abrimos el archivo <code>~/.bashrc</code> y añadimos al final, la siguiente linea:</p>

<pre><code>PATH=$PATH:$HOME/.rvm/bin</code></pre>

<p align="justify">Lo mismo con el archivo <code>~/.bash_profile</code>, añadimos un par de lineas al final:</p>

<pre><code>[[ -s "$HOME/.profile" ]] && source "$HOME/.profile"
[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"</code></pre>

<p align="justify">Lo que vamos a hacer después es escribir éstos dos comandos en terminal, e instalamos los paquetes que necesita Ruby para funcionar:</p>

<pre><code>$ source ~/.rvm/scripts/rvm
$ rvm requirements</code></pre>

<p align="justify">Ahora, ya con el RVM instalado, procedemos a instalar Ruby:</p>

<pre><code>$ rvm install 2.1.0</code></pre>

<p align="justify">Una vez instalado, para comenzar a utilizarlo podemos teclear el siguiente comando:</p>

<pre><code>$ rvm use 2.1.0</code></pre>

<p align="justify">Revisa si estas usando efectivamente Ruby 2.1.0 (xD)</p>

<pre><code>$ ruby -v
ruby 2.1.0p0 (2013-12-25 revision 44422) [x86_64-linux]</code></pre>

<p align="justify">Y si lo que deseas es dejar ésta versión de Ruby como predeterminada, simplemente escribe ésto en tu terminal:</p>

<pre><code>$ rvm --default use 2.1.0</code></pre>

<p align="justify">Finalmente, instalamos el Rails. Nótese que no se necesita el <code>sudo</code> para instalarlo! (xD)</p>

<pre><code>$ gem install rails</code></pre>

<p align="justify">Dicho comando instalará la última versión del Rails. De querer una mas antigua (por ejemplo la 3.2.16) podemos hacer lo siguiente:</p>

<pre><code>$ gem install rails --version=3.2.16</code></pre>

<p align="justify">Con ello, el <code>rails</code> quedará instalado como <strong>gema</strong>, y el resto de gemas que requiere también serán instaladas, incluyendo la <code>bundler</code>.</p>

<p align="justify">Como tip extra, recomiendo una de éstas dos opciones para optimizar el desarrollo de nuestras aplicaciones en Rails. La primera, es instalar Node.js, un framework de JavaScript necesario a partir de la versión 3.x de Rails para compilar código JS. (¡Muy funcional!)</p>

<pre><code>$ sudo apt-get install nodejs</code></pre>

<p align="justify">La otra opción (aunque yo recomiendo la anterior), si no se quiere instalar Node.js, añadir al <code>Gemfile</code> de todas las apps que se construyan en Rails, lo siguiente:</p>

<pre><code>gem 'therubyracer'</code></pre>

<p align="justify">¡Y listo! Ya podemos empezar a desarrollar aplicaciones en RubyOnRails e incluso instalar diferentes versiones tanto del <code>rails</code> como de <code>ruby</code>, simplemente usando una versión que escojamos de RVM y en ella instalar esa otra versión de Rails. Un pequeño ejemplo:</p>

<pre><code>$ rvm gemset create rails3213
$ rvm use ruby-2.1.0@rails3213
$ gem install rails --version=3.2.13</code></pre>

<p align="justify">Ahí podremos ver como instalamos otra versión del rails acoplándola a una nueva gemset creada por nosotros mismos. En dicho caso, para comprobar que están tanto en el gemset creado, como también la otra versión instalada del rails y en uso, tecleamos lo siguiente:</p>

<pre><code>$ rvm gemset list
   (default)
   global
=> rails3213

$ rails -v
Rails 3.2.13</code></pre>

<p align="justify">¡OK! Ésto ha sido todo por ahora, cualquier duda pueden contactarme vía <a href="http://twitter.com/repadev" title="twitter" target="_blank">Twitter</a>, <a href="http://gplus.to/repadev" title="googleplus" target="_blank">Google+</a>, y conectar vía <a href="http://co.linkedin.com/in/IngRafaPA" title="linkedin" target="_blank">LinkedIn</a>.
