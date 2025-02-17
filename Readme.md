# React native workshop

## Diferentes "aproaches" de desarrollo de aplicaciones para iOS y Android

### 1. Programación nativa

Este es el aproach más directo y simple de todos. Utilizar los lenguajes y herramientas proporcionados por las diferentes plataformas o sistemas operativos para moviles. En este caso nos centraremos en iOS y Android, debido a su gran penetración y cuota de mercado. Hoy por hoy el resto son "paisaje".

Con programación nativa desarrollamos directamente en el lenguage propuesto y, si somos buenos desarrolladores, conseguiremos hacer la versión más eficiente posible. Podremos sacar el máximo partido a cada plataforma y tendremos acceso a todas las funcionalidades tal cual las provee el sistema operativo del teléfono sin intermediarios.

Los lenguajes utilizados son Swift para iOS desarrollando con Xcode y Java/Kotlin para Android, utilizando Android Studio, tanto Xcode como Android estudio, son entornos de trabajo completos para tener a mano todas las herramientas para hacer el desarrollo de nuestra applicación.
Si lo que te gusta es el desarrollo movil, este es el camino.

La ventaja, principal de esto es evidente, más rendimiento, más flexibilidad y más control de lo que estamos haciendo.
La desventaja, tambien es clara, es necesario un expero en clada plataforma, conocer los pormenores de cada lenguaje y sistema operativo y por último y para nada despreciable, el echo que hay que mantener dos bases de código, totalmente independientes.

Por esta razón muchas startups o empresas que hacen pruebas de concepto, optan por soluciones híbridas.

### 2. Soluciones hibridas "blandas"

Con estas soluciones tu escribes solo una base de código y en la "complilación" se pueden generar aplicaciones en Swift y en Java o lo que sea. En esta hibridación se escribe el código en un lenguaje y se traduce directamente a Nativo.

En este grupo se incluyen react-native y flutter.

- La ventaja es que sólo tienes una base de código y podrás generar la aplicación para la plataforma que necesites. Con esto consigues un rendimiento similar (no igual) al que consigues programando en nativo directamente.

- Las desventajas son más de las que parecen, sobre todo para desarrolladores como vosotros, desarrolladores web.
  - Cuando escribimos código en react native o Flutter tenemos que tener en cuenta que en realidad estamos escribiendo código nativo y por tanto no se genera un Html, Css y javascript, si no que se genera código en Java o en swift + javascript, que se comunica con la capa nativa del telefono a través de un bridge.
  - A menudo se confunde el conocimiento en React con el Conocimiento en React-native y lo unico que se consigue es crear un engendro, ya que los desarrolladores web no saben exactamente a que se están enfrentando.

### 4. Soluciones hibridas "duras"

En este caso de desarrolla una aplicación totalmente web en la cual podríamos usar el javascript que conocéis, en este caso React y lo que se hace una vez se termina es ponerle una capa que hace de puente entre el telefono y la aplicación web. De manera que el usuario está "navegando" por nuestro Html Css y javascript y cuando nuestra aplicación usa alguna funcionalidad que es nativa...como la cámara, entonces habla con el teléfono a través del bridge.

En este grupo se incluyen soluciones como Capacitor/cordova

- La ventaja principal, es que un desarrollador web, sabe exactamente lo que está haciendo y todos sus conocimientos son aplicables, tal cual.

  - Se puede usar una aplicación ya terminada y ponerle este bridge directamente y violà, ya tienes tu app.
  - Con esto consigues aún menos bases de código.

- La desventaja, es que al final es una aplicación web y por tanto el rendimiento será menor.
  - Dependemos totalmente de lo que esté implementado en el bridge, aunque si necesitamos algo siempre podemos extenderlo.

## Introducción a React Native y diferencias con React.js

### 1. Introducción a React Native

- **Definición:** React Native es un framework de código abierto desarrollado por Facebook que permite crear aplicaciones móviles nativas para iOS y Android utilizando JavaScript y React.
- **Origen del proyecto:**

Mark Zuckerberg, de Facebook, comentó en 2012 que confiar en HTML para las versiones móviles en lugar de las nativas no era una decisión ideal para la empresa. Los problemas de inestabilidad estaban presentes con la versión móvil de Facebook basada en HTML5, la cual también era lenta en las tareas de recuperación de datos, por lo que la empresa se centró en encontrar una alternativa adecuada para ofrecer mejores experiencias de usuario en plataformas móviles.

Jordan Walke de Facebook ideó un método innovador para crear elementos de la interfaz de usuario de iOS utilizando un hilo de JavaScript de fondo. Facebook llevó a cabo un Hackathon interno para desarrollar el prototipo para mejorar el prototipo y desarrollar aplicaciones nativas con la tecnología.

Facebook lanzó la primera configuración de React JavaScript en 2015 después de muchos meses de desarrollo. Christopher Chedeau luego reveló que Facebook había comenzado a usar el marco React Native para sus aplicaciones Ads Manager App y Group App.

### 2. Diferencias clave entre React Native y React.js

- **Plataforma:** React.js se utiliza para el desarrollo de aplicaciones web, mientras que React Native se utiliza para el desarrollo de aplicaciones móviles nativas.
- **Componentes:** React.js utiliza componentes web estándar como `div`, `span`, etc., mientras que React Native utiliza componentes nativos como `View`, `Text`, `Image`, etc.
- **Renderizado:** React.js renderiza al DOM del navegador, mientras que React Native renderiza a los componentes nativos del sistema operativo.

### 3. Flex en React Native es vertical

- **Modelo de caja flex:** En React Native, el diseño predeterminado es vertical, es decir, los componentes hijos se colocan uno debajo del otro de manera predeterminada.

  ```javascript
  const styles = StyleSheet.create({
    container: {
      flex: 1,
      justifyContent: "center",
      alignItems: "center",
    },
  });
  ```

- **Diferencia con CSS Flexbox:** En CSS, el contenedor flexbox es horizontal por defecto. En React Native, para cambiar la dirección del eje principal, se utiliza flexDirection: 'row'.

### 4. Evitar cambiar cómo se gestiona el CSS y usar siempre StyleSheet

- **Estilización con StyleSheet:** React Native utiliza StyleSheet.create para definir estilos de manera eficiente. Esto ayuda a mejorar el rendimiento y la consistencia en toda la aplicación.

```javascript
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#fff",
    alignItems: "center",
    justifyContent: "center",
  },
});
```

- **Beneficios de StyleSheet:**
  - Mejora del rendimiento al crear solo una vez los estilos.
  - Mejor legibilidad y mantenimiento del código.
  - Coherencia en la aplicación de estilos.

### 5. La jerarquía de componentes impide que la generación de la aplicación web sea del todo válida

- Jerarquía de componentes: En React Native, la jerarquía de componentes está diseñada para aplicaciones móviles, lo que implica ciertas limitaciones cuando se intenta reutilizar el código para aplicaciones web.
- Limitaciones de reutilización: Mientras que algunas aplicaciones sencillas pueden ser portadas entre React Native y React.js con facilidad, aplicaciones más complejas con interfaces de usuario avanzadas y uso intensivo de APIs nativas no se traducirán bien a un entorno web.
- Ejemplo de limitación:
  - Uso de componentes nativos: Componentes como ScrollView, FlatList, y otros que interactúan con APIs nativas del sistema operativo no tienen equivalentes directos en el entorno web.
  - Interacciones y gestos: Las interacciones táctiles y gestos en React Native no tienen un equivalente directo en la web, lo que requiere una reimplementación.

### 6. Conceptos adicionales importantes

- **Hot Reloading y Fast Refresh:** React Native soporta características como Hot Reloading y Fast Refresh que permiten ver los cambios en el código en tiempo real sin necesidad de recompilar toda la aplicación.
- **Acceso a APIs nativas:** React Native permite el acceso a APIs nativas del dispositivo (como cámara, GPS, acelerómetro, etc.) utilizando módulos nativos y bibliotecas de terceros.
- **Desarrollo y pruebas:** El uso de Expo puede simplificar el desarrollo y la prueba de aplicaciones React Native al proporcionar un conjunto de herramientas y servicios preconfigurados.

**Ejemplo práctico:**

- Estructura básica de la aplicación:

```javascript
import { useState } from "react";
import { StyleSheet, Text, View, Button } from "react-native";

export default function App() {
  const [count, setCount] = useState(0);

  return (
    <View style={styles.container}>
      <Text>¡Counter! {count}</Text>
      <Button title="Incrementar" onPress={() => setCount(count + 1)} />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#fff",
    alignItems: "center",
    justifyContent: "center",
  },
});
```

## Configuración del entorno de desarrollo para React Native

### 1. Instalación de Node.js y npm

- **Node.js:** React Native requiere Node.js, que incluye npm (Node Package Manager).
- **Instalación:**
  - Ve a la [página de descarga de Node.js](https://nodejs.org/) y descarga la versión recomendada para la mayoría de los usuarios.
  - Sigue las instrucciones de instalación para tu sistema operativo.

### 2. Creación de una cuenta en Expo

- Cuenta en Expo: Tener una cuenta te permite utilizar funcionalidades adicionales como el almacenamiento en la nube y la colaboración en proyectos.
- Registro:
  - Ve a la página de registro de Expo y crea una cuenta.
  - También puedes registrarte directamente desde la línea de comandos:

```bash
expo register
```

### 3. Creación de un proyecto básico con Expo

Crear un proyecto:
https://docs.expo.dev/tutorial/create-your-first-app/

```bash
npx create-expo-app@latest
npm run reset-project  //script to remove the boilerplate code
npx create-expo-app myApp --template blank
```

### 4. Ejecución del proyecto en un emulador o dispositivo físico

Iniciar el proyecto:

```bash
cd MiPrimeraApp
npm install
npm start
```

- Ejecutar en un dispositivo físico:

  - Instala la aplicación Expo Go desde la App Store (iOS) o Google Play Store (Android).

    - [Expo Go en App Store](https://apps.apple.com/us/app/expo-go/id982107779)
    - [Expo Go en Google Play Store](https://play.google.com/store/apps/details?id=host.exp.exponent)

  - Escanea el código QR que aparece en la terminal o en el navegador con la aplicación Expo Go para ejecutar tu proyecto en el dispositivo.

- Ejecutar en un emulador:
  - iOS: Necesitarás Xcode instalado en tu Mac. Abre Xcode y configura un emulador.
  - Android: Necesitarás Android Studio. Instala Android Studio y configura un dispositivo virtual (AVD).

### 5. Configuración adicional (opcional)

- Configurar ESLint y Prettier: Para mantener la calidad y consistencia del código.

## Estilización con StyleSheet

React Native utiliza un sistema de estilización que es similar al de CSS en la web, pero en lugar de utilizar hojas de estilo en cascada, se utiliza el módulo `StyleSheet` para definir estilos en JavaScript. Es un sistema similar a CSS Modules o Styled components. Esto proporciona varias ventajas, incluyendo un mejor rendimiento y la capacidad de mantener los estilos dentro del mismo archivo que los componentes.

### 1. Creación de un objeto StyleSheet

- **Uso básico:**

  ```javascript
  import { StyleSheet } from "react-native";

  const styles = StyleSheet.create({
    container: {
      flex: 1,
      justifyContent: "center",
      alignItems: "center",
      backgroundColor: "#fff",
    },
    text: {
      fontSize: 20,
      color: "black",
    },
  });
  ```

### 2. Aplicación de estilos a componentes

- Ejemplo de uso en un componente:

```javascript
import React from "react";
import { View, Text, StyleSheet } from "react-native";

const MyComponent = () => {
  return (
    <View style={styles.container}>
      <Text style={styles.text}>¡Hola Mundo!</Text>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
    backgroundColor: "#fff",
  },
  text: {
    fontSize: 20,
    color: "black",
  },
});

export default MyComponent;
```

## Componentes básicos en React Native

React Native proporciona una serie de componentes básicos que son los bloques de construcción fundamentales para crear interfaces de usuario en aplicaciones móviles. A continuación, se describen algunos de los componentes más utilizados, junto con ejemplos de cómo usarlos.

# Table of Contents

1. [View](#1-view)
2. [Text](#2-text)
3. [Image](#3-image)
4. [TextInput](#4-textinput)
5. [Button](#5-button)
6. [ScrollView](#6-scrollview)
7. [FlatList](#7-flatlist)
8. [TouchableOpacity](#8-touchableopacity)

### 1. View

- **Descripción:** El componente `View` es un contenedor que soporta el diseño con flexbox, estilo, y manejo de toques. Sería "lo más parecido" a un `div` en React.js.
- **Uso:**

  ```javascript
  import React from "react";
  import { View, StyleSheet } from "react-native";

  const MyComponent = () => {
    return (
      <View style={styles.container}>
        <View style={styles.box} />
      </View>
    );
  };

  const styles = StyleSheet.create({
    container: {
      flex: 1,
      justifyContent: "center",
      alignItems: "center",
    },
    box: {
      width: 100,
      height: 100,
      backgroundColor: "blue",
    },
  });

  export default MyComponent;
  ```

### 2. Text

- **Descripción:** El componente Text se utiliza para mostrar texto. En react native, no se puede poner texto directamente en un `View`, se debe usar el componente `Text`, si no lo usas dará error.
- **Uso:**

  ```javascript
  import React from "react";
  import { Text, View, StyleSheet } from "react-native";

  const MyComponent = () => {
    return (
      <View style={styles.container}>
        <Text style={styles.text}>¡Hola Mundo!</Text>
      </View>
    );
  };

  const styles = StyleSheet.create({
    container: {
      flex: 1,
      justifyContent: "center",
      alignItems: "center",
    },
    text: {
      fontSize: 20,
      color: "black",
    },
  });

  export default MyComponent;
  ```

### 3. Image

- **Descripción:** El componente Image se utiliza para mostrar imágenes. Es importante tener en cuenta que las imágenes deben tener un tamaño específico para evitar problemas de rendimiento.
- **Uso:**

  ```javascript
  import React from "react";
  import { Image, View, StyleSheet } from "react-native";

  const MyComponent = () => {
    return (
      <View style={styles.container}>
        <Image
          source={{ uri: "https://reactnative.dev/img/tiny_logo.png" }}
          style={styles.image}
        />
      </View>
    );
  };

  const styles = StyleSheet.create({
    container: {
      flex: 1,
      justifyContent: "center",
      alignItems: "center",
    },
    image: {
      width: 50,
      height: 50,
    },
  });

  export default MyComponent;
  ```

### 4. TextInput

- **Descripción:** El componente TextInput se utiliza para la entrada de texto.
- **Uso:**

  ```javascript
  import React, { useState } from "react";
  import { TextInput, View, StyleSheet } from "react-native";

  const MyComponent = () => {
    const [text, setText] = useState("");

    return (
      <View style={styles.container}>
        <TextInput
          style={styles.input}
          placeholder="Escribe algo"
          onChangeText={setText}
          value={text}
        />
      </View>
    );
  };

  const styles = StyleSheet.create({
    container: {
      flex: 1,
      justifyContent: "center",
      alignItems: "center",
    },
    input: {
      height: 40,
      borderColor: "gray",
      borderWidth: 1,
      width: "80%",
      paddingLeft: 8,
    },
  });

  export default MyComponent;
  ```

### 5. Button

- **Descripción:** El componente Button se utiliza para crear botones interactivos.
- **Uso:**

  ```javascript
  import React from "react";
  import { Button, View, StyleSheet, Alert } from "react-native";

  const MyComponent = () => {
    return (
      <View style={styles.container}>
        <Button
          title="Presióname"
          onPress={() => Alert.alert("Botón presionado")}
        />
      </View>
    );
  };

  const styles = StyleSheet.create({
    container: {
      flex: 1,
      justifyContent: "center",
      alignItems: "center",
    },
  });

  export default MyComponent;
  ```

### 6. ScrollView

- **Descripción:** El componente ScrollView se utiliza para crear una vista que puede desplazarse.
- **Uso:**

  ```javascript
  import React from "react";
  import { ScrollView, Text, StyleSheet } from "react-native";

  const MyComponent = () => {
    return (
      <ScrollView style={styles.container}>
        <Text style={styles.text}>Elemento 1</Text>
        <Text style={styles.text}>Elemento 2</Text>
        <Text style={styles.text}>Elemento 3</Text>
      </ScrollView>
    );
  };

  const styles = StyleSheet.create({
    container: {
      flex: 1,
      marginTop: 20,
    },
    text: {
      fontSize: 18,
      margin: 10,
    },
  });

  export default MyComponent;
  ```

### 7. FlatList

- **Descripción:** El componente FlatList se utiliza para renderizar listas grandes de datos de manera eficiente.
- **Uso:**

  ```javascript
  import React from "react";
  import { FlatList, Text, View, StyleSheet } from "react-native";

  const DATA = [
    { id: "1", title: "Elemento 1" },
    { id: "2", title: "Elemento 2" },
    { id: "3", title: "Elemento 3" },
    // Añadir más elementos según sea necesario
  ];

  const MyComponent = () => {
    return (
      <FlatList
        data={DATA}
        renderItem={({ item }) => <Text style={styles.item}>{item.title}</Text>}
        keyExtractor={(item) => item.id}
      />
    );
  };

  const styles = StyleSheet.create({
    item: {
      padding: 20,
      fontSize: 18,
      height: 44,
    },
  });

  export default MyComponent;
  ```

### 8. TouchableOpacity

- **Descripción:** El componente TouchableOpacity se utiliza para crear elementos que responden a toques con retroalimentación de opacidad.
- **Uso:**

  ```javascript
  import React from "react";
  import { TouchableOpacity, Text, StyleSheet, Alert } from "react-native";

  const MyComponent = () => {
    return (
      <TouchableOpacity
        style={styles.button}
        onPress={() => Alert.alert("Botón presionado")}
      >
        <Text style={styles.buttonText}>Presióname</Text>
      </TouchableOpacity>
    );
  };

  const styles = StyleSheet.create({
    button: {
      alignItems: "center",
      backgroundColor: "#DDDDDD",
      padding: 10,
    },
    buttonText: {
      fontSize: 20,
    },
  });

  export default MyComponent;
  ```

## Ejercicio práctico: Crear una aplicación de saludo en React Native

### Enunciado

En este ejercicio, crearás una aplicación simple en React Native que muestra un saludo al usuario y tiene un botón que, al ser presionado, cambia el mensaje de saludo. La aplicación constará de un componente principal que mostrará el mensaje y el botón, y un componente de estilización que contendrá los estilos.
