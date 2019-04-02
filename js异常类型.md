### 代码(编译)错误
  A）语法错误（SyntaxError）：
  eg：拼写错误。
  该错误下，浏览器会直接报错，整个代码都不会执行。
  B）范围错误（RangeError）：
  该错误下，错误之前的代码会执行，之后代码不会执行。
  C）引用错误（ReferenceError）：
  该错误下，错误之前的代码会执行，之后代码不会执行。
  D）类型错误（TypeError）：
  该错误下，错误之前的代码会执行，之后代码不会执行。

### 运行错误：
  A）运行错误（runtime error）：
  eg：系统资源不可用（内存分配失败，文件打开失败，数据库打开失败等）
  B）逻辑错误（bug）：
  eg：程序控制不当（除数为0；负数开方等）

A）Error：基类型。即：所有的错误都继承该类型。提供这个基类型的主要目的是提供给开发人员抛出自定义的错误。
eg：throw new Error(输出错误信息)。

B）SyntaxError：语法错误。即：解析错误。
eg:var 1a；
显示：Uncaught SyntaxError: Unexpected number

C）RangeError: 范围错误。即：数字超出有效范围会抛出该错误。
eg:var a= new Array(-1);
显示：Uncaught RangeError: Invalid array length

D）ReferenceError:引用错误。即：在找不到对象会抛出错误。
  a）引用了一个不存在的变量
  eg: console.log(a);
  显示：Uncaught ReferenceError: a is not defined
  b）将变量赋值给一个无法被赋值的对象
  eg:console.log()= 1;
  显示：Uncaught ReferenceError: Invalid left-hand side in assignment

E）TypeError：类型错误。通常在if控制流中和全等，相等的比较中存在类型转换。
  a）变量或参数不是预期类型，比如，对字符串、布尔值、数值等原始类型的值使用new命令，就会抛出这种错误，因为new命令的参数应该是一个构造函数。
  eg: var a= new 123;
  显示：Uncaught TypeError: 123 is not a function
  b）调用对象不存在的方法
  eg:var a;a.aa();
  显示：Uncaught TypeError: Cannot read property ‘aa’ of undefined

F）EvalError：eval错误。即：未恰当使用eval()函数会抛出该错误。例如未将eval当作函数使用。
eg：new eval()。

G）URLError：url错误。即：使用与url相关函数参数不正确。
主要是encodeURI()、decodeURI()、encodeURIComponent()、decodeURIComponent()、escape()和unescape()这六个函数。这种类型不常见。
eg: decodeURI(’%2’)
显示：Uncaught URIError: URI malformed

参考链接：https://blog.csdn.net/Night20181029/article/details/83716144
