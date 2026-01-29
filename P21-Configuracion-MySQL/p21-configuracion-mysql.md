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
    <h3 class="texto-subapartados">24 de Enero de 2026</h3>
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
  <li><a href="#parametrosdestacables">Configuración Parámetros Destacables</a>
    <ul>  
      <li><a href="#espacio">Espacios de Almacenamiento</a>
        <ul>
          <li><a href="#myisam">MyISAM</a></li>
          <li><a href="#merge">MERGE</a>
          <li><a href="#memory">Memory</a>
          <li><a href="#innodb">InnoDB</a>
          <li><a href="#blackhole">Blackhole</a>
          <li><a href="#otrosmotores">Otros Motores</a>
        </ul>
      </li>
    </ul>
  </li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 3 ---------------->

<!-- Contiene anclajes a los diferentes ejercicios (están en siguientes páginas) -->
# **Índice**

<ul style="list-style: none; margin-bottom: 0; padding-bottom: 0; margin-top: 5px; padding-top: 10px;">
  <li>
    <ul>
      <li><a href="#confespacios">Configuracion Espacios</a></li>
      <li><a href="#confinnodb">Configuracion InnoDB</a></li>
      <li><a href="#confmyisam">Configuracion MyISAM</a></li>
      <li><a href="#pordefecto">Definir Característica por Defecto</a></li>
      <li><a href="#accesoremoto">Acceso Remoto</a></li>
      <li><a href="#politica">Política de Contraseñas</a></li>
    </ul>
  </li>
</ul>
<ol class="indice" start="4" style="margin-top: 0; padding-top: 0;">
  <li><a href="#diccionario">Estructura del Diccionario de Datos</a></li>
  <li><a href="#ficheroslog">Ficheros Logs</a></li>
  <li><a href="#documentacion">Documentación Configuración</a></li>
  <li><a href="#resumen">Resumen Variables más Importantes</a></li>
  <li><a href="#usuarios">Consulta de Usuarios y Privilegios</a></li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 4 ---------------->


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


<!---------------- PÁGINA 5 ---------------->


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


<!---------------- PÁGINA 6 ---------------->


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


<!---------------- PÁGINA 7 ---------------->


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


<!---------------- PÁGINA 8 ---------------->


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


<!---------------- PÁGINA 9 ---------------->


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


<!---------------- PÁGINA 10 ---------------->


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


<!---------------- PÁGINA 11 ---------------->


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


<!---------------- PÁGINA 12 ---------------->


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


<!---------------- PÁGINA 13 ---------------->


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


<!---------------- PÁGINA 14 ---------------->


<h1 id="configuracion">Configuración del Servidor</h1>

<p class="parrafo-primero">La Configuración del Servidor se puede realizar desde la Línea de Comandos, desde el Fichero de Configuración de Opciones del Servidor ("my.ini" en Windows y "my.cnf" en Linux) y por supuesto desde las Variables de Entorno.</p>


<h5>Orden de Comprobación para el Inicio del Servicio MySQL</h5>

<ol class="ol-sin-numero">
  <li><span class="purple">1º/ Variables de Entorno</span></li>
  <li><span class="purple">2º/ Fichero de Configuración de Opciones</span></li>
  <li><span class="purple">3º/ Línea de Comandos</span></li>
</ol>


<h5>Orden de Prioridad de los Métodos de Configuración</h5>

<ol class="ol-sin-numero">
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


<!---------------- PÁGINA 15 ---------------->


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



<!---------------- PÁGINA 16 ---------------->


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


<!---------------- PÁGINA 17 ---------------->


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


<!---------------- PÁGINA 18 ---------------->


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


<!---------------- PÁGINA 19 ---------------->


<h1 id="configuracion">Configuración del Servidor</h1>


<h4 id="modossql">Modos SQL del Servidor</h4>

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


<!---------------- PÁGINA 20 ---------------->


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


<!---------------- PÁGINA 21 ---------------->


<h1 id="configuracion">Configuración del Servidor</h1>


<h5 class="margen-superior-interior">Orden de Lectura Variables Globales</h5>

<ol class="ol-sin-numero">
  <li><span class="purple">1º/ Valor por Defecto (Inicio del Servicio)</span></li>
  <li><span class="purple">2º/ Valor establecido en el fichero de configuración</span></li>
  <li><span class="purple">3º/ Valor introducido por Línea de Comandos</span></li>
  <li><span class="purple">4º/ Valor modificado con la orden SET GLOBAL</span></li>
</ol>

<h5>Prioridad Variables Globales</h5>

<ol class="ol-sin-numero">
  <li><span class="purple">1º/ Valor modificado con la orden SET GLOBAL</span></li>
  <li><span class="purple">2º/ Valor introducido por Línea de Comandos</span></li>
  <li><span class="purple">3º/ Valor establecido en el fichero de configuración</span></li>
  <li><span class="purple">4º/ Valor por Defecto (Inicio del Servicio)</span></li>
</ol>


<h5 class="margen-superior-interior">Orden de Lectura Variables de Sesión</h5>

<ol class="ol-sin-numero">
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


<!---------------- PÁGINA 22 ---------------->


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


<!---------------- PÁGINA 23 ---------------->


<h1 id="configuracion">Configuración del Servidor</h1>


<h4>Variables: Distinción y Usos</h4>

<p class="parrafo-normal">La administración de un Servidor de MySQL requiere distinguir cuatro categorías de variables según su naturaleza y propósito.</p>

<p class="parrafo-normal">En primer lugar, las <span class="blue">Variables de Entorno</span>, que pertenecen al sistema operativo y <span class="purple">configuran el contexto previo al inicio del programa</span>.</p>

<p class="parrafo-normal">Una vez en ejecución, el motor utiliza <span class="blue">Variables de Sistema</span> para <span class="purple">realizar ajustes</span>, las cuales se dividen en <span class="red">estáticas (ejemplos: basedir, port, ...)</span> que exigen un reinicio para su aplicación; y <span class="green">dinámicas</span>, que permiten ajustes en caliente mediante comandos SET a nivel Global o de Sesión.</p>

<p class="parrafo-normal">Por último, existen las <span class="blue">Variables de Estado</span>, que a diferencia de las anteriores son indicadores de solo lectura que actúan como contadores en tiempo real para la <span class="purple">monitorización del rendimiento</span>.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 24 ---------------->


<h1 id="parametrosdestacables">Configuración Parámetros Destacables</h1>


<h4 id="espacio">Espacio de Almacenamiento</h4>

<p class="parrafo-normal">Los Motores de Almacenamiento controlan la forma en la que se implemetan las tablas. MySQL permite almacenar tablas de distintos motores en la misma Base de Datos.</p>

<p class="parrafo-normal">Orden <span class="blue">SHOW ENGINES \G</span>: Ver los Motores de Almacenamiento Disponibles. El campo "Support" nos indica si están o no habilitados.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/1-motores-disponibles.png">
</div>


<h5 id="myisam" class="h5-especial margen-superior-interior">Motor Almacenamiento MyISAM <span class="red">Uso desaconsejado en la actualidad</span></h5>

<p class="parrafo-normal">Es una versión mejorada del Motor ISAM. MyISAM <span class="red">no permite transacciones, ni bloqueos menores a los realizados por una tabla completa</span>. Tampoco permite restricciones de clave foránea entre tablas.</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Más eficiente con número elevado de lecturas</span></li>
  <li><span class="purple">La Gestión de Almacenamiento se realiza con tres ficheros</span>:
    <ol>
      <li>Fichero de Datos (.MYD)</li>
      <li>Fichero de Índices (.MYI)</li>
      <li>Fichero de Metadatos (.SDI)</li>
    </ol>
  </li>
  <li><span class="purple">Cada tabla va en un fichero</span>: el tamaño máximo de la tabla es el que permita el sistema de ficheros de la partición, así como el número máximo de filas lo marca la capacidad del disco duro</li>
  <li><span class="purple">Opción de Reparación Automática <span class="brown">(--myisam-recover-options=BACKUP,FORCE)</span></span>: esta opción permite reparar tablas si encuentran fallos cuando se inicia el servicio, algo que puede retardar la puesta en marcha</li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 25 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<ol class="ol-sin-romanos margen-superior-interior">
  <li><span class="purple">Opciones de Reparación Manual</span>: 
    <ol>
      <li>Orden <span class="blue">CHECK TABLE;</span></li>
      <li>Orden <span class="blue">REPAIR TABLE;</span></li>
      <li><span class="green">Utilidad myisamchk</span></li>
    </ol>
  </li>
  <li><span class="purple">Permite la inserción de filas mientras se realizan consultas de lectura</span></li>
  <li><span class="purple">Permite indexación de texto completo (FULLTEXT)</span>
    <ol>
      <li>Tipos de Datos: CHAR, VARCHAR, TEXT y FULLTEXT</li>
      <li>Límite 500 caracteres</li>
      <li>No permite búsquedas con patrones (LIKE)</li>
    </ol>  
  </li>
  <li><span class="purple">Escrituras retrasadas de clave DELAY_KEY_WRITE</span>
    <ol>
      <li>Los cambios de índices se almacenan en "buffer de índices"</li>
      <li>Mejora rendimiento en tablas con muchos accesos</li>
    </ol>  
  </li>
  <li><span class="purple">Compresión de Clave</span>: almacena valores de cadenas similares sucesivas</li>
  <li><span class="purple">Opción Compresión de Tablas <span class="green">(Utilidad myisampack)</span></span>: las tablas se convierten en Sólo Lectura</li>
  <li><span class="purple">Tiene más funciones para columnas AUTO_INCREMENT</span></li>
</ol>


<h5 id="merge" class="h5-especial margen-superior-interior">MRG_MyISAM (MERGE) <span class="red">Uso desaconsejado en la actualidad</span></h5>

<p class="parrafo-normal">Agrupa varias tablas MyISAM en 'una tabla virtual'. La ventaja de este motor es que permite superar los límites en las tablas del motor MyISAM. Cabe destacar, que cuando se realiza una consulta a una tabla, esta actúa en toda la agrupación.</p>

<p class="parrafo-normal"><span class="green">Ejemplo de Uso</span>: Registro de Datos de Acceso a una Página Web, donde la información crece de manera exponencial. 'MERGE' permite optar por la creación de tablas mensuales, medida que reducirá el almacenamiento y el tiempo en las consultas. Al estar las doce tablas agrupadas, se podrá realizar una estadística anual teniendo en cuenta todas y cada una de las tablas.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 26 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h5 id="memory" class="h5-especial margen-superior-interior">MEMORY</h5>

<p class="parrafo-normal">El motor MEMORY destaca por su alta velocidad al gestionar los datos directamente en la Memoria RAM, siendo útil para tablas de consulta rápida o almacenamiento temporal de datos no críticos.</p>

<ol class="ol-sin-romanos">
  <li>Las tablas se almacenan en la Memoria RAM</li>
  <li>Las tablas se inician siempre limpias, porque residen en una memoria volátil</li>
  <li>Las filas de datos son de longitud fija, según lo indicado por la definición del tipo de dato utilizado <span class="cursiva">(Ejemplo: Para una fila con tipo de dato VARCHAR(100), se reservan los 100 caracteres)</span></li>
</ol>


<h5 id="innodb" class="h5-especial margen-superior-interior">InnoDB</h5>

<p class="parrafo-normal">El motor de almacenamiento InnoDB es el más utilizado en la actualidad y el que aporta un máximo rendimiento al permitir procesar gran número de datos.</p>

<ol class="ol-sin-romanos">
  <li>Permite búsquedas de texto con datos del tipo FULLTEXT</li>
  <li>Es muy eficiente con operaciones de grabación elevadas ya que <span class="brown">los bloqueos se realizan a nivel de fila</span>, permitiendo mucha más concurrencia</li>
  <li><span class="brown">Detecta automáticamente las Transacciones Sólo Lectura</span>:
    <ol>
      <li>Transacciones Lectura-Escritura: llevan asignada una ID</li>
      <li>Transacciones Sólo Lectura: NO llevan asignada una ID</li>
    </ol>
  </li>
</ol>


<h5 class="margen-superior-interior">Estado de Transacciones Sólo Lectura</h5>

<p class="parrafo-normal">InnoDB permite habilitar el estado de <span class="brown">"Transacciones Sólo Lectura"</span> para un Cliente, para ello se deben realizar los siguientes pasos:</p>

<ol class="ol-numerico">
  <li>Iniciar el estado 'Transacciones Sólo Lectura' con la orden: <span class="blue">START TRANSACTION READ ONLY;</span></li>
  <li>Mientras dure este "paréntesis", se permitirán consultas, pero no creaciones ni inserciones de contenido</li>
  <li>Finalizar el estado 'Transacciones Sólo Lectura' con la orden: <span class="blue">COMMIT;</span></li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 27 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<p class="parrafo-primero"><span class="green">Ejemplo "Transacciones Sólo Lectura"</span>: en las dos próximas imágenes se puede ver en el Cliente MySQL Workbench como al habilitar el estado de "Transacciones de Sólo Lectura", queda bloqueada la inserción de datos. Una vez cerrado este estado, la inserción vuelve a estar operativa.</p>

<h5 align="center">Activación Transacciones Sólo Lectura</h5>

<div class="imagenes">
  <img src="img/parametros/2-transacciones-read-only-start.png">
</div>

<h5 align="center" class="margen-superior-interior">Desactivación Transacciones Sólo Lectura</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/3-transacciones-read-only-commit.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 28 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h5 class="margen-superior-interior">Almacenamiento en InnoDB (Tablespace)</h5>

<p class="parrafo-normal">En el motor InnoDB las Tablas e Índices se almacenan en uno o varios conjuntos de archivos denominados "Tablespace" (TS), que el propio motor se encarga de gestionar.</p>

<p class="parrafo-normal cursiva">Si en el equipo que actúa como servidor MySQL hay particiones de disco libres, estas se pueden destinar a este propósito.</p>

<p class="parrafo-normal">En las <span class="red">versiones antiguas de MySQL</span>, todo el Servidor se almacenaba por defecto en una <span class="green">única Tablespace (TS)</span> que se encontraba ubicada en el directorio Data con el nombre <span class="green">ibdata1</span>: C:\ProgramData\MySQL\MySQL Server 8.0\Data\ibdata1. El tamaño inicial de este fichero es de 12 MB.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/4-almacenamiento-ts.png">
</div>

<p class="parrafo-normal margen-superior-interior">Las <span class="red">versiones más recientes de MySQL</span> tienen activada por defecto la opción <span class="brown">innodb_file_per_table (innodb_file_per_table = 1)</span>. Esta característica habilita la creación de <span class="green">una Tablaspace (TS) por cada tabla contenida en el Servidor MySQL</span>.</p>

<ol class="ol-sin-romanos">
  <li>El contenido se clasifica por Bases de Datos</li>
  <li><span class="purple">Cada tabla tendrá su propio archivo con formato .ibd</span></li>
  <li>El archivo <span class="purple">ibdata1</span> no dejará de existir, ya que <span class="purple">es el encargado de cohesionar todas las Tablaspace (TS)</span></li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 29 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<div class="imagenes margen-superior">
  <img src="img/parametros/5-ts-organizacion-1.png">
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/6-ts-organizacion-2.png">
</div>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 30 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h5 class="margen-superior-interior">Estado Transacciones Seguras</h5>

<p class="parrafo-normal">InnoDB permite habilitar el estado de <span class="brown">"Transacciones Seguras"</span> para que un cliente realice transacciones con la total tranquilidad de poder revertir los cambios en caso de error.</p>

<ol class="ol-numerico">
  <li>Iniciar el estado 'Transacciones Seguras' con la orden: <span class="blue">START TRANSACTION;</span></li>
  <li>Mientras el estado esté activo, se podrán realizar creaciones e inserciones</li>
  <li>Para finalizar este estado se deben confirmar las transacciones o deshacer los cambios:
    <ol class="ol-circle">
      <li>Deshacer cambios: <span class="blue">ROLLBACK;</span></li>
      <li>Confirmar cambios: <span class="blue">COMMIT;</span></li>
    </ol>
  </li>
</ol>

<h5 align="center">Deshacer Cambios en Transacciones Seguras</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/7-transacciones-seguras-rollback.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 31 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h5 align="center" class="margen-superior-interior">Confirmar Cambios en Transacciones Seguras</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/8-transacciones-seguras-commit.png">
</div>


<h5 class="margen-superior-interior">InnoDB: Bloqueos Explícitos en Filas</h5>

<p class="parrafo-normal">InnoDB permite asegurar resgistros específicos sin impedir que otros usuarios trabajen con el resto de la tabla, mientras se realiza una consulta en el ámbito transaccional.</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Bloqueo Compartido (FOR SHARE)</span>: Permite que otros lean la fila, pero nadie puede modificarla.</li>
  <li><span class="purple">Bloqueo Exclusivo (FOR UPDATE)</span>: Es un bloqueo total. Solo tú puedes leer y modificar esa fila. Los demás deben esperar a que tú termines (COMMIT o ROLLBACK) para poder acceder a ella.</li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 32 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h5 align="center" class="margen-superior-interior">Bloqueo Compartido</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/9-bloqueo-compartido.png">
</div>


<h5 align="center" class="margen-superior-interior">Bloqueo Exclusivo</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/10-bloqueo-exclusivo.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 33 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h5 class="margen-superior-interior">InnoDB: Claves Foráneas</h5>

<p class="parrafo-normal">InnoDb permite las Claves Foráneas, que son columnas en una tabla "hija" que apuntan a la Clave Primaria de otra tabla "padre".</p>


<div class="imagenes margen-superior-interior">
  <img src="img/parametros/11-clave-foranea.png">
</div>



<h5 class="margen-superior-interior">InnoDB: Acciones en Cascada</h5>

<p class="parrafo-normal">Define qué debe pasar con los "hijos" cuando el "padre" cambia o desaparece. Se configuran con estas reglas:</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">ON DELETE CASCADE</span>: Si borras al padre, MySQL borra automáticamente a todos sus hijos. Es ideal para limpiezas profundas</li>
  <li><span class="purple">ON UPDATE CASCADE</span>: Si cambias el ID del padre, los IDs en las tablas hijas se actualizan solos para no perder la conexión</li>
  <li><span class="purple">ON DELETE SET NULL</span>: Si borras al padre, los hijos se quedan, pero su columna de referencia se pone a NULL (quedan "huérfanos" pero no se borran)</li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 34 ---------------->


<h1>Configuración Parámetros Destacables</h1>



<h5 align="center" class="margen-superior-interior">Inclusión de Acción en Cascada en Tabla "Hija"</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/12-cascada-muestra.png">


<h5 align="center" class="margen-superior-interior">Inserción de Datos en Tablas "Padre" e "Hija"</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/13-insercion.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 35 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h5 align="center" class="margen-superior-interior">Eliminación Datos en Tabla "Padre"</h5>

<p class="parrafo-normal">En la imagen se puede observar como al eliminar la categoría "5" de la tabla "categorias" (asociada a Alimentación), se han borrado los productos "Botella Agua 2L" y "Macarrones 1KG"; los cuales estaban vinculados con esa categoría.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/14-eliminar-cascada.png">
</div>


<h5 id="blackhole" class="h5-especial margen-superior-interior">BLACKHOLE</h5>

<p class="parrafo-normal">El motor BLACKHOLE se utiliza en escenarios específicos de replicación y auditoría, donde es necesario capturar operaciones de escritura sin persistir los datos localmente. Este motor descarta la información almacenada, pero registra todas las operaciones en el binary log.</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Servidor BLACKHOLE</span>: es el servidor MySQL que recibe las operaciones de escritura (INSERT, UPDATE, DELETE), pero no almacena los datos. Su función es generar eventos en el binary log que serán utilizados por otros servidores para reconstruir la información.</li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 36 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<ol class="ol-sin-romanos margen-superior-interior">
  <li><span class="purple">Servidor Real (InnoDB)</span>: replica desde el servidor BLACKHOLE y aplica los eventos del binary log, reconstruyendo los datos de forma persistente. Este servidor puede ser utilizado para consultas o como origen de nuevas réplicas.</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/15-blackhole.png">
</div>


<h5 class="h5-especial margen-superior-interior">Otros Motores de Almacenamiento</h5>

<ol id="otrosmotores" class="ol-sin-romanos">
  <li><span class="purple">FEDERATED</span>: NO está habilitado por defecto en MySQL <span class="brown">(--federated)</span>. Este motor permite accesos a tablas remotas que gestionan otros motores.</li>
  <li><span class="purple">ARCHIVE</span>: almacena filas que se escriben una vez y nunca se modifican.</li>
  <li><span class="purple">CSV</span>: valores separados por comas. Este motor almacena cada tabla en un fichero con extensión .csv. Cada fila de la tabla ocupa una línea dentro de los ficheros.</li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 37 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h4 id="confespacios">Configuración de Espacios de Almacenamiento</h4>


<h5 class="h5-especial">Directorio de Datos</h5>

<p class="parrafo-normal">MySQL guarda las Bases de Datos que se crean en el proceso de instalación del Servidor y por supuesto, las que se crean a posteriori.</p>

<p class="parrafo-normal">El directorio de almacenamiento se suele establecer en el proceso de instalación, aunque también se puede añadir/modificar posteriormente en la directiva <span class="purple">datadir</span> dentro del Fichero de Configuración.</p>


<h5 id="confinnodb" class="h5-especial">Motor InnoDB</h5>

<p class="parrafo-normal">Gestiona tres recursos: los Espacios para Tablas "Tablespace" (TS), la Caché y los Logs.</p>

<p class="parrafo-normal">Los valores por defecto asociados a estos recursos son:</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Espacios de Tablas (TS)</span>: 12 MB (autoextensible) - ibdata1</li>
  <li><span class="purple">Ficheros Log</span>: 5 MB - ib_logfile0 - ib_logfile1</li>
</ol>


<h5 class="h5-especial margen-superior-interior">Configuración InnoDB (Fichero de Configuración)</h5>


<h5>Espacio para Tablas Compartido</h5>

<p class="parrafo-normal"><span class="brown">innodb_data_file_path</span>: define el nombre del fichero, el tamaño y los atributos de los Espacios para Tablas (TS).</p>

<p class="parrafo-normal-sin-justificar">Configuración por defecto: <span class="brown">innodb_data_file_path = ibdata1:12M:autoextend</span></p>


<h5>Espacio Temporal Global</h5>

<p class="parrafo-normal"><span class="brown">innodb_temp_data_file_path</span>: define el nombre del fichero, el tamaño y los atributos del Espacio Temporal para las Tablas.</p>

<p class="parrafo-normal">Configuración por defecto: <span class="brown">innodb_data_file_path = ibtmp1:12M:autoextend</span></p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 38 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h5 class="margen-superior-interior">Tamaño de Página</h5>

<p class="parrafo-normal"><span class="brown">innodb_page_size</span>: define el tamaño de las páginas (la unidad mínimo de lectura-escritura).</p>

<p class="parrafo-normal">Configuración por defecto (16 KB): <span class="brown">innodb_page_size = 16384</span></p>

<ol class="ol-sin-romanos">
  <li><span class="purple">16 KB</span>: ideal para la mayoría de aplicaciones web</li>
  <li><span class="purple">4-8 KB</span>: útil para cargas de trabajo con muchas escrituras pequeñas o ante la coincidencia con un tamaño de bloque del sistema de ficheros de la partición</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/18-pagina.png">
</div>


<h5>Tamaño de Caché</h5>

<p class="parrafo-normal"><span class="brown">innodb_buffer_pool_size</span>: define el área de la memoria RAM donde InnoDB almacena en caché tanto los datos de las tablas como sus índices.</p>

<p class="parrafo-normal">Configuración por defecto: <span class="brown">innodb_buffer_pool_size = 128M</span></p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Equipos con < 4GB RAM</span>: 50% del tamaño de la RAM</li>
  <li><span class="purple">Equipos con 8-32 GB</span>: 50-70% del tamaño de la RAM</li>
  <li><span class="purple">Equipos con más 32 GB</span>: 75% del tamaño de la RAM</li>
</ol>

<p class="parrafo-normal">En la configuración de mi servidor he optado por establecer un valor de 2 GB. Aunque la MV tiene 6 GB, al ser un laboratorio de pequeñas pruebas he entendido que es una cantidad más que suficiente (33% de la RAM).</p>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/16-cache-1.png">
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/17-cache-2.png">
</div>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 39 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h5 class="margen-superior-interior">Ficheros Log</h5>

<p class="parrafo-normal"><span class="brown">innodb_log_files_in_group</span>: define el número de ficheros log que utilziará InnoDB.</p>

<p class="parrafo-normal">Configuración por defecto: <span class="brown">innodb_log_files_in_group = 2</span></p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Tamaño del Buffer 1-8 GB</span>: 1 Fichero Log / GB</li>
  <li><span class="purple">Tamaño del Buffer + 8 GB</span>: 0,75 Ficheros Log / GB</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/19-logs.png">
</div>


<h5 class="margen-superior-interior">Tamaño del Registro de Transacciones (Ficheros Log)</h5>

<p class="parrafo-normal"><span class="brown">innodb_redo_log_capacity</span>: define el tamaño del registro de transaccines (de los ficheros log).</p>

<p class="parrafo-normal">Configuración por defecto (100 MB): <span class="brown">innodb_redo_log_capacity = 100663296</span></p>

<p class="parrafo-normal">Lo ideal es establecer un <span class="purple">25% del Tamaño del Buffer</span>.</p>

<p class="parrafo-normal">En la configuración de mi servidor he optado por establecer un tamaño de 1000MB para los dos Ficheros Log con los que contará.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/20-tamaño-logs.png">
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/21-tamaño-logs-cambiado.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 40 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h5 class="margen-superior-interior">Ruta del Directorio de los Ficheros Log</h5>

<p class="parrafo-normal"><span class="brown">innodb_log_group_home_dir</span>: define la ruta donde se almacenan los ficheros log.</p>

<p class="parrafo-normal">Lo ideal es <span class="purple">establecer una ruta distinta (a poder ser en otro disco duro) para aumentar el rendimiento</span>.</p>

<p class="parrafo-normal">En la configuración de mi servidor he optado por añadir un disco de 2 GB (recordamos que tenemos un máximo de 1000MB para los ficheros) y establecer ahí el directorio de los Ficheros Log.</p>

<p class="parrafo-normal">También será necesario mover el directorio <span class="green"><#innodb_redo</span> (ubicado en C:\ProgramData\MySQL\MySQL Server 8.0\Data\) con su contenido a la nueva ubicación, ya que MySQL no lo hace automáticamente. Esta acción es fundamental para poder iniciar el servicio con la nueva configuración.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/22-ruta-logs.png">
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/23-ruta-logs-cambiada.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 41 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h5 class="margen-superior-interior">Ver Espacio Reutilizable</h5>

<p class="parrafo-normal">Utilizando dentro de la Base de Datos deseada la orden <span class="blue">SHOW TABLE STATUS \G</span>, se obtiene información de interés sobre cada una de las tablas que contiene.</p>

<p class="parrafo-normal">El campo <span class="cursiva">Data_free</span> nos indica el espacio reutilizable que tiene cada tabla.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/parametros/24-ver-espacio-reutilizable.png">
</div>



<h4 id="confmyisam" class="margen-superior-interior">Configuración MyISAM</h4>

<p class="parrafo-normal">Aunque no se recomienda el uso de este motor de almacenamiento, haremos alguna apreciación sobre su configuración.</p>

<p class="parrafo-normal">La gestión del almacenamiento se realiza con tres ficheros, aunque nos centraremos en los Ficheros de Datos (.MYD) y de Índices (.MYI).</p>

<p class="parrafo-normal">Con respecto a la Caché, utiliza la del Sistema Operativo donde está instalado el Servidor MySQL.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 42 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h5 class="margen-superior-interior">Tamaño de Caché de Claves (Índices)</h5>

<p class="parrafo-normal">La opción <span class="brown">key_buffer_size</span>, indica el espacio de memoria RAM que MySQL reserva para almacenar los índices de las tablas MyISAM. Se recomienda establecer una cantidad que no supere el 25% de la Memoria RAM.</p>

<p class="parrafo-normal">Si el valor de key_buffer_size es el adecuado, el servidor mostrará valores muy próximos a 0 en las siguientes variables:</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">key_reads</span>: Lectura de Disco</li>
  <li><span class="purple">key_reads_request</span>: Solicitudes Lectura de Disco</li>
  <li><span class="purple">key_write</span>: Escritura de Disco</li>
  <li><span class="purple">key_write_request</span>: Solicitudes de Escritura de Disco</li>
</ol>


<h5>Tamaño de cada Bloque de la Caché</h5>

<p class="parrafo-normal">La opción <span class="brown">key_cache_block_size</span>, es el tamaño de cada bloque de la caché. Por defecto esta cantidad es de 1024. Cuanto más grande sea el tamaño de los bloques, habrá menos desperdicio de caché de índices, pero se incrementará el número de bloques que no se leen, por eso es necesario equilibrarlo.</p>



<h5>Cachés Diferenciadas</h5>

<p class="parrafo-normal">Se considera una buena práctica crear una caché diferenciada para las tablas que tengan más uso. Cada caché se asociará a un conjunto de variables del sistema:</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">key_buffer_size</span></li>
  <li><span class="purple">key_cache_block_size</span></li>
  <li><span class="purple">key_cache_limits</span></li>
  <li><span class="purple">key_cache_threshold</span></li>
</ol>

<p class="parrafo-primero">En el Fichero de Configuración será necesario hacer referencia a esas nuevas cachés, asociándolas con las variables correspondientes. Simplemente con su mención y la asignación de un valor, las nuevas cachés estarán operativas.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 43 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<p class="parrafo-primero green">Ejemplo para la Caché de la Tabla prueba1:</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">prueba1.key_buffer_size </span>= "valor"</li>
  <li><span class="purple">prueba1.key_cache_block_size </span>= "valor"</li>
  <li><span class="purple">prueba1.key_cache_limits </span>= "valor"</li>
  <li><span class="purple">prueba1.key_cache_threshold </span>= "valor"</li>
</ol>

<p class="parrafo-normal">Las variables asociadas a la caché por defecto también se pueden mencionar con la misma sintaxis: <span class="purple">default.key_buffer_size</span>, aunque no es necesario.</p>


<h5>Asignar una Tabla a una Caché</h5>

<p class="parrafo-normal">Se realizaría en un Cliente MySQL con la orden: <span class="blue">CACHE INDEX tabla1, tabla2 IN prueba1;</span>.</p>


<h4 id="pordefecto">Definición Características por Defecto de una Base de Datos</h4>

<ol class="ol-sin-romanos">
  <li><span class="purple">Quitar InnoDB como motor por defecto</span>: skip-innodb</li>
  <li><span class="purple">Añadir motor por defecto</span>: store-engine = "motor"</li>
  <li><span class="purple">Conjunto de Caracteres por defecto</span>: character_set_database = "conjunto"</li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 44 ---------------->


<h1>Configuración Parámetros Destacables</h1>



<h4 id="accesoremoto">Configuración de Acceso Remoto SGBD</h4>

<h5>Configuración en el Servidor</h5>

<p class="parrafo-normal">Instalador MySQL Installer (Windows): será necesario activar la opción TCP/IP y el Puerto durante el proceso de instalación.</p>

<p class="parrafo-normal">Fichero de Configuración (Windows y Linux): establecer la variable "port" y asignarle el valor del puerto deseado para la escucha. Es fundamental tener también comentada (#) la variable skip-networking.</p>



<h5>Configuración Clientes en formato Consola</h5>

<p class="parrafo-normal">Aunque ya se realizó en la práctica de instalación de MySQL, recordamos que para que un usuario puede acceder de manera remota habrá hacer una modifación en el host de acceso. Por defecto cuando se crea un usuario, este se crea para el servidor local (localhost).</p>

<p class="parrafo-normal">En el ejemplo que se muestra a continucación se procede a crear un nuevo usuario denominado "remoto" y a modificar el usuario "estudiante". Las órdenes utilizadas serán:</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Creación Nuevo Usuario</span>: <span class="blue">CREATE USER 'remoto'@'%' IDENTIFIED BY 'abc123.';</span></li>
  <li><span class="purple">Modificación Usuario</span>: <span class="blue">ALTER USER 'estudiante'@'%' IDENTIFIED BY 'abc123.';</span></li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/25-acceso-remoto.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 45 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h5 class="margen-superior-interior">Configuración Cliente MySQL Workbench</h5>

<p class="parrafo-normal">La configuración en MySQL Workbench es muy sencilla. En el campo Hostname será necesario colocar la Dirección IP donde está ubicado el equipo que contiene el Servidor MySQL Workbench, así como el puerto de escucha. También, pondremos el nombre del usuario con capacidad para acceder de manera remota.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/26-acceso-remoto-workbench.png">
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/27-acceso-remoto-workbench-2.png">
</div>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 46 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h5 class="margen-superior-interior">Establecimiento de Conexiones de Acceso desde la Consola</h5>

<p class="parrafo-normal">Para acceder desde una consola se pueden utilizar diferentes opciones:</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Host del Servidor</span>: <span class="brown">--host / -h</span></li>
  <li><span class="purple">Puerto de Acceso</span>: <span class="brown">--port -P</span></li>
  <li><span class="purple">Contraseña</span>: <span class="brown">--password / -p</span></li>
  <li><span class="purple">Usuario</span>: <span class="brown">--user / -u</span></li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/28-pruebas-accceso.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 47 ---------------->


<h1>Configuración Parámetros Destacables</h1>


<h4 id="politica">Política de Contraseñas</h4>


<h5>Caducidad de la Contraseña</h5>

<p class="parrafo-normal">En el Fichero de Configuración y a través de la opción <span class="brown">default-password-lifetime</span> se puede establecer una caducidad para las contraseñas de usuario. Si el valor es '0', estas nunca caducarán.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/30-variable-caducidad.png">
</div>

<p class="parrafo-normal">Además, desde un Cliente MySQL podemos asignar una caducidad a un usuario concreto con la orden: <span class="blue">ALTER USER 'usuario'@'host' PASSWORD EXPIRE INTERVAL 90 DAY;</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/parametros/29-caducidad-contraseña.png">
</div>


<h5>Acceso con Contraseña Caducada</h5>

<p class="parrafo-normal">En el Fichero de Configuración y a través de la opción <span class="brown">disconnect_on_expired_password</span> se puede permitir que un usuario se conecte cuando su contraseña está caducada. El objetivo es que la renueve tras su conexión.</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Valor 0</span>: <span class="brown">Permite conexión</span></li>
  <li><span class="purple">Valor 1</span>: <span class="brown">NO permite conexión</span></li>
</ol>


<h5>Reutilización de Contraseñas</h5>

<p class="parrafo-normal">En el Fichero de Configuración y a través de la opción <span class="brown">password_history</span> se puede habilitar/deshabilitar la reutilización de contraseñas.</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Valor 0</span>: <span class="brown">Permite repetir contraseñas</span></li>
  <li><span class="purple">Valor 1</span>: <span class="brown">NO permite repetir contraseñas</span></li>
</ol>

<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 48 ---------------->


<h1>Configuración Parámetros Destacables</h1>



<h5 class="margen-superior-interior">Intervalo de días para poder Reutilizar la Contraseña</h5>

<p class="parrafo-normal">En el Fichero de Configuración y a través de la opción <span class="brown">password_rescue_interval</span> se puede establecer el número de días que tienen que pasar para poder volver a usar una contraseña anterior.</p>


<h5>Petición de Contraseña Actual para Establecer una Nueva Contraseña</h5>

<p class="parrafo-normal">En el Fichero de Configuración y a través de la opción <span class="brown">password_require_current</span> se puede habilitar/deshabilitar la petición de la contraseña actual para establcer una nueva.</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Valor OFF</span>: <span class="brown">Desactivado</span></li>
  <li><span class="purple">Valor ON</span>: <span class="brown">Ativado</span></li>
</ol>


<div class="imagenes margen-superior-interior">
  <img src="img/parametros/31-politica-contraseñas.png">
</div>


<div class="imagenes margen-superior-interior">
  <img src="img/parametros/32-politica-contraseñas-variables.png">
</div>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 49 ---------------->


<h1 id="diccionario">Estructura del Diccionario de Datos</h1>

<p class="parrafo-primero">Los Metadatos muestran la informacion de los datos almacenados en el Servidor MySQL <span class="cursiva">(nombres de las Bases de Datos, nombres de las Tablas, Tipos de Datos, Permisos de Accceso, ...)</span>.</p>

<p class="parrafo-normal">Toda esta información se puede ver a través de las múltiples posibilidades de la orden <span class="blue">SHOW</span>, pero también se puede acceder a ella cosultando la <span class="darkblue">Bases de Datos INFORMATION_SCHEMA</span>.</p>


<h4>Base de Datos INFORMATION_SCHEMA</h4>

<p class="parrafo-normal">Está constituida con acceso de Sólo Lectura (Consultas), autorizando de esta manera que los usuarios de la Base de Datos tengan acceso sólamente a las filas permitidas.</p>


<h5>Ventajas</h5>

<ol class="ol-sin-romanos">
  <li>Datos almacenados en Tablas</li>
  <li>Consultas con la sentencia SELECT</li>
  <li>Gran flexibilidad en consultas de metados</li>
  <li>Facilita la migración desde otras Bases de Datos</li>
</ol>


<h5>Ver Bases de Datos almacenadas en el Servidor</h5>

<p class="parrafo-normal blue">SELECT SCHEMA_NAME FROM INFORMATION_SCHEMA.SCHEMATA;</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">SCHEMA_NAME</span>: Columna</li>
  <li><span class="purple">INFORMATION_SCHEMA</span>: Base de Datos</li>
  <li><span class="purple">SCHEMATA</span>: Tabla</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/diccionario/1-bases-datos.png">
</div>

<p class="parrafo-normal margen-superior-interior">Esto equivale a la orden: <span class="blue">SHOW DATABASES;</span></p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 50 ---------------->


<h1>Estructura del Diccionario de Datos</h1>


<h5 class="margen-superior-interior">Ver Todas las Tablas y Columnas de INFORMATION_SCHEMA</h5>

<p class="parrafo-normal blue">SHOW TABLES FROM INFORMATION_SCHEMA;</p>

<div class="imagenes margen-superior-interior">
  <img src="img/diccionario/2-tablas-information_schema.png">
</div>


<p class="parrafo-normal green margen-superior-interior">Ejemplo Mostrar Tablas de una Base de Datos: <span class="blue">SELECT * FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_SCHEMA = "asxbd";</span></p>

<ol class="ol-sin-romanos">
  <li><span class="purple">*</span>: Columna (Todas)</li>
  <li><span class="purple">INFORMATION_SCHEMA</span>: Base de Datos</li>
  <li><span class="purple">TABLES</span>: Tabla</li>
  <li><span class="purple">TABLE_SCHEMA</span>: Columna (asxbd)</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/diccionario/3-ejemplo-1.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 51 ---------------->


<h1>Estructura del Diccionario de Datos</h1>


<p class="parrafo-normal green margen-superior-interior">Ejemplo Mostrar Columnas de una Tabla de una Base de Datos: <span class="blue">SELECT * FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_SCHEMA = "asxbd";</span></p>

<ol class="ol-sin-romanos">
  <li><span class="purple">*</span>: Columna (Todas)</li>
  <li><span class="purple">INFORMATION_SCHEMA</span>: Base de Datos</li>
  <li><span class="purple">COLUMNS</span>: Tabla</li>
  <li><span class="purple">TABLE_NAME</span>: Columna (clientes)</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/diccionario/4-ejemplo-2.png">
</div>


<h5>Relaciones de Equivalencia más destacadas: SHOW - INFORMATION_SCHEMA</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/diccionario/5-relacion-equivalencia.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 52 ---------------->


<h1 id="ficheroslog">Ficheros Log</h1>

<p class="parrafo-primero">Por defecto todos los Ficheros de Registro (Log) se almacenan en el directorio Data. Esta ruta se puede modificar tanto en el Fichero de Configuración ("my.ini" en Windows y "my.cnf" en Linux), como en la Línea de Comandos.</p>

<p class="parrafo-normal">La opcion más recomendable es realizarlo a través del Fichero de Configuración, pero si se hace desde la Línea de Comandos hay que tener en cuenta que esto sólo estará permitido si el Servidor MySQL no está instalado como servicio del Sistema Operativo desde MySQL Installer.</p>


<h5>Opciones de Configuración</h5>

<ol class="ol-sin-romanos">
  <li><span class="purple">Activar Registro de Consultas</span>: <span class="brown">general_log=1</span></li>
  <li><span class="purple">Registro de Consultas</span>: <span class="brown">general_log_file="ruta"</span></li>
  <li><span class="purple">Activar Registro Consultas Lentas</span>: <span class="brown">slow_query_log=1</span></li>
  <li><span class="purple">Registro Consultas Lentas</span>: <span class="brown">slow_query_log_file="ruta"</span></li>
  <li><span class="purple">Registro de Errores</span>: <span class="brown">log_error="ruta"</span></li>
  <li><span class="purple">Registro Binario (Operaciones modificación)</span>: <span class="brown">log-bin="ruta"</span></li>
</ol>


<h5>Formato de los Ficheros Log</h5>

<p class="parrafo-normal">Además, en el Fichero de Configuración podemos activar un el formato corto o resumido asignándole a la opción el valor "1":</p>

<ol class="ol-sin-romanos">
  <li><span class="purple">Formato Resumido</span>: <span class="brown">log_short_format</span></li>
  <li><span class="purple">Formato Largo</span>: <span class="brown">log_long_format</span></li>
</ol>


<h5>Limpieza de Contenido de los Ficheros Log</h5>

<p class="parrafo-normal">Cuando se realice algún cambio en las rutas o cuando se desee reiniciar el contenido de los Ficheros Log se recomienda introducir en el Servidor MySQL la orden: <span class="purple">FLUSH LOGS;</span></p>


<h5>Recomendaciones</h5>

<ol class="ol-sin-romanos">
  <li>Activar los Registros y Configurar las Rutas en el Fichero de Configuración</li>
  <li>Habilitar los Ficheros Log para que se inicien con el Servidor</li>
  <li>Almacenar los Ficheros Logs en una ruta diferente a la de los Datos</li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 53 ---------------->


<h1 id="ficheroslog">Ficheros Log</h1>


<h5>Configuración Realizada</h5>

<p class="parrafo-normal">A la hora de realizar la configuración de las nuevas rutas es importante tener en cuenta varias cosas:</p>

<ol class="ol-sin-romanos">
  <li>Los directorios de las rutas deben estar creados con anterioridad</li>
  <li>El usuario <span class="green">NT SERVICE\MySQL</span> debe contar con permisos y control total en esos directorios</li>
</ol>


<div class="imagenes margen-superior-interior">
  <img src="img/logs/configuracion-logs.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 54 ---------------->


<h1 id="documentacion">Documentación de la Instalación</h1>


<h5 class="margen-superior-interior">Copia de Seguridad Fichero de Configuración</h5>

<p class="parrafo-normal">Cuando se finalice la configuración, será de gran utilidad realizar una Copia de Seguridad de los Ficheros de Configuración. Se recomienda que esta copia se aloje en otros discos o medios por si se requiere un rescate de esa documentación.</p>


<h5>Lista de Valores de las Variables</h5>

<p class="parrafo-normal">Otra buena práctica consistirá en realizar una extracción de los valores de las variables (de sesión y globales) que utiliza el Servidor MySQL.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/docs/extraccion-variables.png">
</div>


<h5 class="margen-superior-interior">Enlaces de Documentación Configuración</h5>


<ol class="ol-sin-romanos margen-superior-interior">
  <li class="purple"><a href="documentos-backup/my.ini" target="_blank">Copia de Seguridad de la Configuración</a></li>
  <li class="purple"><a href="documentos-backup/listado-valores-variables-mysql.txt" target="_blank">Listado Valores de Sesión de las Variables</a></li>
  <li class="purple"><a href="documentos-backup/listado-valores-globales-variables-mysql.txt" target="_blank">Listado Valores Globales de las Variables</a></li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 55 ---------------->


<h1 id="resumen">Resumen Variables más Importantes</h1>

<div class="imagenes margen-superior">
  <img src="img/variables/resumen-variables.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 56 ---------------->


<h1 id="usuarios">Consulta de Usuarios y Privilegios</h1>

<div class="imagenes margen-superior">
  <img src="img/usuarios/usuarios-privilegios.png">
</div>