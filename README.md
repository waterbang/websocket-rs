### 如何使用

![image](https://user-images.githubusercontent.com/38105714/170466979-cf96b989-30f4-4075-8cea-3a145f40ef0d.png)

#### 启动 terminal 1

    cargo run

#### 启动 terminal 2 注册客户端

    curl -X POST 'http://localhost:8000/register' -H 'Content-Type: application/json' -d '{ "public_key": "bMr9vohVtvBvWRS3p4bwgzSMoLHTPHSvVj"  }'

输出如下信息
>{"url":"ws://127.0.0.1:8000/ws/32cc16e896554ef7b8ef7e7ff0f285eb"}%

#### 在terminal 2 连接服务器

    websocat -t ws://127.0.0.1:8000/ws/90891d9dc8fc4742b217ddb908ab0f91

接下来就可在此端口给服务端发送消息，如：

> {"function":["openScanner","openDWebView"]}

#### 启动 terminal 3 给客户端发送消息

    curl -X POST 'http://localhost:8000/publish' \
    -H 'Content-Type: application/json' \
    -d '{"public_key": "bMr9vohVtvBvWRS3p4bwgzSMoLHTPHSvVj" , "function": "openScanner", "message": "hello world"}'

>function 的openScanner 客户端会收到 hello world

#### 注销客户端

    curl -X DELETE 'http://localhost:8000/register/90891d9dc8fc4742b217ddb908ab0f91‘
