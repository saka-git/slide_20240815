---
theme: seriph
background: https://richka.co/wp-content/uploads/2020/09/anders-jilden-uwbajDCODj4-unsplash.jpg
layout: center
---

<!-- 背景画像とテキストアニメーション -->

<div
  v-motion
  :initial="{ opacity: 0, y: 50 }"
  :enter="{ opacity: 1, y: 0, transition: { delay: 500 } }"
  class="text-center text-5xl font-bold"
>
  test...　
</div>

<style>
section {
  background-image: url('https://richka.co/wp-content/uploads/2020/09/anders-jilden-uwbajDCODj4-unsplash.jpg');
  background-size: cover;
  color: #ffffff;
}
</style>

---

layout: center

---

# Honoのテスト

---

# 使うもの

- Hono(割愛)
- Vitest
- testing-library系
- @vitest/coverage-v8

---

# インストールよろしく

---

# その他設定

---

# package.json

```json
  "scripts": {
    "dev": "wrangler dev src/index.ts",
    "deploy": "wrangler deploy --minify src/index.ts",
    "test": "vitest",
    "test:watch": "vitest --watch"
  },
```

---

# vitest.config.ts

```ts
import { defineConfig } from "vitest/config";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
  test: {
    environment: "jsdom",
    setupFiles: "./setupTests.ts",
    coverage: {
      enabled: true,
    },
  },
});
```

---

# setupTests.ts

## 今回使わないけどここに設定書く

---

# まずはHono関係なくテスト

---

# テストしたいコード

```ts
import { Hono } from "hono";

const app = new Hono().get("/", (c) => {
  return c.text("Hello World");
});

export default app;
```

---

# テストコード

```ts
import app from "./index";
import { expect, describe, it } from "vitest";

describe("Testing My App", () => {
  it("Should return 200 response", async () => {
    // ここ注意"/"
    const req = new Request("http://localhost:8787/");
    const res = await app.fetch(req);
    expect(res.status).toBe(200);
    expect(await res.text()).toBe("Hello World");
  });
});
```

---

# npm run test

---

# 結果

```

 RERUN  src/sample/test1/index.ts x2

 ✓ src/sample/test1/index.test.ts (1)
   ✓ Testing My App (1)
     ✓ Should return 200 response

 Test Files  1 passed (1)
      Tests  1 passed (1)
   Start at  00:48:00
   Duration  36ms

 % Coverage report from v8
----------|---------|----------|---------|---------|-------------------
File      | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s
----------|---------|----------|---------|---------|-------------------
All files |     100 |      100 |     100 |     100 |
 index.ts |     100 |      100 |     100 |     100 |
----------|---------|----------|---------|---------|-------------------

 PASS  Waiting for file changes...
       press h to show help, press q to quit
```

---

# カバレッジでた

---

# 次はHonoを使ってみる

---

# テストしたいコード

同じ

```ts
import { Hono } from "hono";

const app = new Hono().get("/", (c) => {
  return c.text("Hello World");
});

export default app;
```

---

# テストコード

```ts {6}
import app from "./index";
import { expect, describe, it } from "vitest";

describe("Testing My App", () => {
  it("Should return 200 response", async () => {
    const res = await app.request("/");
    expect(res.status).toBe(200);
    expect(await res.text()).toBe("Hello World");
  });
});
```

---

# 変更点

```ts
const req = new Request("http://localhost:8787/");
const res = await app.fetch(req);
```

↓

```ts
const res = await app.request("/");
```

---

# 結果は割愛

---

# bodyあり、POST

---

# テストしたいコード

```ts
const app = new Hono().post("/", async (c) => {
  const data = await c.req.parseBody<{ message: string }>();
  return c.text(`Message is ${data.message}`);
});
```

---

# テストコード

```ts
it("Should return 200 response", async () => {
  const formData = new FormData();
  formData.append("message", "Hi");
  const res = await app.request("/", {
    method: "POST",
    body: formData,
  });
  expect(res.status).toBe(200);
  expect(await res.text()).toBe("Message is Hi");
});
```

---

# ヘルパー関数

---

# 型つくよ

```ts
const res = await testClient(app).foo.bar.$get();
```

---

# 比較

  <img src="/20240905/no_type.png" class="" />
  <img src="/20240905/type.png" class="" />

---

# ヘッダー

```ts
const res = await app.request("/posts", {
  method: "POST",
  body: JSON.stringify({ message: "hello hono" }),
  headers: new Headers({ "Content-Type": "application/json" }),
});
```

---

# ここ見てね

- https://hono.dev/docs/guides/testing
- https://zenn.dev/yusukebe/articles/9a6335ed793c43

---
