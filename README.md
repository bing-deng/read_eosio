
## 阅读 eosio 源代码

#### [eosjs](https://github.com/EOSIO/eosjs)
* src 下文件
```

-- eosjs-api-interfaces.ts
-- eosjs-api.ts
-- eosjs-ecc.d.ts
-- eosjs-jsonrpc.ts
-- eosjs-jssig.ts
-- eosjs-numeric.ts
-- eosjs-rpc-interfaces.ts # 定义rpc 接口返回数据结构
-- eosjs-rpcerror.ts
-- eosjs-serialize.ts
-- index.ts
-- ripemd.es5.js
-- ripemd.js
-- rpc-web.ts
-- tests
-- transaction.abi.json
```
* eosjs-rpc-interfaces.ts 文件中包含 rpc 定义的数据结构如

```


/** Return value of `/v1/chain/get_info` */
export interface GetInfoResult {
    server_version: string;
    chain_id: string;
    head_block_num: number;
    last_irreversible_block_num: number;
    last_irreversible_block_id: string;
    head_block_id: string;
    head_block_time: string;
    head_block_producer: string;
    virtual_block_cpu_limit: number;
    virtual_block_net_limit: number;
    block_cpu_limit: number;
    block_net_limit: number;
}
```
