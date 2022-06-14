#### [Volver a Estudio del problema](estudio.md)

# Ejecución del Proyecto

## Documentación e implementación del proyecto de FRONT END

### Configuración inicial
Para crear el proyecto inicial de react usamos [_Create React App_](https://github.com/facebook/create-react-app) que nos genera un proyect vacio de _React_, pero ya con todas las dependencias esenciales para el proyecto, y con algunos comandos integrados como:
- `npm start`: Ppara lanzar en un servidor de desarrollo local la pagina
- `npm build`: Para empaquetar el proyecto para un despliegue real.
- `npm test` : para ejecutar test de la aplicación.

La estructura de archivos del proyecto se basa en la plantilla basica de React que hemos usado, 

 ![raiz del proyecto](../images/frontFiles.png) 
 
 teniendo una carpeta `src` que contiene todo el codigo fuente del proyecto, dividido en subcarpetas para organizar paginas, componentes, servicios, etc
 
  ![src](../images/frontFilesSrc.png)

### Diseño de la página

Para el rediseño se plantearon varios _mock ups_ orientativos de la nueva pagina:

![mock up 3](../images/mockUp3.png)
![mock up 1](../images/mockUp1.png)
![mock up 2](../images/mockUp2.png)

Tras consultarlo con supervisores se decidió seguir el estilo del último ejemplo.

Siguiendo este diseño base, se diseña e implementa en react la nueva página. Las vistas en las que se decide que se va a dividir son:

#### Vista principal(_Home_):

Es la _landing page_ que ve un usario nada más entrar, muestra cierta información clave y sirve como portal de entrada al resto de vistas.


![home](../images/home.png)
![home](../images/home2.png)

#### Vista de _Log In_:
Accesible en la barra de navegación, es desde donde los estudiantes ya registrados pueden iniciar sesión.
![log in](../images/login.png)

#### Vista del formulario para Empresas:

Aqui empresas interesadas en trabajar con NBTI pueden dar su información de contacto.

![empresas](../images/enterprise.png)

#### Vista del formulario para Hospedajes:

En esta vista familias de acogida o quien quiera puede dar sus datos de contacto para que NBTI tenga su información.

![hosting](../images/hosting.png)

#### Vista de registro de estudiantes:

Esta es la vista con el formulario mas complejo, ya que vamos a hacer que el estudiante rellene toda la información de su curriculum y su cuenta.


Al tener que rellenar tanta información, hemos segmentado el fomrulario en varios pasos para mejorar la experiencia de usuario, con una barra de progreso.

![paso 1](../images/register1.png)

En el primer paso se rellena y valida la información básica de usuario.

![paso 2](../images/register21.png)
![paso 2](../images/register22.png)


En este paso se rellena la mayoría de la información personal del estudiante, incluidas fotos del DNI, teléfono, etc.

![paso 3](../images/register3.png)

En este paso el estudiante puede añadir las diferentes experiencias de trabajo, usando los botones para añadir o quitar las que necesite.

![paso 4](../images/register4.png)

Igual que en el anterior, puede rellenar tantas formaciones/educaciones como quiera el estudiante.

![paso 5](../images/register5.png)

Aquí pueden especificar los idiomas que dominen y a qué nivel. Formato similar a los anteriores.

![paso 6](../images/register6.png)

En el último paso pueden rellenar su experiencia de voluntariado, también formato con lista de formularios.

#### Barra de navegación:

![navbar](../images/navbarunlogged.png)
![navbar](../images/navbarLogged.png)

En la barra de navegacion podemos acceder a las vistas principales, y si la sesión esta iniciada muestra la foto de perfil en un botón.

![navbar](../images/navbarDrop.png)

Este botón despliega las diferentes opciones para usuarios registrados.

#### Vista del perfil de estudiante.

![perfil](../images/perfil1.png)

Un estudiante registrado pued acceder a su perfil y ver la información que rellenó en su registro. En esta vista hay dos subvistas, la principal que vemos arriba.

![perfil](../images/perfil2.png)

Y en la otra vista podemos ver un pdf con un curriculum generado con los datos del estudiante.

### Implementación de la aplicación REACT


La apliación web funciona con una _Single Page Website_, existe un archivo HTML raíz, que el _framework_ cambia dinamicamente para mostrar el contenido que queramos. Todo el marcado y diseño de la pagina se hace a traves de HTML generado en ficheros _Javascript_. definiendo funciones especiales: componentes de _React_.

#### Componentes de _REACT_

 Un componente de React no es mas que una función de javascript que retorna HTML, y que debe cumplir algunas convenciones, como ser una *función pura*


Este es un ejemplo sencillo de un componente de _React_:
```
import React from "react";
import "./styles.css";

function DownloadButton({ children }) {
  return (
    <>
      <button className="button">
        <span className="button_lg">
          <span className="button_sl"></span>
          <span className="button_text"> {children} </span>
        </span>
      </button>
    </>
  );
}

export default DownloadButton;
```


podemos llamar a un componente de _React_ dentro de codigo HTML llamandolo como una etiqueta HTML:

`<DownloadButton>Download in English</DownloadButton>`

Combinando componentes podemos crear una página web compuesta por diferentes componentes reutilizables.

#### Componente principal y Router

_React_ proporciona un sistema para redirigir el contenido segun la ruta escrita en la página, el componente principal de la _web_ contiene una barra de navegación y las diferentes rutas posibles para la página:



```
import ...

function App() {
  const [locale, setLocale] = useState(
    localStorage.getItem("language") === "es"
      ? LOCALES.SPANISH
      : LOCALES.ENGLISH
  );

  return (
    /** Provider to changes languages */
    <I18Provider locale={locale}>
      <Navbar setLocale={setLocale} />

      {/* ROUTES */}

      <ThemeProvider theme={theme}>
         <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/enterprise" element={<Enterprise />} />
        <Route path="/hosting" element={<Hosting />} />
        <Route path="/encrypt" element={<Encrypt />} />
        <Route path="/login" element={<LoginAuth />} />
        <Route path="/register" element={<CvPage />} />
        <Route path="/profile" element={<Profile />} />
        <Route path="/spinner" element={<Spinner />} />
        <Route path='/edit/:id' element={<Edit/>}/>
        <Route path="*" element={<h1>Error 404</h1>} />
      </Routes>
      </ThemeProvider>

      <Footer />
      <Cookies />
    </I18Provider>
  );
}

export default App;



```

Diferentes rutas renderizan diferentes componentes de _React_.

#### _Hooks_ de _React_

Una funcionalidad clave de React, que se usa en todas partes del código, es el uso de _hooks_ una estructura para controlar información dinamicamente a través de componentes teniendo en cuenta el ciclo de renderizado de la web.

##### State Hook:

Esta es la estructura más simple, permite persistir un valor/objeto de _Javascript_ a traves de renderizados de la web. se usa llamando a `useState()`, un ejemplo de nuestro proyecto:

` const [student, setStudent] = useState({});`

El _hook_ nos devuelve dos variables: la primera el *accesor* desde donde leemos el valor guardado en el _hook_ y la segunda un método para modificar el valor en el _hook_

##### Effect Hook:

está estructura permite ejecutar código en cada renderizado, o cuando cambie el valor de hook del componente, se usa normalmente para manejar efectos secundarios en la página, animaciones, operaciones que dependen de otros cambios, etc.
```
 useEffect(()=>{
    AuthService.getCurrentUser().then((user) => {
      if (user != null) {
        navigate("/");
      }
    });
  }
  ,[] )
```
En este ejemplo se usa para que el componente recupere los datos de usuario en el primer renderizado.


#### Generación dinámica de formularios:

Una de las partes mas extensas de este proyecto es lidiar con un formulario con un gran cantidad potencial de datos, para esto, hemos implementado un sistema que genera formularios según un objeto JSON que describe la estructura del formulario. 

Un ejemplo de estos archivos JSON:

```
{
  	name: { type: "text", validation: "text" },
	dni: { type: "text", validation: "text" },
	city: { type: "text", validation: "text" },
	photo: { type: "image", validation: "basic" },
	firstSurname: { type: "text", validation: "text" },
	secondSurname: { type: "text", validation: "text" },
	nationality: {
	  type: "option",
	  options: nationalityOptions,
	  validation: "basic",
	},
	phone: { type: "phone", validation: "phone" },
	birthDate: { type: "date", validation: "basic" },
	gender: {
	  type: "radio",
	  options: ["Male", "Female", "Other"],
	  validation: "basic",
	},
	email: { type: "email", validation: "email" }
}
  ```
Este JSON esta dandonos que campos debe tener el formulario, de que tipo, y que validacion requiere, aparte de algunos valores para tipos especiales de inputs.


```
export function inputGeneration(inputs, values, onChange, formik) {
  const inputHtml = [];
  for (const [key, input] of Object.entries(inputs)) {
    let currentInput;
    switch (input.type) {
      case "tags":
          currentInput=(
            <div>
            <TagInput
            label={key} 
            value = {values[key]}
            onChange={onChange} 
            whitelist= {input.whitelist}
            formik={formik}
            />
            </div>
          )
        break;
      case "radio":
      ...
```

este JSON es procesado con esta función junto con el objeto de valores que van a ser asociados a cada _input_ y la función que va a manejar los cambios en el formulario. La funcón genera html encadenando componentes de React personalizados para cada input, segun el JSON aportado.

Para el caso de formularios como el de experiencia laboral, que podian ser multiples formularios iguales, hay un componente especial para el esos casos, que usa recursividad para volver a llamar a la función generador de formularios, `inputGeneration`, repitiendo el proceso.

```
...
 const formArray = values.map((element, index) => {
    return (
      <>
        <ArrayDiv className="col" key={index}>
          {inputGeneration(
            inputList,
            props.values[index],
            (e) => subOnChange(e, index),
            formik[index]
          )}
...
```


#### Generación de curriculum en PDF:

Además de guardar la información del curriculum del estudiante, tambien tenemos que generar una versión PDF del curriculum, para ello usamos _pdfMake_. una libreria que nos permite generar pdfs según un objeto JSON que define el contenido y la estructura. Parecido a lo que hemos hecho nosotros para generar formularios, pero en este caso es una libreria externa, y los JSON son mas complejos pues tambien estilizan el PDF.

Ejemplo de configuracion de _PdfMake_

```
...
 style: ["font"],
      alignment: "justify",
      margin: [0, 5, 0, 0],
      text: [
        {
          text: `${value.title}.
     `,
          bold: true,
          italics: false,
          fontSize: 15,
        },

        `${value.company} [${value.startDate}]  [${value.endDate}]
      
...
```



































