Tipos
=====

.. note::

   * Las variables o campos empiezan con **$**
   * Los tipos de las variables se indican como en Typescript, i.e., nombre: Tipo
   * Los campos opcionales vienen encerrados con corchetes cuadrados **[]**

.. _tipo-partida:

TIPO_PARTIDA
------------

**Enum**

El tipo de la partida.

.. code-block:: none

   ("NORMAL")

.. _tipo-promocionar:

TIPO_PROMOCIONAR
----------------

**Enum**

El tipo de ficha a la que se desea promocionar.

.. code-block:: none

   ("CABALLO" | "ALFIL" | "REINA" | "TORRE")

.. _mensaje:

MENSAJE
-------

**Enum**

Un mensaje sobre un movimiento.

.. code-block:: none

   ("JAQUEMATE" | "JAQUE" | "ENPASSANT | "ENROQUE" | "MOVIMIENTOINVALIDO" | "MOVIMIENTOVALIDO" | "EMPATE" | "PROMOCION")

ESTADOPARTIDA
-------------

**Enum**

El estado de la partida.

.. code-block:: none

   ("ESPERANDO" | "JUGANDOSE" | "EMPATE" | "JAQUEMATE")

.. _color:

COLOR
-----

**Enum**

El color del turno del jugador.

.. code-block:: none

   ("BLANCO" | "NEGRO")

.. _casilla:

Casilla
-------

**Arreglo**

La posicion de la casilla en el tablero.

.. code-block:: none

   $fila: number, $columna: number

.. _movimiento:

Movimiento
----------

**Estructura u Objeto**

Un movimiento en el tablero.

.. code-block:: none

   {
      casillaInicio: Casilla
      casillaDestino: Casilla
      mensajes: MENSAJE[]
      [tipo: TIPO_PROMOCIONAR]
   }

.. _date:

Date
----

**Formato**

Día de creación de la partida.

El formato es ``yyyy-MM-dd``

.. _partida:

Partida
-------

Datos de una partida.

**Estructura u Objeto**

.. code-block:: none

   {
      idPartida: string
      date: Date
      nickNameBlancas: string
      nickNameNegras: string
      tipo: TIPO_PARTIDA
      estado: ESTADOPARTIDA
   }
