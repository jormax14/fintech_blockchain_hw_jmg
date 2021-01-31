## proof_of_work
- navigate to location with geth & tools and run puppeth to create genesis block.
~~~
./puppeth
~~~
- once genesis block configuration done, export the configuration into json file.
~~~
jmgcoin.json
~~~
- now need to use geth to create data directory for each node where keystore folder will house node's addresses.
~~~
./geth account new --datadir node1
./geth account new --datadir node2
~~~
- then get will be used to initialize the nodes via the exported json file which contains the information about the genesis block for jmgcoin.
~~~
./geth init jmgcoin.json --datadir node1
./geth init jmgcoin.json --datadir node2
~~~
- now it is time to mine by getting node 1 going...
~~~
./geth --datadir node1 --mine --minerthreads 1
~~~
- ...and then get node 2 going and being sure to pass the enode from node 1 into the command.
~~~
./geth --datadir node2 --port 30304 --rpc --bootnodes "enode://9fabe70f8250181d2eb8659c55570c22e1ef24da4138275661facd59464624c1d033804b1addb635b42c95a582a41f8aa74b2976669b42d0a71cce2abd96e2f3@127.0.0.1:30303" --ipcdisable
~~~
- finally it is off to the races with creating a custom node in mycrypto and accessing you wallet with the private key.