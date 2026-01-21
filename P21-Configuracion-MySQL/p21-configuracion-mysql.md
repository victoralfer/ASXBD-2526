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

<!-- Imagen del IES Lois Peña Novo -->
<div class="logo-ies">
  <img src="img/logoies.jpg" alt="IES Lois Peña Novo">
</div>

<!-- Contiene anclajes a los diferentes ejercicios (están en siguientes páginas) -->
# **Índice**

<ul class="indice">
  <li><a href="#procesos">Procesos y Servicios</a>
    <ul>
      <li><a href="#cierre">Proceso de Cierre</a></li>
      <li><a href="#inicio">Proceso de Inicio</a></li>
      <li><a href="#servicios">Servicios que MySQL proporciona</a></li>
    </ul>
  </li>
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


<h1 id="procesos">Procesos y Servicios SGBD</h1>


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


<h1 id="procesos">Procesos y Servicios SGBD</h1>


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


<h5 class="red">Cliente mysql</h5>

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

<h1 id="procesos">Procesos y Servicios SGBD</h1>


<h5 class="red margen-superior-interior">Utilidad mysqladmin (Administrador MySQL)</h5>

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

<h1 id="procesos">Procesos y Servicios SGBD</h1>

<div class="imagenes margen-superior">
  <img src="img/procesos/12-mysqladmin-subprocesos.png">
  <p class="num-romano">VI</p>
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/13-mysqladmin-estado-apagado.png">
  <p class="num-romano">VII</p>
</div>

<h5 class="red margen-superior-interior">Utilidad mysqlcheck (Chequeador MySQL)</h5>

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

<h1 id="procesos">Procesos y Servicios SGBD</h1>


<h5 class="red margen-superior-interior">Utilidad mysqldump (Backup Secuencial)</h5>

<p class="parrafo-normal">Trabaja de forma secuencial (un solo hilo). Esto significa que procesa una tabla detrás de otra. Si tenemos una tabla con mucha información, todas las demás tendrán que esperar su turno.</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="purple">Backup Esquema y Datos</span>: <span class="blue">mysqldump -u root -p asxbd > esquema-datos.sql</span></li>
  <li><span class="purple">Backup Sólo del Esquema</span>: <span class="blue">mysqldump -u root -p -d asxbd > esquema.sql</span></li>
  <li><span class="purple">Backup Sólo de los Datos</span>: <span class="blue">mysqldump -u root -p -t asxbd > datos.sql</span></li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/procesos/17-mysqldump.png">
</div>


<h5 class="red margen-superior-interior">Utilidad mysqlpump (Backup Multi-Hilo)</h5>

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

<h1 id="procesos">Procesos y Servicios SGBD</h1>


<h5 class="red margen-superior-interior">Utilidad mysqlimport (Importador de Datos)</h5>

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


<h1 id="procesos">Procesos y Servicios SGBD</h1>

<div class="imagenes margen-superior">
  <img src="img/procesos/22-mysqlimport-prueba.png">
</div>



