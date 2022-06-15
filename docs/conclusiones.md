##### [Volver a Documentación del Sistema](documentacion.md)


# Conclusiones
## Grado de cumplimiento de ls objetivos fijados
Desde el principio el proyecto planteado era mucho mas grande de lo que se podía hacer en 3 meses, el tiempo de la asignatura, debido a que el proyecto no es solo nuestro TFG, sino también el proyecto de NBTI, aun así hemos podido segmentar y organizar adecuadamente el proyecto y tener implementado un producto mínimo viable con varios casos de usos completos para la fecha de finalización del TFG. En ese sentido, aun que el proyecto completo no esté terminado, hemos cumplido nuestros objetivos.

 En un proyecto real, usando metodología _Agile_ los ciclos de desarrollo del _software_ se intentan hacer lo mas cortos posibles, para tener un producto funcional testeable y poder recibir _feedback_ de más valor del cliente. Nuestro proyecto ha seguido esa filosofía desarrollando en estos tres meses solo las funcionalidades clave para poder enseñarlas y probarlas antes.
## Propuesta de modificiaciones o amplicaciones futuras al sistema implementado
Para el futuro tenemos varias ampliaciones en mente ya preparadas, como otro proyecto de _front end_ hermano con un _dashboard para administradores. Ampliar las secciones de la web principal con mas información de la empresa. Dar mas información al usuario sobre los terminos de uso de la página y de como usamos la información y mejorar el diseño de algunas secciones como el perfil que se han quedado con un diseño inicial prototipo.

### SPRING + AWS
Una mala decisión de implementación que nos hemos dado cuenta, pero no era feasible cambiar con el tiempo que nos quedaba es la elección de usar conjuntamente _Spring_ y _AWS Lambda_.

 _AWS lambda_ funciona invocando una instancia del backend bajo demanda, cuando se hace una petición. Eso significa que tiene que levantar el servidor con mucha frecuencia, y Spring tiene un tiempo de inicialización muy alto por diseño. Spring nos da grandes facilidades de implementación a cambio de que tenga que realizar muchas operaciones de escaneo y reflexión interna, generandonos gran parte del código. Esto siempre va a implicar un tiempo de inicio alto del servidor.

 Hemos hecho todas las optimizaciones posibles para reducir el tiempo de inicio del _back end_, pero mientras usemos _Spring_ siempre será mas alto que con un implementación diseñada para tener un inicio rápido.
 
 No nos dimos cuenta de este problema hasta que ya teníamos gran parte del proyecto desarrollado, y eliminar _Spring_ de las dependencias implicaba hacer el _back end_ desde cero, y sin las multiples ventajas que nos proporciona _Spring_.

 Si en el futuro volvemos a desarrollar con AWS, no cometermos el mismo error de diseño. Y si tuviesemos tiempo suficiente, migrar el proyecto de _back end_ a una implementación de Java puro.

 ##### [siguiente Sección: Bibliografía](bibliografia.md)