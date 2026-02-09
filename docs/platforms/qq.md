# QQ 机器人配置指南

## 1. 账号注册与登录
1.  访问 [QQ 开放平台官网](https://q.qq.com/)。
  **注意**：无法直接使用普通 QQ 账号登录，请先在页面完成 **开发者账号注册**。
  **实名校验**：设置超级管理员时，姓名、身份证号必须与手机号实名信息一致，且绑定的 QQ 号也需与手机号匹配。
  ![](/docs/assets/qq_create_1.png)
    创建完成后使用绑定的 QQ 号登录。
## 2. 创建机器人
1.  进入后台，选择 **“机器人”** 页签，点击 **“创建机器人”**。
![](/docs/assets/qq_create_2.png)

2.  配置名称、头像等基本信息后点击确认，提交创建。
![](/docs/assets/qq_create_3.png)

3.  点击创建的机器人，进入机器人详情页

## 3. 沙箱环境配置 (无需发布即可使用)

### 启用沙箱模式
1.  在左侧菜单选择 **“开发” -> “沙箱配置”**。
2.  在“消息列表配置”中点击 **“添加成员”**，添加自己的QQ。
![](/docs/assets/qq_create_4.png)
3.  点击右侧的 **“二维码”**，使用手机 QQ 扫码。
4.  在手机端点击 **“添加使用”** 即可在 QQ 好友列表中看到该机器人。
![](/docs/assets/qq_create_5.jpg)


## 4. 获取开发凭证 (AppID & AppSecret)
1.  点击创建的机器人，进入机器人详情页，点击左侧菜单 **“管理” -> “开发管理”**。
2.  **AppID**：直接点击右侧“复制”即可获取。
3.  **AppSecret**：
    *   点击“生成”按钮。
    *   使用 **超级管理员 QQ** 扫码验证身份。
    *   点击“重置”并复制生成的密钥。
    *   **注意**：AppSecret 不会明文存储，请务必妥善保存。
    ![](/docs/assets/qq_create_6.png)
    ![](/docs/assets/qq_create_7.png)

## 5. 完成ChatAgentCore服务配置
1.  启动ChatAgentCore服务后，进入web配置管理界面[ChatAgentCore配置管理](http://localhost:36598/admin/)，填入Key和Secret后点击保存配置，与QQ建立连接。
    ![](/docs/assets/qq_create_8.png)
2.  给 QQ 机器人发送消息。
![](/docs/assets/qq_create_9.jpg)
