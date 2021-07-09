# Instrucciones para configurar bitcoin core

## Luego de configurar la máquina en Ubuntu. Descargar y verificar firmas antes de descomprimir.

Por seguridad, el link del tar se debe sacar directamente de la página de bitcoincore.org

Descargar el tar y el listado de checksums

    wget https://bitcoincore.org/bin/bitcoin-core-0.21.1/bitcoin-0.21.1-x86_64-linux-gnu.tar.gz
    wget https://bitcoincore.org/bin/bitcoin-core-0.21.1/SHA256SUMS.asc

Verificar que el checksum aparezca dentro del listado, ejecutando el siguiente comando:

    sha256sum --ignore-missing --check SHA256SUMS.asc

Debería aparecer lo siguiente:

![image](https://user-images.githubusercontent.com/48094194/124680608-581cc400-de8c-11eb-86ad-14eaec912a4b.png)

Obtenga una copia de las llaves del release:

    gpg --keyserver hkp://keyserver.ubuntu.com --recv-keys 01EA5486DE18A882D4C2684590C8019E36C2E964

Verificar que el archivo haya sido igualmente firmado:

    gpg --verify SHA256SUMS.asc

Algo del siguiente estilo debe aparecer:

![image](https://user-images.githubusercontent.com/48094194/124680752-b0ec5c80-de8c-11eb-896f-feb20330083b.png)

Una vez verificado que el archivo es legítimo, descomprimirlo:

    tar xvzf bitcoin-0.21.1-x86_64-linux-gnu.tar.gz

Install bitcoin core bin files:

    sudo install -m 0755 -o root -g root -t /usr/local/bin bitcoin-0.21.1/bin/
    
    bitcoind --version

Arrancar la sincronización en la testnet

    bitcoind -testnet \
      -rpcuser=<user> -rpcpassword=<password> \
      -fallbackfee=0.0002 \
      -txindex=1 -server

Pendientes:

  - Configurar el bitcoin.config
  - Configurar logs y monitorización
  - Demonizar
  - Configurar el network
  - Correr lightning node

References:

https://netweblog.wordpress.com/2020/08/25/bitcoin-testnet-tutorial-for-developers/

https://bitcoin.org/en/full-node#configuration-tuning

https://en.bitcoinwiki.org/wiki/Bitcoind

https://stadicus.github.io/RaspiBolt/raspibolt_30_bitcoin.html

https://gist.github.com/bretton/0b22a0503a9eba09df86a23f3d625c13

Maybe later for lightning:
https://stopanddecrypt.medium.com/a-complete-beginners-guide-to-installing-a-bitcoin-full-node-on-linux-2021-edition-46bf20fbe8ff
https://gist.github.com/itoonx/95aec9a3b4da01fd1fd724dffc056963

Bitcoin github:

https://github.com/bitcoin/bitcoin

