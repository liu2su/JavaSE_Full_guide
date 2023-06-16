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
