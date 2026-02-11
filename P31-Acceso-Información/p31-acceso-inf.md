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
    <h3 class="texto-subapartados">Unidad 3 - Acceso a la Información</h3>
  <h3 class="titulos-subapartados">Práctica:</h3>
    <h3 class="texto-subapartados">P31-Acceso-Información</h3>
  <h3 class="titulos-subapartados">Fecha:</h3>
    <h3 class="texto-subapartados">11 de Febrero de 2026</h3>
</div>

<footer>
  <h6>Víctor Álvarez Fernández - ASXBD - 2º ASIR</h6>
</footer>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 2 ---------------->


<!-- Contiene anclajes a los diferentes ejercicios (están en siguientes páginas) -->
# **Índice**

<ol class="indice">
  <li><a href="#caracteristicas">Características de Seguridad</a></li>
  <li><a href="#interna">Seguridad Interna</a></li>
  <li><a href="#externa">Seguridad Externa</a>
    <ul>  
      <li><a href="#vistas">Vistas</a>
        <ul>
          <li><a href="#creacion">Creación</a></li>
          <li><a href="#restricciones">Restricciones</a>
          <li><a href="#check">Verificaciones</a>
          <li><a href="#with">Claúsula de Seguridad</a>
          <li><a href="#algorithm">Claúsula Algorithm</a>
          <li><a href="#modificacion-borrado">Modificación y Borrado</a>
          <li><a href="#esquema">Esquema de Creación</a>
          <li><a href="#workbench">Creación en MySQL Workbench</a>
          <li><a href="#operaciones">Operaciones Autorizadas</a>
          <li><a href="#semantica">Restricciones Semánticas y Sintácticas</a>
        </ul>
      </li>
      <li><a href="#sinonimos">Sinónimos</a></li>
      <li><a href="#cifrado">Técnicas de Cifrado</a></li>
      <li><a href="#autorizaciones">Gestión de Autorizaciones</a>
        <ul>
          <li><a href="#bdmysql">Base de Datos mysql</a></li>
          <li><a href="#usuario">Cuentas de Usuario</a>
          <li><a href="#privilegios">Sentencias para Mostrar Privilegios</a>
          <li><a href="#derechos-privilegios">Tipos de Derechos / Privilegios</a>
          <li><a href="#permisos">Asignación / Revocado de Permisos</a>
          <li><a href="#limitaciones">Limitación de Recursos</a>
          <li><a href="#roles">Roles</a>
          <li><a href="#autenticacion">Mecanismos de Autenticación</a>
        </ul>
      </li>
    </ul>
  </li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 3 ---------------->


<h1 id="caracteristicas">Características de Seguridad</h1>


<p class="parrafo-primero">La persona administradora de la SGBD tratará de proteger el acceso al directorio de datos y al servidor.</p>

<h4>Seguridad Interna</h4>

<p class="parrafo-normal">Trata de bloquear una instalación para impedir que accedan persona no autorizadas en local.</p>

<h5>Ataques Posibles: Sistema de Ficheros</h5>

<ol class="ol-sin-romanos">
  <li>Copias / Eliminación de Tablas</li>
  <li>Lecturas de Información Delicada</li>
</ol>

<h4>Seguridad Externa</h4>

<p class="parrafo-normal">Se centra en problemas que pueden surgir con clientes que se conectan en remoto. Sus objetivos son establecer Políticas de Acceso a la Base de Datos a través de sentencias y Configurar el Servidor para que admita conexiones seguras a través de los protocolos SSL/TLS.</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Conceder Permisos</span>: GRANT</li>
  <li><span class="purple">Retirar Permisos</span>: REVOKE</li>
</ol>

<h4>Control de Integridad</h4>

<p class="parrafo-normal">El administrador es el responsable de: </p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Crear Vistas</span>: <span class="blue">CREATE VIEW</span></li>
  <li><span class="purple">Gestión de Transacciones</span></li>
  <li><span class="purple">Acceso Concurrente</span>:
    <ol>
      <li><span class="blue">BEGIN WORK</span></li>
      <li><span class="blue">COMMIT / ROLLBACK</span></li>
      <li><span class="blue">LOCK TABLE</span></li>
    </ol>
  </li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 4 ---------------->


<h1 id="interna">Seguridad Interna</h1>

<h4>Recomendaciones</h4>

<ol class="ol-sin-romanos">
  <li>Crear un usuario en la instalación para que se ejectute en el servidor. NO debe ser "root"</li>
  <li>Cambiar el propietario del directorio de datos (Data)</li>
  <li>Asignar una contraseña al usuario "root" de MySQL</li>
</ol>


<h4>Protección Socket en GNU/Linux</h4>

<ol class="ol-sin-romanos">
  <li>Proteger el directorio por defecto <span class="brown">/tmp/mysql.sock</span> para que sólo puedan borrar ficheros los propietarios. Para ello se debe establecer el "StickyBit" en el directorio /tmp con el comando <span class="brown">chmod +t /tmp</span></li>
  <li>Cambiar la ruta del fichero socket. Se realiza actualizando la sección <span class="green">[mysqld]</span> del fichero de configuración my.cnf, con la directiva <span class="brown">socket = /path/to/socket</span></li>
</ol>


<h4>Protección Ficheros de Opciones de MySQL en GNU/Linux</h4>

<p class="parrafo-normal">Estos ficheros SÓLO deben estar accesibles para el administrador y el propietario.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 5 ---------------->


<h1 id="externa">Seguridad Externa: Vistas</h1>


<p class="parrafo-primero" id="vistas">Una vista es una tabla "virtual" que es percibida por los usuarios y que permite recoger datos de una o de varias tablas.</p>

<ol class="ol-sin-romanos">
  <li>Información siempre actualizada (no se almacena en disco)</li>
  <li>Se puede crear una vista partiendo de una tabla o de otras vistas</li>
</ol>


<h5>¿Por qué destacan?</h5>

<ol class="ol-sin-romanos">
  <li><span class="purple">Confidencialidad</span>: sólo muestran datos concretos y no permiten el acceso a ciertas columnas</li>
  <li><span class="purple">Integridad Referencial y de Cuentas de Usuario</span>: <span class="blue">CHECK</span> (compila, pero no ejectua)</li>
  <li><span class="purple">Integridad del Dominio</span>: no permite visualizar/actualizar más que los datos que pertecen a un dominio. <span class="cursiva">Ejemplo: Clientes cuya población sea Lugo</span></li>
  <li><span class="purple">Flexibilidad</span>: factila la resolución de sentencias no soportadas por las consultas SELECT</li>
</ol>


<h4 id="creacion">Creación de Vistas</h4>

<p class="parrafo-normal">Sintaxis: <span class="blue">CREATE VIEW</span> <span class="red">nomVista <span class="brown">[columnas_virtuales]</span></span> <span class="blue">AS</span> <span class="green">sentencia_SELECT <span class="darkblue">[WITH [CASCADE|LOCAL] CHECK OPTION]</span></span></p>

<p class="parrafo-normal">Por defecto, las vistas se crean en la Base de Datos que está seleccionada en ese momento. Por ello, para crear una vista en otra Base de Datos se recomienda preceder el nombre de la Base de Datos antes del nombre de la vista, para no tener que entrar y salir en la Base de Datos deseada. <span class="cursiva">Ejemplo: asxbd.nomVista</span>.</p>

<p class="parrafo-normal">En uno de los próximos ejemplos que mostramos, se ha creado la vista <span class="red">descuentos</span> que cuenta con las columnas 'virtuales' producto y precio que tienen una relación 1:1 con las columnas nombre y "precio*0.7" extraídas de la consulta realizada sobre la tabla productos. Este ejemplo es ideal para demostrar la importancia de las vistas, que permiten agilizar las consultas y/o mejorar la información contenida en las tablas.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 6 ---------------->


<h1>Seguridad Externa: Vistas</h1>


<h4>Tipos de Vistas</h4>

<h5>Referidas a Tablas Base</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/vistas/1-vista-tabla-base.png">
</div>

<h5>Referidas a otras Vistas</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/vistas/2-vista-de-vista.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 7 ---------------->


<h1>Seguridad Externa: Vistas</h1>


<h5>Uso de JOINs</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/vistas/3-vista-de-join.png">
</div>

<h5>Uso de SubConsultas</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/vistas/4-vista-de-subconsulta.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 8 ---------------->


<h1>Seguridad Externa: Vistas</h1>


<h4 id="restricciones">Restricciones de las Vistas</h4>

<ol class="ol-sin-romanos">
  <li>La setencia SELECT no puede referirse a variables de sistema ni cuentas de usuario</li>
  <li>La sentencia SELECT no puede hacer referencia a tablas temporales</li>
  <li>Las vistas no se pueden asociar disparadores</li>
  <li>Si la definición se encuentra en un procedimiento almacenado, no puede hacer referencia a parámetros o variables locales del procedimiento</li>
  <li>Todas las tablas/vistas mencionadas en la sentencia SELECT deben existir</li>
</ol>


<h4 id="check">Verificar Borrado de Tablas y/o Vistas</h4>

<p class="parrafo-normal">Utilizando la sentencia <span class="blue">CHECK TABLE</span> se puede comprobar si una vista está OK, dañada o si no existe.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/vistas/5-verificacion-ok.png">
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/vistas/6-verificacion-error.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 9 ---------------->


<h1>Seguridad Externa: Vistas</h1>


<h4 id="with">Claúsula WITH CHECK OPTION</h4>

<p class="parrafo-normal">Esta cláusula es muy útil porque impedirá que se inserten o modifiquen datos que no cumplan con el filtro (WHERE) de la propia vista.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/vistas/7-vista-with.png">
</div>

<h5>Opciones</h5>

<p class="parrafo-normal">Si utilizamos <span class="blue">WITH CASCADED CHECK OPTION</span>, se comprobarán las condiciones de todas las vistas que intervienen en la actual. También se podría escribir <span class="blue">WITH CHECK OPTION</span>, ya que CASCADED es la opción por defecto de esta claúsula.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/vistas/8-vista-with-cascaded.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 10 ---------------->


<h1>Seguridad Externa: Vistas</h1>

<p class="parrafo-primero">Si tan sólo se busca comprobar la condición en la vista actual sin acudir a sus "padres" o "abuelos", se utiliza <span class="blue">WITH LOCAL CHECK OPTION</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/vistas/9-vista-with-local.png">
</div>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 11 ---------------->


<h1>Seguridad Externa: Vistas</h1>


<h4 id="algorithm">Claúsula ALGORITHM</h4>

<p class="parrafo-normal">Esta claúsula afecta al algoritmo de procesamiento de las vistas.</p>

<h5>Opciones</h5>

<p class="parrafo-normal"><span class="blue">MERGE</span>: es el valor predefinido de esta claúsula (podría obviarse). Este algoritmo es el más eficiente porque, en lugar de crear una tabla temporal, "fusiona" la definición de la vista directamente con la consulta lanzada, permitiendo que sea actualizable. Incluso con el motor de almacenamiento InnoDB, que es el más habitual, no es necesario indicar la claúsula ALGORITHM si lo que se quiere es optar por su valor MERCE.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/vistas/10-vista-merge.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 12 ---------------->


<h1>Seguridad Externa: Vistas</h1>


<p class="parrafo-primero"><span class="blue">TEMPTABLE</span>: este valor indica que se deben usar tabla temporales para la creación de la vista. Su uso es necesario cuando se aplican agrupaciones (<span class="green">GROUP BY</span> y <span class="green">HAVING</span>), funciones de agregado (<span class="green">SUM()</span>, <span class="green">MIN()</span>, <span class="green">COUNT()</span>, <span class="green">AVG()</span>,...) o cuando se quieren eliminar duplicados (<span class="green">DISTINCT</span>).</p>

<div class="imagenes margen-superior-interior">
  <img src="img/vistas/11-vista-tablas-temporales.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 13 ---------------->


<h1>Seguridad Externa: Vistas</h1>


<h4 id="modificacion-borrado">Modificación y Borrado de Vistas</h4>

<h5>Modificación de Vistas</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">ALTER VIEW</span> <span class="red">nomVista <span class="brown">[columnas_virtuales]</span></span> <span class="blue">AS</span> <span class="green">sentencia_SELECT <span class="darkblue">[WITH [CASCADE|LOCAL] CHECK OPTION]</span></span></p>


<div class="imagenes margen-superior-interior">
  <img src="img/vistas/12-modificacion-vista.png">
</div>

<h5>Borrado de Vistas</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">DROP VIEW</span> [IF EXISTS] <span class="red">nomVista</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/vistas/13-eliminar-vista.png">
</div>


<h4 class="margen-superior-interior" id="esquema">Mostrar Esquema de Creación de una Vista</h4>

<p class="parrafo-normal">Sintaxis: <span class="blue">SHOW CREATE VIEW <span class="red">nomVista</span></span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/vistas/14-esquema-vista.png">
</div>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 14 ---------------->


<h1>Seguridad Externa: Vistas</h1>


<h4 id="workbench">Creación de Vistas en MySQL Workbench</h4>

<p class="parrafo-normal">Para crear una vista de forma gráfica en MySQL Workbench, habrá que dirigirse al panel Schemas en la barra lateral izquierda, desplegar la base de datos deseada y hacer clic derecho sobre la sección Views para seleccionar la opción "Create View...". Se abrirá una nueva pestaña con un editor donde se podrá redactar la consulta SELECT que definirá la vista. Una vez escrita la consulta, al pulsar el botón "Apply" en la esquina inferior derecha, Workbench generará automáticamente el script SQL correspondiente.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/vistas/15-workbench.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 15 ---------------->


<h1>Seguridad Externa: Vistas</h1>


<p class="parrafo-primero">En el proceso de creación será necesario seleccionar el Algoritmo y el Tipo de Concurrencia, aunque los habitual es utilizar los valores por defecto ya que son los más modernos y eficientes.</p>

<p class="parrafo-normal"><span class="brown">Algorithm</span>: se pueden seleccionar los valores <span class="darkblue">Copy</span> (operaciones sobre tabla temporal) o <span class="darkblue">Inplace</span> (reconstrucción de la tabla), siendo este último el utilizado por defecto.</p>

<p class="parrafo-normal"><span class="brown">Lock type (Concurrencia)</span>: se pueden elegir los valores <span class="darkblue">Exclusive</span> (bloqueo completo), <span class="darkblue">Shared</span> (bloque compartido - Sólo Lectura) o <span class="darkblue">None</span> (sin bloqueo - 100% concurrencia), que es la opción por defecto.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/vistas/16-workbench-2.png">
</div>


<h4 id="operaciones">Operaciones Autorizadas</h4>

<ol class="ol-sin-romanos">
  <li>Consultas: <span class="blue">SELECT</span></li>
  <li>Inserciones: <span class="blue">INSERT ... INTO ... VALUES</span></li>
  <li>Modificaciones: <span class="blue">ALTER</span></li>
  <li>Borrados: <span class="blue">DROP</span></li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 16 ---------------->


<h1>Seguridad Externa: Vistas</h1>


<h4 id="semantica">Restricciones Semánticas y Sintácticas</h4>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="green">No se pueden actualizar/cargar datos en vistas que contengan agrupaciones (GROUP BY), funciones de agregado ni uniones (UNION)</span>. Estas vistas serán de Sólo Lectura y utilizan tablas temporales (algoritmo TEMPTABLE).</li>
  <li><span class="green">No se pueden actualizar/cargar datos en vistas que contienen columnas que no están en la tabla "física"</span>. Es decir, no se podrían cargar datos en vistas que contienen columnas que están asociadas a operaciones aritméticas.</li>
  <li><span class="green">No se pueden actualizar/cargar datos si no se conocen las columnas de la tabla física</span>. Un vista puede filtrar sólo dos columnas y la tabla física contener muchas más.</li>
</ol>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 17 ---------------->


<h1 id="sinonimos">Seguridad Externa: Sinónimos</h1>


<p class="parrafo-primero">Un sinónimo es un objeto de la Base de Datos, cuya función es proporcionar un nombre alternativo a otro objeto (local o remoto) para facilitar su localización. Además, proporciona una capa de protección al cliente antes posibles cambios que realicen en el nombre o ubicación del objeto base. Su utilidad queda demostrada cuando una tabla cambia de Base de Datos o cuando cambia de Servidor.</p>

<h5>Ventajas para una Aplicación Cliente:</h5>

<ol class="ol-sin-romanos">
  <li>No requiere menciones complejas para acceder a objetos concretos</li>
  <li>No requiere modificaciones si hay cambios de ubicación</li>
</ol>


<h5>Creación de Sinónimos</h5>

<p class="parrafo-normal">En MySQL no existe ninguna sentencia para crear sinónimos, por lo que estos se deben generar con un procedimiento almacenado en la Base de Datos "sys" que se genera con la instalación del propio Servidor MySQL. Además, este tipo de sinómimos sólo pueden referirse a Bases de Datos.</p>

<p class="parrafo-normal">Para utilizar este procedimiento es necesario utilizar la sentencia CALL (Llamada)</p>

<ol class="ol-sin-romanos">
  <li><span class="brown">sys</span>: Base de Datos que almacena el procedimiento</li>
  <li><span class="brown">create_synonym_db()</span>: Procedimiento Almacenado</li>
  <li><span class="brown">INFORMATION_SCHEMA</span>: Objeto que deseamos 'sinonimar'</li>
  <li><span class="brown">info</span>: nombre del sinónimo que deseamos crear</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/sinonimos/1-creacion-sinonimo.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 18 ---------------->


<h1>Seguridad Externa: Sinónimos</h1>


<h5>Ver Sinónimos Creados</h5>

<p class="parrafo-normal">Los sinónimos se pueden ver con si fueran una Base de Datos con la sentencia: <span class="blue">SHOW DATABASES;</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/sinonimos/3-ver-sinonimos.png">
</div>


<h5>Ver Tablas de un Sinónimo</h5>

<p class="parrafo-normal">Para ver las tablas de un sinónimo, lo hacemos como si consultaramos la tabla de una Base de Datos: <span class="blue">SHOW TABLES FROM <span class="darkblue">bd</span>;</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/sinonimos/2-ver-tablas-sinonimo.png">
</div>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 19 ---------------->


<h1>Seguridad Externa: Sinónimos</h1>


<h5>Ver Vista de un Sinónimo</h5>

<p class="parrafo-normal">Las vistas de un sinónimo se pueden ver con: <span class="blue">SHOW FULL TABLES FROM <span class="red">nomSinonimo</span>;</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/sinonimos/4-ver-vistas-sinonimos.png">
</div>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 20 ---------------->


<h1 id="cifrado">Seguridad Externa: Técnicas de Cifrado</h1>


<p class="parrafo-primero">La encriptación protege los datos que viajan por Internet.</p>


<h4>Variables que controlan el cifrado en MySQL</h4>

<p class="parrafo-normal">Controlan la encriptaión de los ficheros log de transacciones en TableSpace encriptados. Los valores que pueden tomar son booleanos (ON/OFF). De manera predeterminada vienen configurados en OFF por lo que será necesario activarlos para comenzar con la encriptación. La encriptación sólo afectará a los nuevos registros y segmentos a partir del cambio, y nunca a los anteriores.</p>

<ol class="ol-sin-romanos">
  <li><span class="brown">innodb_redo_log_encrypt</span></li>
  <li><span class="brown">innodb_undo_log_encrypt</span></li>
  <li><span class="brown">binlog_encryption</span></li>
</ol>


<h4>Funciones relacionadas con la encriptación</h4>

<h5>Técnicas de Cifrado Simétrico (HASH)</h5>

<ol class="ol-sin-romanos">
  <li><span class="brown">SHA2(<span class="green">'texto'</span>, <span class="red">longitud de la huella digital</span>)</span></li>
  <li><span class="brown">AES_ENCRYPT(<span class="green">'texto'</span>, <span class="red">'clave'</span>)</span>: la más recomendable</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/cifrado/1-cifrado-hash.png">
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/cifrado/2-cifrado-hash.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 21 ---------------->


<h1>Seguridad Externa: Técnicas de Cifrado</h1>

<h5>Técnicas de Cifrado Asimétrico (Claves)</h5>

<p class="parrafo-normal">El proceso consistiría en crear una clave privada, posteriormente una clave pública a través de la clave privada, y para finalizar realizando la encriptación con la clave pública.</p>

<ol class="ol-sin-romanos">
  <li><span class="brown">CREATE_ASYMETRIC_PRIV_KEY(<span class="darkblue">'método'</span>, <span class="red">longitud de la huella digital</span>)</span>: Crea una Clave Privada</li>
  <li><span class="brown">CREATE_ASYMETRIC_PUB_KEY(<span class="darkblue">'método'</span>, <span class="purple">mención a la clave privada</span>)</span>: Crea una Clave Pública</li>
  <li><span class="brown">ASYMETRIC_ENCRYPT(<span class="darkblue">'método'</span>, <span class="green">'texto'</span>, <span class="purple">mención a clave pública</span>)</span>: Encripta texto plano usando clave/privada</li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 22 ---------------->


<h1 id="autorizaciones">Seguridad Externa: Autorizaciones</h1>

<p class="parrafo-primero">El administrador de la Base de Datos tiene que establecer una Política de Accesos que indique las cuentas de usuario que tendrán acceso a la Base de Datos y los elementos de la Base de Dstos a lo que tendrá acceso cada una de las cuentas de usuario.</p>


<h5>Tipos de Permisos</h5>

<ol class="ol-sin-romanos">
  <li>Nivel de Base de Datos</li>
  <li>Nivel de Tabla</li>
  <li>Nivel de Columna</li>
</ol>

<h5>Ver Privilegios</h5>

<p class="parrafo-normal">Para ver los privilegios con los que cuenta el Servidor MySQL, ejecutamos la sentencia: <span class="blue">SHOW PRIVILEGES;</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/autorizaciones/1-autorizaciones.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 23 ---------------->


<h1>Seguridad Externa: Autorizaciones</h1>


<h4 id="bdmysql">Base de Datos mysql</h4>

<p class="parrafo-normal">Se crea de manera automática al instalar el Servidor MySQL y contiene las tablas que controlan el acceso al servidor.</p>


<ol class="ol-sin-romanos">
  <li><span class="brown">user</span>: información de las cuentas de usuario, equipos y contraseñas que pueden acceder al servidor. Contiene también los permisos gloables (se recomienda que estén desactivados)</li>
  <li><span class="brown">db</span>: información de la bases de datos a las que pueden acceder los usuarios</li>
  <li><span class="brown">tables_priv</span>: permisos de tablas concretas</li>
  <li><span class="brown">columns_priv</span>: permisos de columnas concretas</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/autorizaciones/2-tablas-control.png">
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/autorizaciones/3-tabla-user.png">
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/autorizaciones/4-tabla-bd.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 24 ---------------->


<h1>Seguridad Externa: Autorizaciones</h1>


<h5>Ver Columnas de la tabla mysql</h5>

<p class="parrafo-normal">Con la sentencia <span class="blue">DESCRIBE user;</span> se puede ver las columnas de la tabla mysql.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/autorizaciones/5-columnas-user.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 25 ---------------->


<h1>Seguridad Externa: Autorizaciones</h1>


<h4 id="usuario">Cuentas de Usuario</h4>

<h5>Creación de Cuentas de Usuario</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">CREATE USER</span> [IF NOT EXISTS] <span class="red">usuario</span> <span class="brown">[IDENTIFIED BY 'contraseña']</span> <span class="darkblue">[WITH restriccion_recursos]</span></p>


<h5>Eliminación de Cuentas de Usuario</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">DROP USER</span> [IF NOT EXISTS] <span class="red">usuario</span></p>


<div class="imagenes margen-superior-interior">
  <img src="img/usuarios/1-creacion-eliminacion-usuarios.png">
</div>

<h5>¿Qué debemos tener en cuenta?</h5>

<ol class="ol-sin-romanos">
  <li>Cuando se crea un usuario <span class="green">no se le añaden privilegios</span>, por lo que sólo tendrá acceso al servidor</li>
  <li>Cuando se añade una <span class="green">contraseña</span>, se recomiena que sea con un <span class="green">hash_string</span></li>
  <li>La claúsula <span class="darkblue">WITH</span> permite establecer restricciones como: MAX_USER_CONNECTIONS, MAX_QUERIES_PER_HOUR, ...</li>
</ol>


<h5>Modificación de Contraseñas</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">ALTER USER</span> <span class="red">'usuario'@'host'</span> <span class="brown">IDENTIFIED BY 'nueva_contraseña'</span></p>

<p class="parrafo-normal">Carga Privilegios en memoria: <span class="blue">FLUSH PRIVILEGES;</span></p>


<div class="imagenes margen-superior-interior">
  <img src="img/usuarios/2-modificar-contraseña.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 26 ---------------->


<h1>Seguridad Externa: Autorizaciones</h1>


<h5>Creación de Usuarios en MySQL Workbench</h5>

<p class="parrafo-normal">Para crear un usuario de forma gráfica en MySQL Workbench, será necesario dirigirse a la pestaña Administration del panel lateral izquierdo (Navigator) y seleccionar la opción Users and Privileges. Al hacer clic en el botón Add Account, se abrirá un formulario donde se podrá definir el nombre del usuario, el tipo de autenticación y la contraseña; posteriormente, en las pestañas superiores como Schema Privileges, se podrán asignar permisos específicos a bases de datos concretas simplemente seleccionando la base de datos y marcando los privilegios deseados (como SELECT o INSERT) antes de pulsar el botón Apply.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/usuarios/3-workbench.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 27 ---------------->


<h1>Seguridad Externa: Autorizaciones</h1>


<h4 id="privilegios">Sentencias para Mostrar Privilegios</h4>

<ol class="ol-sin-padding-sup-inf">
  <li>Información de un Usuario (host, contraseña y restricciones): <span class="blue">SHOW CREATE USER <span class="green">usuario</span>;</span></li>
  <li>Privilegios de un Usuarios: <span class="blue">SHOW GRANTS <span class="green">usuario</span>;</span></li>
  <li>Listado de Usuarios: <span class="blue">SELECT <span class="brown">user, host</span> FROM mysql.user;</span></li>
  <li>Descripción de Privilegios: <span class="blue">SHOW PRIVILEGES;</span></li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/usuarios/4-info-usuario.png">
  <div class="num-romano">I</div>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/usuarios/5-privilegios-usuario.png">
  <div class="num-romano">II</div>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/usuarios/6-listado-usuarios.png">
  <div class="num-romano">III</div>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/usuarios/7-ver-privilegios.png">
  <div class="num-romano">IV</div>
</div>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 28 ---------------->


<h1>Seguridad Externa: Autorizaciones</h1>


<h4 id="derechos-privilegios">Tipos de Privilegios</h4>

<div class="imagenes">
  <img src="img/usuarios/8-tabla-privilegios.png">
</div>


<h4 id="permisos">Asignación y Revocado de Permisos</h4>

<ol class="ol-sin-romanos">
  <li>Asignación de Permisos: <span class="blue">GRANT <span class="purple">privilegios</span> ON <span class="brown">objeto</span> TO <span class="green">usuario</span>;</span></li>
  <li>Asignación de Todos los Permisos: <span class="blue">GRANT <span class="purple">ALL PRIVILEGES</span> ON <span class="brown">objeto</span> TO <span class="green">usuario</span>;</span></li>
  <li>Revocación de Permisos: <span class="blue">REVOKE <span class="purple">privilegios</span> ON <span class="brown">objeto</span> FROM <span class="green">usuario</span>;</span></li>
  <li>Revocación de Todos los Permisos: <span class="blue">GRANT <span class="purple">ALL PRIVILEGES, GRANT OPTION</span> FROM <span class="green">usuario</span>;</span></li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/usuarios/9-asignar-revocar.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 29 ---------------->


<h1>Seguridad Externa: Autorizaciones</h1>


<h5>Tipos de Objetos</h5>

<div class="imagenes">
  <img src="img/usuarios/10-objetos.png">
</div>


<h5>Recomendaciones</h5>

<ol class="ol-sin-romanos">
  <li>Por seguridad, NO se deben conceder privilegios de caracter global</li>
  <li>Se requiere especial atención al establecer privilegios en la Base de Datos mysql
    <ol>
      <li>ALTER: podría modificar tablas de privilegios</li>
      <li>DROP: podría eliminar todas las limitaciones existentes</li>
      <li>GRANT: podría concender privilegios a otros usuarios</li>
      <li>SHUTDOWN: podría provocar un apagado del Servidor</li>
    </ol>
  </li>
</ol>



<h4 id="limitaciones">Limitación de Recursos en Cuentas de Usuario</h4>


<h5>Creación de Cuenta</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">CREATE USER</span> <span class="red">'usuario'@'host'</span> <span class="darkblue">WITH restricciones</span>;</p>


<h5>Modificación de Cuenta</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">ALTER USER</span> <span class="red">'usuario'@'host'</span> <span class="darkblue">WITH restricciones</span>;</p>


<h5>Limitaciones más habituales</h5>

<ol class="ol-sin-romanos">
  <li>Máximo de Consultas por Hora: <span class="darkblue">max_queries_per_hour</span></li>
  <li>Máximo de Cargas por Hora: <span class="darkblue">max_updates_per_hour</span></li>
  <li>Máximo de Conexiones por Hora: <span class="darkblue">max_connections_per_hour</span></li>
  <li>Máximo Conexiones Simultáneas: <span class="darkblue">max_user_connections</span></li>
</ol>


<div class="imagenes margen-superior-interior">
  <img src="img/usuarios/11-limitaciones.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 30 ---------------->


<h1>Seguridad Externa: Autorizaciones</h1>


<h4 id="roles">Roles</h4>

<p class="parrafo-normal">Un ROL en términos de los SGBD no es más que una colección de privilegios a los que se les asigna un nombre. Los roles se pueden asignar a cuentas de usuario para que cuenten con determinados privilegios.</p>


<h5>Creación de un Rol</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">CREATE ROL</span> [IF NOT EXISTS] <span class="green">nomRol</span>;</p>

<div class="imagenes margen-superior-interior">
  <img src="img/rol/1-crear-rol.png">
</div>


<h5>Agrupar Permisos en un Rol</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">GRANT</span> <span class="purple">privilegios</span> ON <span class="brown">objeto</span> TO <span class="green">nomRol</span>;</p>

<div class="imagenes margen-superior-interior">
  <img src="img/rol/2-asignar-permisos-rol.png">
</div>


<h5>Ver Privilegios de un Rol</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue"> SHOW GRANTS</span> FOR <span class="green">nomRol</span>;</p>

<div class="imagenes margen-superior-interior">
  <img src="img/rol/3-ver-privilegios-rol.png">
</div>


<h5>Eliminar Privilegios de un Rol</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">REVOKE</span> <span class="purple">privilegios</span> ON <span class="brown">objeto</span> FROM <span class="green">nomRol</span>;</p>

<div class="imagenes margen-superior-interior">
  <img src="img/rol/4-eliminar-privilegios-rol.png">
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/rol/5-eliminar-todos-privilegios-rol.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 31 ---------------->


<h1>Seguridad Externa: Autorizaciones</h1>


<h5>Eliminar un Rol</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">DROP ROL</span> [IF EXISTS] <span class="green">nomRol</span>;</p>

<div class="imagenes margen-superior-interior">
  <img src="img/rol/6-eliminar-rol.png">
</div>


<h5>Asignar un Rol a una Cuenta de Usuario</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">GRANT</span> <span class="green">nomRol</span> TO <span class="brown">usuario</span>;</p>

<div class="imagenes margen-superior-interior">
  <img src="img/rol/7-añadir-rol-usuario.png">
</div>


<h5>Establecer Roles por Defecto</h5>

<p class="parrafo-normal">Establecer un rol por defecto significa definir qué conjunto de privilegios se activarán automáticamente en el momento en que un usuario inicia sesión en el servidor. Por seguridad, MySQL asigna inicialmente el valor NONE por defecto; garantizando únicamente el acceso al Servidor.</p>

<p class="parrafo-normal">Para establecer un rol por defecto será necesario el uso de la sentencia <span class="blue">SET DEFAULT ROLE { NONE | ALL | 'nomRol' } TO <span class="brown">usuario</span>;</span></p>

<ol class="ol-sin-romanos">
  <li>Privilegio Mínimo (Acceso): <span class="darkblue">NONE</span></li>
  <li>Todos los Privilegios: <span class="darkblue">ALL</span></li>
  <li>Nombre de un rol</li>
</ol>


<div class="imagenes margen-superior-interior">
  <img src="img/rol/8-asignar-rol-defecto.png">
</div>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 33 ---------------->


<h1>Seguridad Externa: Autorizaciones</h1>


<h4 id="autenticacion">Mecanismos de Autenticación de Cuentas de Usuario</h4>

<p class="parrafo-normal">Son los métodos utilizados por MySQL para cifrar contraseñas.</p>

<h5>Opciones</h5>

<ol class="ol-sin-romanos">
  <li>Nativo (sin cifrar)</li>
  <li><span class="green">sha256</span></li>
  <li><span class="green">caching_sha2_password</span>: recomendado</li>
</ol>

<h5>Modificar Método Autenticación de un Usuario</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">ALTER USER</span> <span class="red">'usuario'@'host'</span> <span class="darkblue">IDENTIFIED WITH metodo_autenticacion BY 'contraseña'</span>;</p>

<div class="imagenes margen-superior-interior">
  <img src="img/cifrado/3-cifrado-usuarios.png">
</div>


<h5>Consultar Método Autenticación Cuentas de Usuario</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">SELECT USER <span class="purple">user, plugin</span> FROM <span class="brown">mysql</span>.<span class="darkblue">user</span></span>;</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">user</span>: columna con nombre de usuario</li>
  <li><span class="purple">plugin</span>: columna con método autenticación</li>
  <li><span class="brown">mysql</span>: Base de Datos mysql (creada en la instalación del Servidor)</li>
  <li><span class="darkblue">user</span>: Tabla de la Base de Datos mysql</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/cifrado/4-consultar-cifrado-usuarios.png">
</div>