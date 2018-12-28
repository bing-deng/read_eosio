
## 阅读 eosjs 源代码

#### [eosjs](https://github.com/EOSIO/eosjs)
> eosjs 使用 TypeScript 
> 依赖库 有 eos-ecc 和 text-eoncoding
> eos-ecc 是椭圆曲线加密的js实现 ,提供了在js 环境中的 加密相关功能，如通过私钥获取公约、 随机生成公私钥等

#####  src 文件

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

##### index.ts

*  导出 可用的类有

```
export { Api, ApiInterfaces, JsonRpc, RpcInterfaces, RpcError, Serialize };
```

##### Api 即 eosjs-api.js  

* Api 的构造方法里的参数有  ``rp`` , ``authorityProvider`` , ``abiProvider`` , ``signatureProvide`` , ``chainId`` , ``textEncoder`` , ``textDecoder`` ,
* `` transact`` 方法是 核心方法，用法发送 交易。

```
public async transact(transaction: any, { broadcast = true, sign = true, blocksBehind, expireSeconds }:
``` 

##### [JsonRpc 即 eosjs-jsonrpc.ts](https://github.com/EOSIO/eosjs/blob/master/src/eosjs-jsonrpc.ts)

* JsonRpc 定义了 rpc 方法对用的链上的的操作 如下，请求 http://endpoit/v1/chain/get_account 和 rpc.get_account 是一样的效果（有参数）。

```
/** Raw call to `/v1/chain/get_account` */
// tslint:disable-next-line:variable-name
public async get_account(account_name: string): Promise<any> {
    return await this.fetch("/v1/chain/get_account", { account_name });
}
```


##### *-interfaces.ts 中定义了 数据结构
* 如eosjs-rpc-interfaces.ts 文件中包含 rpc 定义的数据结构如

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
