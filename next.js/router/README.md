# 解析Next.js的router

### 把appRouter对象注册到Provider
![Alt text](./images/image.png)

### push方法解析
传递当前href到navigate方法
![Alt text](./images/image-1.png)

navagate方法来自于useNavigate
![Alt text](./images/image-2.png)

小结：push方法其实触发了dispatch({navigateType: 'push'})事件

#### 解析dispatch
dispatch来自于ActionQueueContext
![Alt text](./images/image-3.png)

ActionQueueContext的值来源createMutableActionQueue
![Alt text](./images/image-4.png)

createMutableActionQueue触发action中的reducer
![Alt text](./images/image-5.png)

触发clientReducer函数，调用navigateReducer
![Alt text](./images/image-6.png)

navigateReducer_noPPR内准备好数据后调用handleMutable
![Alt text](./images/image-7.png)

handleMutable获取最终数据后更新reducerState


appRouterState更新触发history更新
![Alt text](./images/image-8.png)
d

### prefetch方法解析
prefetch同push也会调用clientReducer方法，执行prefetchReducer
![Alt text](./images/image-9.png)

prefetchReducer函数内调用fetchServerResponse
![Alt text](./images/image-10.png)

fetchServerResponse调用fetch方法获取静态资源
![Alt text](./images/image-11.png)

抓包获取静态资源列表
![Alt text](./images/image-12.png)

Link组件的prefetch也是同样调用此prefetch方法预下载

