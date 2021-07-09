# Los siguientes son comandos útiles para ser corridos directamente en el shell con el cli de bitcoin:

Cuando se trabaja en testnet hay que espeficar la red como parámetro. Si el nodo está corriendo de forma manual especificar el usuario y contraseña que arrancaron el nodo.

Ejemplo en mainnet:

    bitcoin-cli getconnectioncount

Ejemplo en testnet sin daemon:

    bitcoin-cli -testnet -rpcuser=<user> -rpcpassword=<password> getconnectioncount

cuántas conexiones tiene el nodo actualmente

    bitcoin-cli getconnectioncount

información general y estado del nodo

    bitcoin-cli -getinfo

crear nueva billetera

    bitcoin-cli createwallet <wallet_name>

crear dirección asociada a la billetera

    bitcoin-cli getnewaddress

generar llave privada para realizar transacciones

    bitcoin-cli dumpprivkey <address>

Listar las direcciones generadas con su balance

    bitcoin-cli listreceivedbyaddress 1 true

Obtener información de la billetera
  
    bitcoin-cli getwalletinfo 

Obtener información detallada de los pares conectados al nodo

    bitcoin-cli getpeerinfo






