# RustChain Node API 文档

本目录包含 RustChain 节点 API 的 OpenAPI/Swagger 文档。

## 文件说明

- `openapi.yaml` - OpenAPI 3.0 规范文件
- `swagger.html` - 自包含的 Swagger UI 页面

## 使用方法

### 查看 API 文档

直接在浏览器中打开 `swagger.html` 文件即可查看交互式 API 文档。

或者使用 Python 启动一个简单的 HTTP 服务器：

```bash
cd docs/api
python3 -m http.server 8000
```

然后在浏览器中访问：http://localhost:8000/swagger.html

### 验证 OpenAPI 规范

使用 swagger-cli 验证 openapi.yaml 文件：

```bash
npm install -g @redocly/cli
redocly lint openapi.yaml
```

### 在 Swagger UI 中测试端点

1. 打开 `swagger.html`
2. 点击任意端点展开详情
3. 点击 "Try it out" 按钮
4. 填写参数（如需要）
5. 点击 "Execute" 发送请求

## API 端点概览

### 公开端点（无需认证）

| 端点 | 方法 | 描述 |
|------|------|------|
| `/health` | GET | 节点健康检查 |
| `/ready` | GET | 就绪探针 |
| `/epoch` | GET | 当前纪元信息 |
| `/api/miners` | GET | 活跃矿工列表 |
| `/api/stats` | GET | 网络统计 |
| `/api/hall_of_fame` | GET | 名人堂排行榜 |
| `/api/fee_pool` | GET | RIP-301 费用池 |
| `/balance` | GET | 矿工余额查询 |
| `/lottery/eligibility` | GET | 纪元资格检查 |
| `/explorer` | GET | 区块浏览器 |

### 认证端点（需要 X-Admin-Key）

| 端点 | 方法 | 描述 |
|------|------|------|
| `/attest/submit` | POST | 提交硬件认证 |
| `/wallet/transfer/signed` | POST | Ed25519 签名转账 |
| `/wallet/transfer` | POST | 管理员转账 |
| `/withdraw/request` | POST | 提现请求 |

## 贡献

如需更新 API 文档，请修改 `openapi.yaml` 文件，然后重新生成 `swagger.html`。

## 参考

- Issue: https://github.com/Scottcjn/rustchain-bounties/issues/502
- RustChain 仓库：https://github.com/Scottcjn/Rustchain
- 实时节点：https://rustchain.org
