# 飞书机器人配置指南 (Feishu)

## 1. 创建企业自建应用
1.  访问 [飞书开发者平台](https://open.feishu.cn/)。
2.  点击 **“创建企业自建应用”**。
![](/docs/assets/feishu_create_1.png)
3.  配置应用名称、描述及图标，点击 **“创建”**。
![](/docs/assets/feishu_create_2.png)

## 2. 添加机器人能力
1.  在左侧目录树选择 **“应用能力” -> “添加应用能力”**。
2.  选择 **“按能力添加”** 页签，点击 **“机器人”** 能力卡片的 **“添加”** 按钮。
![](/docs/assets/feishu_bot_1.png)

## 3. 配置权限 (推荐快捷导入)
为了确保 AI 助手功能完整，建议一次性配置所需权限：
1.  在左侧目录树选择 **“开发配置” -> “权限管理”-> “批量导入/导出权限”** 按钮。
![](/docs/assets/feishu_config_1.png)
2.  在 **“导入”** 页签中，将以下 JSON 替换原有示例：

```json
{
  "scopes": {
    "tenant": [
      "im:chat:read",
      "im:chat:update",
      "im:message.group_at_msg:readonly",
      "im:message.p2p_msg:readonly",
      "im:message.pins:read",
      "im:message.pins:write_only",
      "im:message.reactions:read",
      "im:message.reactions:write_only",
      "im:message:readonly",
      "im:message:recall",
      "im:message:send_as_bot",
      "im:message:send_multi_users",
      "im:message:send_sys_msg",
      "im:message:update",
      "im:resource"
    ],
    "user": [
      "contact:user.employee_id:readonly"
    ]
  }
}
```
![](/docs/assets/feishu_config_2.png)
3.  点击 **“下一步，确认新增权限”**，并在弹窗中点击 **“申请开通”**。
![](/docs/assets/feishu_config_3.png)

## 4. 获取配置信息
1.  在左侧目录树选择 **“基础信息” -> “凭证与基础信息”**。
2.  在 **“应用凭证”** 模块中，记录 **App ID** 和 **App Secret** (将用于 ChatAgentCore 的配置)。
![](/docs/assets/feishu_config_4.png)

## 5. 完成ChatAgentCore服务配置
1.  启动ChatAgentCore服务后，进入web配置管理界面[ChatAgentCore配置管理](http://localhost:36598/admin/)，填入Key和Secret后点击保存配置，与飞书建立连接。
    ![](/docs/assets/feishu_config_5.png)

## 6. 配置事件订阅 (关键)
1.  在左侧目录树选择 **“开发配置” -> “事件与回调”**。
![](/docs/assets/feishu_config_6.png)
2.  **事件订阅方式**：选择 **“使用长连接接收事件”** (WebSocket)。
![](/docs/assets/feishu_config_7.png)
3.  点击 **“添加事件”**，搜索 `im.message.receive_v1` ，添加接收消息事件后，点击右下角的确认添加。
![](/docs/assets/feishu_config_8.png)

## 7. 发布应用
1.  点击顶部的 **“创建版本”** 按钮。
![](/docs/assets/feishu_config_9.png)
2.  按需配置应用版本号（如 `1.0.0`）、默认能力及更新说明，然后点击保存按钮。
![](/docs/assets/feishu_config_10.png)
3.  点击页面右上角的 **“确认发布”**，完成应用发布。
![](/docs/assets/feishu_config_11.png)

## 8. 使用UOSAI助手
1.  在开发者小助手中会收到应用发布成功的消息，打开应用后发送消息。
![](/docs/assets/feishu_ai_1.jpg)
![](/docs/assets/feishu_ai_2.jpg)
