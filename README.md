<h1>11086 - Programación en AmbienteWeb - UNLU<br>
Primer Parcial 2020<h1><br>

<h3>Imagine una aplicación web "portal de noticias" y responda las siguientes consignas:<br><br><h3>

1. ¿Por qué las sesiones pueden guardar mucha más información que las cookies? ¿Qué almacenaría para esta app en cookies y/o sesiones?<br>

<h3>
Desde el punto de vista de la cantidad de informacion, las cookies manejan informacion de un usuario y un dispositivo ya que corren del lado del cliente, sin embargo las sesiones manejan infomacion estadistica, es decir, los dispositivos y lugares desde los que se accedio a una sesion.<br>

En el contexto de la app de noticias, en las cookies guardare los cliks referidos a las noticias y en las sesiones las noticias clikeadas, para saber que noticia es mas importante para el promedio de usuarios que de lo que busca este tipo de app, publicar noticias interesantes a los usuarios, y una manera de saberlo es recolectando informacion de las noticias que se ven.<br>

Al usuario logeado, le mostraria informacion relacionada con las noticias que vio.<br>
<h3>

2. ¿Qué ventajas ofrece el uso de Virtualhost en el contexto de servidores Web (en gral y en particular para
esta app)?<br>

<h3>Un virtualHost, me permitiria en esta app, dividir el servidor de noticias en diferentes secciones. Digamos que mi portal de noticias es www.clarin.com, mis virtualhost serian:<br>

www.deportes.clarin.com<br>
www.cine.clarin.com<br>
www.teatro.clarin.com<br>
www.economia.clarin.com<br>
www.buenavida.clarin.com<br>

Permite dividir a los grupos de trabajo, evitando que un redactor de una seccion en perticular, tenga acceso a informacion de otra seccion que no necesariamente debe saber. 
</h3><br>

3. Defina con sus palabras la diferencia principal entre contenido estático y dinámico.<br>

<h3>El contenido estatico, es aquella informacion que no va a cambiar independientemente de las peticion que se le haga al servidor. En el portal de noticias, el logo de la app, las diferentes secciones (sociedad, el mundo, economia, deportes, etc), el footer, donde tenemos datos de contacto (telefono, correo, etc). A parte, debemos sumar a las estrtucuras que usaremos para mostrar el contenido que si cambiara esas estructuras como estilos de las planillas de datos, o listados de noticias, es decir, la estrutura del listado de noticias es estatico, luego la noticia/ articulo es dinamico. 
Contenido dinamico, para empezar con ejemplos: le fecha y la hora, </h3>

4. ¿Cómo aplicaría el modelo MVC para el diseño de esta app?. No necesita escribir código alguno, sino argumentar conceptualmente como separaría la lógica de la app en estos tres elementos.<br>

<h3>
En la app de noticias, las Vistas mostraran los resultados, que la Capa controladora, con funcion de dispacher, redireccione al usuario, con el resultado obtenido de la capa de Modelos la cual tendra el contenido de los articulos. 
En terminos generales, el controlador recibira las peticiones GET sobre los articulos y pedira esa informacion a la capa de modelos. 
La capa de modelo, tendra almacenada en su base de datos, los articulos y otra informacion referida al usuario. Aqui es donde tendre toda mi logica de negocios,  es decir, para brindar un ejemplo dependiendo del tipo de usuario (pago, o free) serviré la pagina o devolvere una respuesta de error al controlador, el cual verá, dependiente del tipo de error mostrar al usuario, usando la vista correspondiente.
<h3><br>

5. a) ¿Por qué es posible afirmar que PDO mejora la seguridad en la capa de base de datos de una app PHP?<br>
b) ¿Qué otras cuestiones debemos tener en cuenta en la capa de base de datos en el sentido de la seguridad?<br>

<h3>
a) PDO es un driver mas que crea una capa de separacion entre el tipo de base de datos que se vaya a usar, por lo que, si llegase a migrar la base de datos a otro gestor (ej mysql a progresql), la capa de modelos no se veria afectada en sus metodos/ llamadas a la DB. <br>

b) otra cuestion a tener en cuenta, es el guardado de la informacion sensible, como ser usuarios y contraseñas, datos sobre tarjetas de credito/ debito del cliente. Es mejor independizar esa parte y delegarla a una entidad que solo se encargue a la autorizacion al sistema. <br>
</h3>

6. La app muestra signos de "envejecimiento" en cuanto al diseño, tanto usuarios finales como redactores del portal lo informan a diario. ¿Qué ideas se le ocurren al respecto?<br>

<h3>
Una cuestion a tener en cuenta, es que necesitare tener como base, un manual de identidad corporativa. Porque, es probable que alguien mas se encargue del diseño, por lo que, debo brindarle las nociones en cuanto a lo que se puede modificar y lo que no. 
De manera que, si quiero mejorar el diseño de mi pagina, solo debo asegurarme de que
el diseñador que se encargue de ello, tenga a mano mi manual de identidad corporativa
para empezar a trabajar. <br>
En este manual, le puedo decir por ejemplo, si mi logo fuera clarin, el mismo, no puede variar el color ni cambiar el logotipo, ya que forma parte de la identidad de la empresa. 
</h3><br>

7. Se le informa al equipo de desarrollo que las nuevas funcionalidades están repercutiendo negativamente en la performance de esta app web en el ambiente productivo, no así en el ambiente de testing (QA). DevOps informa que existe últimamente mucha carga a nivel de bases de datos. ¿Qué se le ocurre hacer en su rol de Desarrollador Web?<br>

<h3>
En el rol de desarrollador web, se puede agregar las siguientes ideas: <br>
- Cargar no toda la pagina web, sino que se una carga a demanda. Por ejemplo, clarin, muestra la primera parte y medida que el usuario baja, te va mostrando mas noticias, asumiendo que de esa forma el mismo esta mas interesado.<br>
- La idea es tambien evitar la perdida de usuarios, ya que a mayor tiempo de carga, es mas probable que el usuario opte por dejar la pagina. <br>
- optimizar la carga de las imagenes: en este caso, buscaria que las imagenes sean del tipo
svg, esto permite que no se tengan que hacer peticiones al servidor por cada imagen, y evitar que, si es una imagen importante, se pierda en la presentacion de la pagina, por una cuestion de respuesta del servidor. El logotipo de la pagina de clarin es del tipo svg.
</h3><br>

8. Imagine ahora que el "portal de noticias" debe considerar tener un "paywall" (ciertos contenidos se vuelven pagos) y por ende almacenará tarjetas de débito / crédito de los clientes.<br>
a) ¿Cuáles son las implicancias de seguridad de esta nueva funcionalidad?<br>
b) ¿Cómo implementaría algún límite sobre la cantidad de noticias que puede ver un usuario que no paga, e.g. puede ver sólo 10 artículos por mes calendario?<br>

<h3>
a) Las implicancias de seguridad son: en la parte de backend, la capa de modelo debe independizar al desarollador y/o administradores del sistema, del manejo de los datos; estos no tienen que tener acceso a los mismos. <br> en la parte del frontend, no se debe mostrar toda el nro de la tarjeta en la pagina sino, los ultimos 4 numeros de los 16 de la tarjeta. Un ejemplo de ello es mercadolibre, te muestra solo los ultimos 4 numeros. 
b) Primero tengo que lograr que el usuario no pago, este logueado. Asumo eso. De hecho, clarin hace eso. Vos te podes loguear con el usuario de google, en concecuencia, alli puedo almacenar en las cookies el usuario y cada vez que solicita una pagina, el servidor maneja la cantidad de ingresos por mes. Esta restriccion se manejara a nivel de capa de modelo, de la siguiente forma: 
* cuando llega la peticion de un articulo, la capa de controlador, toma esa peticion y el usuario y le solicita a la capa modelo dicha noticia. 
* Hasta aqui el circuito siempre es el mismo. Sin embargo, la capa de modelo, aplicara una regla de negocio sobre las visualizaciones de los articulos, y pasaran dos cosas: 
- o bien me brinda la pagina
- o bien, le envia una respuesta de error al controlador, diciendole que no es posible entregar dicha informacion, porque el usuario llegó al limite de visualizaciones mensuales. <br>
* el controlador toma ese msj, y lo envia usando la vista correspondiente al usuario final. <br>

Aqui es donde se puede ver, la aplicacion de la logica de negocios implementada en la capa de modelo.<br> 
</h3>

9. Se requiere implementar un buscador de noticias dentro de esta app. Explique qué responsabilidades tiene cada capa de la aplicación en la resolución de la búsqueda. ¿Qué método HTTP le parece el más adecuado para implementar esto? ¿Qué problemas observa?<br>

<h3>
Vista: se mostrara los resultados de la query ingresada. <br>
Controlador: enviara la query a la capa de modelo. <br>
Modelo: tomara la query, y retornara los resultados correspondientes al controller, pero brindara solo un resumen y un apuntador a cada resultado. <br>

Cuando el usuario hace click sobre la noticia de interes recien ahi, el controlador llamara a un metodo distinto del modelo pidiendo la noticia completa.<br>

La query puede viajar mediante el metodo HTTP-GET.<br>
</h3>

10. Se requiere que la experiencia del sitio sea uniforme en versiones de Chrome/Firefox/IE de hasta 3 años atrás. ¿Cómo puede cumplir con dicho requisito? ¿Qué estrategias adoptaría desde el punto de vista del diseño e implementación?<br><br>

<h3>
Una de las cosas a tener en cuenta es el motor de renderizado (Browser Engine), en Chrome y IE no cambia pero en Firefox si, por lo que tendria que tener en cuenta posibles diseños, tanto para Blink como para Gecko, y para que la misma sea incluida en mi manual de identidad corporativa. 
</h3>


