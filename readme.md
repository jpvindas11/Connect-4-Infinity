=====================================================================================================================  

                                                CONNECT 4 INFINITY


                                             Universidad de Costa Rica


                                    Bachillerato en Computación con Varios Énfasis

                                    
                                              Programación II CI-0113


                                              Proyecto#1 I Ciclo 2024

=====================================================================================================================



    -/ Explicación de cómo jugar


    *Controles*
        1. Los controles del juego son las teclas direccionales y la tecla del espacio.
        2. En el menú principal del juego, se podrá mover entre las opciones con las flechas de izquierda a derecha
        y seleccionar el modo de juego con el espacio.
        3. En el juego, se podrá mover la posición donde se desea colocar una ficha con las flechas horizontales,
        con el espacio se podrá colocar la ficha, y con las flechas verticales se podrá mover la cámara verticalmente
        cuando hayan elementos fuera de la pantalla.
        4. En caso de jugar en modo multijugador, ambos jugadores compartirán los controles.
    
    *Jugar*
        1. Se presenta el juego de 4 en línea, con la adición de poseer un tablero infinito, se pueden colocar fichas fuera de el tablero para expandirlo dinámicamente, tanto horizontal 
        como verticalmente, no te puedes quedar sin espacio.
        2. Hay dos modos de juego, el multijugador y contra una inteligencia artificial.
        3. En el multijugador, puedes jugar con otra persona, compartiendo los controles, deberás conectar 4 fichas de tu color antes que tu rival para ganar.
        4. En el modo AI, podrás jugar contra una inteligencia artificial que querrá retarte.



    
    -/ Explicación de la programación

        -Se utilizaron diferentes archivos .cpp para escribir la lógica de 3 aspectos importantes:

            - El manejo de la lógica del juego (Jugar junto a la AI)
            - El manejo del tablero
            - La interfaz

        * Manejo de la lógica:

            1. Se utilizó el main.cpp, GameManager.cpp y GameManager.h
            2. En el main está el objeto con la clase GameManager para manejar toda la lógica del juego, y ponerla
            dentro de un loop
            3. En el GameManager se manejan distintos elementos, en el header se declaran los métodos que serán explicados a continuación, además de que contiene los objetos de las 
            clases GameGraphics, y Matrix
            4. En el constructor se inicializan valores de las variables, como el estado de juego y manejo de los controles
            5. En el evento update, se manejan inputs, actualizaciones según el modo de juego, que llama a un menú, al modo multijugador, o al modo AI, cada uno con sus propios métodos 
            que se actualizan condicionalmente al gameState.
            6. Los inputs son manejados con un evento de la librería de SDL2, que permite detectar input del teclado, se usó para actualizar variables de movimiento y seleccionar     
            elementos.
            7. Los movimientos de fichas y colocaciones se manejan en el GameManager, con métodos como P1Move y P2Move que envían información a la clase Matrix sobre dónde y qué número 
            de ficha colocar, además de una clase que lee la matriz para determinar si se ha ganado o no todavía.
        
        * Manejo del tablero:

            1. Se utilizó Matrix.cpp y Matrix.h
            2. En el header se declaran nuevamente las variables, como la matriz, los métodos para navegar, obtener valores específicos, agregar columnas y filas, además de un método 
            para tener en cuenta índices negativos.
            3. Todos estos métodos son llamados desde el GameManager a la hora de realizar movimientos, para tener un mayor control y orden.

        * Manejo de la interfaz: 

            1. Se utilizaron las librerías de SDL2 y SDL2_image para la creación de la interfaz.
            2. Para el manejo total se utilizó GameGraphics.cpp
            3. Se inicializan funciones como las texturas que se utilizarán, la pantalla, un renderer, y variables que guardan valores para dibujar las texturas a partir de rectángulos 
            Rect.
            4. Se tiene un método init(), que es llamado desde GameManager para inicializar SDL, asignar las texturas con un método, que crea surfaces para asignar las texturas, luego 
            se modifican los valores de las variables Rect para asignar anchura, altura, x, y para los elementos de la pantalla.
            5. El función update atrapa variables del GameManager, que son importantes para lo que se necesita dibujar en cada momento, como los elementos de un menú, o del modo de 
            juego.
            6. En la función render, se dibujan los elementos en pantalla con un orden específico, según el estado en el que esté el juego, aquí se muestra el tablero en caso de estar 
            jugando, se muestran las texturas de los botones y la pantalla de título, y los mensajes de victoria por jugador, entre otros.
        
        * Explicación de la AI

        1. En el método aiMove(), primero se verifica que sea el primer moviento, esto porque el primer mov no es una jugada de peligro dentro de las condiciones por las que juega la 
        ia, entonces al verificar que la matriz vale 1, ya que el jugador es representado con un 1 entonces el bot aqui juega en un lugar aleatorio, si singleRow y singleCol son iguales 
        a -1, entonces significa que encontró más movimientos, entonces no es el primer movimiento y empieza a jugar defensivo de acuerdo a sus restricciones analizando la matriz.
        2. El primer if después de esto, lo que hace es verificar si es un numero suelto, como por asi decirlo un  numero 1 suelto, esto hace que no se caiga cuando no es jugada de 
        peligro y se salió de la matriz, y ahora si verifica luego de esto si se encontraron dos seguidos en horizontal, vertical o en diagonal.



        Profesor: Sergio Moya Valerín

        Estudiantes:

            Leonardo Sibaja Campos     C37537
            Jordan Obando Brenes       C25597
            Juan Pablo Vindas Ureña    C38554



======================================================================================================================
