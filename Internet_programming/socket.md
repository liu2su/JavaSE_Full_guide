我对sokect的理解：socket就像他的名字一样：插口，可以理解为一个程序与另外一个程序的数据交换窗口。
sokect这个类内部管理着输出流和输入流，通过I/O流传输数据，使用的是TCP/IP协议
当我们从C输出S或者从S输出C时，都需要告诉socket什么时候输出结束，所以我们需要使用socket.shutdownOutput()方法，告诉另一端的sokect输入结束。

比如下面的代码
## 服务端代码

```java
public class Server {
    public static void main(String[] args) throws IOException {
        ServerSocket serverSocket = new ServerSocket(9999);
        System.out.println("Port 9999 listening");
        Socket socket = serverSocket.accept();
        System.out.println("Listening result:"+ socket.getClass());
        InputStream receive = socket.getInputStream();
        byte[] buffer = new byte[1024];
        int lenght = 0;
        while((lenght = receive.read(buffer)) != -1){
            System.out.println(new String(buffer,0,lenght));
        }
        OutputStream sender = socket.getOutputStream();
        sender.write("server response".getBytes());
        socket.shutdownOutput();
        sender.close();receive.close();
        socket.close();serverSocket.close();
    }
}
```
## 客户端代码
```java
public class client {
    public static void main(String[] args) throws IOException {
        Socket socket9999 = new Socket(InetAddress.getLocalHost(),9999);
        System.out.println("client socket:" + socket9999.getClass());
        OutputStream send = socket9999.getOutputStream();
        send.write("hello".getBytes());
        send.write("server".getBytes());
        socket9999.shutdownOutput();
        InputStream clientReceive = socket9999.getInputStream();
        byte[] buf = new byte[1024];
        int length = 0;
        while((length = clientReceive.read(buf)) != -1){
            System.out.println(new String(buf,0,length));
        }
        clientReceive.close();send.close();
        socket9999.close();
    }
}
```



如果我们只是实现client发送到server，可以不加这个结束标记，为什么结束标记也没有发生阻塞呢？其实是有结束标记的，结束标记是程序末尾是socket.close()，在执行客户端的close后，服务端才开始执行输出。
