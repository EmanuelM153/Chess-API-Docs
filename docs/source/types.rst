Tipos
===

TIPO_PROMOCIONAR
----------------

**Enum**

El tipo de ficha a la que se desea promocionar.

.. code-block: js

   ("CABALLO" | "ALFIL" | "REINA" | "TORRE")

CASILLA
-------

**Estructura de datos**

La posicion de la casilla en el tablero.

.. code-block: js

   [$fila : number, $columna : number]

MENSAJE
-------

**Enum**

Un mensaje sobre un movimiento.

.. code-block: js

   ("JAQUEMATE" | "JAQUE" | "ENPASSANT | "   "ENROQUE | "MOVIMIENTOINVALIDO" | "MOVIMIENTOVALIDO" | "EMPATE" | "PROMOCION")

ESTADOPARTIDA
-------------

**Enum**

El estado de la partida.

.. code-block: js

   ("ESPERANDO" | "JUGANDOSE" | "EMPATE" | "JAQUEMATE")

COLOR
-----

**Enum**

El color del turno del jugador.

.. code-block: js

   ("BLANCO" | "NEGRO")
