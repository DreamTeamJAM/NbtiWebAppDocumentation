##### [Volver al indice](../README.md#índice)

# Estudio del problema y análisis del sistema

## Introducción

Este proyecto integrado, aunque sea parte de nuestra evaluación en el grado, también es un proyecto real para la empresa en la que estamos realizando nuestras prácticas, y por tanto va a tener un enfoque profesional, orientado a solucionar los problemas reales que se nos han expuesto en la empresa.

 Nuestro cliente es la empresa [NBTI](https://nbti.eu/about-us/), cuyos servicios principales son asistir y asesorar a centros educativos en sus proyectos de movilidad a otros paises europeos, principalmente a Irlanda.
 Manejan y administran las movilidades de cientos de estudiantes cada año, proporcionandoles asistencia casi constante durante su movilidad y en los procesos previos. Actualmente tienen una web anticuada y sin ninguna funcionalidad. Su sistema informático y base de datos interno se basa exclusivamente en hojas de cálculo.
 
  Nuestro trabajo es modernizar la pagina Web de la empresa y automatizar o agilizar parte de sus procesos internos redundantes.
 
 ## Funciones y rendimientos deseados
 
 ### Rediseño de la web:
 La [_web_ a reemplazar](https://nbti.eu) de NBTI está desarrollada en _Wordpress_ y solo tiene páginas estáticas con alguna información antigua de la empresa. El diseño, estilización y experiencia de usario es mediocre. Queremos mantener los colores y estética básica de la web, pero rediseñarla completamente para que tenga una presentación más moderna y atractiva,
 
### Formularios para clientes:

NBTI maneja constantemente información de los estudiantes a los que asiste, las empresas en las que trabajan, y los alojamientos en los que les hospedan. Todos estos datos los manejan en hojas de cálculo y los reciben manualmente haciendo llamadas o recibiendo correos.

 Una de las tareas es automatizar parte del proceso, teniendo en la web formularios para rellenar y que los datos recogidos se almacenen y organicen solos en una base de datos.
 
 ## Objetivos
 
 El producto final consistirá en una nueva página web, mas moderna, en la que además de mostrar la información habitual de la empresa, dispondrá de un sistema de registro y _log in_ para los estudiantes Erasmus.
 
 Los estudiantes registrados podrán rellenar formularios con los datos que necesita NBTI y de su Curriculum Vitae. La propia página generará con estos datos un Curriculum estandarizado en un archivo PDF. Los estudiantes registrados pueden acceder a un perfil con la información que han proporicionado y modificarla.

Además, habrá dos formularios de contacto dirigidos a empresas y alojamientos que quieran trabajar con NBTI.

Toda estos datos se guardán en una base de datos a traves de una API privada, a la que tienen accceso los empleados de NBTI.
 
 ## Modelo de la Solución
 
 Para desarrollar este proyecto, tenemos que evaluar los diferentes recursos que vamos a necesitar, y modelar la estructura y arquitectura del proyecto
 
 ### Recursos Humanos
 
 En un proyecto de software, el recurso esencial es el personal que va a desarrollar todo el proyecto. Los desarrolladores de la aplicación, ademas de analistas, arquitectos de software, administradores de sistemas, diseñadores, etc.
 
 Este proyecto va a ser por suspuesto diseñado y desarrollado integramente por nosotros. Vamos a ser el único personal informático, pero además contamos con personal de la empresa para suministrarnos material necesario como fotos y videos, colores de la empresa, logos registrados, textos, etc.
 
 También el personal administrativo de NBTI nos suministra información sobre la estructura de los datos con los que trabajan, para crear un modelo para la base de datos adecuado y adaptado a sus necesidades.
 
 ### Recursos Hardware
 
 El proyecto es integramente software, solo necesitamos los equipos que vamos a usar para desarrollar, con los periféricos que use cada desarrollador.
 
  Para alojar y desplegar el proyecto será necesario un servidor dedicado o contratar espacio, o una alternativa similar. La empresa ya tiene espacio contratado con un dominio para su página, que podemos reutilizar. Además necesitamos alojar la base de datos nueva, y el _back end_ que la maneja. Para ello vamos a usar _Amazon Web Services_(AWS) un conjunto de servicios en la nube para administrar cualquier aspecto del proyecto. El coste en AWS es proporcional al tráfico a traves de tus aplicaciones.

### Recursos Software

El proyecto va a estar dividido en dos partes, el _front end_ y el _back end_.

 #### FRONT END

Para el _front_ utilizaremos la librería _React.js_ como _framework_ base para desarrollar la aplicación web. 




























































