---
Created: 22:46 29-12-2024
tags:
  - issue
---
Link relate:
- https://wagmi.sh/react/getting-started

---

TLDR: 
- Setup kết nối config wagmi , react query và với viem với eth (chain khác thì không biết)
- Tạo các cấu hình 
```js
import { http, createConfig } from 'wagmi'
import { mainnet, sepolia } from 'wagmi/chains'

export const config = createConfig({
  chains: [mainnet, sepolia],
  transports: {
    [mainnet.id]: http(),
    [sepolia.id]: http(),
  },
})
```
- Tôi vẫn chưa biết cần quan tâm tham số gì trong config nên sẽ liệt kê từ từ
	- chains : `mainnet` trong docs là chain chính của ethernium
	- transports : 
	- ....
- Khi setup một chương trình đơn giản cần 
- 