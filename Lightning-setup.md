# Por ahora el nodo de lighning está corriendo así.

# No está en daemon y por lo tanto en tmux

Va a estar corriendo en la sesión 0 de tmux

    tmux a -t 0

ctrl +b +d


    lnd --bitcoin.active --bitcoin.testnet --debuglevel=debug --bitcoin.node=bitcoind \
    --bitcoind.rpcuser=btcpay --bitcoind.rpcpass=btcpay --bitcoind.zmqpubrawblock=tcp://127.0.0.1:28332 \
    --bitcoind.zmqpubrawtx=tcp://127.0.0.1:28333 --externalip=167.86.126.161

# Este es el comando de base para correr el lncli

    lncli --macaroonpath=/home/btcpay/.lnd/data/chain/bitcoin/testnet/admin.macaroon
