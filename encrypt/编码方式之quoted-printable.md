# 编码方式之quoted-printable



quoted-printable可译为可打印字符引用编码，我们收邮件，查看信件原始信息，经常会看到这种类型的编码。



最多时候，我们在邮件头里面能看到这样的编码：Content-Transfer-Encoding：quoted-printable

它是多用途互联网邮件扩展（MIME）一种实现方式。其中MIME是一个互联网标准，它扩展了电子邮件标准，致力于使其能够支持非ASCII字符、二进制格式附件等多种格式的邮件消息。目前http协议中，很多采用MIME框架！quoted-printable就是说一些可打印常用字符，表示一个字节中所有非打印字符方法



## 编码方式

任何一个8位的字节值可编码为3个字符：一个等号“=”后跟随两个十六进制数字（0-9和A-F）表示该字节的数值。例如，ASCII码换页符（十进制为12）可以表示为“=0c”，等号“=”（十进制为61）必须表示为“=3D”，除了可打印ASCII字符和换行符外，所有字符必须表示为这种格式。



所有可打印ASCII字符（十进制的范围为33到126）可用ASCII字符编码直接表示，但是等号“=”（十进制为61，在可打印字符中）不能这样直接表示，而应表示为“=3D”。ASCII的水平制表符（tab）与空格符，十进制为9个32，如果不出现在行尾则可以用其ASCII字符编码直接表示。如果这两个字符出现在行尾，必须表示为“=09”和“=20”.

如果数据中包含有意义的行结束标志，必须转化为ASCII回车（CR）换行（LF）序列，既不能用原来的ASCII字符也不能用QR编码的“=”转义字符序列。相反，如果字节值13与10有其他的不是行结束的含义，他们必须QR编码为“=0D”和“=0A”.

quoted-printable编码的数据的每行长度不能超过76个字符，为满足此要求又不改变被编码文本，在QR编码结果的每行末尾加上软换行（soft line break），即在每行末尾加上一个”=“，但并不会出现在解码得到的文本中。

编码里面，有几个特定限定，一些可打印字符不用编码，当然如果你按照规范编码后，也一样可以显示。

很多时候，我们用些常见字符表示所有8位其他非打印字符，这种通过quoted-printable编码，只是对该字节转为16进制后，做简单增加前缀！然后做些特殊字符处理机课！它的简单即编码高效，也让该编码在邮件格式里面，得到了广泛应用！



在线编解码网址：http://web.chacuo.net/charsetquotedprintable























