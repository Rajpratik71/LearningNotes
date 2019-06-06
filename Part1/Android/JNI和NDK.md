JNI 的理解:
	JNI的全称是JAVA Native Interface（Java 本地接口）是一层接口，是用来沟通java 代码和c/c++ 代码的，是java 和C/C++ 之间的桥梁。通称JNI，JAVA 可以完成对外部C/C++ 编写的库函数的调用，相对的，外部C/C++ 也能调用java 中封装好的类和方法。

	java 的优点是跨平台，和操作系统之间的调用有jvm 完成，但是一些和操作系统相关的操作就无法完成，JNI 的出现刚好弥补了这个缺点，也完善了Java 语言，将java 扩展的更为强大。	

	JNI 是java 调用Native 语言的一种特性
	JNI 是属于java 的，与android 无直接关系

	实现步骤
	1、 在java 中声明native 方法
	2、编译上诉java 源文件javac 得到（.class 文件）
	3、通过javah 命令导出JNI 的头文件(.h 文件)
	4、使用java 需要交互的本地代码实现在java 中声明的Native 方法
	5、编译.so 库文件
	6、通过java 命令执行java 程序，最终实现java 调用本地代码



NDK
    定义：Native Development Kit， 是Android 的一个工具开发包
    NDK 是属于android 的，与java 并无直接关系
    作用： 快速开发c、c++ 的动态库，并自动将so 和应用打包成apk。 即可通过NDK 在android 中使用JNI 与本地代码交互

    特点：
    	性能方面
    	 1、运行效率高：在开发要求高性能的需要功能中，采用c/c++ 更加有效率； 如使用本地代码执行算法，能大大提高算法的执行效率。
    	 2、代码安全性高：java 是半解释型语言，容易被反编译后得到源代码。 而本地有些代码类型如C 、c++ 则不会，能提高系统的安全性。
    	 3、功能拓展性好：可方便地使用其他开发语言的开源库。除了java 的开源库，还可以使用开发语言的开源库
    	 4、使用方面：易于代码复用和移植。用本地代码（C、c++）开发的代码不仅可以在android 中使用，还可嵌入到其他类型平台上使用。

    额外功能：
    	1、提供了把.so 和.apk 打包的工具 而jni 开发没有，只是把.so 文件放到文件系统的特定位置
    	2、NDK 提供的库有限，仅用于处理算法效率和敏感问题
    	3、提供了交叉编译器，用于生成特定的cpu 平台动态库	 


jni 和ndk 的关系
JNI 是java 的接口，用于java 与本地语言（C、c++）交互
ndk 是android 的工具开发包，快速开发c、c++ 的动态库，并自动将.so 和应用一起打包成apk

JNI 是实现的目的，NDK是在android 中实现jni 的手段，即在android 的开发环境中，通过ndk 从而实现jni 的功能。


