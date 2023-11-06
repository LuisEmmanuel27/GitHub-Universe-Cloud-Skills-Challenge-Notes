# Ejercicio: Crear la lógica del juego

Con Codespaces configurado, el objetivo es desarrollar el minijuego de consola de Python. Debes crear la lógica del juego siguiendo las especificaciones y usar GitHub Copilot para ayudar a crear los métodos.

## Especificación

### Reglas del juego:

-   La piedra gana a las tijeras (las rompe).
-   Las tijeras han ganado al papel (lo cortan).
-   El papel gana a la piedra (la envuelve).
-   El minijuego es multijugador y el equipo juega el papel del oponente y elige un elemento aleatorio de la lista de elementos

### Interacción con el jugador:

-   La consola se usa para interactuar con el jugador.
-   El jugador puede elegir una de las tres opciones: rock, paper o scissors.
-   El jugador puede elegir si vuelve a jugar.
-   Se debe advertir al jugador si introduce una opción no válida.
-   El jugador ve su puntuación al final del juego.

### Validación de la entrada del usuario:

-   En cada ronda, el jugador debe entrar en una de las opciones de la lista y ser informado de si ganó, perdió o empató con el oponente.
-   El minijuego debe controlar las entradas del usuario, colocarlas en minúsculas e informar al usuario si la opción no es válida.
-   Al final de cada ronda, el jugador debe responder si quiere jugar de nuevo o no.

Con Visual Studio Code en el explorador y GitHub Copilot para ayudarle, cree un minijuego que cumpla las especificaciones anteriores.

## Comprobar el trabajo

1. Ejecute el minijuego en la consola con el comando python app.py.

2. En el símbolo del sistema, escriba una de las opciones del juego: rock, paper o scissors.

3. El minijuego debe informar al jugador de si ganó, perdió o empató con el oponente.

4. Elija para continuar jugando.

5. En el símbolo del sistema, escriba:screen.

6. El minijuego debe informar al jugador si la opción que ha especificado no es válida.

7. Repita los pasos 2 y 4 para jugar unas cuantas rondas y elija no seguir jugando.

8. Compruebe si el minijuego ha terminado y si muestra su puntuación, informándole del número de victorias y rondas.

Enhorabuena por completar este ejercicio de desafío. Ha creado un minijuego de consola de Python con GitHub Copilot.

## Código que me genero Copilot:

    # create a list of play options
    t = ["Rock", "Paper", "Scissors"]

    # assign a random play to the computer

    computer = t[random.randint(0,2)]

    # set player to False

    player = False

    while player == False:
    # set player to True
        player = input("Rock, Paper, Scissors?")
        if player == computer:
            print("Tie!")
        elif player == "Rock":
            if computer == "Paper":
                print("You lose!", computer, "covers", player)
            else:
                print("You win!", player, "smashes", computer)
        elif player == "Paper":
            if computer == "Scissors":
                print("You lose!", computer, "cut", player)
            else:
                print("You win!", player, "covers", computer)
        elif player == "Scissors":
            if computer == "Rock":
                print("You lose!", computer, "smashes", player)
            else:
                print("You win!", player, "cut", computer)
        else:
            print("That's not a valid play. Check your spelling!")
    # player was set to True, but we want it to be False so the loop continues
        player = False
        computer = t[random.randint(0,2)]
