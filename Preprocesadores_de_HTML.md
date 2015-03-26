
#Preprocesadores de HTML
Un preprocesador es una herramienta que toma los valores introducidos y los transforma a otro estado. Puede ser que le des un archivo en SASS y lo transforma a CSS (o viceversa). El resultado de esa transformación es el archivo preprocesado.

###Algunos preprocesadores de html son:
* HAML
* JADE
* Twig
* SLIM 
* Handlebars
##HAML
Es un lenguaje de marcado ligero que se usa para describir el XHTML de un documento Web sin emplear el código embebido tradicional. Está diseñado para solucionar varios problemas de los motores de plantillas tradicionales y también para ser un lenguaje de marcado tan elegante como sea posible.

 Haml funciona como reemplazo de sistemas de plantillas de páginas embebidas como PHP, RHTML y ASP. Sin embargo, Halm elimina la necesidad de escribirXHTML explícito dentro de la plantilla, por ser en sí una descripción de XHTML, más algo de código para generar contenido dinámico.
 
* El marcado debería ser bonito: No debería usarse solamente como una herramienta para lograr que los navegadores muestren una página como el autor lo desee. El renderizado no es lo único que la gente tiene que ver; también se tiene que ver, modificar y entender el marcado. Por tanto, este debería ser tan amable y placentero como el resultado del renderizado.
* El marcado no debe repetirse:
1. XHTML implica grandes repeticiones. La mayoría de los elementos deben ser nombrados dos veces: una vez antes de su contenido y otra después.
2. ERB agrega aun más repetición y caracteres innecesarios.
3. Halm evita todo esto recurriendo al sangrado en vez del texto para determinar dónde empiezan y terminan los elementos y los bloques de código.
4. Esto no solo da como resultado plantillas más compactas sino que además hace el código mucho más limpio a la vista.
* El marcado debería tener buen sangrado: Uno de los mayores problemas de los lenguajes de plantillas tradicionales es que no solo no fomentan el código bien sangrado sino que encima lo hacen difícil o incluso imposible de escribir. El resultado es un XHTML confuso e ilegible. Halm formatea las etiquetas de manera que todas estén bien sangradas y reflejen la estructura subyacente del documento.
* La estructura de XHTML debería ser clara: XML y XHTML son formatos fundados sobre la idea de un documento estructurado. Tal estructura se refleja en su marcado, y asimismo debería reflejarse en metamarcado como Haml. Debido a que la lógica de Haml se basa en el sangrado de elementos hijos, esta estructura se preserva naturalmente, lo que hace al documento mucho más fácil y lógico de leer por simples humanos.

###Ejemplo de muestra 
![enter image description here](https://lh3.googleusercontent.com/5cUxuqhVg5y5SBbkPjVes_7uRmudISymgfspK7jxu6k=s0 "ejemplo haml.PNG")

El Haml de arriba produce este XHTML

![enter image description here](https://lh3.googleusercontent.com/9LUMKnX1uPc8VRCYiRV-d-Yo2DOsoDv_cTpWzOc2PPk=s0 "ejemplo2 haml.PNG")

##Jade

En lugar de alegrarte la vida con las CSS, lo hace con el HTML.
En resumen, vendría a ser cómo atajar en el código html, aunque como veremos realmente va mucho más allá, y con él puedes hacer cosas que con el html no podrías montar… pero sí, en resumen es quitarte algo de trabajo en el desarrollo del html, que evidentemente, si lo sumas a Stylus ya tienes que tus trabajos de maquetación quedan bastante reducidos en tiempo.

html
  body
    //
      #content
        h1 Example

---------- Sacaría ----------

    <body>
     <!--
      <div id="content">
        <h1>Example</h1>
      </div>
       -->
    </body>
 
 
---------- Vamos más allá ----------
 ul
    li.first: a(href='#') foo
    li: a(href='#') bar
    li.last: a(href='#') baz

La potencia y rapidez con que se puede maquetar uniendo esto a stylus. De este modo, podemos reciclar el código CSS para nuestro html, o al revés, cada uno lo utilizará como le vea más conveniente.
Su potencia no se queda aquí, ya que jade soporta filtros, iteraciones, condicionales, templates, y mucho más…
Les recomendamos encarecidamente echar un vistazo tanto a jade como a stylus, estamos convencidos de que también agilizará y nos ayudará en nuestro trabajo.

![enter image description here](https://lh3.googleusercontent.com/4IIIq36uSYcfaYmfQOwKbJ2QQ8pDglsakl84uaKJRFc=s0 "ejemplo jade.PNG")

Jade es un motor de plantillas de alto rendimiento fuertemente influenciado por Haml e implementado con JavaScript para node y browsers. 


##Twig
####Ramita de plantilla Designer
A continuacion se describe la sintaxis y la semántica del motor de plantillas y será más útil como referencia para esas plantillas Twig creando.
####Synopsis
Una plantilla es simplemente un archivo de texto. Puede generar cualquier formato basado en texto (HTML, XML, CSV, LaTeX, etc.). No tiene una extensión específica, .html o .xml están muy bien.

Una plantilla contiene variables o expresiones, que son reemplazados con valores cuando se evalúa la plantilla, y las etiquetas, que controlan la lógica de la plantilla.

A continuación se muestra una plantilla mínima que ilustra algunos conceptos básicos:

    <!DOCTYPE html>
    <html>
    <head>
        <title>My Webpage</title>
    </head>
    <body>
      <ul id="navigation">
        {% for item in navigation %}
        <li><a href="{{ item.href }}">{{ item.caption }}</a></li>
        {% endfor %}
     </ul>

        <h1>My Webpage</h1>
        {{ a_variable }}
    </body>
</html>


####Variables
La aplicación pasa las variables en las plantillas para la manipulación en la plantilla. Las variables pueden tener atributos o elementos que puede acceder, también. La representación visual de una variable depende en gran medida de la aplicación proporciona.
Puede utilizar un punto para acceder a los atributos de una variable (métodos o propiedades de un objeto PHP o elementos de un array PHP), o el llamado sintaxis "subíndice" ([]) (.):
{{ foo.bar }}
{{ foo['bar'] }}

Cuando el atributo contiene caracteres especiales (como - que serían interpretadas como el operador menos), utilizar la función de atributo en lugar de acceder al atributo de la variable:

{# equivalent to the non-working foo.data-foo #}
{{ attribute(foo, 'data-foo') }}

####Configuración de variables
Puede asignar valores a variables dentro de los bloques de código. Misiones utilizan la etiqueta conjunto:
{% set foo = 'foo' %}
{% set foo = [1, 2] %}
{% set foo = {'foo': 'bar'} %}

####Filtros
Las variables pueden ser modificados por filtros. Los filtros se separa de la variable por una barra vertical (|) y pueden tener argumentos opcionales entre paréntesis. Múltiples filtros pueden ser encadenados. La salida de un filtro se aplica a la siguiente.

El ejemplo siguiente elimina todas las etiquetas HTML desde el nombre y títulos de los casos es el siguiente:

{{ name|striptags|title }}

Los filtros que aceptan argumentos tienen paréntesis alrededor de los argumentos. Este ejemplo se unirá a una lista por comas:

{{ list|join(', ') }}

Para aplicar un filtro en una sección de código, envuélvalo en la etiqueta de filtro:

{% filter upper %}
    This text becomes uppercase
{% endfilter %}

####Funciones
Las funciones pueden ser llamadas para generar contenido. Las funciones son llamados por su nombre seguido de paréntesis (()) y pueden tener argumentos.

Por ejemplo, la función de margen devuelve una lista que contiene una progresión aritmética de números enteros:

{% for i in range(0, 3) %}
    {{ i }},
{% endfor %}

####Nombrando Argumentos
Se agregó el soporte para los argumentos con nombre en el Twig 1.12: Nuevo en la versión 1.12.
{% For i in range (bajo = 1, alta = 10, paso = 2)%}
     {{Yo}},
{% Endfor%}

Utilizando argumentos con nombre hace que sus plantillas más explícito sobre el significado de los valores que usted pasa como argumentos:

{{Data | convert_encoding ('UTF-8', 'iso-2022-jp')}}
{# Versus #}
{{Datos | convert_encoding (de = "iso-2022-jp ', a' = UTF-8 ')}}

Los argumentos con nombre también pueden permitir que salte algunos argumentos para los que no desee cambiar el valor por defecto:

{# El primer argumento es el formato de fecha, que por defecto es el formato de fecha global si se pasa nulo #}
{{"Ahora" | Fecha (null, "Europa / París")}}
{# O saltar el valor de formato utilizando un argumento con nombre para la zona horaria #}
{{"Ahora" | Fecha (zona horaria = "Europa / París")}}

También puede utilizar ambos argumentos posicionales y nombrados en una llamada, en cuyo caso los argumentos posicionales siempre deben venir antes de argumentos con nombre:

{{"Ahora" | Fecha ('d / m / YH: i', zona horaria = "Europa / París")}}

##Slim
Slim es un lenguaje de plantillas, cuyo objetivo es reducir la vista sintaxis para las partes esenciales sin llegar a ser críptico. Comenzó como un ejercicio para ver cuánto podría ser eliminada de una plantilla estándar HTML (<,>, etiquetas de cierre, etc ...). A medida que más personas se interesaron por SLIM, la funcionalidad creció y también lo hizo la flexibilidad de la sintaxis.

Una breve lista de las características:
#####Sintaxis elegante: 
* Sintaxis abreviada y sin etiquetas de cierre (Uso de sangría en su lugar)
* Modo de estilo de HTML con etiquetas de cierre
* Etiquetas configurables de acceso directo `(# para <div id = "...">` y. Para `<div class = "...">`en la configuración por defecto).
#####Seguridad:
* HTML automática escapar por defecto
* Soporte para html?
#####Altamente configurable
#####Extensible a través de los siguientes plugins:
* Lógica menos modo similar al del bigote
* Incluye
* Traductor / I18n
#####Alto rendimiento:
*	Velocidad comparable a ERB / Erubis
*	Streaming apoyo en Rails

#####Con el apoyo de todos los principales marcos (Rails, Sinatra, ...)
#####Soporte Unicode completo para las etiquetas y atributos
#####Motores implícitos como Markdown y Textil

###¿Por qué utilizar Slim?

Slim le permite escribir plantillas muy mínimos que son fáciles de mantener y prácticamente garantiza que usted escribe HTML bien formado y XML.
También pensamos que la sintaxis Slim también es estético y lo hace mucho más divertido de escribir plantillas. Ya que se puede utilizar slim como un gota en el reemplazo de todo el marco principal se puede empezar fácilmente.
La arquitectura Slim es muy flexible y permite escribir extensiones y plugins de sintaxis.

####Ejemplo de sintaxis

Aquí está un ejemplo rápido para demostrar lo que una plantilla slim se ve así:

 doctype html
html
  head
    title Slim Examples
    meta name="keywords" content="template language"
    meta name="author" content=author
    link rel="icon" type="image/png" href=file_path("favicon.png")
    javascript:
      alert('Slim supports embedded javascript!')

  body
    h1 Markup examples

    #content
      p This example shows you how a basic Slim file looks.

    == yield

    - if items.any?
      table#items
        - for item in items
          tr
            td.name = item.name
            td.price = item.price
    - else
      p No items found. Please add some inventory.
        Thank you!

    div id="footer"
      == render 'footer'
      | Copyright &copy; #{@year} #{@author}


##Handlebars
Handlebars es un popular sistema de plantillas en Javascript que te permite crear y formatear código HTML de una manera muy sencilla. En lugar de hacer operaciones tediosas en librerías como jQuery para tocar el DOM insertando elementos de manera independiente con append o prepend, te permite crear bloques de código HTML, escritos directamente con HTML que poblarás con datos que te vengan de un JSON. Es tan sencillo como escribir HTML y tan potente que te permite realizar operaciones de recorrido de estructuras que encontramos en otros sistemas de plantillas en lenguajes como PHP.

Debe utilizar Handlebars.js cuando: 

* Se utiliza un marco de JavaScript front-end como Backone.js, Ember.js, y similares; más front-end JavaScript marcos se basan en motores de plantillas
* La aplicación o pagina se actualizará con frecuencia-
* Usted tiene varias pilas tecnología que dependen de los datos desde el servidor y desea que todas las pilas de tecnología para procesar los mismos datos
* Su aplicación tiene mucha interactividad y es muy sensible
* Usted desea gestionar fácilmente su contenido HTML.

Las razones por las que deben utilizar Handlebars.js:

* Handlebars es uno de los más avanzados (pre-compilación y similares), rico en características, y popular de todos los motores de plantillas de JavaScript, y tiene la comunidad más activa.
* Handlebars es un motor de plantillas-lógica menos, lo que significa que hay poca o ninguna lógica en las plantillas que se encuentran en la página HTML.

###Las tres partes principales de Handlebars Templating:

Para utilizar Manillar, primero se vincula al archivo Handlebars.js en el bloque de cabecera de su página HTML, tal como lo hace para jQuery o cualquier archivo .js 
Luego hay tres piezas principales de código que utiliza para Handlebars Templating: 

1- Handlebars.js Expresiones : Un Handlebars simple expresión se escribe así, donde el "contenido" puede ser una variable o una función auxiliar con o sin-parámetros:   
Ejemplo: 
*"{{Contenido}}"*.

 2- Los datos (o contexto): La segunda pieza de código en Handlebars Templating son los datos que desea mostrar en la página. Se pasa los datos como un objeto (un objeto común de JavaScript) a la función manillares. El objeto de datos se llama el contexto. Y este objeto puede estar compuesto de arrays, cadenas, números, otros objetos, o una combinación de todos estos.
 Ejemplo: 
 var theData = {clientes: [{nombre: "Michael", Apellidos: "Alexander", edad: 20 }, {nombre: "John", Apellidos: "Allen", edad: 29 }]};
 
3- El Handlebars Compile Función: La última pieza de código que necesitamos para manillares de plantillas es en realidad una ejecución de dos pasos
1. Compilar la plantilla con la función Handlebars.compile. 
2. A continuación, utilice esa función compilado para invocar el objeto de datos que se le pasa.

 