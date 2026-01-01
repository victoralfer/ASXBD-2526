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
    <h3 class="texto-subapartados">Unidad 0 - Git & Markdown</h3>
  <h3 class="titulos-subapartados">Práctica:</h3>
    <h3 class="texto-subapartados">P02-Conflictos</h3>
  <h3 class="titulos-subapartados">Fecha:</h3>
    <h3 class="texto-subapartados">1 de Enero de 2026</h3>
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
- [Instalación Tortoise-SVN](#instalación-tortoise-svn)
  - [Configuración Tortoise-SVN](#configuración-tortoise-svn)
  - [Subida de Archivos en el Servidor](#subida-de-archivos-en-el-servidor)
  - [Descarga de Archivos en el Cliente](#descarga-de-archivos-en-el-cliente)
- [Conflicto en GIT](#conflicto-en-git)
- [Herramienta de Resolución](#herramienta-de-resolución)
- [Análisis Proceso de Resolución](#análisis-proceso-de-resolución)
  - [Paso 1: Detección del Conflicto](#paso-1-detección-del-conflicto)
  - [Paso 2: Ejecución de la Herramienta de Resolución](#paso-2-ejecución-de-la-herramienta-de-resolución)
  - [Paso 3: Opciones de Resolución](#paso-3-opciones-de-resolución)
  - [Paso 4: Finalización y Marcado como Resuelto](#paso-4-finalización-y-marcado-como-resuelto)
  - [Paso 5: Commit final](#paso-5-commit-final)
  - [Paso 6: Descargar última versión respositorio](#paso-6-descargar-última-versión-en-el-resto-de-equipos)


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 3 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

# **Instalación Tortoise-SVN**

<p class="parrafo-normal">Lo primero que vamos a realizar es la <span class="green">Instalación de Tortoise-SVN tanto en el equipo anfitrión con en la máquina virtual. La máquina virtual tiene su tarjeta de red configurada en modo <span class="cursiva">Adaptador Puente</span>, lo que le permite conectarse con su propia dirección IP a la misma LAN que el ordenador anfitrión.</p>

#### **Configuración Tortoise-SVN** 

<ol>
  <li><span class="cursiva">Equipo Anfitrión</span>: 
    <ol>
      <li>Creamos la <span class="blue">carpeta ASXBD-2526-G1</span>, la cual acogerá los ficheros de configuración.</li> 
      <li>Dentro de la carpeta creamos un nuevo repositorio: <span class="red">TortoiseSVN > Create respository here.</span></li>
    </ol>
  </li>
  <li><span class="cursiva">Equipo Anfitrión</span>: nos aparecerá una ventana emergente con la <span class="green">URL física donde se ha creado el repositorio</span>. <span class="purple">Pulsamos en OK.</span></li>
  <li><span class="cursiva">Equipo Anfitrión</span>: <span class="blue">compartimos la carpeta ASXBD-2526-G1 en nuestra red para los usuarios deseados</span>. En este caso para Todos, con el Nivel de Permisos: Lectura y Escritura.</li>
  <li><span class="cursiva">Máquina Virtual</span>: <span class="blue">creamos una carpeta que vamos a denominar con el mismo nombre: ASXDB-2526-G1</span>.
    <ol>
      <li>Menú Contextual - <span class="red">TortoiseSVN > Checkout...</span></li>
      <li>Añadimos la URL del respositorio (recurso compartido en la LAN), incluyendo delante de la URL el protocolo 'file': <span class="green">file:\\VIC-WIN11\Users\Víctor\Nextcloud\FP\MÓDULOS\Sistemas de Gestión de Bases de Datos\ASXBD-2526-G1</span></li>
      <li><span class="purple">Pulsamos en el botón OK</span>.</li>
    </ol>
  </li>
  <li><span class="cursiva">Máquina Virtual</span>: nos emergerá una ventana indicando que el Checkout se ha realizado correctamente. <span class="purple">Pulsamos en el botón OK</span>.</li>
</ol>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 4 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

<h1>Instalación Tortoise-SVN</h1>


#### **Subida de Archivos en el Servidor** 

<ol start="6">
  <li><span class="cursiva">Equipo Anfitrión</span>: 
    <ol>
      <li><span class="blue">Creamos una carpeta para alojar los trabajos realizados:</span> 'Mi_Trabajo'.</li>
      <li>Menú contextual - <span class="red">TortoiseSVN > Checkout</span>. <span class="purple">Pulsamos en el botón OK</span>.</li>
    </ol>
  </li>
  <li><span class="cursiva">Equipo Anfitrión</span>: 
    <ol>
      <li><span class="blue">Añadimos la carpeta 'Plantilla'</span> que hemos descargado del Aula Virtual.</li>
      <li>Menú contextual - <span class="red">TortoiseSVN > Add...</span></li>
    </ol>
  </li>
  <li><span class="cursiva">Equipo Anfitrión</span>: en la ventana emergente, <span class="blue">seleccionamos los ficheros/directorios que deseamos añadir al repositorio</span>. <span class="purple">Pulsamos en el botón OK</span>.</li>
  <li><span class="cursiva">Equipo Anfitrión</span>: nos aparecerá otra ventana emergente que nos indicará que el proceso se ha completado correctamente.</li>
  <li><span class="cursiva">Equipo Anfitrión</span>: <span class="blue">accedemos a la carpeta con los trabajos realizados</span> 'Mi_Trabajo':
    <ol>
      <li>Menú contextual - <span class="red">TortoiseSVN > Commit...</span></li>
      <li>En la ventana emergente que aparece, podemos comprobar en la parte inferior los ficheros modificados o creados; y en la parte superior un campo para escribir un mensaje u observación de los ficheros que vamos a cargar en el Servidor.</li>
      <li><span class="purple">Pulsamos en el botón OK</span>.</li>
    </ol>
  </li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 5 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

<h1>Instalación Tortoise-SVN</h1>


#### **Descarga de Archivos en el Cliente** 

<ol start="11">
  <li><span class="cursiva">Máquina Virtual</span>: <span class="blue">creamos una carpeta para alojar los trabajos 'Trabajo-SVN'</span>.
    <ol>
      <li>Descargamos las últimas modifaciones: Menú contextual - <span class="red">TortoiseSVN > Update</span>.</li>
      <li><span class="purple">Pulsamos en el botón OK</span>.</li>
    </ol>
  </li>
  <li><span class="cursiva">Máquina Virtual</span>: Comprobamos que se ha descargado la carpeta 'Plantilla'.</li>
</ol>

<div class="imagenes">
  <img src="img/practica/tortoise-1.png">
  <p class="num-romano">I</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 6 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

<h1>Instalación Tortoise-SVN</h1>


<div class="imagenes margen-superior">
  <img src="img/practica/tortoise-2.png">
  <p class="num-romano">II</p>
</div>

<div class="imagenes margen-superior">
  <img src="img/practica/tortoise-3.png">
  <p class="num-romano">III</p>
</div>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 7 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

<h1>Instalación Tortoise-SVN</h1>


<div class="imagenes margen-superior">
  <img src="img/practica/tortoise-4.png">
  <p class="num-romano">IV</p>
</div>

<div class="imagenes margen-superior">
  <img src="img/practica/tortoise-5.png">
  <p class="num-romano">V</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 8 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

<h1>Instalación Tortoise-SVN</h1>


<div class="imagenes margen-superior">
  <img src="img/practica/tortoise-6.png">
  <p class="num-romano">VI</p>
</div>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 9 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

<h1>Instalación Tortoise-SVN</h1>


<div class="imagenes margen-superior">
  <img src="img/practica/tortoise-7.png">
  <p class="num-romano">VII</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 10 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

<h1>Instalación Tortoise-SVN</h1>

<div class="imagenes margen-superior">
  <img src="img/practica/tortoise-8.png">
  <p class="num-romano">VIII</p>
</div>

<div class="imagenes margen-superior">
  <img src="img/practica/tortoise-9.png">
  <p class="num-romano">IX</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 11 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

<h1>Instalación Tortoise-SVN</h1>


<div class="imagenes margen-superior">
  <img src="img/practica/tortoise-10.png">
  <p class="num-romano">X</p>
</div>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 12 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

<h1>Instalación Tortoise-SVN</h1>

<div class="imagenes margen-superior">
  <img src="img/practica/tortoise-11.png">
  <p class="num-romano">XI</p>
</div>

<div class="imagenes margen-superior">
  <img src="img/practica/tortoise-12.png">
  <p class="num-romano">XII</p>
</div>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 13 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

# **Conflicto en GIT**

<p class="parrafo-normal purple">Un conflicto es una situación en la que el sistema de control de versiones no puede fusionar automáticamente los cambios realizados en uno o varios archivos.</p>

<h4>¿Cuándo se produce?</h4>

<p class="parrafo-normal">Cuando dos o más usuarios modifican las mismas líneas de un archivo y uno de ellos intenta subir sus cambios <span class="cursiva">(opción 'Commit')</span> sin haber incorporado previamente los realizados por otros usuarios, que además ya están cargados en el Servidor SVN.</p>

<h4>¿Cuándo NO se produce?</h4>

<p class="parrafo-normal">No hay conflicto si los usuarios trabajan en archivos diferentes o si modifican partes distintas de un mismo archivo; en estos casos, el sistema realiza una fusión 'automática'.</p>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 14 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

# **Herramienta de Resolución**

<p class="parrafo-normal">Para gestionar los conflictos de forma visual, TortoiseSVN incluye una herramienta llamada <span class="green">TortoiseMerge</span>, la cual viene activada por defecto.</p>

<p class="parrafo-normal">Menu Contextual - <span class="red">Setting > Diff Viewer > Merge Tool > TortoiseMerge</span>.</p>

<div class="imagenes margen-superior">
  <img src="img/resolucion/resolucion-1.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 15 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

# **Análisis Proceso de Resolución**

#### Paso 1: Detección del conflicto

<p class="parrafo-normal">Cuando intentamos cargar en el Servidor SVN una modificación de nuestros archivos con la opción 'Commit', habiendo en el Servidor SVN una versión más reciente con respecto a lo que tenemos alojado localmente; se desplegará una ventana emergente alertando de un conflicto.</p>

<div class="imagenes">
  <img src="img/resolucion/resolucion-2.png">
</div>

<p class="parrafo-normal">Tras la alerta, podremos continuar con el proceso de carga de los archivos modificados en nuestro equipo o cancelar el proceso de subida.</p>

<div class="imagenes">
  <img src="img/resolucion/resolucion-3.png">
</div>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 16 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

# **Análisis Proceso de Resolución**

<p class="parrafo-normal">Si optamos por la opción de cargar los archivos modificados localmente; una nueva ventana emergente nos comunicará que estos se han subido, pero que se ha generado un conflicto.</p>

<div class="imagenes">
  <img src="img/resolucion/resolucion-4.png">
</div>

<div class="imagenes margen-superior">
  <img src="img/resolucion/resolucion-5.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 17 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

# **Análisis Proceso de Resolución**

#### Paso 2: Ejecución de la Herramienta de Resolución

<p class="parrafo-normal">Si accedemos a una de las carpetas donde están cualquiera de los conflictos; veremos que se han generado una serie de archivos que comparten nombre, pero no extensión.</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">.md</span>: es la versión del archivo modificada localmente.</li>
  <li><span class="purple">.md.mine</span>: es el archivo antes de realizar los cambios locales.</li>
  <li><span class="purple">.md.r5</span>: es la versión 'base' del archivo. Es decir, la versión que tenía el archivo antes de que se hicieran modificaciones tanto en los equipos de otros usuarios como en el equipo local.</li>
  <li><span class="purple">.md.r6</span>: es la versión que ahora mismo está en el Servidor.</li>
</ol>

<p class="parrafo-normal">Para poder acceder a la <span class="blue">Herramienta de Resolución de Conflictos</span>, tenemos que ejecutar desde el menú contextual del archivo con extension .md <span class="cursiva">(versión local)</span> la opción <span class="red">'Edit conflicts'</span>.</p>

<div class="imagenes margen-superior">
  <img src="img/resolucion/resolucion-6.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 18 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

# **Análisis Proceso de Resolución**

#### Paso 3: Opciones de Resolución

<p class="parrafo-normal">En la <span class="blue">Herramienta de Resolución de Conflictos</span> nos encontramos con una interfaz en la que podemos distinguir de manera clara tres secciones:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">Theirs (izquierda)</span>: son los cambios realizados por los otros usuarios en el Servidor.</li>
  <li><span class="purple">Mine (derecha)</span>: son los cambios realizados localmente y que se ha intentado subir.</li>
  <li><span class="purple">Merged (abajo)</span>: es el resultado final del archivo tras decidir si se opta por una de las otras dos opciones o por una alternativa que se puede editar directamente desde ahí.</li>
</ol>

<div class="imagenes margen-superior">
  <img src="img/resolucion/resolucion-7.png">
</div>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 19 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>


# **Análisis Proceso de Resolución**

<p class="parrafo-normal">Dentro de la <span class="blue">Herramienta de Resolución de Conflictos</span> podemos hacer clic derecho tanto en los cambios realizados por los otros usuarios (Theirs) como localmente (Mine); y elegir entre estas cuatro opciones:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">Use this text block</span>: Acepta la modificación sobre la que se ha hecho click (Theirs / Mine).</li>
   <li><span class="purple">Use this whole file</span>: Acepta el fichero completo sobre el que se ha hecho click (Theirs / Mine).</li>
  <li><span class="purple">Use text block from 'mine' before 'theirs'</span>: Acepta ambos cambios, poniendo la modificación Local antes que la del Servidor.</li>
  <li><span class="purple">Use text block from 'mine' before 'theirs'</span>: Acepta ambos cambios, poniendo la modificación del Servidor antes que la Local.</li>
</ol>

<div class="imagenes margen-superior">
  <img src="img/resolucion/resolucion-8.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 20 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

# **Análisis Proceso de Resolución**

#### Paso 4: Finalización y Marcado como Resuelto

<p class="parrafo-normal">Una vez que el panel inferior <span class="cursiva">(Merged)</span> de la <span class="blue">Herramienta de Resolución de Conflictos</span> tiene el contenido deseado:</p>

<ol class="ol-sin-padding-sup-inf">
  <li>Guardamos <span class="cursiva">(Save)</span> el archivo.</li>
  <li><span class="green">Hacemos click en el icono 'Mark as Resolved'</span>. Esto le indica a Servidor SVN que ya se ha resuelto el conflicto manualmente.</li>
</ol>

<div class="imagenes margen-superior">
  <img src="img/resolucion/resolucion-9.png">
</div>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 21 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

# **Análisis Proceso de Resolución**

#### Paso 5: Commit final

<p class="parrafo-normal">Para que la solución sea definitiva, tenemos que cargar desde el equipo local los archivos en el Servidor SVN, utilizando como es habitual la opción <span class="red">'Commit'</span>.</p>

<div class="imagenes">
  <img src="img/resolucion/resolucion-10.png">
</div>

<div class="imagenes margen-superior">
  <img src="img/resolucion/resolucion-11.png">
</div>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 22 ---------------->

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

# **Análisis Proceso de Resolución**

#### Paso 6: Descargar última versión en el resto de equipos

<p class="parrafo-normal">Por supuesto, el resto de usuarios tendrán que actualizar sus copias locales descargando la última versión del repositorio utilizando la opción <span class="red">'Update'</span>.</p>

<div class="imagenes margen-superior">
  <img src="img/resolucion/resolucion-12.png">
</div>

