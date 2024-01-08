https://besu.hyperledger.org/private-networks/tutorials/qbft

Terminal > cd Node-1 > 
besu --data-path=data --genesis-file=../genesis.json --rpc-http-enabled --rpc-http-api=ETH,NET,QBFT --host-allowlist="*" --rpc-http-cors-origins="all"
> Retrieve the enode for Node-1
enode://739a537732a1f15d369f2c48071e31d573964670921db9e47b14d44aa2c81aa21b57600bb2d7ee4dd9204c81931aa8819f6f0d1405e9f4e32a7a0f524562e58a@127.0.0.1:30303

New Terminal > cd Node-2 >
besu --data-path=data --genesis-file=/Users/weihan/Desktop/Blockchain/genesis.json --bootnodes=enode://739a537732a1f15d369f2c48071e31d573964670921db9e47b14d44aa2c81aa21b57600bb2d7ee4dd9204c81931aa8819f6f0d1405e9f4e32a7a0f524562e58a@127.0.0.1:30303 --p2p-port=30304 --rpc-http-enabled --rpc-http-api=ETH,NET,QBFT --host-allowlist="*" --rpc-http-cors-origins="all" --rpc-http-port=8546

New Terminal > cd Node-3 >
besu --data-path=data --genesis-file=/Users/weihan/Desktop/Blockchain/genesis.json --bootnodes=enode://739a537732a1f15d369f2c48071e31d573964670921db9e47b14d44aa2c81aa21b57600bb2d7ee4dd9204c81931aa8819f6f0d1405e9f4e32a7a0f524562e58a@127.0.0.1:30303 --p2p-port=30305 --rpc-http-enabled --rpc-http-api=ETH,NET,QBFT --host-allowlist="*" --rpc-http-cors-origins="all" --rpc-http-port=8547

New Terminal > cd Node-4 >
besu --data-path=data --genesis-file=/Users/weihan/Desktop/Blockchain/genesis.json --bootnodes=enode://739a537732a1f15d369f2c48071e31d573964670921db9e47b14d44aa2c81aa21b57600bb2d7ee4dd9204c81931aa8819f6f0d1405e9f4e32a7a0f524562e58a@127.0.0.1:30303 --p2p-port=30306 --rpc-http-enabled --rpc-http-api=ETH,NET,QBFT --host-allowlist="*" --rpc-http-cors-origins="all" --rpc-http-port=8548


Confirm the private network is working > 
curl -X POST --data '{"jsonrpc":"2.0","method":"qbft_getValidatorsByBlockNumber","params":["latest"], "id":1}' localhost:8545

{
    "jsonrpc":"2.0",
    "id":1,
    "result":[
        "0x10165df0299415ff30e47dd079d8e406745c35ec",
        "0xa77fa22ab0daa4ed54e055d8f2c3a3eb4e41760c",
        "0xdd9c64f795c60c0fd80a9b92b4494a571b016593",
        "0xff36fc9d7a0f0285cd0f088163d94270f487e85f"
    ]
}   