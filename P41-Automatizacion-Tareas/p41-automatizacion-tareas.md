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
    <h3 class="texto-subapartados">Unidad 4 - Automatización de Tareas</h3>
  <h3 class="titulos-subapartados">Práctica:</h3>
    <h3 class="texto-subapartados">P41-Automatizacion-Tareas</h3>
  <h3 class="titulos-subapartados">Fecha:</h3>
    <h3 class="texto-subapartados">18 de Febrero de 2026</h3>
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
  <li><a href="#herramientas">Herramientas para la Automatización</a></li>
  <li><a href="#rutinas">Rutinas: Funciones y Procedimientos</a>
    <ul>  
      <li><a href="#funciones">Funciones</a></li>
      <li><a href="#procedimientos">Procedimientos</a></li>
      <li><a href="#llamadas">Llamadas</a></li>
      <li><a href="#sentencias">Sentencias: SELECT y SELECT INTO</a></li>
      <li><a href="#otras">Otras Operaciones y Consultas</a></li>
      <li><a href="#parametros">Parámetros y Variables</a></li>
      <li><a href="#condicionales">Sentencias: Condicionales</a></li>
      <li><a href="#bucles">Sentencias: Bucles</a></li>
      <li><a href="#cursores">Cursores</a></li>
      <li><a href="#excepciones">Manejo de Excepciones</a></li>
    </ul>
  </li>
  <li><a href="#disparadores">Disparadores</a></li>
  <li><a href="#eventos">Eventos: Planificación de Tareas</a></li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 3 ---------------->


<h1 id="herramientas">Herramientas para la Automatización</h1>

<p class="parrafo-primero">MySQL cuenta con dos posibles herramientas para la automatización de tareas, la primera de ellas cuenta con entorno gráfico y se llama MySQL Entreprise Monitor; la otra alternativa y la más recomendada porque implica tener un amplio conocimiento es basada en la programación a través de Procedimientos Almacenados.</p>

<p class="parrafo-normal">Los Procedimientos Almacenados son secuencias de código que se almacenan del lado del Servidor y que aportan una serie de ventajas:</p>

<ol class="ol-sin-romanos">
  <li>Permiten incluir de Instrucciones Compuestas (bucles, condicionales, ...)</li>
  <li>Reducen la sobrecarga de la red al estar almacenadas en el Servidor</li>
  <li>Permiten incluir cálculos complejos</li>
  <li>Permiten estandarizar operaciones de cálculo</li>
  <li>Proporcionan un mecanismo para procesar errores</li>
  <li>Cuentan con un control de acceso de datos sensibles mediante privilegios otorgados</li>
</ol>

<h4>Métodos de Ejecución</h4>

<ol class="ol-sin-romanos">
  <li><span class="darkblue">Funciones</span>: devuelven el resultado de un cálculo y se usan en expresiones</li>
  <li><span class="darkblue">Procedimientos</span>: se utilizan para realizar cálculos generales o generar conjuntos de resultados que se muestran al cliente</li>
  <li><span class="darkblue">Disparadores</span>: se asocian a una tabla y se ejecutan cuando esta se modifica con los eventos INSERT, UPDATE y DELETE</li>
  <li><span class="darkblue">Eventos</span>: se ejecutan en un momento concreto según su progración</li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 4 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<p class="parrafo-primero">Conjunto de Comandos almacenados en el Servidor, que son llamados por los clientes.</p>

<ol class="ol-sin-romanos">
  <li><span class="darkblue">Funciones</span>: devuelven un sólo valor</li>
  <li><span class="darkblue">Procedimientos</span>: pueden devolver varios valores o incluso ninguno</li>
</ol>


<h4 id="funciones">Funciones</h4>

<p class="parrafo-normal">Sintaxis: <span class="blue">CREATE DEFINER = <span class="green">'usuario'@'host'</span> FUNCTION <span class="red">nomFuncion()</span> <span class="purple">SQL SECURITY {DEFINER | INVOKER}</span> <span class="brown">BEGIN <span class="darkblue">sentencias;</span> END</span></span></p>

<h4 id="procedimientos">Procedimientos</h4>

<p class="parrafo-normal">Sintaxis: <span class="blue">CREATE DEFINER = <span class="green">'usuario'@'host'</span> PROCEDURE <span class="red">nomProcedimiento()</span> <span class="purple">SQL SECURITY {DEFINER | INVOKER}</span> <span class="brown">BEGIN <span class="darkblue">sentencias;</span> END</span></span></p>


<h5>Nivel de Seguridad</h5>

<ol class="ol-sin-romanos">
  <li><span class="purple">DEFINER</span>: se ejecuta con los permisos del creador de la rutina</li>
  <li><span class="purple">INVOKER</span>: se ejecuta con los permisos del cliente que lo invoca</li>
</ol>

<p class="parrafo-normal">Se recomienda que el usuario creador sea el administrador de la SGBD y que cuente con los permisos de Consultas (SELECT) y de Ejecución (EXECUTE) en todas las bases de datos y tablas del Servidor para mayor comodidad a la hora de crear las rutinas.</p>

<p class="parrafo-normal">Si cuando se crea la rutina no se indica la claúsula <span class="purple">SQL SECURITY</span>, por defecto el valor de la misma será <span class="purple">DEFINER</span>.</p>

<p class="parrafo-normal">Si en la rutina se utiliza el valor <span class="purple">INVOKER</span>, será necesario que el usuario que haga la llamada desde el lado del cliente cuente con permisos de Ejecución (EXECUTE) para poder ejecutarla.</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 5 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<h5>Uso de Delimitadores: DELIMITER</h5>

<p class="parrafo-normal">En MySQL, el carácter punto y coma (;) se utiliza por defecto para indicar el final de una sentencia. Sin embargo, al crear rutinas que contienen múltiples instrucciones en su interior, surge un conflicto: el servidor interpretaría el primer punto y coma interno como el final de toda la creación, dejando el código incompleto y generando un error de sintaxis. Para solucionar esto, se utiliza la instrucción <span class="darkblue">DELIMITER $$</span>. Esto le indica a MySQL que cambie temporalmente el símbolo de finalización por <span class="darkblue">$$</span>, permitiendo que todo el bloque de código se procese como una única unidad. Una vez definida la rutina, se emplea <span class="darkblue">DELIMITER ;</span> para restablecer el punto y coma como el delimitador estándar para las consultas habituales.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/rutinas/1-ejemplo-contador-usuarios.png">
</div>


<h4 id="llamadas">Llamadas</h4>

<ol class="ol-sin-romanos">
  <li><span class="darkblue">Funciones</span>: <span class="blue">SELECT</span> <span class="red">nomFuncion()</span>;</li>
  <li><span class="darkblue">Procedimientos</span>: <span class="blue">CALL</span> <span class="red">nomProcedimiento()</span>;</li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 6 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<h4 id="sentencias">Sentencias: SELECT y SELECT INTO</h4>


<h5>SELECT</h5>

<ol class="ol-sin-romanos">
  <li><span class="darkblue">Funciones</span>: NO muestran el resultado en pantalla</li>
  <li><span class="darkblue">Procedimientos</span>: Si muestran el resultado en pantalla</li>
</ol>


<h5>SELECT INTO</h5>

<ol class="ol-sin-romanos">
  <li><span class="darkblue">Funciones</span>: almacena el resultado en una variable</li>
  <li><span class="darkblue">Procedimientos</span>: almacena el resultado en una variable</li>
</ol>


<div class="imagenes margen-superior-interior">
  <img src="img/rutinas/2-ejemplo-producto-gama-alta.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 7 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<h4 id="otras">Otras Operaciones y Consultas</h4>


<h5>Eliminar una Rutina</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">DROP {FUNCTION | PROCEDURE} [IF EXISTS] <span class="red">{nomFuncion | nomProcedimiento}</span>;</p>

<div class="imagenes margen-superior-interior">
  <img src="img/rutinas/3-eliminar-procedimiento.png">
</div>


<h5>Consultar Rutinas Creada</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">SHOW CREATE {FUNCTION | PROCEDURE} <span class="red">{nomFuncion | nomProcedimiento}</span>;</p>

<div class="imagenes margen-superior-interior">
  <img src="img/rutinas/4-consultar-procedimiento-creado.png">
</div>


<h5>Consultar Estado de Todos los Procedimientos</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">SHOW PROCEDURE STATUS;</p>

<div class="imagenes margen-superior-interior">
  <img src="img/rutinas/5-consultar-estado-todos-procedimientos.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 8 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<h5>Consultar Estado de un Procedimiento según un patrón</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">SHOW PROCEDURE STATUS <span class="brown">LIKE ''</span>;</p>

<div class="imagenes margen-superior-interior">
  <img src="img/rutinas/6-consultar-estado-segun-pratron-procedimientos.png">
</div>


<h4 id="parámetros">Parámetros y Variables</h4>

<h5>Declaración de Variables: DECLARE</h5>

<p class="parrafo-normal">Crea una variable con el nombre y el tipo de dato indicado. Los datos pueden ser de tipo valor (INT, FLOAT, DECIMAL,... ) de tipo fecha (DATE, TIME, YEAR,... ) o de tipo cadena (CHAR, VARCHAR, TEXT, ...).</p>

<p class="parrafo-normal">Sintaxis: <span class="blue">DECLARE</span> <span class="red">nomVariable</span> <span class="green">tipo_dato</span>;</p>

<p class="parrafo-normal">Una variable se puede declarar con un valor por defecto (inicial o de arranque) que puede tener un valor concreto o uno nulo:</p>

<ol class="ol-sin-padding-sup-inf">
  <li><span class="darkblue">Valor Concreto</span>: <span class="blue">DECLARE</span> <span class="red">a</span> <span class="green">INT</span> <span class="brown">DEFAULT 5</span>;</li>
  <li><span class="darkblue">Valor NULL</span>: <span class="blue">DECLARE</span> <span class="red">a</span> <span class="green">INT</span> <span class="brown">DEFAULT</span>;</li>
</ol>


<h5>Declaración de Variables: SET</h5>

<p class="parrafo-normal">Crea una variable utilizando el operador <span class="brown">=</span>.</p>

<p class="parrafo-normal">Sintaxis: <span class="blue">SET</span> <span class="red">nomVariable</span> <span class="brown">=</span> <span class="green">valorNumerico</span>;</p>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 9 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<h5 id="parametros">Parámetros</h5>

<p class="parrafo-normal">Permiten pasar datos a las rutinas, e incluso devolverlos en el caso concreto de los procedimientos. Estos son los tipos de parámetros que se pueden utilizar:</p>

<ol class="ol-sin-romanos">
  <li><span class="darkblue">IN</span>: Parámetros de Entrada (por defecto)</li>
  <li><span class="darkblue">OUT</span>: Parámetros de Salida (sólo en los Procedimientos). El procedimiento puede asignar valores a estos parámetros que son devueltos cuando se realiza una llamada.</li>
  <li><span class="darkblue">INOUT</span>: Parámetros de Entrada/Salida (sólo en los Procedimientos). Permiten pasar valores, que podrán ser modificados.</li>
</ol>

<p class="parrafo-normal">Alcance de las Variables: no se puede ver el valor de una variable fuera del procedimiento salvo que el <span class="darkblue">parámetro sea de tipo OUT</span> o la <span class="brown">variable sea de tipo sesión (@)</span>.</p>


<div class="imagenes margen-superior-interior">
  <img src="img/rutinas/7-procedimiento-parametro-entrada-in.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 10 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<div class="imagenes margen-superior">
  <img src="img/rutinas/8-procedimiento-parametro-salida-out.png">
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/rutinas/9-procedimiento-parametro-inout.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 11 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<h4 id="condicionales">Condicionales</h4>

<h5>Condicional Simple: IF</h5>

<p class="parrafo-normal">Tiene solamente una condición.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/condicionales/1-condicional-simple.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 12 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<h5>Condicional Múltiple: IF - ELSEIF - ELSE</h5>

<p class="parrafo-normal">Puede tener varias condiciones. No se recomienda su uso con más de tres condiciones.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/condicionales/2-condicional-multiple.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 13 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<h5>Condicional Múltiple: CASE</h5>

<p class="parrafo-normal">Puede tener varias condiciones. Se recomienda su uso a partir de una cuarta condición.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/condicionales/3-condicional-case.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 14 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<h4 id="bucles">Bucles</h4>

<h5>Bucle Simple: LOOP</h5>

<p class="parrafo-normal">El bucle se repite hasta que se ejecute la sentencia <span class="green">LEAVE</span>.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/bucles/1-loop.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 15 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<h5>Bucle con Condición: REPEAT - UNTIL</h5>

<p class="parrafo-normal">El bucle se repite hasta que se cumpla una condición.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/bucles/2-repeat-until.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 16 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<h5>Bucle con Condición: WHILE</h5>

<p class="parrafo-normal">El bucle se repite mientras se cumple una condición.</p>

<div class="imagenes margen-superior-interior">
  <img src="img/bucles/3-while.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 17 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<h4 id="cursores">Cursores</h4>

<p class="parrafo-normal">Los cursores son herramientas que permiten recorrer una tabla, fila por fila para extraer un resultado con una consulta (SELECT).</p>

<p class="parrafo-normal">Sintaxis: <span class="blue">DECLARE</span> <span class="red">nomCursor</span> CURSOR FOR <span class="brown">sentencia_SELECT</span>;</p>

<p class="parrafo-normal">La declaración de los cursores se debe realizar tras la declaración de todas las variables que llevará la rutina.</p>


<h5>Manipulación de Cursores</h5>

<ol class="ol-sin-romanos">
  <li><span class="darkblue">OPEN</span>: Inicializa el conjunto de resultados asociados al cursor. <span class="blue">OPEN</span> <span class="red">nomCursor</span>;</li>
  <li><span class="darkblue">FETCH</span>: Extrae contenido de las filas (una o varias columnas). <span class="blue">OPEN</span> <span class="red">nomCursor</span> INTO <span class="green">variable (columna)</span>;</li>
  <li><span class="darkblue">OPEN</span>: Cierra el cursor. <span class="blue">CLOSE</span> <span class="red">nomCursor</span>;</li>
</ol>

<div class="imagenes margen-superior-interior">
  <img src="img/cursores/1-cursor.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 18 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<div class="imagenes margen-superior">
  <img src="img/cursores/2-cursor.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 19 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<h4 id="excepciones">Manejo de Excepciones</h4>

<p class="parrafo-normal">Las excepciones permiten manejar situaciones NO deseadas que pueden producirse durante la ejecución de una rutina. Para ello, se utiliza la instrucción <span class="brown">HANDLER</span>. Esta instrucción se encarga de indicar a MySQL que hacer en caso de que se produzca un error.</p>

<p class="parrafo-normal">Sintaxis: <span class="blue">DECLARE</span> <span class="green">tipo_actuacion</span> <span class="brown">HANDLER</span> FOR <span class="red">condición</span> <span class="darkblue">acciones</span>;</p>

<h5>Tipos de Actuación</h5>

<ol class="ol-sin-romanos">
  <li><span class="darkblue">CONTINUE</span>: se ejecuta el "plan B" y el procedimiento continua su curso</li>
  <li><span class="darkblue">EXIT</span>: se ejecuta el "plan B" y el procedimiento finaliza inmediatamente</li>
</ol>

<h5>Condición</h5>

<ol class="ol-sin-romanos">
  <li><span class="darkblue">Código de Error de MySQL</span>: código de MySQL que indica el tipo de error (Ej: 1062)</li>
  <li><span class="darkblue">SQLSTATE 'código'</span>: códigos de estado de MySQL que tienen un significado concreto. También, podemos encontrar dentro de esta gama los SQLEXCEPTION y SQLWARNING, siendo ambos muy habituales</li>
  <li><span class="darkblue">NOT FOUND</span>: es la condición utilizada para indicar que el cursor llega al final y se desea volver al inicio</li>
</ol>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 20 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>

<h5>Ejemplo Excepción con CONTINUE</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/errores/1-continue.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 21 ---------------->


<h1 id="rutinas">Rutinas: Funciones y Procedimientos</h1>


<h5>Ejemplo Excepción con EXIT</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/errores/2-exit.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>



<!---------------- PÁGINA 22 ---------------->


<h1 id="disparadores">Disparadores</h1>


<p class="parrafo-primero">Tipo especial de rutina almacenada que se activa cuando ocurre un evento de tipo INSERT, UPDATE o DELETE. Los disparadores (triggers) se almacenan en la Base de Datos en la que se definen.</p>

<h4>Momento en el que actúa un Disparador</h4>

<ol class="ol-sin-romanos">
  <li><span class="darkblue">BEFORE</span> (antes): es ideal para corregir datos antes de guardarlos</li>
  <li><span class="darkblue">AFTER</span> (después): es muy útil para actualizar otras tablas o dejar un registro de incidencias</li>
</ol>


<h4>Eventos de un Disparador</h4>

<ol class="ol-sin-romanos">
  <li><span class="green">INSERT</span>: se utiliza para insertar datos en una tabla. Cuando se utiliza en un disparador permite el uso del calificador <span class="brown">NEW</span> para referirse a los nuevos datos a insertar en una columna.</li>
  <li><span class="green">UPDATE</span>: se utiliza para actualizar datos en una tabla. Cuando se utiliza en un disparador permiten el uso de los calificadores <span class="brown">NEW</span> para referirse a los posibles nuevos datos, y <span class="brown">OLD</span> para referirse a los datos actuales de la tabla.</li>
  <li><span class="green">DELETE</span>: se utiliza para eliminar datos de una tabla. Cuando se utiliza en un disparador permite el uso del calificador <span class="brown">OLD</span> para referirse a los datos actuales de la tabla.</li>
</ol>


<p class="parrafo-normal">Sintaxis: <span class="blue">CREATE TRIGGER <span class="red">nomDisparador</span> <span class="darkblue">{BEFORE | AFTER}</span> <span class="green">{INSERT | UPDATE | DELETE}</span> ON <span class="purple">nomTabla</span> FOR EACH ROW </span> <span class="cursiva">sentencia;</span></p>



<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 23 ---------------->


<h1 id="disparadores">Disparadores</h1>


<h5>Ejemplo de Disparador AFTER - UPDATE</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/disparador/1-after-update.png">
</div>

<div class="imagenes margen-superior-interior">
  <img src="img/disparador/2-after-update.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 24 ---------------->


<h1 id="disparadores">Disparadores</h1>


<h5>Ejemplo de Disparador BEFORE - INSERT</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/disparador/3-before-insert.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 25 ---------------->


<h1 id="disparadores">Disparadores</h1>


<h5>Ejemplo de Disparador BEFORE - UPDATE (OLD - NEW)</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/disparador/4-before-update-old-new.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 26 ---------------->


<h1 id="disparadores">Disparadores</h1>


<h5>Ejemplo de Disparador AFTER - DELETE</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/disparador/5-after-delete.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 27 ---------------->


<h1 id="disparadores">Disparadores</h1>


<h5>Consultas Disparadores</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">SHOW TRIGGERS;</span></p>


<div class="imagenes margen-superior-interior">
  <img src="img/disparador/6-consultas-disparadores.png">
</div>


<h5>Eliminar Disparador</h5>

<p class="parrafo-normal">Sintaxis: <span class="blue">DROP TRIGGER <span class="red">nomDisparador</span>;</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/disparador/7-eliminar-comentario borrado.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 28 ---------------->


<h1 id="eventos">Eventos: Planificación de Tareas</h1>


<p class="parrafo-primero">Los eventos son tareas programadas que se ejecutan en un momento dado.</p>


<h4>Comprobar Encendido del Planificador</h4>

<p class="parrafo-normal">Sintaxis: <span class="blue">SHOW PROCESSLIST;</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/eventos/1-comprobar-encendido.png">
</div>

<h5>Activar / Desactivar el Planificador</h5>

<p class="parrafo-normal">El planificador se puede activar o desactivar de la misma manera que se activa una variable global de tipo booleana.</p>

<ol class="ol-sin-romanos">
  <li>Encendido: <span class="blue">SET GLOBAL event_scheduler = ON;</span></li>
  <li>Apagado: <span class="blue">SET GLOBAL event_scheduler = OFF;</span></li>
</ol>


<h4>Crear un Evento de Planificación</h4>

<p class="parrafo-normal">Sintaxis: <span class="blue">CREATE EVENT <span class="red">nomEvento</span> ON <span class="brown">SCHEDULE</span> <span class="darkblue">{AT | EVERY}</span> DO <span class="green">sentencias;</span></span></p>


<h4>Tipos de Planificación</h4>

<ol class="ol-sin-romanos">
  <li><span class="darkblue">AT</span>: se ejecuta en una fecha y hora concreta</li>
  <li><span class="darkblue">EVERY</span>: se ejecuta periódicamente (cada hora, día, semana, mes, ...)</li>
</ol>


<h5>Evento con Ejecución Concreta: AT</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/eventos/2-evento-at.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 29 ---------------->


<h1 id="eventos">Eventos: Planificación de Tareas</h1>


<h5>Evento con Ejecución Periódica: EVERY</h5>

<div class="imagenes margen-superior-interior">
  <img src="img/eventos/3-evento-every.png">
</div>


<h4>Ver todos los Eventos</h4>

<p class="parrafo-normal">Sintaxis: <span class="blue">SHOW EVENTS;</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/eventos/4-ver-eventos.png">
</div>


<h4>Modificar un Evento</h4>

<p class="parrafo-normal">Sintaxis: <span class="blue">ALTER EVENT <span class="red">nomEvento</span> ON SCHEDULE <span class="darkblue">EVERY 2 MONTH</span>;</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/eventos/5-modificar-evento.png">
</div>


<h4>Eliminar un Evento</h4>

<p class="parrafo-normal">Sintaxis: <span class="blue">DROP EVENT <span class="red">nomEvento</span>;</span></p>

<div class="imagenes margen-superior-interior">
  <img src="img/eventos/6-eliminar-evento.png">
</div>


<!-- Salto de Página -->
<div style="page-break-after: always;"></div>


<!---------------- PÁGINA 30 ---------------->


<h1 id="eventos">Eventos: Planificación de Tareas</h1>


<h4>Claúsulas</h4>

<p class="parrafo-normal">Cuando se crea un evento se pueden utilizar una serie de claúsulas que nos permitan establecer una fecha y/o hora de inicio (<span class="brown">STARTS</span>), una fecha y/o hora de fin (<span class="brown">ENDS</span>), e incluso una claúsula para almacenar el evento aunque este haya expirado (<span class="brown">ON COMPLETION PRESERVE</span>)</p>

<div class="imagenes margen-superior-interior">
  <img src="img/eventos/7-evento-clausulas.png">
</div>


<h4>Desactivar o Activar Eventos (Tareas)</h4>

<p class="parrafo-normal">En un momento dado, se puede optar por desactivar o activar un evento (tarea) por una determinada situación.</p>

<p class="parrafo-normal">Sintaxis Desactivar: <span class="blue">ALTER EVENT <span class="red">nomEvento</span> <span class="green">DISABLE</span>;</span></p>

<p class="parrafo-normal">Sintaxis Activar: <span class="blue">ALTER EVENT <span class="red">nomEvento</span> <span class="green">ENABLE</span>;</span></p>


<div class="imagenes margen-superior-interior">
  <img src="img/eventos/8-desc-act-evento.png">
</div>