
## 阅读 eosjs 源代码

#### [eosjs](https://github.com/EOSIO/eosjs)
> eosjs 使用 TypeScript 。
> 依赖库 有 eos-ecc 和 text-eoncoding。
> eos-ecc 是椭圆曲线加密的js实现 ,提供了在js 环境中的 加密相关功能，如通过私钥获取公约、 随机生成公私钥等。
> srouce 中主要的文件是 ``eosjs-api.js`` 和 ``eosjs-josnrpc.ts`` 两个文件

#### 支持范围
* 浏览器 支持
* nodejs 支持
* react-native 不支持，（依赖库 eos-ecc 不支持React-native ）,参考下文 ref 有个fork 的仓库 支持 React-natve

#### docs 目录
 * ``2.-Transaction-Examples.md``  使用 `` api.transact`` 交易的写法
 *  `` 3.-Browsers.md`` 浏览器里如何使用 eosjs
 *  `` 4.-Reading blockchain-Examples.md `` 如何获取eos链上数据 列举了 ``get_table_rows`` ``get_currency_balance`` `` get_account`` 的使用范例

####  src 文件

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

*  导出 可用的模块有

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


#### *-interfaces.ts 中定义了 数据结构
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


#### ref
* [eosjs-ecc](https://github.com/EOSIO/eosjs-ecc)
* [支持Reat-native 版本的eosjs](https://github.com/Game-X-Coin/eosjs-rn)

# EOSIO
