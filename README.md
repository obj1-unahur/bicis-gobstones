# Depósitos de bicicletas

![muchas_bicis](muchasbicis.jpg "Buscá tu bici si te animás")

Nos piden construir un modelo cuyo objetivo es informatizar parte de la gestión de los depósitos municipales de bicicletas en Ciudad Gótica.


## 1. Bicis con canasto
En esta primera etapa nos piden modelar bicicletas que tienen un canasto. Por razones que veremos luego, conviene modelar __por separado__ bicicleta y canasto.

De cada bicicleta se informa: el _rodado_ (p.ej. 26), y el _largo_ en centímetros (p.ej. 120 para una bici de 1.20 metros de largo).
De cada canasto se informa el volumen. 

A partir de estos datos, debe poder obtenerse la siguiente información referida a una bici:
- _altura_: se calcula como `rodado * 3 + 15`.
- _velocidad de crucero_: si la bici tiene más de 120 cm, entonces se calcula como `rodado + 6`, si no, como `rodado + 2`.
- _carga_: es la suma de la carga que puede llevar cada accesorio.
- _peso_: es la suma de `rodado / 2` más el peso total de los accesorios.

El peso de un canasto se calcula como `volumen / 10`, y su carga como `volumen * 2`.

P.ej. para una bici rodado 26, largo 110 cm, con un canasto de volumen 30, tenemos: altura 93, velocidad de crucero 28, carga 60, peso 16.

También debe ser posible obtener la carga y el peso del canasto (en el ejemplo, 3 y 60 respectivamente).


## 2. Bicis con un accesorio
Ahora el modelo se vuelve más complejo: cada bicicleta incluye un _accesorio_ que puede ser un canasto (como en el punto anterior), un farolito o un morral para bicis.

Debe poder obtenerse, para una bici, la misma información que en el punto anterior, más el siguiente ítem adicional:
- _tieneLuz_: es verdadero si al menos su accesorio es luminoso.

La información sobre los nuevos accesorios es la siguiente.

1. **Farolito**: pesa 1 kg, no lleva carga (o sea, lleva 0 kg de carga), es luminoso.
1. **Morral de bici**: para cada uno se informa el largo (en centímetros), y si tiene ojo de gato o no. El peso es fijo, 2 kg. La carga se calcula como `largo / 3`. Es luminoso si tiene ojo de gato.

Respecto de los **canastos**, tener en cuenta que no son luminosos.

<br>
Para que tengan una idea y por las dudas, va una foto de un morral para bici.

![morral](morral_bici.jpg "Esto es un morral para bici")

Van tres ejemplos adicionales de bicis.
* una bici rodado 28, de 150 cm de largo, su accesorio es un farolito.  
Para esta bici tenemos: altura 99, velocidad de crucero 34, carga 0, peso 15 (14 de la bici + 1 del farolito), tiene luz.
* una bici rodado 20, largo 90 cm, su accesorio es un morral de largo 6 y sin ojo de gato.  
Para esta bici tenemos: altura 75, velocidad de crucero 22, carga 2, peso 12 (10 de la bici + 2 del morral), no tiene luz.
* una bici rodado 20, largo 90 cm, su accesorio es un morral de largo 15 y con ojo de gato.  
Para esta bici tenemos: altura 75, velocidad de crucero 22, carga 5, peso 12 (10 de la bici + 2 del morral), tiene luz.


## 3. Bicis con varios accesorios
En esta versión, contemplar que cada bicicleta tiene **varios** accesorios. 

Algunas de las definiciones sobre una bici cambian levemente:
- _carga_: es la _suma_ de la carga que puede llevar cada accesorio.
- _peso_: es la suma de `rodado / 2` más el _peso total_ de los accesorios.
- _tieneLuz_: es verdadero si _al menos uno_ de los accesorios es luminoso.

Agregar un método para consultar la _cantidad de accesorios livianos_ de una bici, o sea, la cantidad de accesorios cuyo peso es menor o igual a 1 kg.

Para una bici rodado 26, largo 110 cm, cuyos accesorios son dos canastos, con volúmenes 10 y 30 respectivamente, tenemos: 
altura 93, velocidad de crucero 28, peso 17 (13 de la bici, 4 de los canastos), carga 80, no tiene luz, y 1 accesorio liviano (el canasto de volumen 10).

Para una bici rodado 26, largo 110 cm, cuyos accesorios son tres morrales, uno de largo 12 sin ojo de gato, otro de largo 9 sin ojo de gato, y otro de largo 21 con ojo de gato, tenemos: 
altura 93, velocidad de crucero 28, peso 19 (13 de la bici, 6 de los morrales), carga 14, tiene luz, y ningún accesorio liviano.

### ¡¡Atención!!
Para bicis con accesorios de distinto tipo (p.ej. un morral y un canasto), el programa va a dar _BOOM_ porque Gobstones no acepta que una lista tenga elementos de distinto tipo. 

No importa: ya veremos que en otros lenguajes esto no es problema.

<br/>
























