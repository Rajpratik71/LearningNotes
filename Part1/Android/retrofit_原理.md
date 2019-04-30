什么是动态代理：
动态代理，利用java 的反射技术，在运行时创建一个实现某些给定接口的新类及其实例对象。代理的是接口，而不是类，更不是抽象类。

动态代理的作用：
解决特定问题：一个接口的实现在编译时无法知道，需要在运行时才能实现
实现某些设计模式：适配器或修饰器
面向切面编程：如AOP 

创建动态代理
利用Java 的Proxy 类，调用Proxy.newProxyInstance(),创建动态对象
InvocationHandler handler = new MyInvocationHandler(...);
Class proxyClass = Proxy.getProxyClass(Foo.class.getClassLoader(),new Class[]{Foo.class});
Foo f = (Foo) proxyClass.getConstructor(new Class[]{InvocationHandler.class}).newInstance(new Object[]{handler});

或更简单
Foo f = （Foo）Proxy.newInstance(Foo.class.getClassLoader(),new Class[]{Foo.class},handler)

Proxy.newProxyInstance() 方法的三个参数
1、类加载器（Class Loader）
2、需要实现的接口数组
3、InvacationHandler接口。所有动态代理类的方法调用，都会交由InvocationHandler接口实现类里的invoke（）方法去处理。这是动态代理的关键


InvocationHandler 接口
接口里有一个invoke（）方法。基本的做法是，创建一个类，实现这个方法，利用反射在invoke（）方法里实现需求；
public class MyInvocationHandler implements InvocaionHandler{
	public Object invoke(Object proxy,Method method,Object[] args) throws Throwable{
		// do something dynamin
	}
}

invoke() 方法同样有三个参数
1、动态代理类的引用，通常情况下不需要它。但可以使用getClass（）方法，得到proxy的Class 类从而取得实例的类信息，如方法列表，annotation等。
2、方法对象的引用，代表被动态代理类调用的方法。从中可得到方法名，参数类型，返回类型等等。
3、args 对象数组，代表被调用方法的参数。注意基本类型（int，long） 会被封装成对象类型（Ingter，Long）



Retrofit 主要的核心代码为步骤2 。

1、定义注解类 使用动态代理的模式在运行时创建一个实现某些给定接口的新类及其实例对象 。代理的是接口，而不是类，更不是抽象类。
2、创建动态代理，通过动态代理的方式或者 类中的方法名，方法名上的注解，方法的参数的注解和参数值 等。     
   Host host = (Host) Proxy.newProxyInstance(Host.class.getClassLoader(), new Class[]{Host.class}, new InvocationHandler() {
            @Override
            public Object invoke(Object o, Method method, Object[] objects) throws Throwable {
                System.out.print("获取方法名称:" + method.getName());
                
                method.getAnnotations(); // 获取方法的注解
                // 获取方法的参数的注解
                Annotation[][] param = method.getParameterAnnotations(); 
                for(Annotation[]  annotations:param){
                    System.out.print("获取方法的参数的注解："+ Arrays.toString(annotations));
                }
                
                System.out.print("获取方法的参数值" + Arrays.toString(objects));            
              
                return null;
            }
        }