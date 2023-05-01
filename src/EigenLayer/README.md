# AUDITORIA ACTUAL: EigenLayer

## LINK: https://code4rena.com/contests/2023-04-eigenlayer-contest

## Descripcion:

EigenLayer es un protocolo que permite recuperar (restaking) el ETH comproletido (staking), para utilizarlo como seguridad criptoeconómica para protocolos y aplicaciones descentralizados.

```Staking es el acto de dejar bloqueadas en depósito criptomonedas para recibir recompensas. Normalmente, esos depósitos se hacen en la propia Blockchain (por ejemplo Ethereum) y se usan para respaldar las operaciones de la red.```

EigenLayer permite recuperar ese ETH comprometido para hacer staking pero usando una app Middleware, es decir, en lugar de depositar en la blockchain directamente, se deposita en un fondo de una empresa que ofrece serviciod adicionales.

EigenLayer ofrece seguridad en ese tipo de operaciones de forma que la empresa Middleware no sea capaz de generar una estafa a los depositantes.

## GAS SAVING:

### 1.- **Uso de `memory` o `storage` para `structs`**

1.1.- Un struct es una variable con varios campos, por ejemplo:


    struct RRIterator {
        bytes data;
        uint256 offset;
        uint16 dnstype;
        uint16 class;
        uint32 ttl;
        uint256 rdataOffset;
        uint256 nextOffset;
    }

1.2.- Posteriormente, se usa en una función, por ejemplo:


    function iterateRRs(bytes memory self, uint256 offset) internal pure returns (RRIterator memory ret) {
        ret.data = self;
        ret.nextOffset = offset;
        next(ret);
    }

1.3.- Como se ve, se llama al struct `RRIterator` como `RRIterator memory ret`.

1.4.- Buscar la palabra struct y apuntar la palabra que va a continuacion, p.e., `RRIterator`.

1.5.- Buscar esa palabra `RRIterator` en el resto del contrato, dentro de una funcion posiblemente, apuntar la linea.

1.6.- La vulnerabilidad: Si se usan todos los campos del struct hay que llamarla como `RRIterator memory ret` y, si no, `RRIterator storage ret` para ahorrar gas.

### 2.- **Vulnerabilidad 6: buscar `¡++`**

2.1.- Buscar `i++` ó `i--` ya que debe sustituirse por `++i` ó `--i`, ya que ahorra gas.

2.2.- Anotar la linea.

### 3.-  **Buscar la palabra `abi.encode`**

3.1.- Buscar `abi.encode` ya que debe sustituirse por abi.encodepacked para ahorrar 100 gas.

3.2.- Anotar la linea.

### 4.- **Buscar la palabra `emit`**

4.1.- Buscar la palabra `emit`

4.2.- Si, entre los () hay una palabra en mayúsculas, apuntar la linea.

4.3.- Ejemplo: `emit(aaa, bbb, CCCC, ddd);`

## LOW RISK:

## MEDIUM RISK:

## HIGH RISK:

1.- **Buscar las palabras `transferFrom`  o `safeTransferFrom`**

1.1.- Buscar `transferFrom`  o `safeTransferFrom`

1.2.- Anotar la linea.

1.3.- La vulnerabilidad viene cuando el `_from`no es el `msg.sender`



