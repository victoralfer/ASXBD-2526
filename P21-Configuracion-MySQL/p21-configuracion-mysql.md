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
    <h3 class="texto-subapartados">Unidad 2 - Configuración de un SGBD</h3>
  <h3 class="titulos-subapartados">Práctica:</h3>
    <h3 class="texto-subapartados">P21-Configuración-MySQL</h3>
  <h3 class="titulos-subapartados">Fecha:</h3>
    <h3 class="texto-subapartados">23 de Enero de 2026</h3>
</div>

<footer>
  <h6>Víctor Álvarez Fernández - ASXBD - 2º ASIR</h6>
</footer>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 2 ---------------->


<!-- Contiene anclajes a los diferentes ejercicios (están en siguientes páginas) -->
# **Índice**

<ul class="indice">
  <li><a href="#procesos">Procesos y Servicios</a>
    <ul>
      <li><a href="#cierre">Proceso de Cierre</a></li>
      <li><a href="#inicio">Proceso de Inicio</a></li>
      <li><a href="#servicios">Servicios que MySQL proporciona</a>
        <ul>
          <li><a href="#clientemysql">Cliente mysql</a></li>
          <li><a href="#mysqladmin">Utilidad mysqladmin (Administrador)</a></li>
          <li><a href="#mysqlcheck">Utilidad mysqlcheck (Chequeador)</a></li>
          <li><a href="#mysqldump">Utilidad mysqldump (Backup Secuencial)</a></li>
          <li><a href="#mysqlpump">Utilidad mysqlpump (Backup Multi-Hilo)</a></li>
          <li><a href="#mysqlimport">Utilidad mysqlimport (Importador)</a></li>
          <li><a href="#mysqlshow">Utilidad mysqlshow (Información)</a></li>
          <li><a href="#mysqlslap">Utilidad mysqlslap (Diagnóstico)</a></li>
        </ul>
      </li>
    </ul>
  </li>
  <li><a href="#configuracion">Configuración del Servidor</a>
    <ul>
      <li><a href="#lineacomandos">Uso de Opciones en Línea de Comandos</a></li>
      <li><a href="#ficherosconfiguracion">Uso de los Ficheros de Configuración</a></li>
      <li><a href="#variablesentorno">Uso de Variables de Entorno</a></li>
      <li><a href="#opcionesmysqld">Opciones Servidor mysqld</a></li>
      <li><a href="#modossql">Modos SQL del Servidor</a></li>
      <li><a href="#variablessistema">Variables de Sistema</a></li>
      <li><a href="#variablesestado">Variables de Estado</a></li>
    </ul>
  </li>
  <li><a href="#parametrosdestacables">Configuración Parámetros Destacables</a></li>
</ul>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 3 ---------------->


<h1 id="procesos">Procesos y Servicios SGBD</h1>

<p class="parrafo-primero">Los procesos más importantes en un Sistema Gestor de Bases de Datos (SGBD) son los de inicio y cierre (parada).</p>

<h4 id="cierre">Proceso de Cierre</h4>

<h5>1º/ Inicio del Proceso de Cierre</h5>

<p class="parrafo-normal">El proceso de cierre 'seguro' se puede ralizar de varias maneras:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">Utilidad mysqladmin</span>: ejecutando la utilidad mysqladmin desde una consola (válido tanto para Linux como para Windows)</li>
  <li><span class="purple">Realizando una parada del Servicio</span>: 
    <ol>
      <li>S.O. Windows: <span class="blue">net stop MySQL80</span> o desde la Consola de Servicios</li>
      <li>S.O. Linux: <span class="blue">systemctl stop mysql</span></li>
    </ol>
  </li>
  <li><span class="purple">Cliente MySQL Workbench</span>: pulsando dentro del menú INSTANCE en Startup/Shutdown <span class="cursiva">(esta opción es menos recomendable, porque aunque ejecutemos el cliente como administrador, este a veces se queda "trabado" y no procede al cierre)</span></li>
  </ol>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/1-parada-mysqladmin.png">
  <p class="num-romano">I</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/2-servicio-dentenido-win.png">
  <p class="num-romano">II</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/3-servicio-detenido-workbench.png">
  <p class="num-romano">III</p>
</div>

<h5 class="margen-superior-interior">2º/ Creación de Subproceso de Apagado</h5>

<p class="parrafo-normal">El subproceso de apagado es necesario si el cierre se hace desde el Cliente MySQL Workbench o desde la utilidad mysqladmin (línea de comandos). Todo esto se realiza de manera automática y no se requiere ninguna configuración adicional.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 4 ---------------->


<h1>Procesos y Servicios SGBD</h1>


<h5 class="margen-superior-interior">3º/ Servidor no acepta más conexiones</h5>

<p class="parrafo-normal">Cuando se realiza el proceso de cierre, el Servidor deja de aceptar conexiones: Cierra los puertos (TCP/IP), los sockets (si estamos en un S.O. Linux), las tuberías (si estamos en un S.O. Windows) y la memoria compartida.</p>

<h5>4º/ Servidor cancela las conexiones con los Clientes</h5>

<p class="parrafo-normal">Cualquier subproceso asociado pasa al estado de "muerto".</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">Transacciones Abiertas</span>: se cancelan y se deshacen para no generar conflictos.</li>
  <li><span class="purple">Procesos UPDATE o INSERT</span>: se realiza una actualización parcial, hasta donde le haya dado tiempo a realizar la última inserción o actualización.</li>
  <li><span class="purple">Parada de un Maestro</span>: se realiza el mismo tratamiento tanto a los procesos asociados al maestro, como a los esclavos.</li>
  <li><span class="purple">Parada de un Esclavo (Servidor Replicación)</span>: 
    <ol>
      <li>Se paran los subprocesos de E/S y SQL</li>
      <li>Se marcan como "muertos" los subprocesos en el Cliente</li>
      <li>Se permite la finalización de la Consulta SQL</li>
      <li>Se cancelan y deshacen las Transacciones Abiertas</li>
    </ol>
  </li>
</ol>

<h5 class="margen-superior-interior red">VER LISTA DE PROCESOS</h5>

<p class="parrafo-normal">Para ver la lista de procesos bastará con utilizar dentro del servidor la orden <span class="blue">SHOW PROCESSLIST;</span>.</p>

<p class="parrafo-normal">Otra alternativa es el uso de la utilidad <span class="blue">mysqladmin -u root -p proc</span> en la línea de comandos. El resultado en ambos casos será el mismo.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/4-ver-subprocesos.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 5 ---------------->


<h1>Procesos y Servicios SGBD</h1>


<h4 id="inicio" class="margen-superior-interior">Proceso de Inicio</h4>

<p class="parrafo-normal">El proceso para iniciar el servicio asociado a MySQL se puede realizar desde:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">Línea de Comandos</span>: 
    <ol>
      <li>S.O. Windows: <span class="blue">net start MySQL80</span> o desde la Consola de Servicios</li>
      <li>S.O. Linux: <span class="blue">systemctl start mysql</span></li>
    </ol>
  </li>
  <li><span class="purple">Reiniciando / Iniciando el equipo que acoge el Servidor MySQL</span>.</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/6-servicio-iniciado.png">
</div>


<h4 id="servicios" class="margen-superior-interior">Servicios que MySQL proporciona</h4>


<h5 id="clientemysql" class="red">Cliente mysql</h5>

<p class="parrafo-normal">Permite la ejecución de diferentes maneras:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">Interactiva</span>: utilizando la opción -e para ejecutar una orden: <span class="blue">mysql -u root -p -e "SELECT * FROM asxbd.clientes;"</span></li>
  <li><span class="purple">Desde un fichero</span>: <span class="blue">mysql -u root -p < fichero-prueba1.sql"</span></li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/7-consulta-mysql.png">
  <p class="num-romano">I</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/8-consulta-mysql-fichero.png">
  <p class="num-romano">II</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/9-contenido-fichero.png" width="50%">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 6 ---------------->


<h1>Procesos y Servicios SGBD</h1>


<h5 id="mysqladmin" class="red margen-superior-interior">Utilidad mysqladmin (Administrador MySQL)</h5>

<p class="parrafo-normal">Esta utilidad permite desde la línea de comandos:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">Crear / Borrar Bases de Datos</span>: <span class="blue">mysqladmin -u root -p CREATE prueba</span> | <span class="blue">mysqladmin -u root -p DROP prueba</span></li>
  <li><span class="purple">Recargar Permisos</span>: <span class="blue">mysqladmin -u root -p FLUSH-PRIVILEGES</span></li>
  <li><span class="purple">Volcar Tablas a Disco</span>: <span class="blue">mysqladmin -u root -p FLUSH-TABLES</span></li>
  <li><span class="purple">Volcar Ficheros Log</span>: <span class="blue">mysqladmin -u root -p FLUSH-LOG</span></li>
  <li><span class="purple">Consultar la Versión Instalada</span>: <span class="blue">mysqladmin -u root -p VERSION</span></li>
  <li><span class="purple">Ver los Subprocesos</span>: <span class="blue">mysqladmin -u root -p PROCESSLIST</span></li>
  <li><span class="purple">Ver el estado del Servidor</span>: <span class="blue">mysqladmin -u root -p STATUS</span></li>
  <li><span class="purple">Apagar el Servidor</span>: <span class="blue">mysqladmin -u root -p SHUTDOWN</span></li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/10-mysqladmin-crear-borrar-bd.png">
  <p class="num-romano">I</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/11-mysqladmin-flush.png">
  <p class="num-romano">II</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/14-mysqladmin-version.png">
  <p class="num-romano">V</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 7 ---------------->


<h1>Procesos y Servicios SGBD</h1>

<div class="imagenes margen-superior">
  <img src="img/procesos/12-mysqladmin-subprocesos.png">
  <p class="num-romano">VI</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/13-mysqladmin-estado-apagado.png">
  <p class="num-romano">VII</p>
</div>

<h5 id="mysqlcheck" class="red margen-superior-interior">Utilidad mysqlcheck (Chequeador MySQL)</h5>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">Verifica Tablas buscando errores</span>: <span class="blue">mysqlcheck -u root -p -c asxbd</span></li>
  <li><span class="purple">Analiza Tablas</span>: <span class="blue">mysqlcheck -u root -p -a asxbd</span></li>
  <li><span class="purple">Repara Tablas (no habilitada en InnoDB)</span></li>
  <li><span class="purple">Optimiza Tablas (no habilitada en InnoDB)</span></li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/15-mysqlcheck-verifica.png">
  <p class="num-romano">I</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/16-mysqlcheck-analiza.png">
  <p class="num-romano">II</p>
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 8 ---------------->


<h1>Procesos y Servicios SGBD</h1>


<h5 id="mysqldump" class="red margen-superior-interior">Utilidad mysqldump (Backup Secuencial)</h5>

<p class="parrafo-normal">Trabaja de forma secuencial (un solo hilo). Esto significa que procesa una tabla detrás de otra. Si tenemos una tabla con mucha información, todas las demás tendrán que esperar su turno.</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">Backup Esquema y Datos</span>: <span class="blue">mysqldump -u root -p asxbd > esquema-datos.sql</span></li>
  <li><span class="purple">Backup Sólo del Esquema</span>: <span class="blue">mysqldump -u root -p -d asxbd > esquema.sql</span></li>
  <li><span class="purple">Backup Sólo de los Datos</span>: <span class="blue">mysqldump -u root -p -t asxbd > datos.sql</span></li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/17-mysqldump.png">
</div>


<h5 id="mysqlpump" class="red margen-superior-interior">Utilidad mysqlpump (Backup Multi-Hilo)</h5>

<p class="parrafo-normal">Es multihilo, lo que se traduce en que realiza el volcado de varias tablas en paralelo, reduciendo drásticamente el tiempo de exportación en servidores con muchos núcleos de CPU.</p>

<p class="parrafo-normal">Su filtro es mucho más potente para realizar backups personalizados. También, permite comprimir la salida (output) mientras se genera, ahorrando tiempo de escritura en disco.</p>

<p class="parrafo-normal blue">mysqlpump -u root -p asxbd > backup-pump.sql</p>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/18-mysqlpump.png">
</div>

<p class="parrafo-normal margen-superior-interior">Antes de comenzar el proceso de backup, nos hace una advertencia para decirnos que Oracle dejará pronto de dar soporte a esta utilidad para sustituirla por MySQL Shell.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 9 ---------------->


<h1>Procesos y Servicios SGBD</h1>


<h5 id="mysqlimport" class="red margen-superior-interior">Utilidad mysqlimport (Importador de Datos)</h5>

<ol class="ol-sin-romanos">
  <li><span class="purple">El fichero tiene que llamarse igual que la tabla donde se insertarán los datos.</span></li>
  <li><span class="purple">El fichero tiene que estar almacenado en la ruta UPLOADS del Servidor MySQL.</span></li>
  <li><span class="purple">Debe estar habilitada la directiva <span class="red">local_infile=1</span> en el Fichero de Configuración de Opciones (Sección [mysqld]).</span></li>
</ol>

<p class="parrafo-normal">Cuando se habilita la directiva <span class="red">local_infile=1</span>, es recomendable tener los Clientes cerrados (MySQL Workbench, MySQL Shell o el cliente MySQL a través de la Línea de Comandos).</p>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/19-mysqlimport-directiva.png">
</div>

<p class="parrafo-normal margen-superior-interior">También, será necesario ejecutar dentro de uno de los Clientes MySQL la orden <span class="red">SET GLOBAL local_infile = 1;</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/20-mysqlimport-variable.png">
</div>

<p class="parrafo-normal-sin-justificar margen-superior-interior">Realizamos la importación: <span class="blue">mysqlimport -u root -p --local --fields-terminated-by="," --lines-terminated-by="\r\n" --columns=nombre,apellidos,email,telefono asxbd "C:\ProgramData\MySQL\MySQL Server 8.0\Uploads\clientes.txt"</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/21-mysqlimport-importacion.png">
</div>

<p class="parrafo-normal margen-superior-interior">Para poder hacer la importación de manera satisfactoria, he tenido que realizar una labor de investigación que me ha llevado a incluir las opciones <span class="brown">--lines-terminated-by="\r\n"</span> <span class="cursiva">(mueve el cursor al principio de la línea y baja de línea)</span>, <span class="brown">--fields-terminated-by=","</span> <span class="cursiva">(indica el separador de campos del fichero)</span> y <span class="brown">--columns=</span> <span class="cursiva">(indica los nombre de las columnas de la tabla)</span>.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 10 ---------------->


<h1>Procesos y Servicios SGBD</h1>

<div class="imagenes margen-superior">
  <img src="img/procesos/22-mysqlimport-prueba.png">
</div>

<h5 id="mysqlshow" class="red margen-superior-interior">Utilidad mysqlshow (Información BD)</h5>

<p class="parrafo-normal">Muestra información sobre Bases de Datos, Tablas, Columnas, Índices, ...</p>

<p class="parrafo-normal">Si nuestra intención es ver las bases de datos de nuestro Servidor MySQL, ejecutamos el siguiente comando: <span class="blue">mysqlshow -u root -p </span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/23-mysqlshow-bd.png" width="45%">
</div>

<p class="parrafo-normal margen-superior-interior">Para el resto de posibilidades la sintaxis es jerárquica: base de datos - tabla. Por ejemplo, para ver la base de datos asxbd: <span class="blue">mysqlshow -u root -p asxbd</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/24-mysqlshow-tabla.png" width="50%">
</div>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 11 ---------------->


<h1>Procesos y Servicios SGBD</h1>


<p class="parrafo-primero">Vamos a ver ahora la tabla stock de la base de datos asxbd: <span class="blue">mysqlshow -u root -p asxbd stock</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/25-mysqlshow-columnas.png">
</div>

<p class="parrafo-normal margen-superior-interior">Si nuestra intención es ver los índices creados en una tabla se añade la <span class="brown">opción -k</span>. Por ejemplo: <span class="blue">mysqlshow -u root -p -k asxbd clientes</span>.</p>


<h5 id="mysqlslap" class="red margen-superior-interior">Utilidad mysqlslap (Diagnóstico)</h5>

<p class="parrafo-normal">Es un programa de diagnóstico, que emula la carga de datos desde diferentes clientes y con múltiples interacciones desde cada uno de ellos.</p>

<p class="parrafo-normal"><span class="green">Ejemplo 1</span>: Simulación de la creación de tablas, inserción de contenido y la realización de consultas por parte de 50 clientes, cada uno con 200 interacciones. <span class="blue">mysqlslap -u root -p --delimiter=";" --create="CREATE TABLE a (b INT); INSERT INTO a VALUES (23)" --query="SELECT * FROM a" --concurrency=50 --iterations=200</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/26-mysqlslap-ejemplo1.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 12 ---------------->


<h1>Procesos y Servicios SGBD</h1>


<p class="parrafo-primero"><span class="green">Ejemplo 2</span>: Simulación de la creación de una tabla con 2 columnas de tipo numérico y 3 columnas de tipo carácter. El emulador autogenerará el contenido. La concurrencia será de 5 clientes y 200 interacciones/cliente. <span class="blue">mysqlslap -u root -p --number-int-cols=2 --number-char-cols=3 --auto-generate-sql --concurrency=5 --iterations=20</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/27-mysqlslap-ejemplo2.png">
</div>


<p class="parrafo-normal-sin-justificar margen-superior-interior"><span class="green">Ejemplo 3</span>: Simulación de la carga de contenido desde dos ficheros sql con instrucciones de creación y consulta respectivamente. <span class="blue">mysqlslap -u root -p --delimiter=";" --create=C:\Users\victo_klhqju1\Desktop\ficheros-prueba\create.sql --query=C:\Users\victo_klhqju1\Desktop\ficheros-prueba\query.sql --concurrency=5 --iterations=5</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/28-mysqlslap-ejemplo3.png">
</div>

<p class="parrafo-normal margen-superior-interior subrayado">Resumen de las Opciones más utilizadas</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">--create:</span> se utiliza para añadir o actualizar contenido de manera directa o a través de un fichero.</li>
  <li><span class="purple">--query:</span> se utiliza para realizar consultas de manera directa o a través de un fichero.</li>
  <li><span class="purple">--delimiter:</span> indica el delimitador que se utilizará para crear o actualizar el contenido.</li>
  <li><span class="purple">--auto-generate-sql:</span> se utiliza para autogenerar el contenido. Será necesario complementarlo con los tipos de datos que se desean.</li>
  <li><span class="purple">--number-int-cols:</span> indica el número de datos de tipo numérico.</li>
   <li><span class="purple">--number-char-cols:</span> indica el número de datos de tipo carácer.</li>
  <li><span class="purple">--concurrency:</span> indica el número de clientes que concurrirán.</li>
  <li><span class="purple">--iterations:</span> indica el número de interacciones por cliente.</li>
</ol>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 13 ---------------->


<h1 id="configuracion">Configuración del Servidor</h1>

<p class="parrafo-primero">La Configuración del Servidor se puede realizar desde la Línea de Comandos, desde el Fichero de Configuración de Opciones del Servidor ("my.ini" en Windows y "my.cnf" en Linux) y por supuesto desde las Variables de Entorno.</p>


<h5>Orden de Comprobación para el Inicio del Servicio MySQL</h5>

<ol class="ol-sin-romanos">
  <li><span class="purple">1º/ Variables de Entorno</span></li>
  <li><span class="purple">2º/ Fichero de Configuración de Opciones</span></li>
  <li><span class="purple">3º/ Línea de Comandos</span></li>
</ol>


<h5>Orden de Prioridad de los Métodos de Configuración</h5>

<ol class="ol-sin-romanos">
  <li><span class="purple">1º/ Línea de Comandos</span></li>
  <li><span class="purple">2º/ Ficheros de Configuración de Opciones</span></li>
  <li><span class="purple">3º/ Variables de Entorno</span></li>
</ol>

<p class="parrafo-normal"><span class="green">Recomendación</span>: lo adecuado sería realizar la configuración en el Fichero de Configuración ("my.ini" o "my.cnf"). Si durante la sesión se requiere alguna modificación puntual, se debe acudir a la Línea de Comandos.</p>


<h4 id="lineacomandos">Uso de Opciones en Línea de Comandos</h4>

<ol class="ol-sin-romanos">
  <li><span class="purple">Las opciones pueden comenzar por <span class="brown">-</span> o por <span class="brown">-- (estas van seguidas de un = y el valor que se quiere asignar a dicha opción)</span></span></li>
  <li><span class="purple">Lista de opciones de un programa: <span class="brown">nombrePrograma --help</span></span></li>
  <li><span class="purple">Valores relacionados con bytes: <span class="brown">K (KB) - M (MB) - G (GB)</span></span></li>
  <li><span class="purple">Espaces: <span class="brown">\b (Retroceso) - \t (Tabulador) - \n (Salto de Línea) - \r (Principio de Línea) - \\ (Barra) - \s (Espacio en Blanco) </span></span></li>
  <li><span class="purple">Opciones para Deshabilitar:</span>
    <ol>
      <li><span class="brown">-disable</span>: -disable-column-names</li>
      <li><span class="brown">-skip</span>: -skip-networking</li>
      <li><span class="brown">Valor 0</span>: flush-time=0</li>
    </ol>
  </li>
    <li><span class="purple">Opciones para Habilitar:</span>
    <ol>
      <li><span class="brown">-enable</span>: -enable-column-names</li>
      <li><span class="brown">Valor 1</span>: flush-time=1</li>
    </ol>
  </li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 14 ---------------->


<h1 id="configuracion">Configuración del Servidor</h1>

<ol class="ol-sin-romanos margen-superior-interior">
  <li><span class="purple">Prefijo --loose:</span> se utiiza para evitar que el servidor de MySQL se detenga si no reconoce una opción</li>
</ol>


<h4 id="ficherosconfiguracion">Uso de Fichero de Configuración de Opciones</h4>

<p class="parrafo-normal">Este es el lugar donde se debe realizar la configuración principal del Servidor MySQL. En Windows, si no se ha modificado la ruta, podemos encontrarlo habitualmente en: <span class="green">C:\ProgramData\MySQL\MySQL Server 8.0\my.ini</span>; y en Linux en <span class="green">/etc/mysql/my.cnf</span>.</p>


<ol class="ol-sin-romanos">
  <li><span class="purple">No usa prefijos iniciales</span>: port = 3306</li>
  <li><span class="purple"><span class="brown">[]</span> indican el inicio de una sección y llevan dentro el nombre de un programa</span>: [mysqld]</li>
  <li><span class="purple">Permite espacios alrededor del = cuando se va a asignar un valor</span>: host = localhost</li>
  <li><span class="purple">Las opciones con nombres compuestos a las cuales se les asigna un valor utilizan <span class="brown">_</span></span>: max_connections = 255</li>
  <li><span class="purple">Las opciones activación/desactivación utilizan <span class="brown">-</span></span>: skip-networking</li>
  <li><span class="purple">Las líneas vacías y/o que utilicen <span class="brown">#</span> se ignoran</span>: # socket=MySQL</li>
</ol>


<h5>Inclusión de Ficheros de Configuración dentro de otros</h5>

<p class="parrafo-normal">MySQL permite incluir líneas dentro de los ficheros de comunicación que llamen a otros ficheros o directorios para implementar otras opciones.</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Llamamiento a Ficheros <span class="brown">(!include rutaFichero)</span></span>: !include /home/alumno/miconf.cnf</li>
  <li><span class="purple">Llamamiento a Directorios <span class="brown">(!include rutaDirectorio)</span></span>: !include /home/alumno/configuraciones/</li>
</ol>


<h5>Otras Opciones en Línea de Comandos</h>

<ol class="ol-sin-romanos">
  <li><span class="purple">Indicarle a un Programa que no lea la configuración por defecto <span class="brown">(--no-defaults)</span></span>: mysqladmin --no-defaults</li>
  <li><span class="purple">Indicarle a un Programa que use un Fichero de Configuración Concreto <span class="brown">(--default-file="ruta")</span></span>: mysqladmin --defaults-file=C:\ProgramData\MySQL\MySQL Server 8.0\configuracion.ini</li>
  <li><span class="purple">Impresión de Valores por Defecto</span>: mysql --print-defaults</li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 15 ---------------->


<h1 id="configuracion">Configuración del Servidor</h1>


<h4 id="variablesentorno">Uso de Variables de Entorno</h4>

<p class="parrafo-normal">Las Variables de Entorno, aunque tienen menor prioridad que los Ficheros de Configuración y la Línea de Comandos; en el orden de comprobación cuando se inicia el Servidor MySQL son el 'primer espada'.</p>

<p class="parrafo-normal">Es decir, si en los ficheros de configuración no se indica ningún valor, los que se cargarán serán los que aporten las Variables de Entorno.</p>

<p class="parrafo-normal">Estos valores se pueden fijar de manera permanente o mientras el Servidor y/o Clientes estén activos.</p>

<div class="imagenes">
  <img src="img/configuracion/1-variables-entorno.png">
</div>


<h5 class="margen-superior-interior">Variables de Entorno más utilizadas en MySQL</h5>

<ol class="ol-sin-romanos">
  <li><span class="purple">MYSQL_HOST</span>: Nombre del equipo que acoge el Servidor</li>
  <li><span class="purple">USER</span>: Usuario que se conecta en el Cliente</li>
  <li><span class="purple">MYSQL_PWD</span>: Contraseña del Cliente</li>
  <li><span class="purple">MYSQL_TCP_PORT</span>: Puerto de Conexión</li>
  <li><span class="purple">PATH</span>: Programas que usa MySQL</li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 16 ---------------->


<h1 id="configuracion">Configuración del Servidor</h1>


<h4 id="opcionesmysqld">Opciones Servidor (mysqld)</h4>

<p class="parrafo-normal">El servidor (mysqld) lee las opciones introducidas desde la Línea de Comandos, las habilitadas en los Ficheros de Configuración y por supuesto las establecidas en las Variables.</p>

<p class="parrafo-normal">En lo referente a los ficheros de configuración, se centra únicamente en las secciones <span class="brown">[mysqld]</span> y <span class="brown">[server]</span>.</p>

<p class="parrafo-normal">Si queremos ver una lista de las Variables con las que trabaja nuestro Servidor MySQL, basta con acceder desde un cliente y teclear la orden: <span class="blue">SHOW VARIABLES \G;</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/configuracion/2-variables-activas-show.png">
</div>

<h5 class="margen-superior-interior">Opciones de Configuración para mysqld</h5>

<p class="parrafo-normal">Las opciones introducidas desde la Línea de Comandos son temporales y se realizan de manera muy puntual para obtener un resultado durante un periodo concreto.</span></p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Ruta de Instalación</span>: --basedir="ruta"</li>
  <li><span class="purple">Ruta de Almacenaje BDs</span>: --datadir="ruta"</li>
  <li><span class="purple">Motor de Almacenamiento por Defecto</span>: --default-storage-engine="tipo"</li>
  <li><span class="purple">Escritura en Disco de todos los Datos de cada sentencia SQL</span>: --flush</li>
  <li><span class="purple">Lista de Tareas para Ejecutar al Arrancar/Reiniciar el Servidor</span>: --init-file="rutaFichero"
    <ol>
      <li class="cursiva">Útil para insertar datos en una tabla</li>
      <li class="cursiva">Cambiar contraseña del usuario "root"</li>
    </ol>
  </li>
</ol>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 17 ---------------->


<h1 id="configuracion">Configuración del Servidor</h1>


<ol class="ol-sin-romanos margen-superior-interior">
  <li><span class="purple">Idioma de los Mensajes de Error</span>: --lc-messages="idioma" (es_ES)</li>
  <li><span class="purple">Puerto de Escucha</span>: --port="puerto"</li>
  <li><span class="purple">Restricción para crear usuarios</span>: --safe-user-create</li>
  <li><span class="purple">Desactivar Tablas de Permisos (útil para cambiar contraseña al root)</span>: --skip-grant-tables</li>
  <li><span class="purple">Deshabilitar Escucha de Puerto</span></span>: --skip-networking</li>
  <li><span class="purple">Establecer Ruta al Socket (Linux)</span>: --socket="ruta"</li>
  <li><span class="purple">Establecer una Ruta para las Tablas Temporales</span>: --temp-dir="ruta"</li>
  <li><span class="purple">Permitir que se ejecute el Servidor MySQL como el usuario del S.O. (Sólo Linux)</span>: --user="usuario"</li>
  <li><span class="purple">Habilitar Importación Datos Masivos desde un Fichero</span>: --local-infile</li>
</ol>


<p class="parrafo-normal margen-superior-interior"><span class="green">Ejemplo Cambio de Idioma Mensajes de Error</span>: Accedemos al Fichero de Configuración e incluímos en la sección [mysqld] la opción <span class="brown">lc-messages=es_ES</span> para establecer el idioma español, ya que predefinidamente está en inglés.</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/configuracion/3-cambiar-idioma-mensajes.png">
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/configuracion/4-comprobacion-cambio-idioma.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 18 ---------------->


<h1 id="configuracion">Configuración del Servidor</h1>


<h4 id="modossql">Los Modos SQL del Servidor</h4>

<p class="parrafo-normal">Definen el tipo de sintaxis que debe usar el Servidor MySQL. Esta característica permite que MySQL se pueda usar en entornos diferentes. Es decir, puede hacer compatible MySQL con otros entornos.</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">El servidor puede trabajar en diferentes modos</span></li>
  <li><span class="purple">El servidor permite hacer combinaciones de varios modos</span></li>
  <li><span class="purple">El servidor permite que cada cliente tenga su propia configuración</span></li>
</ol>

<p class="parrafo-normal">Los modos se puede establecer a través de la opción <span class="brown">--sql-mode="modos"</span> en la Línea de Comandos, <span class="brown">sql-mode = "modos"</span> en el Fichero de Configuración o con el comando <span class="brown">SET [SESSION|GLOBAL] sql_mode="modos";</span> en las Variables.</p>

<p class="parrafo-normal">Para poder ver los modos que están activos en el Servidor MySQL se puede teclear la sentencia <span class="blue">SHOW VARIABLES LIKE 'sql_mode'</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/configuracion/5-modos-sql.png">
</div>


<h4 id="variablessistema">Variables del Sistema del Servidor</h4>

<p class="parrafo-normal">Las Variables del Sistema del Servidor son el lugar donde el Servidor MySQL (mysqld) almacena la configuración. Los nombres de estas opciones suelen coincidir tanto en la Línea de Comandos, como en los Ficheros de Configuración, e incluso en las Variables; pero no siempre es así.</p>

<p class="parrafo-normal">Por ejemplo, el <span class="green">Motor de Almacenamiento</span> se puede asignar a través de las opciones <span class="brown">--default-storage-engine (Línea de Comandos)</span>, <span class="brown">default_storage_engine (Ficheros de Configuración)</span> y <span class="brown">default_storage_engine (Variable)</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/configuracion/6-storage-engine.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 19 ---------------->


<h1 id="configuracion">Configuración del Servidor</h1>


<h5 class="margen-superior-interior">Variables Dinámicas</h5>

<p class="parrafo-normal">Como ya vimos anteriormente, la modificación de los valores de la variables se puede realizar de manera distinta en Windows y en Linux. Linux ofrece la posibilidad de modificar el valor desde la propia Línea de Comandos sin tener que acceder a un Cliente MySQL, mientras que en Windows esta operación sólo se puede realizar desde un Cliente MySQL con la instrucción <span class="blue">SET [SESSION|GLOBAL] VARIABLE = valor;</span></p>

<p class="parrafo-normal">Esta instrucción no permite que se añadan sufijos en el caso de tener que introducir cantidades para referirnos a KB, MB o GB; teniendo que expresar estas cantidades en bytes o utilizando múltiplos para alcanzar el resultado deseado.</p>

<p class="parrafo-normal"><span class="green">Ejemplo Asignación Tamaño del Buffer de Lectura</span>: si queremos establecer en la variable <span class="brown">read_buffer_size</span> la cantidad de 2MB, tendremos que expresarla en bytes: 2*1024*1024. El resultado de la orden sería: <span class="blue">SET GLOBAL read_buffer_size=2*1024*1024;</span></p>


<h5>Tipos de Variables Dinámicas</h5>

<ol class="ol-sin-romanos">
  <li><span class="purple">Globales:</span> afectan al comportamiento general del Servidor MySQL.
    <ol>
      <li>Obtienen los valores en el Proceso de Inicio del servicio</li>
      <li>Para modificar estos valores se requiere tener privilegios</li>
      <li>Los cambios afectarán a todos los Clientes</li>
      <li>Los nuevos valores tendrán efecto en los Clientes que ya estaban conectados cuando se abra una nueva sesión</li>
    </ol>
  </li>
  <li><span class="purple">Sesión:</span> afectan al comportamiento del Cliente que se conecta.
    <ol>
      <li>Obtienen los valores de las Variables Globales</li>
      <li>No se requieren permisos especiales para su modificación</li>
      <li>Los nuevos valores tendrán efecto inmediato en todos los Clientes</li>
    </ol>
  </li>
</ol>

<p class="parrafo-normal">Si cuando se introduce la orden en el Cliente MySQL no se indica el tipo de variable, por defecto se entiende que es de 'SESSION'.</span></p>

<p class="parrafo-normal"><span class="green">Valor Default</span>: muchas variables permiten su uso volver a los valores por defecto.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 20 ---------------->


<h1 id="configuracion">Configuración del Servidor</h1>


<h5 class="margen-superior-interior">Orden de Lectura Variables Globales</h5>

<ol class="ol-sin-romanos">
  <li><span class="purple">1º/ Valor por Defecto (Inicio del Servicio)</span></li>
  <li><span class="purple">2º/ Valor establecido en el fichero de configuración</span></li>
  <li><span class="purple">3º/ Valor introducido por Línea de Comandos</span></li>
  <li><span class="purple">4º/ Valor modificado con la orden SET GLOBAL</span></li>
</ol>

<h5>Prioridad Variables Globales</h5>

<ol class="ol-sin-romanos">
  <li><span class="purple">1º/ Valor modificado con la orden SET GLOBAL</span></li>
  <li><span class="purple">2º/ Valor introducido por Línea de Comandos</span></li>
  <li><span class="purple">3º/ Valor establecido en el fichero de configuración</span></li>
  <li><span class="purple">4º/ Valor por Defecto (Inicio del Servicio)</span></li>
</ol>


<h5 class="margen-superior-interior">Orden de Lectura Variables de Sesión</h5>

<ol class="ol-sin-romanos">
  <li><span class="purple">1º/ Valor de la Variable Global</span></li>
  <li><span class="purple">2º/ Valor modificado con la orden SET SESSION</span></li>
</ol>


<h5>Prioridad Variables de Sesión</h5>

<ol class="ol-sin-romanos">
  <li><span class="purple">1º/ Valor modificado con la orden SET SESSION</span></li>
  <li><span class="purple">2º/ Valor de la Variable Global</span></li>
</ol>


<h5 class="margen-superior-interior">Valores Máximos</h5>

<p class="parrafo-normal">Se pueden utilizar en variables que permitan modificación en tiempo de ejecucion, aplicando en ellas el <span class="red">prefijo --maximum</span>.</span></p>

<p class="parrafo-normal"><span class="green">Ejemplo</span>: --maximum-net-buffer-length</p>

<p class="parrafo-normal">Esta variable controla el tamaño máximo del buffer que MySQL utiliza para enviar y recibir datos a través de la red.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/configuracion/7-maximum.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 21 ---------------->


<h1 id="configuracion">Configuración del Servidor</h1>


<h4 id="variablesestado">Variables de Estado del Servidor</h4>

<p class="parrafo-normal">Estas variables proporcionan información del estado del Servidor MySQL. Hay dos tipos: de Sesión y Globales.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/configuracion/8-variables-sesion.png">
</div>

<p class="parrafo-normal margen-superior-interior">Orden <span class="blue">FLUSH STATUS;</span>: es una herramienta fundamental para la depuración de rendimiento. Su función es resetar los contadores de las variables de etado, permitiendo iniciar las mediciones desde cero.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/configuracion/9-flush-status.png">
</div>


<h4 class="margen-superior-interior">Conclusiones de la Gestión del Servidor MySQL (mysqld)</h4>

<p class="parrafo-normal">En entornos Windows, la gestión del servidor MySQL se realiza de forma óptima a través del servicio MYSQL80, lo que impide la ejecución directa del comando mysqld desde la línea de comando.</p>

<p class="parrafo-normal">Por este motivo, la metodología adecuada para aplicar configuraciones permanentes se debe realizar en el Fichero de Configuración, donde se permite el uso de múltiplos (K, M, G) y prefijos como maximum para limitar recursos.</p>

<p class="parrafo-normal">Para modificaciones temporales sin reinicio, se debe emplear el comando SET desde el cliente MySQL: el nivel GLOBAL afecta a todas las conexiones futuras, mientras que el nivel SESSION permite realizar ajustes temporales en el usuario actual.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 22 ---------------->


<h1 id="configuracion">Configuración del Servidor</h1>


<h4>Variables: Distinción y Usos</h4>

<p class="parrafo-normal">La administración de un Servidor de MySQL requiere distinguir cuatro categorías de variables según su naturaleza y propósito.</p>

<p class="parrafo-normal">En primer lugar, las <span class="blue">Variables de Entorno</span>, que pertenecen al sistema operativo y <span class="purple">configuran el contexto previo al inicio del programa</span>.</p>

<p class="parrafo-normal">Una vez en ejecución, el motor utiliza <span class="blue">Variables de Sistema</span> para <span class="purple">realizar ajustes</span>, las cuales se dividen en <span class="red">estáticas (ejemplos: basedir, port, ...)</span> que exigen un reinicio para su aplicación; y <span class="green">dinámicas</span>, que permiten ajustes en caliente mediante comandos SET a nivel Global o de Sesión.</p>

<p class="parrafo-normal">Por último, existen las <span class="blue">Variables de Estado</span>, que a diferencia de las anteriores son indicadores de solo lectura que actúan como contadores en tiempo real para la <span class="purple">monitorización del rendimiento</span>.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 23 ---------------->


<h1 id="parametrosdestacables">Configuración Parámetros Destacables</h1>

