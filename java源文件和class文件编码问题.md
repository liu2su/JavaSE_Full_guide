## java源文件和class文件编码问题

这个问题是我在新电脑编译我的旧.java文件时发现的，compile文件时发生乱码，这就让我研究了一下.java文件和class文件的编码原理。以前没有发现问题的原因是我的电脑是中文系统，系统默认的字符集是GBK，而我的.java文件也是使用的GBK字符集。

但是新的电脑是美版电脑，使用的是US的字符集（名字忘了），总之这是一个由于**在JAVA项目中，源文件存储采用不同的字符集导致项目输出乱码**的问题。

先看一张图：

![mechanismofcharacterset](https://github.com/liu2su/Java-SEnote/assets/96462566/dd25f980-876a-4a2f-81c0-2726bd72925a)

Java文件编译后形成class

这里Java文件的编码可能有多种多样，但Java编译器会自动将这些编码按照Java文件的编码格式正确读取后产生class文件，这里的class文件编码是Unicode编码（具体说是UTF-16编码）。
 
因此，在Java代码中定义一个字符串：String s="汉字";不管在编译前java文件使用何种编码，在编译后成class后，他们都是一样的----Unicode编码表示。

而cmd使用javac对.java文件进行编译是，会使用Windows默认的字符集，因为我以前的电脑是中文系统，字符集默认就是GBK，.java文件也是使用GBK编码的，到了新电脑，字符集不再是GBK
了，javac尝试使用系统默认字符集编译时，就会形成乱码。
**最后总结：在javac的使用中，最好采用-encoding参数指明.java文件使用的字符集，以免造成不可恢复的中文乱码。**
