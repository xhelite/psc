# 服务能力前置 (PSC - Pre Service Capability)

前后端分离应用，前端 Vue 3，后端 Spring Cloud。

## 项目结构

```
psc/
├── backend/          # Spring Cloud 后端
├── frontend/         # Vue 3 前端
├── pom.xml           # Maven 父工程
└── README.md
```

## 功能说明

- **上布局（1 份）**：移网手机号码、输入框、查询按钮
- **下布局（10 份）**：表格展示（序号、服务、营业、网元、操作）
- **查询**：点击查询调用后端 `/api/query` 接口，随机生成表格数据
- **同步**：点击某行「同步」按钮，调用后端 `/api/sync` 接口，将网元列同步为营业列，操作列变为「一致（灰色）」

## IDEA 导入

1. 使用 IntelliJ IDEA 打开 `psc` 目录（选择根目录下的 `pom.xml`）
2. 等待 Maven 依赖下载完成
3. 前端需在 `frontend` 目录单独执行 `npm install`

## 启动方式

### 1. 启动后端

```bash
cd psc/backend
mvn spring-boot:run
```

后端默认端口：8080

### 2. 启动前端

```bash
cd psc/frontend
npm install
npm run dev
```

前端默认端口：5173，已配置代理转发 `/api` 到后端。

### 3. 访问

浏览器打开：http://localhost:5173

## 接口说明

| 接口   | 方法 | 说明                         |
|--------|------|------------------------------|
| /api/query | GET  | 查询，随机生成表格数据       |
| /api/sync  | POST | 同步，将网元列同步为营业列内容 |

## 表格样例

| 序号 | 服务 | 营业 | 网元 | 操作 |
|-----|------|------|------|------|
| 1 | 状态 | 正常 | 停机 | 同步 |
| 2 | 短信 | 开通 | 开通 | 一致（灰色）|
| 3 | 长权 | 国内 | 国际 | 同步 |
| 4 | 来显 | 开通 | 关闭 | 同步 |
