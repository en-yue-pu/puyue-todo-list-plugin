直接官网范例跑出来就这样
本身是需要plugin调用现存API的,
但是这个简单就是临时存储数据在拿出 没有用API 直接plugin内部保存

# 坑
## 1

.well-known/ai-plugin.json
```{
    "schema_version": "v1",
    "name_for_human": "puyue TODO",//不能太长
    "name_for_model": "puyuetodo",
    "description_for_human": "puyue TODO list.",//不能太长
    "description_for_model": "puyue Plugin TODO list",//不能太长
    "auth": {
      "type": "none" // 没有验证 https://techdiylife.github.io/ChatGPT-programming-handbook/contents/chat-plugins-overview.html#27-%E6%8F%92%E4%BB%B6%E8%BA%AB%E4%BB%BD%E9%AA%8C%E8%AF%81
    },
    "api": {
      "type": "openapi",
      "url": "https://puyue-todo-list-plugin-armkas.replit.app/openapi.yaml"//这里是花括号中最后一个不能带逗号
    },
    "logo_url": "https://puyue-todo-list-plugin-armkas.replit.app/logo.png",//可以是任何网络图片连接
    "contact_email": "legal@example.com",//无视
    "legal_info_url": "http://example.com/legal"//无视
  }
```
  
## 2

openapi.yaml文件中url别忘了设定 

(我这里用的是在线编译器replit这样就能直接deploy(部署)到服务器)

openapi.yaml 是让chatgpt读的详细式样书 输入什么 输出什么 格式属什么 等等

#replit

收费 一个仓库单独最低0.2美元一天,但是太差0.4的才能用
仓库必须是自己名下的,或者自己github仓库导入过来的,别人的仓库invite你进去能修改但是不能deploy
deploy和run是独立的 run是localhost
deploy时候有一个可选设置是build 要加 ``pip install -r requirements.txt`` 导入包

# 以下是本来的readme

# ChatGPT plugins quickstart

Get a todo list ChatGPT plugin up and running in under 5 minutes using Python. If you do not already have plugin developer access, please [join the waitlist](https://openai.com/waitlist/plugins).

## Setup

To install the required packages for this plugin, run the following command:

```bash
pip install -r requirements.txt
```

To run the plugin, enter the following command:

```bash
python main.py
```

Once the local server is running:

1. Navigate to https://chat.openai.com. 
2. In the Model drop down, select "Plugins" (note, if you don't see it there, you don't have access yet).
3. Select "Plugin store"
4. Select "Develop your own plugin"
5. Enter in `localhost:5003` since this is the URL the server is running on locally, then select "Find manifest file".

The plugin should now be installed and enabled! You can start with a question like "What is on my todo list" and then try adding something to it as well! 

## Getting help

If you run into issues or have questions building a plugin, please join our [Developer community forum](https://community.openai.com/c/chat-plugins/20).
