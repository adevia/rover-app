# ROVER MISSION CONTROL - MARS (V.1.0)

## Descripción

La aplicación "ROVER MISSION CONTROL" es una simulación interactiva que permite a los usuarios controlar un rover en un entorno de Marte representado en una cuadrícula. Los usuarios pueden establecer coordenadas iniciales y mover el rover en diferentes direcciones. La aplicación también detecta obstáculos en el camino del rover y notifica al usuario si el movimiento está bloqueado.

# ALERTA: TOP SECRET
Esta app es confindencial y por ello necesitarás las credenciales correctas para poderla visualizar. Si estás leyendo esto es porque has sido elegido como sujeto de prueba para llevar a cabo una exploración en marte. 
Las credenciales de acceso creadas para tu usuario son las siguientes: 

Credential: housfy
Password: frontend

## MISIóN
Explorar un cuadrante desconocido del territorio Marte.

## Funcionalidades
- **Control del Rover**: Puedes mover el rover en cuatro direcciones (norte, este, sur y oeste).
- **Detección de Obstáculos**: De manera predeterminada la app incluye seis(6) obstaculos distribuidos en el tablero  y el rover notificará al usuario si intenta moverse a una posición ocupada, en las siguientes posiciones:
{ x: 10, y: 4}
{ x: 20, y: 20}
{ x: 34, y: 6}
{ x: 50, y: 20}
{ x: 60, y: 16}
{ x: 80, y: 2}
- **Visualización de Obstáculos**: Los obstáculos se muestran en la cuadrícula y están inicialmente ocultos. Se vuelven visibles cuando el rover intenta entrar en su posición.
- **Coordenadas del Rover**: Se visualizan las coordenadas actuales del rover, junto con un mensaje informativo en caso de detectar un obstáculo.

## Pasos de Instalación
Para ejecutar la aplicación en tu máquina local, sigue estos pasos:

1. **Clona el repositorio**:
   ```bash
   git clone https://github.com/adevia/rover-app.git 

2. **Navega a la carpeta del proyecto**:
En la terminal usa el comando:
cd rover-app

3. **Instala las dependencias**:
Usa el comando:
npm install

4. **Ejecuta la aplicación**:
Usa el comando npm run serve

5. **Abre tu navegador favorito**:
Para ver la app en acción, pon en la barra de navegación:
http://localhost:8080

## Instrucciones para manejar el ROVER
1. **Establecer coordenadas iniciales**:
- Antes de mover el ROVER, debes establecer sus coordenadas iniciales. En la app, encontrarás un componente de entrada donde puedes ingresar valores para las coordenadas 'X' (horizontal) 'Y' (vertical).
- Recuerda que para esta primera exploración, solo abarcaremos coordenadas dentro de este rango:
-- 'X': de 0 a 84
-- 'Y': de 0 a 24
- Una vez ingreses las coordenadas de punto de partida del ROVER, presiona el boton 'Set ROVER initial point' para establecer la posición.

2. **Controlar el movimiento del ROVER**
El ROVER puede moverse en cuatro(4) direcciones (norte, sur. este y oeste) usando los sigueintes comandos: 
- F : Mueve el ROVER hacia adelante. 
- R : Cambia la dirección del ROVER hacia la derecha.
- L : Cambia la dirección del ROVER hacia la izquierda.
Usa el campo de introducción de comandos incluyendo los comandos que crees para explorar, por ejemplo FFRRFFRL. Esto hará que el ROVER avance dos casillas, rote dos veces hacia la derecha, avance dos casillas más y rote una vez hacia a la izquierda. 
La forma más sencilla que tendrás para saber hacia donde vas, estará indicada por la cabeza del ROVER. 

3. **Comportamiento de obstáculos**
Si el ROVER se encuentra en su recorrido con un obstaculo:
- El movimiento se dentendrá y el ROVER regresará automáticamente a su última posición válida. Esto quiere decir que tendrás que rodear el obstáculo o intentar una nueva ruta.
- Se notificará por medio de un mensaje la aparición del obstáculo con sus coordenadas. Estás aparecerán también junto a las coordenadas actuales del ROVER, en la parte inferior de la cuadricula.
- Los obstáculos encontrados se marcarán con un circulo rojo y quedarán activos hasta reiniciar la app. 

### CONSIDERACIONES
- Se planea para futuros desarrollos, generar un documento con las coordenadas exactas de los obstáculos y una representación del mapa. 
- Además se ha dejado creada la posibilidad de establecer un punto de llegada, que en la siguiente versión, servirá como punto final para generar los informes de la exploración.  
- Se proyecta añadir nuevos obstáculos en la cuadrícula en una nueva versión de la app, para que se generen de manera dinámica.

#### Disfruta de tu misión de exploración en Marte, no te preocupes por perder el ROVER. Siempre sabras dónde está y podrás recuperarlo facilmente. 

Andrés Devia Torres