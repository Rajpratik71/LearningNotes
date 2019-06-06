ButterKnife 是控件注入框架，可以帮助安卓开发这省去初始化控件的重复性工作，简单快捷的初始化布局文件的控件，极大的提升开发效率。 也不会导致内存溢出等问题。

ButterKnife 的优点：
1、强大的View 绑定和click 事件处理功能，简化代码，提升开发效率。
2、方便的处理Adatper 里的ViewHolder 绑定问题
3、运行时不会影响APP 的效率，使用配置方便。
4、代码清晰，可读性强。


和IOC 架构的区别
共同特点：同样实现了解耦的目的
核心技术：运行是通过反射技术（reflect） VS  butterKnife 使用注解处理器技术（APT）
开发使用：两者几乎一样，傻傻分不清。
代码难易：Ioc 编程更具挑战性
程序稳定：两者暂未发现致命缺陷
两者缺陷：reflect 会消耗一定性能，APT 会增加apk大小
开发最求：更偏向编译期的APT 技术。


APT（Annotation Processing Tool）
是一种处理注解的工具，它对源代码文件进行检测找出其中Annotation，根据注解自动生成代码，如果想要自定义的注解处理器能够正常运行，必须要通过APT 工具来进行处理。也可以这样理解，只有通过声明APT 工具后，程序在编译期间自定义注解解释器才能执行。

AROUTR、EventBus :都使用了APT 技术。


ButterKnife 原理： https://blog.csdn.net/tigriswing/article/details/80749833
1、加载了一个新的class 文件，不是我们项目中的。
2、View view = source.findViewById();
3、注解处理器 列： MainActivity_ViewBinding 类如何生成呢？ 首先，要生成这个类就要得到这个类必须的基础信息，这就涉及到了annotationProcessor 技术，和APT 技术类似，它是一种注解处理器。来处理注解。com.google.auto.service.auto-service:1.0-rc2  （注解处理器服务，来一行一行编写生成MainActivity_ViewBinding 类）
4、 ButterKnifeProcessor extends AbstractProcess 

问题1： butterKnife 为什么不能使用private 标识 属性。
   答： 使用了private 之后不能通过类.属性直接调用 。


Annotation Processor （注解处理器）
https://blog.csdn.net/qq_20521573/article/details/82321755
1、 了解 annotation processor 
 Annotation Processor 是Javac 的一个工具，它用来在编译时扫描和处理注解。通过
Anonotation Processor