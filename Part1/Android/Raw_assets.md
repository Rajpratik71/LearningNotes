相同点：两者目录下的文件在打包后会原封不动的保存在apk包，不会被编译成二进制文件

不同点：一、 raw 中的文件会被映射到R.java 文件中，访问的时候直接使用资源ID 即R.id.filename；
           assets 文件夹下的文件不会被映射到R.java中，访问的时候需要AssetManager类。
       二、raw不可以有目录结构，而assets则可以有目录结构，也就是assets 目录下可以在建立文件夹
       三、在AssertManager中不能处理单个超过1MB的 文件，不然会报异常，raw没这个限制可以放个4MB 的MP3文件没问题。
       四、assts 文件夹是存放不进行编译加工的原生文件，即该文件夹里面的文件不会像xml，java文件被预编译，可以存放一些图片，html，js，css 等文件。     