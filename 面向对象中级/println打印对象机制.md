我们都知道当println输出对象时调用的是toSring方法，看下面的代码

```java
public void list(){
        for(int i = 0; i <= houseList.length-1;i++){
//            if(houseList[i] == null){
//                break;
//            }
            System.out.println(houseList[i]);
        }
    }

```

当对象为null时不会调用toString代码造成空指针错误，而是会输出null
