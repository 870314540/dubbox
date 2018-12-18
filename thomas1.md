1 sample

- provider
```

注册中心URL 
com.alibaba.dubbo.config.ServiceConfig.doExportUrls 
registry://10.112.6.12:2181/com.alibaba.dubbo.registry.RegistryService?application=test-provider&dubbo=2.5.3&pid=6816&registry=zookeeper&timestamp=1522284700436

dubbo协议服务URL 
com.alibaba.dubbo.rpc.protocol.dubbo.DubboProtocol.export 
dubbo://10.112.6.12:20880/cn.javacoder.test.dubbo.IHelloWorldService?application=test-provider&dubbo=2.5.3&interface=cn.javacoder.test.dubbo.IHelloWorldService&methods=say&pid=6816&side=provider&timestamp=1522284835101

com.alibaba.dubbo.config.ServiceConfig.doExportUrls 
registry://10.112.6.12:2181/com.alibaba.dubbo.registry.RegistryService?application=test-provider&dubbo=2.5.3&export=dubbo%3A%2F%2F10.112.6.12%3A20880%2Fcn.javacoder.test.dubbo.IHelloWorldService%3Fapplication%3Dtest-provider%26dubbo%3D2.5.3%26interface%3Dcn.javacoder.test.dubbo.IHelloWorldService%26methods%3Dsay%26pid%3D5896%26side%3Dprovider%26timestamp%3D1522285487513&pid=5896&registry=zookeeper&timestamp=1522285483033

com.alibaba.dubbo.config.ServiceConfig.doExportUrls中根据registry://协议的registry参数生成真正的注册中心URL 
zookeeper://10.112.6.12:2181/com.alibaba.dubbo.registry.RegistryService?application=test-provider&dubbo=2.5.3&interface=com.alibaba.dubbo.registry.RegistryService&pid=5896&timestamp=1522285483033

订阅URL，com.alibaba.dubbo.registry.zookeeper.ZookeeperRegistry.doSubscribe，当/dubbo/cn.javacoder.test.dubbo.IHelloWorldService/configurators路径有变化时回调我们的ChildListener， 用下面的URL表示override 协议 
provider://10.112.6.12:20880/cn.javacoder.test.dubbo.IHelloWorldService?application=test-provider&category=configurators&check=false&dubbo=2.5.3&interface=cn.javacoder.test.dubbo.IHelloWorldService&methods=say&pid=7000&side=provider&timestamp=1522285781420

当配置规则发生变化时notify协议 
override://0.0.0.0/cn.javacoder.test.dubbo.IHelloWorldService?category=configurators&dynamic=false&weight=10

```


- 服务消费端

```

com.alibaba.dubbo.config.ReferenceConfig.createProxy 
registry://10.112.6.12:2181/com.alibaba.dubbo.registry.RegistryService?application=test-consumer&dubbo=2.5.3&pid=6400&registry=zookeeper&timestamp=1522287127711]

com.alibaba.dubbo.registry.integration.RegistryProtocol.refer 
zookeeper://10.112.6.12:2181/com.alibaba.dubbo.registry.RegistryService?application=test-consumer&dubbo=2.5.3&pid=6400&refer=application%3Dtest-consumer%26cluster%3Dfailfast%26dubbo%3D2.5.3%26interface%3Dcn.javacoder.test.dubbo.IHelloWorldService%26methods%3Dsay%26pid%3D6400%26say.async%3Dtrue%26side%3Dconsumer%26timestamp%3D1522287125643&timestamp=1522287127711

消费者协议 
com.alibaba.dubbo.registry.integration.RegistryProtocol.doRefer 
consumer://10.112.6.12/cn.javacoder.test.dubbo.IHelloWorldService?application=test-consumer&cluster=failfast&dubbo=2.5.3&interface=cn.javacoder.test.dubbo.IHelloWorldService&methods=say&pid=6400&say.async=true&side=consumer&timestamp=1522287125643

订阅协议 
com.alibaba.dubbo.registry.integration.RegistryProtocol.doRefer， 由category参数表示要订阅providers,configurators,routers三类通知消息 
consumer://10.112.6.12/cn.javacoder.test.dubbo.IHelloWorldService?application=test-consumer&category=providers,configurators,routers&cluster=failfast&dubbo=2.5.3&interface=cn.javacoder.test.dubbo.IHelloWorldService&methods=say&pid=6400&say.async=true&side=consumer&timestamp=1522287125643

当配置规则发生变化时notify协议 
override://0.0.0.0/cn.javacoder.test.dubbo.IHelloWorldService?category=configurators&dynamic=false&weight=10

关闭invoker 
empty://10.112.6.12/cn.javacoder.test.dubbo.IHelloWorldService?application=test-consumer&category=providers&cluster=failfast&dubbo=2.5.3&interface=cn.javacoder.test.dubbo.IHelloWorldService&methods=say&pid=6400&say.async=true&side=consumer&timestamp=1522287125643



``` 