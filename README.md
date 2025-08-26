# sftp-test

快速免费搭建临时 SFTP 服务，用于开发测试环境中的 SFTP 连接与文件上传下载测试。

⚠️ 仅供开发测试使用，请勿用于生产或商业用途。

---

## 🚀 使用步骤

### 1. Fork 本仓库

点击右上角 **Fork**，将仓库复制到你的 GitHub 账号下。

---

### 2. 注册 ngrok 并获取 Authtoken

1. 访问 [ngrok 注册页面](https://dashboard.ngrok.com/)，使用 GitHub / Google 或邮箱注册。
2. 登录后绑定信用卡（仅验证身份，不扣费）。
3. 进入 [获取 Authtoken 页面](https://dashboard.ngrok.com/get-started/your-authtoken)，复制你的 **ngrok Authtoken**。

---

### 3. 配置 GitHub Secrets

1. 进入你 Fork 的仓库，点击 **Settings → Secrets and variables → Actions**。
2. 点击 **New repository secret**。
3. 填写：
   - **Name**: `NGROK_AUTH_TOKEN`
   - **Value**: 你的 ngrok Authtoken
4. 点击 **Add secret**。

---

### 4. 运行工作流，获取 SFTP 信息

1. 进入仓库 **Actions** 标签，找到 **SFTP Server with Ngrok** 工作流，点击 **Run workflow**。
2. 选择分支（如 `main`），运行工作流。
3. 等待执行完成（约 1～3 分钟）。
4. 在工作流日志中查看 SFTP 登录信息：
   - 用户名（如 `testuser`）
   - 密码（如 `testpassword`）
   - ngrok 公网地址（如：`4.tcp.ngrok.io:10741`）

![](https://s3.xuehappy.com/2025/08/a839f62259ae8fb19d4507bbf5a39e81.png)
### 5.测试连接

示例连接命令：
```shell
sftp -P 10741 testuser@4.tcp.ngrok.io
```
![](https://s3.xuehappy.com/2025/08/e8886cf14b3932bc027c07dadbc5fedf.png)


## ⏳ 注意事项

- 服务运行约 **30 分钟后自动停止**，请及时测试。
- 如需再次使用，请重新运行工作流。
- 默认账号信息以工作流日志输出为准。
- ngrok 免费版有连接时长等限制。

---

## 📌 免责声明

仅供学习测试，禁止商用或非法使用。使用风险自负，请遵守 ngrok 服务条款。