# unitymov
# README: Scripts de Jugador y Cámara

## Resumen

Este proyecto incluye dos scripts esenciales para un juego en Unity: **PlayerController** y **CameraController**. Estos scripts trabajan juntos para gestionar el movimiento del jugador, los saltos, las interacciones con los objetos del juego y mantener una vista constante del jugador a través de la cámara.

---

## Script PlayerController

Este script se adjunta al objeto jugador y maneja el movimiento, los saltos y las interacciones con coleccionables y peligros.

### Funcionalidades
1. **Movimiento**: El jugador se mueve según la entrada del teclado o el controlador.
2. **Salto**: El jugador puede saltar cuando está en el suelo al presionar la tecla `Espacio`.
3. **Coleccionables**: Recoger objetos etiquetados como `pickup` incrementa un contador y actualiza la interfaz.
4. **Peligros**: Si el jugador toca un objeto etiquetado como `dead`, se reinicia a una posición inicial.
5. **Condición de victoria**: El juego muestra un mensaje de victoria cuando el jugador recoge 8 objetos.

### Desglose del Código

#### Variables
- `Rigidbody rb`: Para aplicar movimiento basado en física.
- `int count`: Rastrea la cantidad de objetos recogidos.
- `float movementX, movementY`: Almacenan la entrada del jugador para el movimiento.
- `float speed`: Controla la velocidad de movimiento del jugador.
- `float jumpForce`: Determina la fuerza aplicada al saltar.
- `TextMeshProUGUI countText`: Actualiza la interfaz con el número de objetos recogidos.
- `GameObject winTextObject`: Muestra un mensaje cuando el jugador gana.
- `Transform playerTransform`: Se utiliza para reiniciar la posición del jugador.

#### Métodos
- **`Start()`**: Inicializa variables, oculta el mensaje de victoria y actualiza la interfaz.
- **`OnMove()`**: Lee la entrada de movimiento del jugador.
- **`SetCountText()`**: Actualiza la interfaz y verifica si el jugador ha ganado.
- **`Update()`**: Comprueba si se presiona la tecla de salto y aplica una fuerza de salto si el jugador está en el suelo.
- **`FixedUpdate()`**: Aplica fuerzas de movimiento basadas en la entrada del jugador.
- **`OnTriggerEnter(Collider other)`**: Gestiona las interacciones con coleccionables (`pickup`) y peligros (`dead`).

---

## Script CameraController

Este script se adjunta al objeto cámara y asegura que siga al jugador mientras mantiene una distancia constante.

### Funcionalidades
1. **Seguir al jugador**: La cámara mantiene una posición fija relativa al jugador.

### Desglose del Código

#### Variables
- `GameObject Player`: Referencia al objeto jugador.
- `Vector3 offset`: Almacena la distancia inicial entre la cámara y el jugador.

#### Métodos
- **`Start()`**: Calcula la distancia inicial entre la cámara y el jugador.
- **`LateUpdate()`**: Actualiza la posición de la cámara para seguir al jugador manteniendo la distancia.

---

## Instrucciones de Configuración

1. **Script PlayerController**:
   - Adjunta este script al objeto jugador.
   - Asegúrate de que el jugador tenga un componente `Rigidbody`.
   - Configura las propiedades `speed`, `jumpForce`, `countText` y `winTextObject` en el Inspector de Unity.

2. **Script CameraController**:
   - Adjunta este script al objeto cámara.
   - Asigna el objeto jugador al campo `Player` en el Inspector de Unity.

3. **Objetos del Juego**:
   - Etiqueta los objetos coleccionables como `pickup` y los peligros como `dead`.
   - Asegúrate de que el objeto de texto de victoria esté asignado a `winTextObject`.

---

## Cómo Usar

1. Usa las teclas de flechas, `WASD` o un controlador para mover al jugador.
2. Presiona `Espacio` para que el jugador salte.
3. Recoge los 8 objetos para ganar el juego.
4. Evita caer en peligros para no reiniciar la posición.

---

## Dependencias

- Sistema de Entrada de Unity: Asegúrate de que el paquete Input System esté instalado y configurado.
- TextMeshPro: Utilizado para elementos de texto de la interfaz.

---

## Posibles Mejoras

- Agregar efectos de sonido para el salto y la recolección de objetos.
- Implementar un temporizador para desafiar a los jugadores a completar el juego más rápido.
- Añadir animaciones para el movimiento y el salto del jugador.

---
