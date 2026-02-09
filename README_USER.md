# ChatAgentCore 用户使用指南 🚀

欢迎使用 ChatAgentCore！本工具是 **uos-ai** 的多平台扩展服务组件，通过它您可以轻松将 AI 助手接入飞书、钉钉、QQ 等聊天平台。

---

## 🛠 第一步：环境准备

1.  **安装 uos-ai**：确保您的系统中已安装 **uos-ai**。
    **skills**和**mcp**在uos-ai应用中配置，默认使用全部。
2.  **协作模式**：ChatAgentCore 作为一个独立的中间件服务运行。

---

## 🏃 第二步：启动服务

根据您的使用环境选择以下方式之一：

### 1. 直接启动二进制 (推荐)
适用于 **deepin 25** 操作系统，直接执行打包后的二进制文件：
```bash
./chatagent-service
```

### 2. 通过 Python 源码启动
如果您处于开发环境，可以直接通过 Python 运行：
```bash
# 安装依赖
pip install -r requirements.txt
# 启动服务
python3 main.py
```

### 3. 自行编译打包
如果您需要自行构建二进制文件，可以使用提供的打包脚本：
```bash
bash build.sh
```
执行后可在 `dist/` 目录找到生成的二进制文件。

### 4. 作为系统服务运行 (Linux/Deepin)
如果您希望程序开机自启且在后台静默运行：
```bash
sudo cp deploy/chatagent.service /etc/systemd/system/
sudo systemctl enable --now chatagent
```
---

## ⚙️ 第三步：可视化配置

您**不需要**手动修改任何配置文件。

1.  **访问后台**：在浏览器打开 [http://127.0.0.1:36598/admin](http://127.0.0.1:36598/admin)
2.  **配置机器人**：
    *   找到您要接入的平台（飞书/钉钉/QQ）。
    *   开启该平台的开关。
    *   填入对应的 `App ID`、`App Secret` 或 `Token` 等凭证信息。

    *平台配置指南*
      - **[飞书 (Feishu) 配置指南](docs/platforms/feishu.md)**
      - **[钉钉 (DingTalk) 配置指南](docs/platforms/dingtalk.md)**
      - **[QQ 机器人配置指南](docs/platforms/qq.md)**
3.  **即时生效**：点击“保存配置”。系统会自动热重载，机器人将立即在对应平台上线。

---

## 💬 第四步：开始对话

- **私聊/群聊**：在聊天平台中直接发消息或 @机器人。
- **消息流转**：
  用户消息 ➔ ChatAgentCore ➔ uos-ai智能体 ➔ ChatAgentCore ➔ 返回结果

---

## ❓ 常见问题

- **Q: 启动后立即退出，报错“端口被占用”？**
  - A: 默认使用 36598 端口，如果被占用，请使用 `./chatagent-service --port 19000` 启动。
- **Q: 机器人在线但无法回复？**
  - A: 请确保在机器人开放平台中已经正确配置了“事件订阅”或“消息接收权限”。

---

祝您使用愉快！如有技术问题请参考项目完整文档。