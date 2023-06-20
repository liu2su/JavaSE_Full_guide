看这样一段代码：
```java
  public class test{
    public static void main(String[] args){
    AA aa = new AA();
    aa.print(10,5,97);
    }
  }

  class AA{
    public void print(int column,int row,char a){
      for(int i = 1;i <= row;i++){
        for(int j = 1;j<= column;j++){
          System.out.print(a);
        }
        System.out.println();
      }
    }

  }
```

我的想法是，既然赋值上，int赋值给char，存在隐式转换：char a = 97;//编译成功，那么传递参数时，给char形参传递一个int应该也是可以编译成功的。

**但是编译失败，显示类型不兼容**说明传递实参给method的形参不存在隐式转换，stackoverflow上有一个回答：

```
I believe that is because it's an assignment. When you're passing the value to the parameter,
it's a different context for the compiler, docs.oracle.com/javase/specs/jls/se8/html/jls-5.html#jls-5.2.
Similar to trying to assign a value too large for an int; int value = 12345678901;.
It can infer if the data type can hold the value. 
```

暂时当做标准答案吧。当然精度低的实参是可以传递给精度高的形参的。
