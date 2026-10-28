---
icon: material-symbols:cached-rounded
---

# LRU Cache

> Keeps cached data in memory using LRU Cache.

## Usage

**Driver name:** `lru-cache`

Keeps cached data in memory using [LRU Cache](https://www.npmjs.com/package/lru-cache).

See [`lru-cache`](https://www.npmjs.com/package/lru-cache) for supported options.

By default, [`max`](https://www.npmjs.com/package/lru-cache#max) setting is set to `1000` items.

A default behavior for [`sizeCalculation`](https://www.npmjs.com/package/lru-cache#sizecalculation) option is implemented based on buffer size of both key and value.

Items can expire individually: pass `ttl` (in seconds, like the redis driver) to `setItem`. `getMeta` returns the remaining `ttl`, and `clear(base)` only removes keys under `base`.

```js
import { createStorage } from "unstorage";
import lruCacheDriver from "unstorage/drivers/lru-cache";

const storage = createStorage({
  driver: lruCacheDriver(),
});

await storage.setItem("session:abc", { user: 1 }, { ttl: 60 });
```
