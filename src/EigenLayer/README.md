# AUDITORIA ACTUAL: EigenLayer

## LINK: https://code4rena.com/contests/2023-04-eigenlayer-contest

## Descripcion:

EigenLayer es un protocolo que permite recuperar (restaking) el ETH comproletido (staking), para utilizarlo como seguridad criptoeconómica para protocolos y aplicaciones descentralizados.

```Staking es el acto de dejar bloqueadas en depósito criptomonedas para recibir recompensas. Normalmente, esos depósitos se hacen en la propia Blockchain (por ejemplo Ethereum) y se usan para respaldar las operaciones de la red.```

EigenLayer permite recuperar ese ETH comprometido para hacer staking pero usando una app Middleware, es decir, en lugar de depositar en la blockchain directamente, se deposita en un fondo de una empresa que ofrece serviciod adicionales.

EigenLayer ofrece seguridad en ese tipo de operaciones de forma que la empresa Middleware no sea capaz de generar una estafa a los depositantes.

## Vulnerabilidades de ahorro de GAS: 

### 1 - Uso de "memory" o "storage" para "structs"

   Un struct es una variable con varios campos, por ejemplo:

```
    struct RRIterator {
        bytes data;
        uint256 offset;
        uint16 dnstype;
        uint16 class;
        uint32 ttl;
        uint256 rdataOffset;
        uint256 nextOffset;
    }
```


    Posteriormente, se usa en una función, por ejemplo:
```
    function iterateRRs(bytes memory self, uint256 offset) internal pure returns (RRIterator memory ret) {
        ret.data = self;
        ret.nextOffset = offset;
        next(ret);
    }
```

    Como se ve, se llama al struct RRIterator como ```RRIterator memory ret```

    Hay que Buscar la palabra "struct" y apuntar la palabra que va a continuacion, que es el nombre del "struct", p.e. "RRIterator"

    Ahora hay que buscar esa palabra en el resto del contrato, dentro de una funcion posiblemente, apuntar la linea.

    La vulnerabilidad: Si se usan todos los campos del struct hay que llamarla como ```RRIterator memory ret``` y, si no, ```RRIterator storage ret``` para ahorrar gas.