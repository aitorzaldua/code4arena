### 1.- Click en: https://code4rena.com/contests/2023-04-ens-contest

### 2.- Ir donde pone scope: Aquí están los contratos a vigilar.

    2.1.- Con click en cada contrato sale el código de cada uno de ellos.

    2.2.- El contrato empieza con la palabra "contract" o "library", lo anterior, no importa.

### 3.- Vulnerabilidad 1: Las variables

     3.1.- Buscar las palabras "uint" - "uint<número>" - "string" - "address" - "bytes"

    3.2.- Si están dentro de una función tal que "function(uint aaa) {}" o "function() {uint aaaa}" no se apuntan.

    3.3.- Apuntar este contrato y en qué lineas están.

    3.4.- Si están agrupadas, la notación normal es tal que "13..21", es decir, hay variables de la 13 a la 21.

### 4.- Vulnerabilidad 2: emit

    4.1.- Buscar la palabra emit

    4.2.- Si, entre los () hay una palabra en mayúsculas, apuntar la linea.

    4.3.- Ejemplo: "emit(aaa, bbb, CCCC, ddd);"

### 5.- Vulnerabilidad 3: uso de "memory" o "storage" para "structs"

    5.1.- Un struct es una variable con varios campos, por ejemplo "struct Superheroe {string name, uint age, string superpower}"

    5.2.- Buscar la palabra "struct" y apuntar la palabra que va a continuacion, que es el nombre del "struct", p.e. "Superheroe"

    5.3.- Ahora hay que buscar esa palabra en el resto del contrato, apuntar la linea.

### 6.- Vulnerabilidad 4: (this).balance puede manipularse

    6.1.- buscar en el contrato la palabra this.balance y anotar la linea.

### 7.- Vulnerabilidad 5: Buscar abi.encode

    7.1.- Buscar abi.encode ya que debe sustituirse por abi.encodepacked para ahorrar 100 gas.

    7.2.- Anotar la linea.

### 8.- Vulnerabilidad 6: buscar ¡++

     8.1.- Buscar i++ ó i-- ya que debe sustituirse por ++i ó --i, ya que ahorra gas.

     8.2.- Anotar la linea.



