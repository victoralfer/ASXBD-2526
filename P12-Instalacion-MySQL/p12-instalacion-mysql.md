<!---------------- PÁGINA 1 ---------------->

<!-- Título Principal (** Texto en Negrita **) -->
  <!-- Los Títulos Principales incorporan 
  una línea debajo que ocupa todo el ancho -->
# **2º ASIR - ASXBD**

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

<!-- Subtítulo -->
## VÍCTOR ÁLVAREZ FERNÁNDEZ

<!-- Subapartados -->
<div id="subapartados">
  <h3 class="titulos-subapartados">Unidad:</h3>
    <h3 class="texto-subapartados">Unidad 1 - Introducción a los SGBD</h3>
  <h3 class="titulos-subapartados">Práctica:</h3>
    <h3 class="texto-subapartados">P12-Instalación-MySQL</h3>
  <h3 class="titulos-subapartados">Fecha:</h3>
    <h3 class="texto-subapartados">7 de Enero de 2026</h3>
</div>

<footer>
  <h6>Víctor Álvarez Fernández - ASXBD - 2º ASIR</h6>
</footer>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 2 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

<!-- Contiene anclajes a los diferentes ejercicios (están en siguientes páginas) -->
# **Índice**

<ol class="indice">
  <li><a href="#descarga">Instalación en Windows 11: MySQL 8.0.44</a>
    <ol>
      <li><a href="#descarga">Descarga MySQL Installer 8.0.44</a></li>
      <li><a href="#instalacion">Instalación MySQL Installer 8.0.44</a></li>
      <li><a href="#configuracion">Configuración MySQL Server 8.0.44</a></li>
      <li><a href="#aplicar-configuracion">Aplicación de Configuración</a></li>
      <li><a href="#activacion-servicio">Activación Servicio MySQL en Windows</a></li>
      <li><a href="#productos-utilidades">Productos y Utilidades</a>
        <ol>
          <li><a href="#mysql-workbench">MySQL Workbench</a></li>
          <li><a href="#mysql-shell">MySQL Shell</a></li>
          <li><a href="#mysql-client">MySQL Command Line Client</a></li>
        </ol>
      </li>
      <li><a href="#mysql-directorios">Directorios de Instalación / Configuración</a>
        <ol>
          <li><a href="#directorio-bin">bin</a></li>
          <li><a href="#directorio-include">include</a></li>
          <li><a href="#directorio-lib">lib</a></li>
          <li><a href="#directorio-share">share</a></li>
          <li><a href="#directorio-data">Data</a></li>
        </ol>
      </li>
      <li><a href="#otras-instalaciones">Otras Instalaciones y Configuraciones</a>
        <ol>
          <li><a href="#visual-c++">Visual C++ v14 Redistributable</a></li>
          <li><a href="#variable-entorno-path">Configurar Variable de Entorno PATH</a></li>
        </ol>
      </li>
    </ol>
  </li>
  <li><a href="#descarga-5">Instalación en Windows 10: MySQL 5.7.44</a>
    <ol>
       <li><a href="#descarga-5">Descarga MySQL Installer 5.7.44</a></li>
       <li><a href="#instalacion-5">Instalación MySQL Installer 5.7.44</a></li>
       <li><a href="#configuracion-5">Configuración MySQL Server 5.7</a></li>
       <li><a href="#aplicar-configuracion-5">Aplicación Configuración</a></li>
       <li><a href="#reconfiguracion-5">Reconfiguración MySQL 5.7.44</a></li>
       <li><a href="#mysql-directorios-5">Directorios de Instalación / Configuración</a></li>
       <li><a href="#variable-entorno-path-5">Configuración Variable de Entorno PATH</a></li>
    </ol>
  </li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 3 ---------------->


<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

<!-- Contiene anclajes a los diferentes ejercicios (están en siguientes páginas) -->
# **Índice**

<ol class="indice" start="3">
  <li><a href="#instalacion-ubuntu">Instalación MySQL en Ubuntu 20.04 LTS</a>
    <ol>
      <li><a href="#instalacion-ubuntu">Instalación MySQL Server</a></li>
      <li><a href="#anadir-usuarios">Añadir y Modificar Usuarios</a></li>
      <li><a href="#configuracion-remoto">Configuracion Acceso Remoto</a></li>
      <li><a href="#acceso-remoto">Acceso desde equipo Remoto</a></li>
      <li><a href="#workbench">Instalación MySQL Workbench</a></li>
      <li><a href="#directorios-ubuntu">Directorios MySQL en Ubuntu</a></li>
    </ol>
  </li>
  <li><a href="#descarga-xampp">MySQL con gestor phpMyAdmin en Windows</a>
    <ol>
      <li><a href="#descarga-xampp">Descarga XAMPP</a></li>
      <li><a href="#instalacion-xampp">Instalación XAMPP</a></li>
      <li><a href="#configuracion-puerto-xampp">Configuración Puerto XAMPP</a></li>
      <li><a href="#inicio-xampp">XAMPP: Inicio Apache y MySQL</a></li>
      <li><a href="#acceso-phpmyadmin">Acceso phpMyAdmin</a></li>
    </ol>
  </li>
  <li><a href="#instalacion-apache">MySQL con gestor phpMyAdmin en Linux</a>
    <ol>
      <li><a href="#instalacion-apache">Instalación Apache</a></li>
      <li><a href="#instalacion-mysql-server">Instalación MySQL Server</a></li>
      <li><a href="#instalacion-workbench">Instalación MySQL Workbench</a></li>
      <li><a href="#instalacion-phpmyadmin">Instalación phpMyAdmin</a></li>
      <li><a href="#acceso-phpmyadmin-linux">Acceso phpMyAdmin</a></li>
    </ol>
  </li>
  <li><a href="#segunda-instancia-windows">Instalación 2ª Instancia en Windows</a></li>
  <li><a href="#segunda-instancia-linux">Instalación 2ª Instancia en Linux</a></li>
</ol>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 4 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="descarga">Descarga MySQL Installer 8.0.44</h1>

<p class="parrafo-primero">Lo primero que tenemos que hacer antes de comenzar el proceso de instalación de MySQL en Windows, es descargar el paquete de archivos binarios deseado desde: <a href="https://dev.mysql.com/downloads/installer" target="_blank" class="blue">https://dev.mysql.com/downloads/installer</a>.</p>

<p class="parrafo-normal">En este caso nos decantamos por la versión 8.0.44, que nos ofrecerá dos posibilidades:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="blue">Web Community</span>: instalación vía web. Descarga sólo los complementos que deseamos instalar posteriormente. Obviamente requiere conexión a Internet para poder continuar con el proceso de instalación.</li>
  <li><span class="blue">Community</span>: instalación offline. Descarga todos los complementos que se ofertan. No requiere conexión a Internet para continuar con el proceso de instalación.</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/instalacion-configuracion/mysql-1-descargar.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 5 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="instalacion">Instalación MySQL Installer 8.0.44</h1>


<p class="parrafo-primero">En esta práctica nos hemos decantado por instalación offline, que aunque requiere una descarga más pesada (558.3M), nos permitirá instalar MySQL en cualquier equipo sin depender de una conexión Internet.</p>

<p class="parrafo-normal">El proceso se inicia con la selección del tipo de instalación que deseamos:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="blue">Server Only</span>: instalacion sólo de MySQL Server</li>
  <li><span class="blue">Client Only</span>: instalacion sólo de las utilidades que se ofertan para los Clientes</li>
  <li><span class="blue">Full</span>: instalacion completa</li>
  <li><span class="blue">Custom</span>: instalacion personalizada</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/instalacion-configuracion/mysql-2-tipo-instalacion.png">
  <p class="num-romano">I</p>
</div>

<p class="parrafo-normal">En nuestro caso, apostaremos por la <span class="green">Instalación personalizada (Custom)</span>.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 6 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Instalación MySQL Installer 8.0.44</h1>


<p class="parrafo-primero">Continuamos con la selección de los productos que deseamos instalar, que serán los siguientes:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="blue">MySQL Server 8.0.44</span>: <span class="purple">Servidor MySQL</span>, que una vez configurado trabaja en segundo plano.</li>
  <li><span class="blue">MySQL Workbench 8.0.44</span>: <span class="purple">Cliente MySQL con interfaz gráfica</span> que nos permite establecer conexiones con diferentes Bases de Datos <span class="cursiva">(Locales o Remotas)</span>. Su panel de control nos permite gestionar usuarios <span class="cursiva">(crear usuarios, gestionar roles, controlar accesos o limitar recursos)</span>. A través del Lenguaje SQL podemos crear Bases de Datos y Tablas, además de cargar datos.</li>
  <li><span class="blue">MySQL Shell 8.0.44</span>: <span class="purple">Cliente MySQL a través de línea de comandos</span>, que nos ofrece la posibilidad de alternar entre lenguajes SQL, JavaScript y Python. Se utiliza en gestión de clústers y configuraciones más avanzadas.</li>
</ol>


<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/instalacion-configuracion/mysql-3-seleccion-productos.png">
  <p class="num-romano">I</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 7 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Instalación MySQL Installer 8.0.44</h1>


<div class="imagenes margen-superior">
  <img src="img/mysql8/instalacion-configuracion/mysql-4-comienzo-instalacion.png">
  <p class="num-romano">II</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/instalacion-configuracion/mysql-5-instalacion-completada.png">
  <p class="num-romano">III</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 8 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="configuracion">Configuración MySQL Installer 8.0.44</h1>


<p class="parrafo-primero">Una vez finalizado el proceso de instalación, es necesario configurar <span class="blue">MySQL Server</span> (el servidor que trabajará en segundo plano).</p>


<h4>Tipo de Servidor y Redes</h4>

<p class="parrafo-normal">La primera elección con la que nos encontramos es la selección del tipo de servidor que deseamos configurar, así como el acceso a nuestro servidor local a través del puerto <span class="cursiva">(TCP 3306 es el predeterminado)</span>.</p>


<ol class="ol-sin-padding-sup-inf">
  <li><span class="blue">Ordenador de Desarrollo</span>: permite la ejecución de varias aplicaciones en diferentes momentos. Consume muy pocos recursos ya que no es un servidor dedicado a la Gestión de Bases de Datos.</li>
  <li><span class="blue">Ordenador Servidor</span>: ofrece el Servicio de Gestión de Base de Datos de manera dedicada, incluyendo la posibilidad de configuración de servicios web, servicios de correo electrónico...</li>
  <li><span class="blue">Ordenador Dedicado</span>: ofrece el Servicio de Gestión de Bases de Datos de manera dedicada. El consumo de recursos es mayor, porque la calidad y potencia del servicio es total.</li>
</ol>


<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/instalacion-configuracion/mysql-6-tipo-redes.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 9 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Configuración MySQL Installer 8.0.44</h1>


<h4>Método de Autenticación</h4>

<p class="parrafo-normal">El instalador de MySQL nos plantea la posibilidad de elegir dos métodos de autenticación:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="blue">Encriptado</span>: es el recomendado para MySQL 8.0.44. Utiliza el algoritmo SHA-256.</li>
  <li><span class="blue">Legacy</span>: en muchos casos es el ideal para integrar productos de terceros o PHP. Es el mótodo de autenticación utilizado en MySQL 5.x.</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/instalacion-configuracion/mysql-7-metodo-autenticacion.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 10 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Configuración MySQL Installer 8.0.44</h1>


<h4>Cuentas y Roles</h4>

<p class="parrafo-normal">En esta pantalla lo prioritario y fundamental es elegir la contraseña para el superusuario 'root'.</p>

<p class="parrafo-normal">También se pueden añadir otros usuarios, asignándoles un rol determinado. <span class="red">En este ejemplo añadiremos al usuario 'estudiante' con un rol de Administrador de la Base de Datos (DB Admin)</span>.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/instalacion-configuracion/mysql-8-añadir-usuarios.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 11 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Configuración MySQL Installer 8.0.44</h1>


<h4>Servicio de Windows</h4>

<p class="parrafo-normal">Esta pantalla nos permite configurar MySQL Server como un servicio de Windows, aplicándole el nombre que deseemos, que de manera predeterminada es MySQL80.</p>

<p class="parrafo-normal">Además, podemos indicar si el servicio arranca con la puesta en marcha del sistema; e incluso la cuenta de usuario que ejecutará el servicio, que es recomendable que sea la cuenta de sistema estándar.</p>

<p class="parrafo-normal green">En este ejemplo nos decantamos por configurar el servicio para que arranque con el usuario de sistema estándar cuando se arranca el equipo.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/instalacion-configuracion/mysql-9-servicio-windows.png">
</div>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 12 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="aplicar-configuracion">Aplicación de la Configuración</h1>


<p class="parrafo-primero">Finalizamos la configuración básica aplicando esta a diversos apartados que dejan el servicio completamento operativo.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/instalacion-configuracion/mysql-10-aplicar-configuracion.png">
  <p class="num-romano">I</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/instalacion-configuracion/mysql-11-configuracion-completa.png">
  <p class="num-romano">II</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 13 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="activacion-servicio">Activación Servicio</h1>


<h4>Consola de Servicios (services.msc)</h4>

<p class="parrafo-normal">Aunque en la ventana 'Servicio de Windows' ya indicamos que este arrancaría de manera automática bajo el nombre MySQL80; esta configuración podemos modificarla desde la Consola de Servicios.</p>

<h4>Línea de Comandos (CMD)</h4>

<p class="parrafo-normal">El servicio se pueda parar, arrancar o reiniciar desde la Línea de Comandos con <span class="red">net <span class="blue">[stop/start/restart]</span> MySQL80</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/instalacion-configuracion/mysql-12-consola-servicios.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 14 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="productos-utilidades">Productos y Utilidades</h1>


<h4 id="mysql-workbench">MySQL Workbench</h4>

<p class="parrafo-normal">Es un cliente MySQL con interfaz gráfica</span> que nos permite establecer conexiones con diferentes Bases de Datos <span class="cursiva">(Locales o Remotas)</span>.</p>

<p class="parrafo-normal">La conexión con el MySQL Server (servidor local) ya quedó configurada con anterioridad como podemos observar en la imagen inferior. El acceso a ella se realiza con los siguientes parámetros:</p>

<ol class="ol-sin-padding-sup-inf">
  <li>Host: localhost(127.0.0.1)</li>
  <li>Puerto: 3306</li>
  <li>Usuario: root</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/cliente-mysql/cliente-mysql-workbench-1.png">
</div>

<p class="parrafo-primero">El interfaz (panel de control) de MySQL Workbench también nos permite gestionar usuarios <span class="cursiva">(crear usuarios, gestionar roles, controlar accesos o limitar recursos)</span>.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 15 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Productos y Utilidades</h1>


<p class="parrafo-primero">Pueden crearse todas las conexiones necesarias añadiendo un nombre a la conexión, el host y puerto que utiliza, además del usuario con el que se pretende acceder a ella.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/cliente-mysql/workbench-1-programa.png">
</div>

<p class="parrafo-primero">Accediendo al servidor deseado (local o remoto), mediante el lenguaje SQL podemos crear Bases de Datos y Tablas, cargar los datos y realizar la consultas necesarias.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/cliente-mysql/workbench-2-acceso.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 16 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Productos y Utilidades</h1>


<h4 id="mysql-shell">MySQL Shell</h4>

<p class="parrafo-normal">Es un cliente MySQL a través de línea de comandos</span>, que nos ofrece la posibilidad de alternar entre lenguajes SQL, JavaScript y Python. Se utiliza en gestión de clústers, importación de grandes volúmenes de datos, así como otras configuraciones más avanzadas.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/cliente-mysql/cliente-mysql-shell-2.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 17 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Productos y Utilidades</h1>


<h4 id="mysql-client">MySQL Command Line Client</h4>

<p class="parrafo-normal">Es un cliente MySQL básico a través de línea de comandos</span>, que nos permite utilizar el lenguaje SQL para crear bases de datos y tablas, además de cargar los datos que se deseen o realizar todo tipo de consultas. Requiere acceso como administrador.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/cliente-mysql/cliente-mysql-command-3.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 18 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="mysql-directorios">Directorios Instalación / Configuración</h1>


<h4 id="directorio-bin">Directorio bin</h4>

<p class="parrafo-normal green">C:\Archivos de Programa\MySQL\MySQL Server 8.0\bin</p>

<p class="parrafo-normal">Este directorio almacena los programas ejecutables que permiten el funcionamiento del Servidor MySQL. Vamos a destacar los siguientes:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">mysqld</span>: Motor del Servidor SQL. Trabajando en segundo plano se encarga entre otras cosas de la gestión de archivos, el procesamiento de consultas, la seguridad, los permisos y las conexiones múltiples al propio servidor.</li>
  <li><span class="purple">mysqldump</span>: Cliente encargado de realizar las Copias de Seguridad. Trabaja en segundo plano.</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/ejecutables-bin.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 19 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Directorios Instalación / Configuración</h1>


<h4 id="directorio-include">Directorio include</h4>

<p class="parrafo-normal green">C:\Archivos de Programa\MySQL\MySQL Server 8.0\include</p>

<p class="parrafo-normal">La carpeta 'include' es fundamental si tenemos pensado desarrollar aplicaciones propias que se conecten directamente a MySQL utilizando lenguajes como C o C++.</p>


<h4 id="directorio-lib">Directorio lib</h4>

<p class="parrafo-normal green">C:\Archivos de Programa\MySQL\MySQL Server 8.0\lib</p>


<p class="parrafo-normal">La carpeta 'lib' es el complemento directo de la carpeta include. Si include contiene los archivos que el programador lee para saber cómo escribir el código, 'lib' contiene los archivos que el ordenador utiliza para ejecutar ese código.</p>


<h4 id="directorio-share">Directorio share</h4>

<p class="parrafo-normal green">C:\Archivos de Programa\MySQL\MySQL Server 8.0\share</p>

<p class="parrafo-normal">La carpeta 'share' es la biblioteca de recursos de MySQL. Mientras que 'bin' tiene los programas y 'lib' el código para que funcionen, share contiene toda la información de apoyo, principalmente textos y configuraciones que el servidor necesita consultar. Dentro podemos encontrar un directorio por cada idioma.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 20 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Directorios Instalación / Configuración</h1>


<h4 id="directorio-data">Directorio Data</h4>

<p class="parrafo-normal green">C:\ProgramData\MySQL\MySQL Server 8.0\Data</p>

<p class="parrafo-normal">Es un directorio que permanece oculto y almacena las Bases de Datos, así como los archivos de registro y error.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/data-oculto.png">
</div>


<h4 class="margen-superior-interior">Fichero my.ini</h4>

<p class="parrafo-normal">El fichero <span class="purple">my.ini</span>, que encontramos dentro del 'directorio Data', permite cambiar diferentes parámetros de la configuración.</p>

<p class="parrafo-normal">Este fichero lo podemos modificar, accediendo como administrador con el programa 'Bloc de Notas'.</p>

<p class="parrafo-normal blue">Puerto Predeterminado del Servidor Local (línea 61)</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/fichero-configuracion/my-1-puerto.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 21 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Directorios Instalación / Configuración</h1>

<p class="parrafo-primero blue">Carpeta de almacenamiento de las Bases de Datos (línea 97) - Data</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/fichero-configuracion/my-2-datadir.png">
</div>

<p class="parrafo-primero blue">Carpeta de almacenamiento de las importaciones de datos (línea 167) - Uploads</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/fichero-configuracion/my-3-secure-file.png">
</div>

<p class="parrafo-primero">Cuando se hacen modificaciones en este fichero, es necesario reiniciar el Servicio MYSQL80: <span class="red">net <span class="green">restart</span> MYSQL80</span></p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 22 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="otras-instalaciones">Otras Instalaciones y Configuraciones</h1>


<h4 id="visual-c++">Visual C++ v14 Redistributable</h4>

<p class="parrafo-normal">Si el equipo donde se pretende instalar y configurar MySQL Server no cuenta con el componente Visual C++ Redistributable, será necesario descargarlo e instalarlo.</p>

<p class="parrafo-normal" style="text-align: center;"><a href="https://aka.ms/vc14/vc_redist.x64.exe" target="_blank" class="blue">Descargar Versión Visual C++ v14 Redistributable</a></p>

<p class="parrafo-normal">Microsoft Visual C++ Redistributable es un paquete de librerías esenciales que permiten que aplicaciones desarrolladas con el lenguaje C++, como MySQL 8.0, funcionen correctamente en Windows.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/otras/visual-c-redistributable.png">
</div>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 23 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Otras Instalaciones y Configuraciones</h1>


<h4 id="variable-entorno-path">Configurar Variable de Entorno PATH</h4>

<p class="parrafo-normal">Configurar la variable de entorno PATH con la ruta de acceso a los programas de MySQL Server, permite al Símbolo de Sistema (CMD) utilizar esos programas sin tener que indicar la ruta completa cada vez que se quiere acceder a ellos.</p>

<p class="parrafo-normal">Ruta: <span class="green">C:\Archivos de Programa\MySQL\MySQL Server 8.0\bin</span></p>


<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/otras/variable-entorno-server.png">
</div>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 24 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Otras Instalaciones y Configuraciones</h1>


<p class="parrafo-primero">Comando: <span class="green">mysql</span> <span class="blue">-u root</span> <span class="purple">-p</span></p>

<ol>
  <li><span class="blue">-u root</span>: esta opción indica que el usuario con el que queremos acceder al programa mysql es 'root'.</li>
  <li><span class="purple">-p</span>: esta opción solicita que se pida la contraseña que se configuró en la instalación.</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql8/otras/acceso-cmd.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 25 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="descarga-5">Descarga MySQL Installer 5.7.44</h1>


<p class="parrafo-primero">Lo primero que tenemos que hacer antes de comenzar el proceso de instalación de MySQL en Windows, es descargar el paquete de archivos binarios deseado desde: <a href="https://dev.mysql.com/downloads/installer" target="_blank" class="blue">https://dev.mysql.com/downloads/installer</a>.</p>

<p class="parrafo-normal">En este caso nos decantamos por la versión 5.7.44, que nos ofrecerá dos posibilidades:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="blue">Web Community</span>: instalación vía web. Descarga sólo los complementos que deseamos instalar posteriormente. Obviamente requiere conexión a Internet para poder continuar con el proceso de instalación.</li>
  <li><span class="blue">Community</span>: instalación offline. Descarga todos los complementos que se ofertan. No requiere conexión a Internet para continuar con el proceso de instalación.</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/1-descarga.png" width="80%">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 26 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="instalacion-5">Instalación MySQL Installer 5.7.44</h1>


<p class="parrafo-primero">En esta práctica nos hemos decantado por instalación offline, que aunque requiere una descarga más pesada (373.7M), nos permitirá instalar MySQL en cualquier equipo sin depender de una conexión Internet.</p>

<p class="parrafo-normal">El proceso se inicia con la selección del tipo de instalación que deseamos:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="blue">Server Only</span>: instalacion sólo de MySQL Server</li>
  <li><span class="blue">Client Only</span>: instalacion sólo de las utilidades que se ofertan para los Clientes</li>
  <li><span class="blue">Full</span>: instalacion completa</li>
  <li><span class="blue">Custom</span>: instalacion personalizada</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/2-tipo-instalacion.png">
  <p class="num-romano">I</p>
</div>

<p class="parrafo-normal">En nuestro caso, apostaremos por la <span class="green">Instalación personalizada (Custom)</span>.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 27 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Instalación MySQL Installer 5.7.44</h1>


<p class="parrafo-primero">Continuamos con la selección de los productos que deseamos instalar, que serán los siguientes:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="blue">MySQL Server 5.7.44</span>: <span class="purple">Servidor MySQL</span>, que una vez configurado trabaja en segundo plano.</li>
  <li><span class="blue">MySQL Workbench 8.0.34</span>: <span class="purple">Cliente MySQL con interfaz gráfica</span> que nos permite establecer conexiones con diferentes Bases de Datos <span class="cursiva">(Locales o Remotas)</span>. Su panel de control nos permite gestionar usuarios <span class="cursiva">(crear usuarios, gestionar roles, controlar accesos o limitar recursos)</span>. A través del Lenguaje SQL podemos crear Bases de Datos y Tablas, además de cargar datos.</li>
  <li><span class="blue">MySQL Shell 8.0.35</span>: <span class="purple">Cliente MySQL a través de línea de comandos</span>, que nos ofrece la posibilidad de alternar entre lenguajes SQL, JavaScript y Python. Se utiliza en gestión de clústers y configuraciones más avanzadas.</li>
  <li><span class="blue">MySQL Documentation 5.7.44</span>: es el manual de MySQL 5.7.44 con toda la documentación oficial de interés.</li>
  <li><span class="blue">Samples and Examples 5.7.44</span>: muestras y ejemplos de la versión en cuestión.</li>
</ol>


<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/3-seleccion-productos.png">
  <p class="num-romano">I</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 28 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Instalación MySQL Installer 5.7.44</h1>


<h4>Chequeo de Requirimientos</h4>

<p class="parrafo-normal">Antes de comenzar la instalación, MySQL Installer 5.7.44 realiza un chequeo para detectar necesidades de los programas que queremos instalar.</p>

<p class="parrafo-normal">En nuestro caso, los tres programas que hemos seleccionado (MySQL Server, MySQL Workbench y MySQLShell) requieren del componente Microsoft Visual C++ 2019 Redistributable.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/4-requerimientos.png">
  <p class="num-romano">II</p>
</div>

<p class="parrafo-primero">El componente Microsoft Visual C++ 2019 Redistributable, se podrá instalar desde el propio asistente de configuración.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/5-visual-redistributable.png">
  <p class="num-romano">III</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 29 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Instalación MySQL Installer 5.7.44</h1>


<p class="parrafo-primero">Tras la instalación del componente solicitado, la instalación a través de MySQL Installer 5.7.44, continúa con total normalidad.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/6-comienzo-instalacion.png">
  <p class="num-romano">IV</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/7-instalacion-finalizada.png">
  <p class="num-romano">V</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 30 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="configuracion-5">Configuración MySQL Installer 5.7.44</h1>


<p class="parrafo-primero">Una vez finalizado el proceso de instalación, es necesario configurar <span class="blue">MySQL Server</span> (el servidor que trabajará en segundo plano).</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/8-comienza-configuracion.png">
</div>

<h4 class="margen-superior-interior">Tipo de Servidor y Redes</h4>

<p class="parrafo-normal">La primera elección con la que nos encontramos es la selección del tipo de servidor que deseamos configurar, así como el acceso a nuestro servidor local a través del puerto <span class="cursiva">(TCP 3306 es el predeterminado)</span>.</p>


<ol class="ol-sin-padding-sup-inf">
  <li><span class="blue">Ordenador de Desarrollo</span>: permite la ejecución de varias aplicaciones en diferentes momentos. Consume muy pocos recursos ya que no es un servidor dedicado a la Gestión de Bases de Datos.</li>
  <li><span class="blue">Ordenador Servidor</span>: ofrece el Servicio de Gestión de Base de Datos de manera dedicada, incluyendo la posibilidad de configuración de servicios web, servicios de correo electrónico...</li>
  <li><span class="blue">Ordenador Dedicado</span>: ofrece el Servicio de Gestión de Bases de Datos de manera dedicada. El consumo de recursos es mayor, porque la calidad y potencia del servicio es total.</li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 31 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Configuración MySQL Installer 5.7.44</h1>


<div class="imagenes margen-superior">
  <img src="img/mysql5/9-tipo-red.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 32 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Configuración MySQL Installer 5.7.44</h1>


<h4>Cuentas y Roles</h4>

<p class="parrafo-normal">En esta pantalla lo prioritario y fundamental es elegir la contraseña para el superusuario 'root'.</p>

<p class="parrafo-normal">También se pueden añadir otros usuarios, asignándoles un rol determinado.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/10-autenticacion.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 33 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Configuración MySQL Installer 5.7.44</h1>


<h4>Servicio de Windows</h4>

<p class="parrafo-normal">Esta pantalla nos permite configurar MySQL Server como un servicio de Windows, aplicándole el nombre que deseemos, que de manera predeterminada es MySQL57.</p>

<p class="parrafo-normal">Además, podemos indicar si el servicio arranca con la puesta en marcha del sistema; e incluso la cuenta de usuario que ejecutará el servicio, que es recomendable que sea la cuenta de sistema estándar.</p>

<p class="parrafo-normal green">En este ejemplo nos decantamos por configurar el servicio para que arranque con el usuario de sistema estándar cuando se arranca el equipo.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/11-servicio-windows.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 34 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Configuración MySQL Installer 5.7.44</h1>


<h4>Permisos de los Archivos del Servidor</h4>

<p class="parrafo-normal">En esta ventana, marcamos la casillas que nos dice: <span class="blue">"Sí, conceder acceso total únicamente al usuario que ejecuta el servicio de Windows (si aplica) y al grupo de administradores. Otros usuarios y grupos no tendrán acceso."</span>.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/12-permisos.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 35 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="aplicar-configuracion-5">Aplicar Configuración</h1>

<p class="parrafo-primero">Finalizamos la configuración básica aplicando esta a diversos apartados que dejan el servicio completamento operativo.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/14-configuracion-aplicada.png">
  <p class="num-romano">I</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/15-configuracion-completada.png">
  <p class="num-romano">II</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 36 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="reconfiguracion-5">Reconfiguración MySQL Server 5.7.44</h1>

<p class="parrafo-primero">Anteriormente el proceso de reconfiguración se realizaba desde <span class="cursiva">MySQLInstanceConfig</span>, que podiamos encontrar en el directorio 'bin'. Actualmente, la versión <span class="blue">MySQL Installer</span>, tanto para MySQL 5.x como para MySQL 8.x, se encarga del proceso de reconfiguración.</p>

<p class="parrafo-normal">Desde el asistente se puede reconfigurar el tipo de servidor (menor a mayor dedicación de recursos del equipo), la conexión de red y si queremos que MySQL Server actue como un servicio o un programa más en el S.0.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/16-reconfiguracion.png">
</div>

<p class="parrafo-primero">Una vez creada la nueva configuración, se genera un archivo (a modo copia de seguridad) con la antigua configuración. Tanto la configuración actual, como las copias de seguridad anteriores se almacenan en: <span class="green">C:\ProgramData\MySQL\MySQL Server 5.7</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/17-nueva-configuracion.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 37 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Reconfiguración MySQL Server 5.7.44</h1>


<p class="parrafo-primero">El resto de criterios se deben reconfigurar manualmente desde el <span class="blue">fichero my.ini</span> que podemos encontrar en: <span class="green">C:\ProgramData\MySQL\MySQL Server 5.7</span>.</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">port</span>: es el puerto del Servidor Local. <span class="cursiva">Línea 61</span> del fichero my.ini.</li>
  <li><span class="purple">datadir</span>: directorio donde se almacenan las Bases de Datos creadas. <span class="cursiva">Línea 97</span> del fichero my.ini.</li>
  <li><span class="purple">secure-file-priv</span>: directorio desde el que se importan los datos. <span class="cursiva">Línea 161</span> del fichero my.ini.</li>
  <li><span class="purple">default-storage-engine</span>: motor por defecto. <span class="cursiva">Línea 104</span> del fichero my.ini.</li>
  <li><span class="purple">max_connections</span>: número máximo de conexiones simultáneas. <span class="cursiva">Línea 167</span> del fichero my.ini.</li>
  <li><span class="purple">character-set-server</span>: juego de caracteres (utf8mb4 es el habitual). <span class="cursiva">Línea 101</span> del fichero my.ini.</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/18-my-ini.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 38 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="mysql-directorios-5">Directorios de Instalación / Configuración</h1>


<h4>Directorios 'bin', 'include', 'lib' y 'share'</h4>

<p class="parrafo-normal">En estos directorios encontramos configuración relacionada con el servidor (MySQL Server).</p>

<p class="parrafo-normal green">C:\Archivos de Programa\MySQL\MySQL Server 5.7</p>


<h4>Directorio 'Data' (oculto)</h4>

<p class="parrafo-normal">En este directorio se encuentran las Bases de Datos creadas.</p>

<p class="parrafo-normal green">C:\ProgramData\MySQL\MySQL Server 5.7\Data</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 39 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="variable-entorno-path-5">Configuración Variable Entorno PATH</h1>

<p class="parrafo-primero">Configurar la variable de entorno PATH con la ruta de acceso a los programas de MySQL Server, permite al Símbolo de Sistema (CMD) utilizar esos programas sin tener que indicar la ruta completa cada vez que se quiere acceder a ellos.</p>

<p class="parrafo-normal">Ruta: <span class="green">C:\Archivos de Programa\MySQL\MySQL Server 5.7\bin</span></p>


<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/19-añadir-variable-entorno-server.png">
  <p class="num-romano">I</p>
</div>

<h4 class="margen-superior-interior">Acceso desde CMD</h4>

<p class="parrafo-primero">Comando: <span class="green">mysql</span> <span class="blue">-u root</span> <span class="purple">-p</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/mysql5/20-acceso-cmd-mysql.png" width="80%">
  <p class="num-romano">II</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 40 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="instalacion-ubuntu">Instalación MySQL en Ubuntu</h1>


<p class="parrafo-primero">Como con cualquier otra instalación, se recomienda realizar con anterioridad una actualización de los paquetes que pueden ser instalados en el equipo:</p>

<p class="parrafo-normal green">apt update</p>

<p class="parrafo-normal">Tras esta recomendación, procedemos a la instalación del MySQL Server:</p>

<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/1-instalacion.png">
</div>

<h4>Comprobación Estado del Servicio MySQL</h4>

<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/2-comprobacion-estado-servicio.png">
</div>

<h4>Comprobación Acceso al Servicio</h4>

<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/3-acceso-mysql.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 41 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="anadir-usuarios">Añadir y Modificar Usuarios</h1>


<h4>Añadir un Usuario Local</h4>

<p class="parrafo-normal">Para añadir un usuario en MySQL Server, primeramente ingresamos en el propio servidor con el comando <span class="blue">mysql</span>. Posteriormente, introducimos la sentencia SQL requerida.</p>

<p class="parrafo-normal green"><span class="purple">create user</span> alumno@localhost identified by 'abc123.';</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">create user</span>: permite crear un usuario.</li>
  <li><span class="green">alumno@localhost</span>: se introduce el nombre del usuario deseado, acompañado del símbolo @ y una dirección IP. Al ser el usuario local se puede utilizar 'localhost'.</li>
  <li><span class="green">identified by</span>: permite añadir una contraseña de identificación para el usuario que estamos creando.</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/4-añadir-usuario-local.png">
</div>

<p class="parrafo-normal">Tras la creación del nuevo usuario, será necesario actualizar privilegios.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/5-actualizar-privilegios.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 42 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Añadir y Modificar Usuarios</h1>


<h4>Acceso Usuarios Locales</h4>

<p class="parrafo-normal">Para acceder en Ubuntu con cualquiera de los usuarios locales a MySQL Server, utilizamos el comando:</p>

<p class="parrafo-normal green">mysql -u alumno p</p>

<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/6-acceso-usuario-local.png">
</div>


<h4>Modificación Usuarios</h4>

<p class="parrafo-normal">Para modificar un usuario en MySQL Server, ingresamos primero en el propio servidor con el comando <span class="blue">mysql</span>. Posteriormente, introducimos la sentencia SQL requerida.</p>

<p class="parrafo-normal cursiva">Aprovechamos este ejemplo para asignarle una contraseña al usuario 'root', la cual será solicitada a partir de ahora para acceder a MySQL Server.</p>

<p class="parrafo-normal green"><span class="purple">alter user</span> root@localhost identified <span class="red">with mysql_native_password</span> by 'abc123.';</p>

<p class="parrafo-normal">Tras la modificación, será necesario actualizar privilegios.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/7-modificar-usuario-root-pedir-contraseña.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 43 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Añadir y Modificar Usuarios</h1>


<h4>Acceso Usuarios Remotos</h4>

<p class="parrafo-normal">Para añadir un usuario remoto en MySQL Server, ingresamos en el propio servidor con el comando <span class="blue">mysql</span>. Posteriormente, introducimos la sentencia SQL requerida.</p>

<p class="parrafo-normal green"><span class="purple">create user</span> <span class="brown">externo@'%'</span> identified by 'abc123.';</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">create user</span>: permite crear un usuario.</li>
  <li><span class="brown">externo@'%'</span>: se introduce el nombre del usuario deseado, acompañado del símbolo @ y el símbolo '%' entrecomillado. Esta sintaxis se utiliza para que ese usuario pueda acceder desde cualquier dirección IP que pertenenza a la LAN.</li>
  <li><span class="green">identified by</span>: permite añadir una contraseña de identificación para el usuario que estamos creando.</li>
</ol>


<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/8-creacion-acceso-usuario-remoto.png">
</div>


<p class="parrafo-normal">Tras la modificación, será necesario actualizar privilegios.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/9-actualizar-permisos.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 44 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="configuracion-remoto">Configuración Acceso Remoto</h1>


<p class="parrafo-primero">Para poder acceder de manera remota a MySQL con otro equipo de la LAN, será necesario realizar una modificación en el fichero de configuración principal de MySQL Server:</p>

<p class="parrafo-normal purple">nano <span class="green">/etc/mysql/mysql.conf.d/mysqld.cnf</span></p>


<p class="parrafo-normal">Concretamente se debe modificar la directiva <span class="blue">bind-address</span> cuya IP apunta a Localhost (127.0.0.1) y establecer <span class="brown">0.0.0.0</span>. Este nuevo parámetro permitirá acceder de manera remota a MySQL Server desde cualquier equipo de la red local.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/10-fichero-configuracion.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 45 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="acceso-remoto">Acceso desde Equipo Remoto</h1>


<h4>Instalación de Cliente MySQL</h4>

<p class="parrafo-normal">Para poder acceder de manera remota desde un equipo de la red local, este deberá tener instalado un Cliente MySQL.</p>

<p class="parrafo-normal">En este ejemplo instalaremos un cliente MySQL es un equipo Debian 12, pero se podría acceder desde un equipo Windows con los clientes 'Command Lines Client' o 'MySQL Workbench'.</p>

<p class="parrafo-normal green">apt install <span class="blue">default-mysql-client</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/11-instalar-client-equipo-red.png">
</div>


<h4>Prueba de Acceso Remoto</h4>

<p class="parrafo-normal">Desde la terminal, y una vez instalado el Cliente MySQL, utilizamos el siguiente comando:</p>


<p class="parrafo-normal green">mysql <span class="blue">-h 192.168.1.82</span> <span class="brown">-u externo</span> <span class="purple">-p</span></p>


<ol class="ol-sin-padding-sup-inf">
  <li><span class="blue">-h 192.168.1.82</span>: esta opción permite introducir la dirección IP o el nombre del host donde se encuentra instalado MySQL Server.</li>
  <li><span class="brown">-u externo</span>: esta opción indica el usuario con el que se pretende acceder a MySQL Server.</li>
  <li><span class="purple">-p</span>: esta opción se utiliza para pedir la contraseña de acceso del usuario mencionado anteriormente.</li>
</ol>


<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/12-acceso-externo.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 46 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="workbench">Instalación MySQL Workbench</h1>


<p class="parrafo-primero">El paquete con la utilidad MySQL Workbench no se encuentra en los respositorios de APT ni de APT-GET por lo que tendremos que instalar SNAPD.</p>

<p class="parrafo-normal green">apt install spapd</p>

<p class="parrafo-normal">Una vez instalado SNAPD, procedemos a instalar MySQL Workbench:</p>

<p class="parrafo-normal green">snapd install mysql-workbench-community</p>

<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/13-instalar-workbench.png">
</div>


<h4>Acceso MySQL Workbench</h4>

<p class="parrafo-normal">El acceso a MySQL Workbench se podrá realizar desde el entorno gráfico de Ubuntu 20.04 LTS, como podemos observar en la imagen.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/14-workbench.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 47 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="directorios-ubuntu">Directorios MySQL en Ubuntu</h1>


<h4>Almacén de las Bases de Datos</h4>

<p class="parrafo-normal green">/var/lib/mysql</p>

<p class="parrafo-normal">Almacena las Bases de Datos creadas en el Servidor.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/15-var-lib-mysql.png">
</div>


<h4>Registros de Errores y Alertas</h4>

<p class="parrafo-normal green">/var/log/mysql</p>

<p class="parrafo-normal">Registros y alertas del Servicio MySQL.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/16-var-log.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 48 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Directorios MySQL en Ubuntu</h1>


<h4>Directorio con Ficheros de Configuración</h4>

<p class="parrafo-normal green">/etc/mysql</p>

<p class="parrafo-normal">Contiene todos los ficheros de configuración. Mención especial para <span class="blue">my.cnf</span> que nos mostrará entre otros el fichero de configuración principal <span class="brown">/etc/mysql/mysql.conf.d/mysqld.cnf</span> en el que ya realizamos modificaciones anteriormente para permitir el acceso remoto.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/ubuntu/17-etc-mysql.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 49 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="descarga-xampp">MySQL con phpMyAdmin - Windows</h1>


<h4>Descarga XAMPP</h4>

<p class="parrafo-normal">Lo primero que haremos es descargar e instalar la aplicación XAMPP para que actue de servidor web local, algo fundamental para utilizar el gestor web phpMyAdmin.</p>

<p class="parrafo-normal">Web Descarga: <a href="https://www.apachefriends.org/es/download.html" target="_blank" class="blue">https://www.apachefriends.org/es/download.html</a></p>


<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/windows/1-xampp-descarga.png">
</div>

<p class="parrafo-primero">Nos decantaremos por descargar la última versión publicada para el Sistema Operativo Windows, que es la 8.2.12.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 50 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>MySQL con phpMyAdmin - Windows</h1>


<h4 id="instalacion-xampp">Instalación XAMPP</h4>

<p class="parrafo-normal">Una vez descargado el paquete de instalación de XAMPP, procedemos a ejecutarlo para que comience el proceso.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/windows/2-xampp-comienza-instalacion.png" width="80%">
  <p class="num-romano">I</p>
</div>

<p class="parrafo-primero">Seleccionamos los componentes necesarios para nuestro objetivo que son <span class="blue">MySQL</span> y <span class="blue">phpMyAdmin</span>:</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/windows/3-xampp-componentes.png" width="80%">
  <p class="num-romano">II</p>
</div>

<p class="parrafo-primero">Seleccionamos la ruta de instalación de XAMPP:</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/windows/4-xampp-directorio.png" width="80%">
  <p class="num-romano">III</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 51 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>MySQL con phpMyAdmin - Windows</h1>


<h4 id="configuracion-puerto-xampp">Configuración Puerto XAMPP</h4>

<p class="parrafo-normal">Como en este equipo Windows ya tenemos instalado MySQL en el puerto 3306, tendremos que realizar una serie de modificaciones en XAMPP para poder arrancar phpMyAdmin de manera correcta.</p>

<p class="parrafo-normal">Abrimos el Panel de Control de XAMPP. Pulsamos en el botón 'Config' correspondiente al servicio MySQL. Al pulsarlo, se despliega un menú contextual con la opción <span class="purple">my.ini</span>, en la que haremos click.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/windows/5-xampp.png">
  <p class="num-romano">I</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/windows/6-mysql-my-ini.png">
  <p class="num-romano">II</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 52 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>MySQL con phpMyAdmin - Windows</h1>

<p class="parrafo-primero">El fichero <span class="purple">my.ini</span> se abrirá en un Bloc de Notas. Tendremos que modificar tanto en la sección <span class="blue">[client]</span> como en <span class="blue">[mysqld]</span> el puerto. En nuestro caso, nos hemos decantado por el 3310.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/windows/7-mysql-my-ini-cambio-puerto.png" width="75%">
  <p class="num-romano">III</p>
</div>

<p class="parrafo-primero">También tendremos que modificar el puerto en la <span class="purple">Configuración General de XAMPP</span>. Dentro del Panel de Control clickamos en el botón 'Config' <span class="cursiva">(tiene una llave inglesa al lado)</span>. Se abrirá una nueva ventana en la que haremos click en 'Service and Port Settings'. Para finalizar en la ventana emergente seleccionamos la pestaña MySQL y cambiamos el puerto a 3310.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/windows/8-cambiar-puerto-configuracion-xampp.png">
  <p class="num-romano">IV</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 53 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>MySQL con phpMyAdmin - Windows</h1>

<p class="parrafo-primero">Por último, tendremos que añadir el puerto en el servidor local modificando el fichero <span class="purple">config.inc</span> <span class="cursiva">(desde el Bloc de Notas y como administrador)</span> que localizaremos en la siguiente ruta:</p>

<p class="parrafo-normal green">C:\xampp\phpMyAdmin\<span class="purple">config.inic</span>.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/windows/9-cambiar-puerto-xampp-phpmyadmin-config-inc.png">
  <p class="num-romano">V</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 54 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>MySQL con phpMyAdmin - Windows</h1>


<h4 id="inicio-xampp">XAMPP: Inicio Apache y MySQL</h4>

<p class="parrafo-normal">Ya tenemos todo preparado para poder arrancar tanto el Servidor Web (Apache) como el Servidor MySQL. Para ello, abrimos el Panel de Control de XAMPP e iniciamos los servicios Apache y MySQL.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/windows/10-iniciar-apache-mysql.png">
</div>


<h4 id="acceso-phpmyadmin">Acceso phpMyAdmin</h4>

<p class="parrafo-normal">Una vez iniciado Apache y MySQL, desde cualquiera de los navegadores que tengamos instalado <span class="cursiva">(Chrome, Firefox...)</span>, podremos acceder al gestor phpMyAdmin tecleando la siguiente URL:</p>

<p class="parrafo-normal green">https://localhost/phpmyadmin</p>


<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/windows/11-acceso-phpmyadmin.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 55 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="instalacion-apache">MySQL con phpMyAdmin - Linux</h1>


<h4>Instalación Apache</h4>

<p class="parrafo-normal">Para afrontar cualquier instalación de manera adecuada en Linux, se recomienda primeramente actualizar los paquetes disponibles:</p>

<p class="parrafo-normal green">apt update</p>

<p class="parrafo-normal">Una vez actualizados los paquetes, comenzaremos con la instalación del Servidor Web Apache, fundamental para poder acceder al gestor phpMyAdmin en Linux.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/linux/1-instalacion-apache.png">
</div>

<p class="parrafo-primero">Ahora es el momento de comprobar que el Servidor Web Apache se ha instalado correctamente. Para ello, accedemos desde una navegador web a la dirección del localhost (Servidor Local).</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/linux/2-apache-instalado.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 56 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>MySQL con phpMyAdmin - Linux</h1>


<h4 id="instalacion-mysql-server">Instalación MySQL Server</h4>

<p class="parrafo-normal">Una vez que se ha instalado el Servidor Web Apache, el siguiente paso será instalar desde la terminal el Servidor MySQL (MySQL Server).</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/linux/3-instalacion-mysql.png">
</div>

<p class="parrafo-primero">Para mayor seguridad, modificamos el usuario 'root' con el objetivo de que al acceder a MySQL Server nos pida su contraseña.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/linux/4-contraseña-usuario-root.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 57 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>MySQL con phpMyAdmin - Linux</h1>


<p class="parrafo-primero">Comprobamos que los cambios se han realizado correctamente, intentando acceder con el usuario 'root' a MySQL.</p>

<p class="parrafo-normal brown">mysql -u root -p</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/linux/5-acceso-usuario-root-contraseña.png">
</div>


<h4 id="instalacion-workbench">Instalación MySQL Workbench</h4>

<p class="parrafo-normal">Procedemos a instalar el cliente MySQL Workbench. Este paquete no se encuentra ni en APT ni en APT-GET, por lo que su instalación se llevará a cabo desde SNAP.</p>

<p class="parrafo-normal green">snap install mysql-worbench-community</p>


<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/linux/6-instalacion-workbench.png">
</div>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 58 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>MySQL con phpMyAdmin - Linux</h1>


<h4 id="instalacion-phpmyadmin">Instalación phpMyAdmin</h4>

<p class="parrafo-normal">El último paquete que instalaremos será el del gestor phpMyAdmin, que nos permitirá gestionar nuestras Bases de Datos.</p>

<p class="parrafo-normal green">apt install phpmyadmin</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/linux/7-comienzo-instalacion-phpmyadmin.png">
  <p class="num-romano">I</p>
</div>

<p class="parrafo-primero">Durante el proceso de instalación, nos pedirá seleccionar el Servidor Web que deseamos utilizar. En nuestro caso, nos decanteremos por Apache <span class="cursiva">(apache2)</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/linux/8-configuracion-servidor-web.png">
  <p class="num-romano">II</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 59 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>MySQL con phpMyAdmin - Linux</h1>


<p class="parrafo-primero">Otro de los pasos en el proceso de instalación será configurar la Base de Datos para phpMyAdmin, algo a lo que responderemos afirmativamente. La instalación también nos pedirá una contraseña para que phpMyAdmin se registre con el Servidor de Bases de Datos <span class="cursiva">(dejaremos este campo sin rellenar)</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/linux/9-instalacion-base-datos.png" width="95%">
  <p class="num-romano">III</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/linux/10-solicitud-contraseña-base-datos-no-necesario.png" width="95%">
  <p class="num-romano">IV</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 60 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>MySQL con phpMyAdmin - Linux</h1>


<h4 id="acceso-phpmyadmin-linux">Acceso phpMyAdmin</h4>

<p class="parrafo-normal">Tras la finalizar la instalación de phpMyAdmin, desde un navegador web accedemos al gestor web desde la URL: <span class="green">https://localhost/phpmyadmin</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/linux/11-acceso-root.png" width="75%">
  <p class="num-romano">I</p>
</div>

<p class="parrafo-primero">Introducimos el usuario 'root' y su contraseña:</p>

<div class="imagenes margen-superior-interior">
  <img src="img/phpMyAdmin/linux/12-phpmyadmin.png">
  <p class="num-romano">II</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 61 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="segunda-instancia-windows">Instalación 2ª Instancia - Windows</h1>


<h4>Descargar MySQL Community Server</h4>

<p class="parrafo-normal">Desde la página oficial de MySQL, descargamos la versión ZIP de MySQL Community Server 8.4.7 LTS.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/segunda-instancia-win/1-descarga-version-zip.png">
</div>


<h4>Extraer contenido a una carpeta</h4>

<p class="parrafo-normal">Extraemos el contenido del ZIP a una carpeta, en nuestro caso hemos elegido la ruta: <span class="green">C:\mysql_segunda_instancia</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/segunda-instancia-win/2-extraer-contenido-carpeta.png">
</div>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 62 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Instalación 2ª Instancia - Windows</h1>


<h4>Crear fichero de configuración my.ini</h4>

<p class="parrafo-normal">Creamos el fichero de configuración <span class="purple">my.ini</span>. Deberá contener al menos:</p>

<ol class="ol-sin-padding-sup-inf">
  <li>Ruta de la Carpeta (basedir)</li>
  <li>Ruta donde se guardarán las Bases de Datos (datadir)</li>
  <li>Puerto (port)</li>
  <li>ID de Servicio único (server-id)</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/segunda-instancia-win/3-creacion-my-ini.png">
</div>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 63 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Instalación 2ª Instancia - Windows</h1>


<h4>Inicializar Directorio de Datos</h4>

<p class="parrafo-normal">Ahora es el momento de inicializar el directorios de datos (data) desde la Línea de Comandos. Primeramente, accedemos a la carpeta 'bin' (ubicación programas binarios). Después ejecutamos el comando mysqld con la ruta del fichero my.ini y la opción --initialize-insecure.</p>

<p class="parrafo-normal-sin-justificar brown">mysqld --defaults-file=C:\mysql_segunda_instancia\my.ini --initialize-insecure<p>

<div class="imagenes margen-superior-interior">
  <img src="img/segunda-instancia-win/4-iniciar-directorio-datos.png">
</div>


<h4>Instalamos el Servicio</h4>

<p class="parrafo-normal">Desde la línea de comandos, instalamos el servicio asociado a la nueva instancia. El comando se debe ejecutar también desde el directorio 'bin'. El comando incluye el nombre que le damos al nuevo servicio "MySQL_Segunda" y la ruta donde se encuentra el fichero de configuración my.ini.</p>

<p class="parrafo-normal-sin-justificar brown">mysqld --install "MySQL_Segunda" --default-file="C:\mysql_segunda_instancia\my.ini"<p>


<div class="imagenes margen-superior-interior">
  <img src="img/segunda-instancia-win/5-instalamos-servicio.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 64 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Instalación 2ª Instancia - Windows</h1>


<h4>Iniciamos el Servicio</h4>

<p class="parrafo-normal">El servicio se puede iniciar desde la Consola de Servicios (services.msc).</p>

<div class="imagenes margen-superior-interior">
  <img src="img/segunda-instancia-win/6-iniciar-nuevo-servicio.png">
</div>


<h4>Configuración MySQL Workbench</h4>

<p class="parrafo-normal">Accedemos al cliente MySQL Workbench para agregar la nueva conexión (MySQL Connections) a la segunda instancia.</p>

<ol class="ol-sin-padding-sup-inf">
  <li>Dirección IP: 127.0.0.1 (la del localhost)</li>
  <li>Puerto: 3307 (el puerto que utiliza la nueva instancia)</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/segunda-instancia-win/7-configuracion-segunda-workbench.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 65 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1 id="segunda-instancia-linux">Instalación 2ª Instancia - Linux</h1>


<h4>Creación del Directorio de Datos</h4>

<p class="parrafo-normal">Primeramente, crearemos el Directorio de Datos para la segunda instancia. Además, le asignamos como usuario y grupo propietario <span class="blue">'mysql'</span>. También establecemos permisos 750 (RWX-R-X----) a ese directorio.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/segunda-instancia-linux/1-crear-directorio-datos.png">
</div>


<h4>Instalar Utilidades de AppArmor</h4>

<p class="parrafo-normal">Después varias horas de pelea con la configuración de la segunda instancia y realizar una interesante labor de investigación, he tenido que recurrir a <span class="red">Instalar las Utilidades de AppArmor</span>.</p>

<p class="parrafo-normal">Hasta este momento, fue imposible poder iniciar la segunda instancia, a pesar de estar bien configurada, porque AppArmor bloqueaba los accesos a varios directorios.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/segunda-instancia-linux/2-instalar-utilidades-apparmor.png">
</div>

<p class="parrafo-primero">Una vez ejecutada la instalación de las Utilidades de AppArmor, y gracias al uso del comando <span class="brown">aa-complain</span> sobre el directorio <span class="brown">/usr/sbin/mysqld</span>, el proceso por fin pudo avanzar.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/segunda-instancia-linux/3-permiso-no-bloqueo-rutas.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 66 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Instalación 2ª Instancia - Linux</h1>


<h4>Configuración de las Instancias</h4>

<p class="parrafo-normal">Tras crear el Directorio de Datos <span class="purple">/var/lib/mysql2</span>, llegó el momento de configurar MySQL Server para incluir una segunda instancia. Dentro de esta configuración es importante destacar la creación de la sección <span class="blue">[mysqld_multi]</span>, que permitirá el uso de varias instancias.</p>

<p class="parrafo-normal">Para configurar el resto de instancias al menos hay que incluir las siguientes directivas con sus parámetros correspondientes:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">user</span>: usuario creador de la Base de Datos (mysql para todos)</li>
  <li><span class="purple">port</span>: puerto asignado a la instancia (diferente)</li>
  <li><span class="purple">datadir</span>: ruta del Directorio de Datos (cada instancia tendrá que tener su ruta correspondiente)</li>
  <li><span class="purple">socket</span>: es un archivo que permite la conexión local cliente-servidor (deberá ser diferente y estar alojado en la misma carpeta)</li>
  <li><span class="purple">pid-file</span>: es un archivo que almacena los procesos del servidor (deberá ser diferente y estar alojado en la misma carpeta)</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/segunda-instancia-linux/4-configuracion-instancias.png" width="90%">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 67 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Instalación 2ª Instancia - Linux</h1>


<h4>Inicializar la Base de Datos</h4>

<p class="parrafo-normal">Para inicializar la Base de Datos, he utilizado el comando <span class="purple">mysqld</span> con las opciones <span class="purple">--initilize-insecure (sin contraseña)</span>, <span class="purple">--user (usuario creador)</span> y <span class="purple">--datadir (dirección del directorio de datos)</span>.</p>

<p class="parrafo-normal cursiva">Me decanté por esta alternativa porque tras investigar el problema que surgía con AppArmor, recomendaban esta opción antes que la de pegar el contenido del Directorio de Datos de la primera instancia en el Directorio de Datos de la segunda instancia.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/segunda-instancia-linux/5-inicializar-base-datos.png">
</div>


<h4>Iniciar Instancias</h4>

<p class="parrafo-normal">Aunque apliqué el comando <span class="cursiva">aa-complain</span> con anterioridad, para no encontrarme con más problemas decidí parar el servicio AppArmor mientras procedía a activar las instancias con el comando <span class="brown">mysqld_multi</span>.</p>

<p class="parrafo-normal">Tuve que utilizar la opción <span class="brown">--defaults-file</span>, porque por si solo no encontraba la ruta del fichero de configuración de MySQL, y por consiguiente no activaba las instancias.</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">report</span>: muestra el estado de las instancias de MySQL.</li>
  <li><span class="purple">start/stop</span>: seguido del número de la instancia, permite su inicio/parada.</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/segunda-instancia-linux/6-iniciar-instancias.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 68 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


<h1>Instalación 2ª Instancia - Linux</h1>


<h4>Configuración de MySQL Workbench</h4>

<p class="parrafo-normal">Accedemos al cliente MySQL Workbench para agregar la nueva conexión (MySQL Connections) a la segunda instancia.</p>

<ol class="ol-sin-padding-sup-inf">
  <li>Dirección IP: 127.0.0.1 (la del localhost)</li>
  <li>Puerto: 3307 (el puerto que utiliza la nueva instancia)</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/segunda-instancia-linux/7-configuracion-workbench.png">
</div>