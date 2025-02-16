## Clase 2: Navegación en React Native

### Navegación en React Native

La navegación es un aspecto esencial en cualquier aplicación móvil. En React Native, la biblioteca más popular para manejar la navegación es `React Navigation`. Esta biblioteca ofrece una variedad de navegadores que se pueden usar para crear diferentes tipos de flujos de navegación en tu aplicación.

### 1. Instalación de React Navigation

#### Paso 1: Instalar `react-navigation`

Primero, necesitas instalar el core de `React Navigation`.

```bash
npm install @react-navigation/native
```

#### Paso 2: Instalar dependencias adicionales

React Navigation depende de otras librerías como `react-native-screens` y `react-native-safe-area-context`, que también necesitas instalar.

```bash
npx expo install react-native-screens react-native-safe-area-context
```

#### Paso 3: Instalar navegadores específicos

Para este ejemplo, instalaremos el stack navigator, que es uno de los navegadores más comunes.

```bash
npm install @react-navigation/native-stack
```

### 2. Configuración del contenedor de navegación

Configura el contenedor de navegación en el archivo `App.js`, donde envolverás toda la estructura de navegación con el `NavigationContainer` y definirás las rutas utilizando un stack navigator.

```javascript
import * as React from "react";
import { View, Text } from "react-native";
import { NavigationContainer } from "@react-navigation/native";
import { createNativeStackNavigator } from "@react-navigation/native-stack";

function HomeScreen() {
  return (
    <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
      <Text>Home Screen</Text>
    </View>
  );
}

const Stack = createNativeStackNavigator();

function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Home" component={HomeScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}

export default App;
```

### 3. Creación de pantallas

Crea dos pantallas básicas, `HomeScreen` y `DetailsScreen`, que representarán las diferentes vistas a las que el usuario puede navegar.

**_screens/HomeScreen.js_**

```javascript
import React from "react";
import { View, Text, Button, StyleSheet } from "react-native";

const HomeScreen = ({ navigation }) => {
  return (
    <View style={styles.container}>
      <Text style={styles.text}>Pantalla de Inicio</Text>
      <Button
        title="Ir a Detalles"
        onPress={() => navigation.navigate("Details")}
      />
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
    fontSize: 24,
    marginBottom: 20,
  },
});

export default HomeScreen;
```

**_screens/DetailsScreen.js_**

```javascript
import React from "react";
import { View, Text, Button, StyleSheet } from "react-native";

const DetailsScreen = ({ navigation }) => {
  return (
    <View style={styles.container}>
      <Text style={styles.text}>Pantalla de Detalles</Text>
      <Button
        title="Volver a Inicio"
        onPress={() => navigation.navigate("Home")}
      />
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
    fontSize: 24,
    marginBottom: 20,
  },
});

export default DetailsScreen;
```

### 4. Actualización de la home

```javascript
import * as React from "react";
import { NavigationContainer } from "@react-navigation/native";
import { createNativeStackNavigator } from "@react-navigation/native-stack";
import HomeScreen from "./screens/HomeScreen";
import DetailsScreen from "./screens/DetailsScreen";

const Stack = createNativeStackNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator initialRouteName="Home">
        <Stack.Screen name="Home" component={HomeScreen} />
        <Stack.Screen name="Details" component={DetailsScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

### 5. Explicación del código

- **`NavigationContainer`**: Es un componente que gestiona el estado de la navegación y debe envolver toda la estructura de navegación.
- **`createNativeStackNavigator`**: Crea un stack navigator, que es un tipo de navegador que gestiona una pila de pantallas.
- **`initialRouteName`**: Especifica la pantalla inicial del navegador.
- **`Stack.Screen`**: Define una pantalla dentro del stack navigator.

### 5. Ejercicio práctico

#### Objetivo

Añadir una tercera pantalla a la aplicación de navegación y configurar la navegación entre las tres pantallas.

#### Instrucciones

1. Crea una nueva pantalla llamada `ProfileScreen.js` en la carpeta `screens`.
2. Configura `App.js` para incluir la nueva pantalla en el stack navigator.
3. Añade botones en `HomeScreen` y `DetailsScreen` para navegar a `ProfileScreen`.
4. Añade un botón en `ProfileScreen` para navegar de vuelta a `HomeScreen`.

### 6. Anidación de navegaciónes en React Navigation

La anidación de navegadores es una técnica común en React Navigation para gestionar flujos de navegación complejos. Puedes anidar navegadores dentro de otros navegadores para crear jerarquías de navegación más avanzadas.

### 1. Anidación de Stack Navigators

#### a. Creación de Navegadores Anidados

Puedes anidar stack navigators para gestionar diferentes flujos de navegación en tu aplicación.

```javascript
const Stack = createNativeStackNavigator();
const ProfileStack = createNativeStackNavigator();

function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Home" component={HomeScreen} />
        <Stack.Screen name="Profile" component={ProfileStackScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}

function ProfileStackScreen() {
  return (
    <ProfileStack.Navigator>
      <ProfileStack.Screen name="Profile" component={ProfileScreen} />
      <ProfileStack.Screen name="Settings" component={SettingsScreen} />
    </ProfileStack.Navigator>
  );
}
```

### 2. Anidación de Tab Navigators

#### a. Creación de Navegadores de Pestañas Anidados

Instalar el tab navigator:

```bash
npm install @react-navigation/bottom-tabs
```

También puedes anidar tab navigators para gestionar diferentes secciones de tu aplicación.

```javascript
const Tab = createBottomTabNavigator();
const HomeStack = createNativeStackNavigator();
const ProfileStack = createNativeStackNavigator();

function App() {
  return (
    <NavigationContainer>
      <Tab.Navigator>
        <Tab.Screen name="Home" component={HomeStackScreen} />
        <Tab.Screen name="Profile" component={ProfileStackScreen} />
      </Tab.Navigator>
    </NavigationContainer>
  );
}

function HomeStackScreen() {
  return (
    <HomeStack.Navigator>
      <HomeStack.Screen name="Home" component={HomeScreen} />
      <HomeStack.Screen name="Details" component={DetailsScreen} />
    </HomeStack.Navigator>
  );
}

function ProfileStackScreen() {
  return (
    <ProfileStack.Navigator>
      <ProfileStack.Screen name="Profile" component={ProfileScreen} />
      <ProfileStack.Screen name="Settings" component={SettingsScreen} />
    </ProfileStack.Navigator>
  );
}
```

### 3. Anidación de Drawer Navigators

**Instalación**

```bash
npm install @react-navigation/drawer
```

Esta instalición depende de estas dos librerías:

```bash
npm install react-native-reanimated react-native-gesture-handler
```

#### a. Creación de Navegadores de Cajón Anidados

Los drawer navigators permiten mostrar un menú lateral con opciones de navegación.

```javascript
const Drawer = createDrawerNavigator();
const HomeStack = createNativeStackNavigator();
const ProfileStack = createNativeStackNavigator();

function App() {
  return (
    <NavigationContainer>
      <Drawer.Navigator>
        <Drawer.Screen name="Home" component={HomeStackScreen} />
        <Drawer.Screen name="Profile" component={ProfileStackScreen} />
      </Drawer.Navigator>
    </NavigationContainer>
  );
}

function HomeStackScreen() {
  return (
    <HomeStack.Navigator>
      <HomeStack.Screen name="Home" component={HomeScreen} />
      <HomeStack.Screen name="Details" component={DetailsScreen} />
    </HomeStack.Navigator>
  );
}

function ProfileStackScreen() {
  return (
    <ProfileStack.Navigator>
      <ProfileStack.Screen name="Profile" component={ProfileScreen} />
      <ProfileStack.Screen name="Settings" component={SettingsScreen} />
    </ProfileStack.Navigator>
  );
}
```

### 7. Añadir botones al header de navegación

#### a. Añadir botones al header

Puedes añadir botones al header de navegación utilizando la opción `options` en el componente de pantalla.

```javascript
<Stack.Screen
  name="Home"
  component={HomeScreen}
  options={{
    headerLeft: () => (
      <Button
        onPress={() => alert("This is a button!")}
        title="Burger"
        color="#000"
      />
    ),
    headerTitle: () => <Text>Inicio</Text>,
    headerRight: () => (
      <Button
        onPress={() => alert("This is a button!")}
        title="Info"
        color="#000"
      />
    ),
  }}
/>
```

### Uso de APIs nativas en React Native

En el desarrollo de aplicaciones móviles, es común interactuar con APIs nativas del dispositivo (como la cámara, el GPS, o el almacenamiento) y con APIs de terceros (como servicios web RESTful o GraphQL). React Native facilita estas integraciones a través de módulos y bibliotecas específicas.

### 1. APIs nativas

#### a. Instalación de módulos nativos

Para acceder a funcionalidades nativas, utilizamos módulos que permiten interactuar con las APIs del sistema operativo. Uno de los enfoques más populares es usar Expo, que proporciona una serie de APIs nativas de manera sencilla.

#### b. Ejemplos de APIs nativas comunes

1. **Cámara**

   - Usar la cámara del dispositivo para capturar fotos o videos.
   - Bibliotecas: `expo-camera`.

2. **GPS**

   - Obtener la ubicación geográfica del dispositivo.
   - Bibliotecas: `expo-location`.

3. **Almacenamiento**
   - Acceder al sistema de archivos del dispositivo para leer o guardar datos.
   - Bibliotecas: `expo-file-system`.

### 2. APIs de terceros

#### a. Instalación de bibliotecas para consumir APIs

Para consumir servicios web externos, podemos usar bibliotecas como `axios` o `fetch`.

#### b. Ejemplos de integración con APIs de terceros

1. **RESTful APIs**

   - Hacer peticiones HTTP a un servidor para obtener o enviar datos.
   - Bibliotecas: `axios`, `fetch`.

### 3. Ejemplos prácticos

#### a. Uso de la cámara con `expo-camera`

1. Instalar `expo-camera`:

```bash
 npx expo install expo-camera
```

2. app.json config

Add these lines to your app.json file:

```json
{
  "expo": {
    "plugins": [
      [
        "expo-camera",
        {
          "cameraPermission": "Allow $(PRODUCT_NAME) to access your camera",
          "microphonePermission": "Allow $(PRODUCT_NAME) to access your microphone",
          "recordAudioAndroid": true
        }
      ]
    ]
  }
}
```

2. Configuración y permisos:

```javascript
import { CameraView, useCameraPermissions } from "expo-camera";
import { useState } from "react";
import { Button, StyleSheet, Text, TouchableOpacity, View } from "react-native";

export default function App() {
  const [facing, setFacing] = useState("back");
  const [permission, requestPermission] = useCameraPermissions();

  if (!permission) {
    // Camera permissions are still loading.
    return <View />;
  }

  if (!permission.granted) {
    // Camera permissions are not granted yet.
    return (
      <View style={styles.container}>
        <Text style={{ textAlign: "center" }}>
          We need your permission to show the camera
        </Text>
        <Button onPress={requestPermission} title="grant permission" />
      </View>
    );
  }

  function toggleCameraFacing() {
    setFacing((current) => (current === "back" ? "front" : "back"));
  }

  return (
    <View style={styles.container}>
      <CameraView style={styles.camera} facing={facing}>
        <View style={styles.buttonContainer}>
          <TouchableOpacity style={styles.button} onPress={toggleCameraFacing}>
            <Text style={styles.text}>Flip Camera</Text>
          </TouchableOpacity>
        </View>
      </CameraView>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: "center",
  },
  camera: {
    flex: 1,
  },
  buttonContainer: {
    flex: 1,
    flexDirection: "row",
    backgroundColor: "transparent",
    margin: 64,
  },
  button: {
    flex: 1,
    alignSelf: "flex-end",
    alignItems: "center",
  },
  text: {
    fontSize: 24,
    fontWeight: "bold",
    color: "white",
  },
});
```

3. Capturar una imagen:
   - Implementar el código para capturar una imagen utilizando la cámara del dispositivo.

```javascript
const targetPixelCount = 1080; // If you want full HD pictures
const pixelRatio = PixelRatio.get(); // The pixel ratio of the device
// pixels * pixelRatio = targetPixelCount, so pixels = targetPixelCount / pixelRatio
const pixels = targetPixelCount / pixelRatio;

const result = await captureRef(this.imageContainer, {
  result: "tmpfile",
  height: pixels,
  width: pixels,
  quality: 1,
  format: "png",
});
```

### 5. Conclusión

El uso de APIs nativas y de terceros es fundamental para aprovechar al máximo las capacidades de los dispositivos móviles y para interactuar con servicios externos. React Native, junto con herramientas como Expo y bibliotecas como `axios`, facilita enormemente estas integraciones, permitiendo desarrollar aplicaciones móviles robustas y funcionales.

### Publicación de la aplicación en la Apple App Store utilizando Xcode Cloud

La publicación de una aplicación móvil en la Apple App Store es el último paso en el proceso de desarrollo. Utilizar Xcode Cloud puede simplificar este proceso mediante la integración continua y la entrega continua (CI/CD). A continuación, se describen los pasos necesarios para publicar una aplicación en dispositivos iOS utilizando React Native, Expo y Xcode Cloud.

### 1. Preparación de la Aplicación

#### a. Configuración de App.json (Expo)

Antes de construir la aplicación, es necesario configurar el archivo `app.json` o `app.config.js` en un proyecto de Expo. Este archivo contiene información importante sobre la aplicación, como su nombre, icono y permisos necesarios.

#### b. Optimización de Activos

Asegúrate de que todos los activos (imágenes, íconos, etc.) estén optimizados para reducir el tamaño de la aplicación y mejorar el rendimiento.

### 2. Construcción de la Aplicación para iOS

#### a. Configurar Certificados y Perfiles de Aprovisionamiento

1. **Crear una Cuenta de Desarrollador de Apple**:

   - Regístrate en el [Apple Developer Program](https://developer.apple.com/programs/) y paga la tarifa anual.

2. **Configurar Certificados en Xcode**:
   - Abre Xcode y ve a `Preferences > Accounts`, añade tu Apple ID y crea un perfil de aprovisionamiento.

#### b. Usar Expo para Construir la Aplicación

1. **Ejecutar el Comando de Construcción**:
   - Utiliza Expo para construir la aplicación y generar un archivo IPA que se puede subir a la App Store.

![expo build ios](https://i.imgur.com/8VJXxF2.png)

### 3. Configuración de Xcode Cloud

#### a. Configurar el Proyecto en Xcode Cloud

1. **Crear un Nuevo Workflow en Xcode Cloud**:

   - Abre Xcode, ve a `Xcode Cloud` y selecciona `Create a new workflow`.

2. **Configurar el Workflow**:
   - Define el workflow seleccionando el esquema, el tipo de dispositivo y la versión de iOS. También puedes configurar triggers para que el workflow se ejecute automáticamente al hacer push en el repositorio.

![xcode cloud workflow](https://developer.apple.com/assets/elements/icons/xcode-cloud/xcode-cloud-64x64.png)

#### b. Configurar Certificados y Perfiles de Aprovisionamiento en Xcode Cloud

1. **Subir Certificados**:
   - Sube tus certificados y perfiles de aprovisionamiento a Xcode Cloud desde la sección `Certificates, Identifiers & Profiles` en tu cuenta de desarrollador de Apple.

### 4. Publicación en TestFlight

#### a. Crear una Nueva Aplicación en App Store Connect

1. **Usar App Store Connect**:

   - Inicia sesión en [App Store Connect](https://appstoreconnect.apple.com/) y crea una nueva aplicación.

2. **Rellenar Información de la Aplicación**:
   - Proporciona detalles como el nombre de la aplicación, la descripción, las capturas de pantalla y el icono.

#### b. Subir el Archivo IPA desde Xcode Cloud

1. **Subir el Archivo IPA**:
   - Configura Xcode Cloud para que suba automáticamente el archivo IPA a TestFlight después de una build exitosa.

#### c. Configurar TestFlight

1. **Configurar Grupos de Prueba**:

   - En App Store Connect, ve a la sección de TestFlight y crea grupos de prueba. Añade los correos electrónicos de los testers.

2. **Invitar Testers**:
   - Invita a los testers para que descarguen la aplicación a través de TestFlight. Los testers recibirán una invitación por correo electrónico para instalar la aplicación.

#### d. Enviar para Pruebas Internas o Externas

1. **Pruebas Internas**:

   - Puedes invitar hasta 25 miembros de tu equipo que tengan acceso a App Store Connect para pruebas internas. No requiere revisión de Apple.

2. **Pruebas Externas**:
   - Para pruebas externas, invita hasta 10,000 usuarios externos. Apple revisará la aplicación antes de permitir pruebas externas.

### 5. Publicación en la App Store

#### a. Completar la Información de la Aplicación

1. **Usar App Store Connect**:

   - Asegúrate de completar toda la información requerida, incluyendo la clasificación por edades, la política de privacidad, y los detalles de contacto.

2. **Seleccionar Países y Regiones**:
   - Selecciona los países y regiones en los que deseas distribuir la aplicación.

#### b. Enviar para Revisión

1. **Enviar la Aplicación para Revisión**:
   - Una vez que toda la información esté completa, envía la aplicación para revisión por parte del equipo de Apple. Este proceso puede tardar algunos días.

### 6. Bonus track

¿Por que, actualmente, no uso react native, o por lo menos no inicio proyectos con react native?
¿Por que otra tecnología me estoy decantando?
