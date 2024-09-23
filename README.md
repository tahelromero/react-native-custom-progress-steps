

![](https://img.shields.io/npm/v/react-native-custom-progress-steps.svg?style=flat)
![](https://img.shields.io/npm/dt/react-native-custom-progress-steps.svg)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

# react-native-custom-progress-steps

Un componente simple y totalmente personalizable de React Native que implementa una interfaz de usuario de pasos de progreso.
* El contenido de cada paso se muestra dentro de un ScrollView personalizable.
* Botones totalmente personalizables se muestran en la parte inferior del componente para moverse entre los pasos.

Ejemplo Uno             |  Ejemplo Dos
:-------------------------:|:-------------------------:
![](assets/react-native-custom-progress-steps_1.gif) [examples/ExampleOne.js](examples/ExampleOne.js)| ![](assets/react-native-custom-progress-steps_2.gif) [examples/ExampleTwo.js](examples/ExampleTwo.js)

## Instalación

Si usas yarn:

```
yarn add react-native-custom-progress-steps
```

Si usas npm:

```
npm i react-native-custom-progress-steps
```

## Uso

```
import { ProgressSteps, ProgressStep } from 'react-native-custom-progress-steps';
```

Simplemente coloca una etiqueta `<ProgressStep />` para cada paso deseado dentro del contenedor `<ProgressSteps />`.

```
<View style={{flex: 1}}>
    <ProgressSteps>
        <ProgressStep label="Primer Paso">
            <View style={{ alignItems: 'center' }}>
                <Text>¡Este es el contenido del paso 1!</Text>
            </View>
        </ProgressStep>
        <ProgressStep label="Segundo Paso">
            <View style={{ alignItems: 'center' }}>
                <Text>¡Este es el contenido del paso 2!</Text>
            </View>
        </ProgressStep>
        <ProgressStep label="Tercer Paso">
            <View style={{ alignItems: 'center' }}>
                <Text>¡Este es el contenido del paso 3!</Text>
            </View>
        </ProgressStep>
    </ProgressSteps>
</View>
```

### Uso de Estilo de Botones
El contenedor y el texto de los botones son totalmente personalizables usando las propiedades `nextBtnStyle, nextBtnTextStyle, previousBtnStyle, y previousBtnTextStyle`.

Ejemplo de uso para cambiar el color del texto de un botón:

```
const buttonTextStyle = {
    color: '#393939'
};

return (
    <View style={{flex: 1}}>
        <ProgressSteps>
            <ProgressStep label="Primer Paso" nextBtnTextStyle={buttonTextStyle} previousBtnTextStyle={buttonTextStyle}>
                <View style={{ alignItems: 'center' }}>
                    <Text>¡Este es el contenido del paso 1!</Text>
                </View>
            </ProgressStep>
            <ProgressStep label="Segundo Paso" nextBtnTextStyle={buttonTextStyle} previousBtnTextStyle={buttonTextStyle}>
                <View style={{ alignItems: 'center' }}>
                    <Text>¡Este es el contenido del paso 2!</Text>
                </View>
            </ProgressStep>
        </ProgressSteps>
    </View>
)
```

### Manejo de Errores y Validación del Paso Actual
La propiedad [`errors`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Ftahelromero%2Fdatos%2FrepositorioNPM%2Freact-native-custom-progress-steps%2FREADME.md%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%2C%22pos%22%3A%7B%22line%22%3A89%2C%22character%22%3A5%7D%7D%5D%2C%221f24ff09-d1d5-463b-853e-09c2906a3eaa%22%5D "Go to definition") debe usarse si hay necesidad de validación y manejo de errores al hacer clic en el botón siguiente. Si deseas evitar que se renderice el siguiente paso, establece la propiedad [`errors`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Ftahelromero%2Fdatos%2FrepositorioNPM%2Freact-native-custom-progress-steps%2FREADME.md%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%2C%22pos%22%3A%7B%22line%22%3A89%2C%22character%22%3A5%7D%7D%5D%2C%221f24ff09-d1d5-463b-853e-09c2906a3eaa%22%5D "Go to definition") en [`true`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Ftahelromero%2Fdatos%2FrepositorioNPM%2Freact-native-custom-progress-steps%2FREADME.md%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%2C%22pos%22%3A%7B%22line%22%3A89%2C%22character%22%3A206%7D%7D%5D%2C%221f24ff09-d1d5-463b-853e-09c2906a3eaa%22%5D "Go to definition"). Por defecto, será [`false`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Ftahelromero%2Fdatos%2FrepositorioNPM%2Freact-native-custom-progress-steps%2FREADME.md%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%2C%22pos%22%3A%7B%22line%22%3A89%2C%22character%22%3A237%7D%7D%5D%2C%221f24ff09-d1d5-463b-853e-09c2906a3eaa%22%5D "Go to definition").

Ejemplo de uso de verificación de validación:

```
state = {
    isValid: false,
    errors: false
};

onNextStep = () => {
    if (!this.state.isValid) {
      this.setState({ errors: true });
    } else {
      this.setState({ errors: false });
    }
};

render() {
    return (
      <View style={{ flex: 1 }}>
        <ProgressSteps>
          <ProgressStep label="Primer Paso" onNext={this.onNextStep} errors={this.state.errors}>
            <View style={{ alignItems: 'center' }}>
              <Text>¡Este es el contenido del paso 1!</Text>
            </View>
          </ProgressStep>
          <ProgressStep label="Segundo Paso">
            <View style={{ alignItems: 'center' }}>
              <Text>¡Este es el contenido del paso 2!</Text>
            </View>
          </ProgressStep>
        </ProgressSteps>
      </View>
    );
}
```

## Documentación

### Componente de Pasos de Progreso
| Nombre                      | Descripción                              | Predeterminado     | Tipo    |
|---------------------------|------------------------------------------|-------------|---------|
| borderWidth               | Ancho de la barra de progreso entre pasos  | 6           | Número  |
| borderStyle               | Tipo de borde para la barra de progreso      | solid       | Cadena  |
| activeStepIconBorderColor | Color del borde exterior para el paso activo | #4bb543     | Cadena  |
| progressBarColor          | Color de la barra de progreso predeterminada        | #ebebe4     | Cadena  |
| completedProgressBarColor | Color de la barra de progreso completada      | #4bb543     | Cadena  |
| activeStepIconColor       | Color del icono del paso activo            | transparente | Cadena  |
| completedStepIconColor    | Color del icono del paso completado         | #4bb543     | Cadena  |
| disabledStepIconColor     | Color del icono del paso deshabilitado          | #ebebe4     | Cadena  |
| labelFontFamily           | Familia de fuentes para la etiqueta del icono del paso      | Fuente predeterminada de iOS/Android | Cadena |
| labelColor                | Color de la etiqueta predeterminada               | gris claro   | Cadena  |
| labelFontSize             | Tamaño de fuente para la etiqueta del icono del paso        | 14          | Número  |
| activeLabelColor          | Color de la etiqueta activa                | #4bb543     | Cadena  |
| activeLabelFontSize       | Tamaño de fuente opcional para la etiqueta del paso activo      | null     | Número  |
| completedLabelColor       | Color de la etiqueta completada             | gris claro   | Cadena  |
| activeStepNumColor        | Color del número del paso activo          | negro       | Cadena  |
| completedStepNumColor     | Color del número del paso completado       | negro       | Cadena  |
| disabledStepNumColor      | Color del número del paso deshabilitado        | blanco       | Cadena  |
| completedCheckColor       | Color de la marca de verificación del paso completado    | blanco       | Cadena  |
| activeStep                | Especificar manualmente el paso activo         | 0           | Número  |
| isComplete                | Establecer todos los pasos en estado activo            | false       | Booleano |
| topOffset                 | Establecer el desplazamiento superior de la barra de progreso              | 30          | Número  |
| marginBottom              | Establecer el margen inferior de la barra de progreso           | 50          | Número  |

### Componente de Paso de Progreso
| Nombre | Descripción | Predeterminado | Tipo |
|------------------|--------------------------------------------------------------------------|----------|---------|
| label | Título del paso actual a mostrar | null | Cadena |
| onNext | Function llamada cuando se presiona el botón siguiente | null | Function |
| onPrevious | Function llamada cuando se presiona el botón anterior | null | Function |
| onSubmit | Function llamada cuando se presiona el botón de envío del paso | null | Function |
| nextBtnText | Texto a mostrar dentro del botón siguiente | Next | Cadena |
| previousBtnText | Texto a mostrar dentro del botón anterior | Previous | Cadena |
| finishBtnText | Texto a mostrar dentro del botón en el último paso | Submit | Cadena |
| nextBtnStyle | Objeto de estilo para proporcionar a los botones siguiente/finalizar | { textAlign: 'center', padding: 8 } | Objeto |
| nextBtnTextStyle | Objeto de estilo para proporcionar al texto del botón siguiente/finalizar | { color: '#007aff', fontSize: 18 } | Objeto |
| nextBtnDisabled | Valor para deshabilitar/habilitar el botón siguiente | false | Booleano |
| previousBtnStyle | Objeto de estilo para proporcionar al botón anterior | { textAlign: 'center', padding: 8 } | Objeto |
| previousBtnTextStyle | Objeto de estilo para proporcionar al texto del botón anterior | { color: '#007aff', fontSize: 18 } | Objeto |
| previousBtnDisabled | Valor para deshabilitar/habilitar el botón anterior | false | Booleano |
| scrollViewProps | Objeto para proporcionar propiedades al componente ScrollView | {} | Objeto |
| scrollable | El contenido del Paso de Progreso debe ser desplazable | true | Booleano |
| viewProps | Objeto para proporcionar propiedades al componente de vista si scrollable es false | {} | Objeto |
| errors | Usado para ayudar con la validación del paso actual. Si es true, el siguiente paso no se renderizará | false | Booleano |
| removeBtnRow | Usado para renderizar el paso de progreso sin la fila de botones | false | Booleano |

## Contribuciones
¡Las solicitudes de contribución siempre son bienvenidas! Siéntete libre de abrir un nuevo problema en GitHub para cualquier cambio que se pueda hacer.

**¿Trabajando en tu primera solicitud de contribución?** Puedes aprender cómo hacerlo en esta serie *gratuita* [Cómo Contribuir a un Proyecto de Código Abierto en GitHub](https://egghead.io/series/how-to-contribute-to-an-open-source-project-on-github)

## Autor
Autor Original - Colby Miller | [https://tahelromero.com](https://tahelromero.com)

## Licencia
MIT
```


# react-native-custom-progress-steps

Un componente simple y totalmente personalizable de React Native que implementa una interfaz de usuario de pasos de progreso.
* El contenido de cada paso se muestra dentro de un ScrollView personalizable.
* Botones totalmente personalizables se muestran en la parte inferior del componente para moverse entre los pasos.

Ejemplo Uno             |  Ejemplo Dos
:-------------------------:|:-------------------------:
![](assets/react-native-custom-progress-steps_1.gif) [examples/ExampleOne.js](examples/ExampleOne.js)| ![](assets/react-native-custom-progress-steps_2.gif) [examples/ExampleTwo.js](examples/ExampleTwo.js)

## Instalación

Si usas yarn:


```
yarn add react-native-custom-progress-steps
```

Si usas npm:


```
npm i react-native-custom-progress-steps
```


Si usas npm:


```
import { ProgressSteps, ProgressStep } from 'react-native-custom-progress-steps';
```


Simplemente coloca una etiqueta `<ProgressStep />` para cada paso deseado dentro del contenedor `<ProgressSteps />`.


```
<View style={{ flex: 1 }}>
  {" "}
  <ProgressSteps>
    {" "}
    <ProgressStep label="Primer Paso">
      {" "}
      <View style={{ alignItems: "center" }}>
        {" "}
        <Text>¡Este es el contenido del paso 1!</Text>{" "}
      </View>{" "}
    </ProgressStep>{" "}
    <ProgressStep label="Segundo Paso">
      {" "}
      <View style={{ alignItems: "center" }}>
        {" "}
        <Text>¡Este es el contenido del paso 2!</Text>{" "}
      </View>{" "}
    </ProgressStep>{" "}
    <ProgressStep label="Tercer Paso">
      {" "}
      <View style={{ alignItems: "center" }}>
        {" "}
        <Text>¡Este es el contenido del paso 3!</Text>{" "}
      </View>{" "}
    </ProgressStep>{" "}
  </ProgressSteps>{" "}
</View>
```


### Uso de Estilo de Botones
El contenedor y el texto de los botones son totalmente personalizables usando las propiedades `nextBtnStyle, nextBtnTextStyle, previousBtnStyle, y previousBtnTextStyle`.

Ejemplo de uso para cambiar el color del texto de un botón:


```
const buttonTextStyle = { color: "#393939" };

return (
  <View style={{ flex: 1 }}>
    {" "}
    <ProgressSteps>
      {" "}
      <ProgressStep
        label="Primer Paso"
        nextBtnTextStyle={buttonTextStyle}
        previousBtnTextStyle={buttonTextStyle}
      >
        {" "}
        <View style={{ alignItems: "center" }}>
          {" "}
          <Text>¡Este es el contenido del paso 1!</Text>{" "}
        </View>{" "}
      </ProgressStep>{" "}
      <ProgressStep
        label="Segundo Paso"
        nextBtnTextStyle={buttonTextStyle}
        previousBtnTextStyle={buttonTextStyle}
      >
        {" "}
        <View style={{ alignItems: "center" }}>
          {" "}
          <Text>¡Este es el contenido del paso 2!</Text>{" "}
        </View>{" "}
      </ProgressStep>{" "}
    </ProgressSteps>{" "}
  </View>
);
```

### Current Step Error and Validation Handling
The `errors` prop should be used if there's a need for validation and error handling when clicking the next button. If you would like to prevent the next step from being rendered, set the `errors` prop to `true`. By default, it will be `false`.

Example usage of validation check:

```
state = {
    isValid: false,
    errors: false
};

onNextStep = () => {
    if (!this.state.isValid) {
      this.setState({ errors: true });
    } else {
      this.setState({ errors: false });
    }
};

render() {
    return (
      <View style={{ flex: 1 }}>
        <ProgressSteps>
          <ProgressStep label="First Step" onNext={this.onNextStep} errors={this.state.errors}>
            <View style={{ alignItems: 'center' }}>
              <Text>This is the content within step 1!</Text>
            </View>
          </ProgressStep>
          <ProgressStep label="Second Step">
            <View style={{ alignItems: 'center' }}>
              <Text>This is the content within step 2!</Text>
            </View>
          </ProgressStep>
        </ProgressSteps>
      </View>
    );
}

```

## Documentation

### Progress Steps Component
| Name                      | Description                              | Default     | Type    |
|---------------------------|------------------------------------------|-------------|---------|
| borderWidth               | Width of the progress bar between steps  | 6           | Number  |
| borderStyle               | Type of border for the progress bar      | solid       | String  |
| activeStepIconBorderColor | Outside border color for the active step | #4bb543     | String  |
| progressBarColor          | Color of the default progress bar        | #ebebe4     | String  |
| completedProgressBarColor | Color of the completed progress bar      | #4bb543     | String  |
| activeStepIconColor       | Color of the active step icon            | transparent | String  |
| completedStepIconColor    | Color of the completed step icon         | #4bb543     | String  |
| disabledStepIconColor     | Color of the disabled step icon          | #ebebe4     | String  |
| labelFontFamily           | Font family for the step icon label      | iOS/Android default font | String |
| labelColor                | Color of the default label               | lightgray   | String  |
| labelFontSize             | Font size for the step icon label        | 14          | Number  |
| activeLabelColor          | Color of the active label                | #4bb543     | String  |
| activeLabelFontSize       | Optional font size for the active step icon label      | null     | Number  |
| completedLabelColor       | Color of the completed label             | lightgray   | String  |
| activeStepNumColor        | Color of the active step number          | black       | String  |
| completedStepNumColor     | Color of the completed step number       | black       | String  |
| disabledStepNumColor      | Color of the disabled step number        | white       | String  |
| completedCheckColor       | Color of the completed step checkmark    | white       | String  |
| activeStep                | Manually specify the active step         | 0           | Number  |
| isComplete                | Set all Steps to active state            | false       | Boolean |
| topOffset                 | Set progress bar top offset              | 30          | Number  |
| marginBottom              | Set progress bar bottom margin           | 50          | Number  |

### Progress Step Component
| Name | Description | Default | Type |
|------------------|--------------------------------------------------------------------------|----------|---------|
| label | Title of the current step to be displayed | null | String |
| onNext | Function called when the next step button is pressed | null | Func |
| onPrevious | Function called when the previous step button is pressed | null | Func |
| onSubmit | Function called when the submit step button is pressed | null | Func |
| nextBtnText | Text to display inside the next button | Next | String |
| previousBtnText | Text to display inside the previous button | Previous | String |
| finishBtnText | Text to display inside the button on the last step | Submit | String |
| nextBtnStyle | Style object to provide to the next/finish buttons | { textAlign: 'center', padding: 8 } | Object |
| nextBtnTextStyle | Style object to provide to the next/finish button text | { color: '#007aff', fontSize: 18 } | Object |
| nextBtnDisabled | Value to disable/enable next button | false | Boolean |
| previousBtnStyle | Style object to provide to the previous button | { textAlign: 'center', padding: 8 } | Object |
| previousBtnTextStyle | Style object to provide to the previous button text | { color: '#007aff', fontSize: 18 } | Object |
| previousBtnDisabled | Value to disable/enable previous button | false | Boolean |
| scrollViewProps | Object to provide props to ScrollView component | {} | Object |
| scrollable | The content of the Progress Step should be scrollable | true | Boolean |
| viewProps | Object to provide props to view component if scrollable is false | {} | Object |
| errors | Used to assist with current step validation. If true, the next step won't be rendered | false | Boolean |
| removeBtnRow | Used to render the progress step without the button row | false | Boolean |

## Contributing
Pull requests are always welcome! Feel free to open a new GitHub issue for any changes that can be made.

**Working on your first Pull Request?** You can learn how from this *free* series [How to Contribute to an Open Source Project on GitHub](https://egghead.io/series/how-to-contribute-to-an-open-source-project-on-github)

## Author
Original Autor - Colby Miller | [https://colbymillerdev.com](https://colbymillerdev.com)

## License
[MIT](./LICENSE)
