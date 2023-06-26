### 包

包的本质是以文件夹为分类的路径区分系统，可以用了区分、管理相同的类，也可以控制访问范围。java.lang包是每个类默认引入的。

基本语法为：
```java 
package folder1.folder2.name //公司名.项目名.业务模块名

```

这里要注意，在IDEA中，想要打包一个类，make sure他的物理路径是正确的。

比如目前有两个文件夹directory A 和 B，A里包含a类， B里包含b类，如果我们想将a打包在B folder下，除了在代码文件内里使用package statement，物理路径也要把a文件放在B文件夹下，否则会报错。
