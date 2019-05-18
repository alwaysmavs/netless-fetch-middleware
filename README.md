# @netless/fetch-middleware

> 一个带有请求超时功能的 fetch 中间件，方便大家做异常流程处理。

[![NPM](https://img.shields.io/npm/v/netless-fetch-middleware.svg)](https://www.npmjs.com/package/netless-fetch-middleware) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

## 1. 说明

本项目技术选型为：`React` `Typescript `
打包工具为： `rollup`  



## 2. 安装

```bash
npm install --save @netless/fetch-middleware

或者

yarn add @netless/fetch-middleware
```


## 3. 接口说明

| 初始化参数   | 说明              | 类型   | 默认值 |
| :----------- | :---------------- | :----- | :----: |
| fetchTimeout | 请超时的时间 (ms) | number | 15000  |
| apiOrigin    | api 的域名        | string |        |

```typescript
const fetcher = new Fetcher(5000, "https://cloudcapiv4.herewhite.com");
```

**自定义类型**

```typescript
export type FetcherParams = {
  path: string;
  body?: Object | RequestInit["body"];
  query?: Object;
  headers?: HeadersInit;
};
```

| 成员方法 | 方法参数类型  |
| :------- | :------------ |
| get      | FetcherParams |
| post     | FetcherParams |
| put      | FetcherParams |
| delete   | FetcherParams |

```typescript
 const json = await fetcher.post<any>({
            path: `room/xxxxxxxxxx`,
            query: {
                token: "xxxxxxxxxx",
            },
            body: {
                name: name,
                limit: limit,
                mode: mode,
            },
        });
```



## 4. 使用概览

```typescript
import Fetcher from "@netless/fetch-middleware";
const fetcher = new Fetcher(5000, "https://cloudcapiv4.herewhite.com");

export class RoomOperator {

    public async createRoomApi(name: string, limit: number, mode: RoomType): Promise<any> {
        const json = await fetcher.post<any>({
            path: `room/xxxxxxxxxx`,
            query: {
                token: "xxxxxxxxxx",
            },
            body: {
                name: name,
                limit: limit,
                mode: mode,
            },
        });
        return json as any;
    }
}
```



## License

MIT © [alwaysmavs](https://github.com/alwaysmavs)
