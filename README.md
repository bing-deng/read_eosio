
## 阅读 eosio 源代码

#### [eosjs](https://github.com/EOSIO/eosjs)

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
