finally是个很厉害的代码块，即使有return，还是会执行，所以下面的代码会输出4
![t-c-f](https://github.com/liu2su/JavaSE_Full_guide/assets/96462566/b9ef935d-c286-4fd1-9de7-f058897b2f64)

那么，catch代码块里会不会执行return呢？会的，请看下面代码块（输出4）：

![t-c-f2](https://github.com/liu2su/JavaSE_Full_guide/assets/96462566/fe4f033c-75ed-47cf-b2b4-434fce673a57)

那么，如果final里面没有return呢？会return catch的，请看下面的代码块：

![t-c-f3](https://github.com/liu2su/JavaSE_Full_guide/assets/96462566/bcc7c955-e5c3-46f2-ae29-ebb8988a69ac)
