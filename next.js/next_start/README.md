# 解析Next.js的 next start启动服务后，怎么处理请求

start命令入口
![Alt text](./images/image.png)

startServer启动服务
![Alt text](./images/image-1.png)

监听请求回调，requestHandler来自于getRequestHandlers返回的第一项
![Alt text](./images/image-2.png)

getRequestHandlers返回initialize的返回值
![Alt text](./images/image-3.png)

requestHandlerImpl
![Alt text](./images/image-4.png)

调用resolveRoutes处理请求，循环routes处理
![Alt text](./images/image-5.png)

routes对应生命周期，依次处理middleware、headers、redirects、rewrites
![Alt text](./images/image-6.png)

最后一个查询如果找到本地文件直接返回
![Alt text](./images/image-7.png)