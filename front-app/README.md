1、默认情况，启动抛出异常：Cannot determine embedded database driver class for database type NONE

不知道使用什么数据库，需要在pom.xml标注使用什么数据库，如h2 
解决思路：修改pom.xml

<dependency>
    <groupId>com.h2database</groupId>
    <artifactId>h2</artifactId>
    <scope>runtime</scope>
</dependency>
2、
org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'APIAccountController': Unsatisfied dependency expressed through field 'accountFeignClient'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'com.simplemall.micro.serv.page.client.AccountFeignClient': FactoryBean threw exception on object creation; nested exception is java.lang.NullPointerException
	at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor$AutowiredFieldElement.inject(AutowiredAnnotationBeanPostProcessor.java:588)
	at org.springframework.beans.factory.annotation.InjectionMetadata.inject(InjectionMetadata.java:88)
	at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor.postProcessPropertyValues(AutowiredAnnotationBeanPostProcessor.java:366)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1264)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:553)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:483)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:306)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:230)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:302)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:197)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:761)
	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:866)
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:542)
	at org.springframework.boot.context.embedded.EmbeddedWebApplicationContext.refresh(EmbeddedWebApplicationContext.java:122)
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:737)
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:370)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:314)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1162)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1151)
	at com.simplemall.micro.serv.page.PageApplication.main(PageApplication.java:20)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.springframework.boot.devtools.restart.RestartLauncher.run(RestartLauncher.java:49)
Caused by: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'com.simplemall.micro.serv.page.client.AccountFeignClient': FactoryBean threw exception on object creation; nested exception is java.lang.NullPointerException
	at org.springframework.beans.factory.support.FactoryBeanRegistrySupport.doGetObjectFromFactoryBean(FactoryBeanRegistrySupport.java:175)
	at org.springframework.beans.factory.support.FactoryBeanRegistrySupport.getObjectFromFactoryBean(FactoryBeanRegistrySupport.java:103)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getObjectForBeanInstance(AbstractBeanFactory.java:1634)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:254)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:202)
	at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:208)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.addCandidateEntry(DefaultListableBeanFactory.java:1309)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.findAutowireCandidates(DefaultListableBeanFactory.java:1275)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1101)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1066)
	at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor$AutowiredFieldElement.inject(AutowiredAnnotationBeanPostProcessor.java:585)
	... 24 common frames omitted
Caused by: java.lang.NullPointerException: null
	at springfox.documentation.schema.property.OptimizedModelPropertiesProvider.beanDescription(OptimizedModelPropertiesProvider.java:317)
	at springfox.documentation.schema.property.OptimizedModelPropertiesProvider.propertiesFor(OptimizedModelPropertiesProvider.java:117)
	at springfox.documentation.schema.property.OptimizedModelPropertiesProvider$$FastClassBySpringCGLIB$$cb306bb2.invoke(<generated>)
	at org.springframework.cglib.proxy.MethodProxy.invoke(MethodProxy.java:204)
	at org.springframework.aop.framework.CglibAopProxy$CglibMethodInvocation.invokeJoinpoint(CglibAopProxy.java:721)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:157)
	at org.springframework.aop.aspectj.MethodInvocationProceedingJoinPoint.proceed(MethodInvocationProceedingJoinPoint.java:85)
	at springfox.documentation.spring.web.caching.CachingAspect.cachedValue(CachingAspect.java:86)
	at springfox.documentation.spring.web.caching.CachingAspect.operationsAndProperties(CachingAspect.java:69)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.springframework.aop.aspectj.AbstractAspectJAdvice.invokeAdviceMethodWithGivenArgs(AbstractAspectJAdvice.java:629)
	at org.springframework.aop.aspectj.AbstractAspectJAdvice.invokeAdviceMethod(AbstractAspectJAdvice.java:618)
	at org.springframework.aop.aspectj.AspectJAroundAdvice.invoke(AspectJAroundAdvice.java:70)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:168)
	at org.springframework.aop.interceptor.ExposeInvocationInterceptor.invoke(ExposeInvocationInterceptor.java:92)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:179)
	at org.springframework.aop.framework.CglibAopProxy$DynamicAdvisedInterceptor.intercept(CglibAopProxy.java:656)
	at springfox.documentation.schema.property.OptimizedModelPropertiesProvider$$EnhancerBySpringCGLIB$$2dd96046.propertiesFor(<generated>)
	at springfox.documentation.schema.DefaultModelProvider.properties(DefaultModelProvider.java:151)
	at springfox.documentation.schema.DefaultModelProvider.modelFor(DefaultModelProvider.java:85)
	at springfox.documentation.schema.DefaultModelProvider$$FastClassBySpringCGLIB$$2c8f6146.invoke(<generated>)
	at org.springframework.cglib.proxy.MethodProxy.invoke(MethodProxy.java:204)
	at org.springframework.aop.framework.CglibAopProxy$CglibMethodInvocation.invokeJoinpoint(CglibAopProxy.java:721)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:157)
	at org.springframework.aop.aspectj.MethodInvocationProceedingJoinPoint.proceed(MethodInvocationProceedingJoinPoint.java:85)
	at springfox.documentation.spring.web.caching.CachingAspect.cachedValue(CachingAspect.java:86)
	at springfox.documentation.spring.web.caching.CachingAspect.modelsAndDependencies(CachingAspect.java:80)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.springframework.aop.aspectj.AbstractAspectJAdvice.invokeAdviceMethodWithGivenArgs(AbstractAspectJAdvice.java:629)
	at org.springframework.aop.aspectj.AbstractAspectJAdvice.invokeAdviceMethod(AbstractAspectJAdvice.java:618)
	at org.springframework.aop.aspectj.AspectJAroundAdvice.invoke(AspectJAroundAdvice.java:70)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:168)
	at org.springframework.aop.interceptor.ExposeInvocationInterceptor.invoke(ExposeInvocationInterceptor.java:92)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:179)
	at org.springframework.aop.framework.CglibAopProxy$DynamicAdvisedInterceptor.intercept(CglibAopProxy.java:656)
	at springfox.documentation.schema.DefaultModelProvider$$EnhancerBySpringCGLIB$$4c625d82.modelFor(<generated>)
	at springfox.documentation.spring.web.scanners.ApiModelReader.read(ApiModelReader.java:66)
	at springfox.documentation.spring.web.scanners.ApiListingScanner.scan(ApiListingScanner.java:91)
	at springfox.documentation.spring.web.scanners.ApiDocumentationScanner.scan(ApiDocumentationScanner.java:62)
	at springfox.documentation.spring.web.plugins.DocumentationPluginsBootstrapper.scanDocumentation(DocumentationPluginsBootstrapper.java:101)
	at springfox.documentation.spring.web.plugins.DocumentationPluginsBootstrapper.onApplicationEvent(DocumentationPluginsBootstrapper.java:87)
	at springfox.documentation.spring.web.plugins.DocumentationPluginsBootstrapper.onApplicationEvent(DocumentationPluginsBootstrapper.java:50)
	at org.springframework.context.event.SimpleApplicationEventMulticaster.invokeListener(SimpleApplicationEventMulticaster.java:167)
	at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:139)
	at org.springframework.context.support.AbstractApplicationContext.publishEvent(AbstractApplicationContext.java:383)
	at org.springframework.context.support.AbstractApplicationContext.publishEvent(AbstractApplicationContext.java:389)
	at org.springframework.context.support.AbstractApplicationContext.publishEvent(AbstractApplicationContext.java:337)
	at org.springframework.context.support.AbstractApplicationContext.finishRefresh(AbstractApplicationContext.java:882)
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:545)
	at org.springframework.cloud.context.named.NamedContextFactory.createContext(NamedContextFactory.java:110)
	at org.springframework.cloud.context.named.NamedContextFactory.getContext(NamedContextFactory.java:79)
	at org.springframework.cloud.context.named.NamedContextFactory.getInstance(NamedContextFactory.java:115)
	at org.springframework.cloud.sleuth.instrument.web.client.feign.TraceFeignContext.getInstance(TraceFeignContext.java:28)
	at org.springframework.cloud.netflix.feign.FeignClientFactoryBean.get(FeignClientFactoryBean.java:128)
	at org.springframework.cloud.netflix.feign.FeignClientFactoryBean.feign(FeignClientFactoryBean.java:85)
	at org.springframework.cloud.netflix.feign.FeignClientFactoryBean.getObject(FeignClientFactoryBean.java:156)
	at org.springframework.beans.factory.support.FactoryBeanRegistrySupport.doGetObjectFromFactoryBean(FactoryBeanRegistrySupport.java:168)
	... 34 common frames omitted
解决方案：swagger2版本过底导致的，需要采用高版本的jar。【笔者产生的此问题，由于采用swagger2-2.2.2版本】

3、https://segmentfault.com/a/1190000009231329#articleHeader6 spring security + JWT