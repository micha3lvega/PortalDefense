# Contexto del Proyecto: Portal Defense (Tower Defense + Cards)

## 📝 Descripción del Proyecto
`PortalDefense` es un videojuego híbrido de estrategia que combina las mecánicas de un **Tower Defense con Laberintos dinámicos** y un sistema de **Construcción de Mazos (Card Battler)**. El juego está diseñado exclusivamente para dispositivos móviles (Android) en formato horizontal (Landscape).

### Mecánica Core (Hito 1)
* **El Laberinto:** El mapa se compone de una cuadrícula ($1280 \times 720$). Hay portales de donde aparecen los enemigos y un castillo central que el jugador debe defender.
* **Las Cartas:** El jugador no compra torres de un menú estático; tiene una mano de cartas. Las cartas le permiten colocar defensas (muros tácticos, guerreros, arqueros o magos) sobre la cuadrícula para alterar el camino de los enemigos en tiempo real.
* **Pathfinding Dinámico:** Cada vez que el jugador altera la cuadrícula colocando un elemento, los enemigos deben recalcular su camino más corto hacia el castillo. Si el jugador bloquea por completo el camino, la acción no debe permitirse.

---

## 🛠️ Especificaciones Técnicas del Entorno (Estricto)
El entorno de desarrollo está configurado en un sistema operativo **Ubuntu Linux**. Se deben respetar estrictamente las versiones de lenguaje y software actuales del desarrollador para evitar conflictos de compilación:

* **Motor de Videojuegos:** Godot Engine 4.3 (Versión .NET/Mono)
* **Renderizador del Proyecto:** Mobile (Optimizado para OpenGL ES 3.0 / Vulkan Mobile)
* **Resolución Base:** $1280 \times 720$ (Stretch Mode: `canvas_items`, Aspect: `keep`)
* **Lenguaje de Programación:** C# (.NET 8) - *Nota: No usar .NET 10 ni versiones anteriores para asegurar compatibilidad nativa con Godot 4.3*.
* **Entorno de Ejecución Móvil:** Java 21 (OpenJDK 21 Temurin LTS) + Android SDK (Gestionado vía Android Studio).
* **Editor de Código:** Visual Studio Code (Configurado como editor externo en Godot).

---

## 📂 Arquitectura Actual del Proyecto

* `Mundo.tscn`: Escena principal en 2D que actúa como el lienzo de juego.
* `Mundo.cs`: Script principal en C# (.NET 8) acoplado al nodo raíz. Controlará la lógica del tablero, el cálculo de rutas y los turnos/estados del juego.
* `TileMapLayer`: Nodo encargado de renderizar visualmente el mapa de cuadrículas. Actualmente utiliza una textura placeholder (`icon.svg` en celdas de $128 \times 128$ píxeles) para simular los caminos y el suelo transitable (*Whiteboxing*).

---

## 🏁 Estado Actual e Hitos de Desarrollo

### 🟩 Hito 1: El Cerebro del Laberinto (En Progreso)
* [x] Inicialización del entorno en Ubuntu (Java 21, .NET 8, Android Studio, Godot 4.3).
* [x] Configuración de la resolución y modo de estiramiento para Pixel Art en móviles.
* [x] Creación de la escena raíz `Mundo` y la malla visual de pruebas (`TileMapLayer`).
* [x] Vinculación del script principal en C# (`Mundo.cs`) con VS Code.
* [ ] **Siguiente paso:** Programar la matriz lógica del mapa en C# y utilizar el algoritmo A* (A-Star) nativo de Godot (`AStar2D`) para conectar matemáticamente las celdas del camino y calcular rutas dinámicas.

### 🟨 Hito 2: El Sistema de Cartas e Invocación
* [ ] Crear la interfaz de usuario móvil (UI) para la mano de cartas.
* [ ] Implementar la mecánica de arrastrar y soltar (*Drag & Drop*) para colocar tropas en la cuadrícula usando coordenadas de celda.
* [ ] Lógica de coste de energía/maná al lanzar cartas.

### 🟨 Hito 3: Oleadas de Enemigos y Combate
* [ ] Spawner de portales enemigos.
* [ ] Movimiento fluido de los enemigos siguiendo el camino calculado por el Hito 1.
* [ ] Sistema de daño y estados de victoria/derrota (Salud del Castillo).