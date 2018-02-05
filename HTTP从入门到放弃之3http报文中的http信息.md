> 本章了解请求和响应是如何运作的

    用于HTTP协议交互的信息被成为HTTP报文，分为报文首部，报文主体
    
    
- 请求报文
    1. 报文首部
        - 请求行  (请求的方法，请求URI HTTP版本)
        - 请求首部字段
        - 通用首部字段
        - 实体首部字段
    2. 空行（CR+LF）
    3. 报文主体
- 响应报文
    1. 报文首部
        - 状态行  （状态码，原因短语  HTTP版本）
        - 响应首部字段
        - 通用首部字段
        - 实体首部字段
    2. 空行（CR+LF）
    3. 报文主体
>  首部字段中包含请求响应的各种条件和属性的各类首部

### 编码提成传输速率

- 压缩传输的内容编码，分类：
    - gzip （GUN zip）
    - compress （UNIX系统的标准压缩）
    - deflate （zlib）
    - identity （不压缩）
- 分块发送的分块传输编码 --把实体主体分块


### 发送多种数据的多部分对象集合
> 通常在文件上传是使用
- multipart/form-data 文件上传时使用
-  multipart/buteranges 响应206（部分内容）包含了多个范围的内容时使用
- content-Type: multipart/form-data ;**boundary**=xxxx    使用boundary花纹多部分对象集合指明的各类实体


### 获取部分内容的范围请求
- 从5001到10000字节Range: bytes=5001-10000，xxxx-xxxx
- 从5001到最后字节Range: bytes=5001-
- 针对范围请求，会响应206 另外对于多重范围的范围请求,会在响应首部加上mutipart/buyeranges
- 若服务器无法响应范围请求，则返回200以及完整实体内容


### 内容协商返回最合适的内容

> 内容协商机制是指客户端和服务端就响应的资源内容进行交涉，然后提供给客户端最合适的资源。
> 一般包括 语言，字符集，编码方式为基准判断响应的资源
-  Accept
-  Accept-Charset
-  Accept- Encoding
-  Accept-Language
-  Content-Language

内容协商技术分为三类：

    - 服务器驱动协商
    - 客户端驱动协商
    - 透明协商

