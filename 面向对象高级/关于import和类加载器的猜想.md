这个问题是我在使用import命令时思考的：

类加载器的去找路径是由classpath提供的， 默认都是当前路径。

import命令是导入类，那么应该也是由类加载器去导入的。

在我思考import语句应该如何导入路径时，总是忽略了package命令，根据我的猜想，package命令显示的包名就是根目录，import语句应该从根目录开始，例子：

```
package exercise.homework; //这个类的包名的根目录在exercie

import exercise.homework.homework06.Horse; //应该从exercise开始import
```
