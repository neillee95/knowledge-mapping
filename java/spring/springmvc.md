##### Spring MVC流程
![Spring MVC流程]

`DispatcherServlet`作为调度器，接收所有请求，将用户请求转发给对应的`HandlerMapping`，HandlerMapping返回`HandlerExecutionChain`给DispatcherServlet。DispatcherServlet获取支持HandlerExecutionHandler中handler的`HandlerAdapter`，HandlerAdapter调用Controller的具体方法处理请求，返回`ModelAndView`。HandlerAdapter将Controller返回的ModelAndView返回给DispatcherServlet，DispatcherServlet将ModelAndView传递给ViewResolver，ViewResolver返回View对象给DispatcherServlet，DispatcherServlet调用View的render方法进行渲染，DispatcherServlet将渲染后的数据返回给用户。

HandlerMapping的实现类:
- BeanNameUrlHandlerMapping
- RequestMappingHandlerMapping
- SimpleUrlHandlerMapping
- WelcomePageHandlerMapping

HandlerAdapter的实现类:
- HttpRequestHandlerAdater
- RequestMappingHandlerAdapter
- SimpleControllerHandlerAdapter
- SimpleServletHandlerAdapter


[Spring MVC流程]: <../../_assets/SpringMVC.png>