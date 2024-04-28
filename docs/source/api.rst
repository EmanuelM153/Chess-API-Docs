API Partidas
============

A continuación se definen las funciones de la API Rest para partidas, con:

* Descripción
* Método Http de acceso
* Datos de entrada
* Datos de salida
* Condiciones para acceder a la funcionalidad

.. note::

   * Las variables o campos empiezan con **$**
   * La API recibe y envía datos en notación JSON
   * Los tipos de las variables se indican como en Typescript, i.e., nombre: Tipo

Crear Partida
-------------

* Se agrega una nueva partida en la base de datos y se devuelven sus datos
* **POST**
* Entrada

   * tipopartida: :ref:`tipo-partida`
   * El tipo de la partida que se desea crear
* Salida

   * idPartida: String

     * El id de la partida
   * turno: :ref:`color`

     * El color del turno que le corresponde al jugador
   * date: :ref:`date`
   * movimientos: string

     * Token **JWT** con un claim: movimientos: :ref:`movimiento` []
* Condiciones

   * Autenticación con token **JWT** válida
   * Usuario existente

Unirse a una Partida
--------------------

* Se agrega un usuario a una partida ya creada en la base de datos y se devuelve información de la partida y del jugador
* **PUT**
* Entrada

   * idPartida: string

      * El id de la partida
* Salida
   * nickName: string

      * El nickName del usuario oponente

   * tipopartida: :ref:`tipo-partida`

      * El tipo de la partida
* Condiciones

   * Autenticación con token **JWT** válida
   * Usuario existente
   * Usuario diferente del usuario oponente
   * Partida existente
   * Partida con cupo

Información Partida
-------------------

* Se obtiene información general de la partida
* **GET**
* Entrada

   * idPartida: string

      * El id de la partida
* Salida

   * informacion: :ref:`partida`
* Condiciones

   * Autenticación con token **JWT** válida
   * Usuario existente
   * Partida existente

Partidas
--------

* Se obtiene una lista de las partidas en las que el jugador esta actualmente participando
* **GET**
* Sin entrada
* Salida

   * partidas: :ref:`partida` []

     * $estado es por tanto ESPERANDO o JUGANDOSE
* Condiciones

   * Autenticación con token **JWT** válida
   * Usuario existente

Histórico
---------

* Se obtiene una lista de las partidas en las que el jugador participó
* **GET**
* Sin entrada
* Salida

   * partidas: :ref:`partida` []

     * $estado es por tanto EMPATE O JAQUEMATE
* Condiciones

   * Autenticación con token **JWT** válida
   * Usuario existente
