# 钉钉机器人配置指南 (DingTalk)

## 1. 创建钉钉应用
1.  登录 [钉钉开放平台](https://open-dev.dingtalk.com/)，开始创建应用。
    注意： 创建钉钉应用需要确保您的钉钉账号拥有有开发者权限。
    ![](/docs/assets/dingtalk_create.png)

2.  在左侧目录树中选择 **“企业内部应用” -> “钉钉应用”  -> “点击创建应用”**。
    ![](/docs/assets/dingtalk_create_1.png)

3.  填写应用名称、图标等信息后保存。
    ![](/docs/assets/dingtalk_create_2.png)

4.  添加机器人。
    ![](/docs/assets/dingtalk_add_bot.png)

5.  点击按钮，开始进入机器人配置。
    ![](/docs/assets/dingtalk_bot_config.png)

6.  添加简介、描述和预览图后点击发布按钮。
    注意： 消息接收模式选择Stream模式。
    ![](/docs/assets/dingtalk_bot_config_1.png)

## 2. 创建消息卡片
1.  登录 [卡片平台](https://open-dev.dingtalk.com/fe/card)。
2.  在左侧选择 **“模板管理” -> “新建模板”**。
    配置模板信息：
    *   **卡片类型**：选择“消息卡片”。
    *   **卡片模板场景**：选择“AI 卡片”。
    *   **关联应用**：选择刚才创建的钉钉应用。

    ![](/docs/assets/dingtalk_card_1.png)
4.  进入卡片模板编辑页面，无需任何操作，依次点击 **“保存”** 和 **“发布”**。
    ![](/docs/assets/dingtalk_card_2.png)

## 3. 授予应用必要权限
1.  依次点击 **“应用开发” -> “钉钉应用”**。
    点击应用名称进入应用详情页。
    ![](/docs/assets/dingtalk_bot_set.png)

2.  在左侧选择 **“开发配置” -> “权限管理”**。
    搜索并申请以下权限：
    *   搜索 `Card`：勾选 **“互动卡片实例写权限”** 和 **“AI卡片流式更新权限”**，点击批量申请。
    ![](/docs/assets/dingtalk_bot_set_1.png)
    *   搜索 `qyapi_robot_sendmsg`：开通 **“企业内机器人发送消息权限”**。
    ![](/docs/assets/dingtalk_bot_set_2.png)

## 3. 发布应用版本
1.  在左侧选择 **“应用发布” -> “版本管理与发布”*，点击 **“创建新版本”**。
    ![](/docs/assets/dingtalk_bot_set_4.png)

2.  配置版本号及可见范围。
    点击 **“保存”** 并点击 **“确认发布”**。
    ![](/docs/assets/dingtalk_bot_set_5.png)
    ![](/docs/assets/dingtalk_bot_set_6.png)

## 4. 获取凭证信息
1.  在左侧选择 **“基础信息” -> “凭证与基础信息”**。
    复制保存 **Client ID** (对应配置中的 AppKey) 和 **Client Secret** (对应 AppSecret)。
    ![](/docs/assets/dingtalk_bot_set_3.png)

## 5. 完成ChatAgentCore服务配置
1.  启动ChatAgentCore服务后，进入web配置管理界面[ChatAgentCore配置管理](http://localhost:36598/admin/)，填入Key和Secret后点击保存配置，与钉钉建立连接。
    ![](/docs/assets/dingtalk_config.png)

## 6. 事件订阅
1.  点击 **“已完成接入，验证连接通道” -> “保存”**。
    ![](/docs/assets/dingtalk_event.png)

## 7. 使用UOSAI助手
1. 启动uos-ai。
2. 在钉钉群中与机器人对话。
![](/docs/assets/dingtalk_chat_1.jpg)
![](/docs/assets/dingtalk_chat_2.jpg)
![](/docs/assets/dingtalk_chat_3.jpg)
![](/docs/assets/dingtalk_chat_4.jpg)
![](/docs/assets/dingtalk_chat_5.jpg)
![](/docs/assets/dingtalk_chat_6.jpg)