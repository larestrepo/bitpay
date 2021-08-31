# Instrucciones para crear BTCpayserver

## Prerequisitos

Instancia de Linux con seguridad básica

## Configurar el dominio

Domain name: bit2cash.org
Host: dynadot

## Instalar BTCPayServer

Las instrucciones detalladas están en 

https://docs.btcpayserver.org/Docker/

```sh

# Login as root
sudo su -

# Create a folder for BTCPay
mkdir BTCPayServer
cd BTCPayServer

# Clone this repository
git clone https://github.com/btcpayserver/btcpayserver-docker
cd btcpayserver-docker

# Run btcpay-setup.sh with the right parameters
export BTCPAY_HOST="btcpay.EXAMPLE.com"
export NBITCOIN_NETWORK="mainnet"
export BTCPAYGEN_CRYPTO1="btc"
export BTCPAYGEN_ADDITIONAL_FRAGMENTS="opt-save-storage"
export BTCPAYGEN_REVERSEPROXY="nginx"
export BTCPAYGEN_LIGHTNING="clightning"
export BTCPAY_ENABLE_SSH=true
. ./btcpay-setup.sh -i
```

Lo que hace btcpay-setup.sh es instalar docker, instalar docker-compose, configurar systemd para btcpayserver, setear las variables de ambiente y arrancar el nodo. 

Cada vez que se quiera hacer una actualización se debe correr este ejecutable, teniendo en cuenta las variables de ambiente. Explicación detallada aparece en el link de la página.

## Las variables de ambiente utilizadas son:

### Para testnet

    export BTCPAY_HOST="bit2cash.org"
    export NBITCOIN_NETWORK="testnet"
    export BTCPAYGEN_CRYPTO1="btc"
    export BTCPAYGEN_LIGHTNING="lnd"
    export LIGHTNING_ALIAS="bit2cash"
    export BTCPAYGEN_ADDITIONAL_FRAGMENTS="opt-add-thunderhub;opt-save-storage-s"
    export BTCPAYGEN_REVERSEPROXY="nginx"
    export BTCPAY_ENABLE_SSH=true

### Para mainnet

    export BTCPAY_HOST="bit2cash.net"
    export NBITCOIN_NETWORK="mainnet"
    export BTCPAYGEN_CRYPTO1="btc"
    export BTCPAYGEN_LIGHTNING="lnd"
    export LIGHTNING_ALIAS="bit2cash"
    export BTCPAYGEN_ADDITIONAL_FRAGMENTS="opt-add-thunderhub;opt-save-storage"
    export BTCPAYGEN_REVERSEPROXY="nginx"
    export BTCPAY_ENABLE_SSH=true

BTCPAYGEN_ADDITIONAL_FRAGMENTS opción máxima de 100GB que mantiene hasta 1 año histórico. 
BTCPAYGEN_LIGHTNING opción lnd.


# Mantenimiento al servidor


    apt update
    apt upgrade -y

En la carpeta de Btc docker, hacer git pull para verificar actualizaciones. 

Setear nuevamente variables de ambiente (ejemplo, verificar si es mainnet o testnet) y correr el ejecutable. 
