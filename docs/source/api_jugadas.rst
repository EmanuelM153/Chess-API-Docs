API Jugadas
===========

A continuación se definen las funciones de la API Rest para las jugadas, con:

* Descripción
* Método Http de acceso
* Datos de entrada
* Datos de salida
* Condiciones para acceder a la funcionalidad

.. note::

   * Las variables o campos empiezan con **$**
   * La API recibe y envía datos en notación JSON
   * Los tipos de las variables se indican como en Typescript, i.e., nombre: Tipo

Mover Ficha
-----------

* Se envía un movimiento y se obtiene una respuesta sobre la validez de este
* **POST**
* Entrada

   * casillaInicio: :ref:`casilla`

      * La casilla inicial del movimiento

   * casillaDestino: :ref:`casilla`

      * La casilla de destino del movimiento

   * idPartida: string

      * El id de la partida

   * movimientos: string

     * Token **JWT** con un claim: movimientos: :ref:`movimiento` []
* Salida

   * movimientos: string

     * Token **JWT** con un claim: movimientos: :ref:`movimiento` []

   * mensaje: :ref:`mensaje` []

     * Información de lo que produjo el movimiento
* Condiciones

   * Autenticación con token **JWT** válida
   * Usuario existente
   * Token **JWT** con el claim de *movimientos* y con firma válida
   * Partida existente
   * Usuario con el turno válido

Obtener Movimientos
-------------------

**Para usuarios espectadores**

* Se obtiene una lista de los movimientos a partir del que tiene el jugador
* **GET**
* Entrada

   * idPartida: string

      * El id de la partida

   * ultimo: number

      * La cantidad de movimientos que el cliente tiene
* Salida

   * movimientos: :ref:`movimiento` []

      * La lista de movimientos para que se actualize el cliente

* Condiciones

   * Autenticación con token **JWT** válida
   * Usuario existente
   * Partida existente

Obtener Movimientos
-------------------

**Para usuarios de la partida**

* Se obtiene una lista de los movimientos a partir del que tiene el jugador
* **GET**
* Entrada

   * idPartida: string

      * El id de la partida

   * ultimo: number

      * La cantidad de movimientos que el cliente tiene
* Salida

   * movimientos: string

     * Token **JWT** con un claim: movimientos: :ref:`movimiento` []

   * movimientos: :ref:`movimiento` []

      * La lista de movimientos para que se actualize el cliente

* Condiciones

   * Autenticación con token **JWT** válida
   * Usuario existente
   * Partida existente
   * Que el usuario este jugando la partida

Obtener Posibilidades
---------------------

* Se obtiene una lista de las posibles jugadas que una ficha puede realizar
* **GET**
* Entrada

   * idPartida: string

      * El id de la partida

   * casilla: :ref:`casilla`

      * La casilla de la ficha

   * movimientos: string

     * Token **JWT** con un claim: movimientos: :ref:`movimiento` []
* Salida

   * casillas: :ref:`casilla` []

      * Las casillas a la que la ficha se puede mover
* Condiciones

   * Autenticación con token **JWT** válida
   * Usuario existente
   * Partida existente
   * Token **JWT** con el claim de *movimientos* y con firma válida

Promocionar Ficha
-----------------

* Se envía el tipo de ficha a la que se desea promocionar
* **POST**
* Entrada

   * tipo: :ref:`tipo-promocionar`

      * El tipo de ficha a la que se desea promocionar

   * idPartida: string

     * El id de la partida

   * movimientos: string

     * Token **JWT** con un claim: movimientos: :ref:`movimiento` []
* Salida

   * validez: boolean

      * Si se realizó la promoción
* Condiciones

   * Autenticación con token **JWT** válida
   * Usuario existente
   * Token **JWT** con el claim de *movimientos* y con firma válida
   * Partida existente
   * Usuario con el turno válido
