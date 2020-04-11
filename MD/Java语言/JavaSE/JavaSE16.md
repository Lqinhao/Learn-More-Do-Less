* IO流分类:

  *  流向:

    *  

  ```java
  输入流:
  	FileReader  Reader
  输出流:
       FileWriter Writer		
   ​		数据类型:		
   ​			字节流:
   ​					字节输入流:
   ​							InputStream()
   ​								方法:read()
   ​									Read(byte[])
   ​									|---->FileInputStream()
   ​										构造器:FileInputStream(File)
   ​					字节输出流:
   ​							OutputStream()
   ​								方法:write()
   ​									Write(byte[])
   ​									|--->FIleOutputStream()
   ​										构造器:FileOutputStream(File)
   ​			字符流:
   ​					字符输入流:
   ​							Reader
   ​								|--->FileReader()
   ​					字符输出流
   ​							Writer
   ​								|----->FileWriter()
   ​	开发中到底使用哪种流:
   ​					文件的单纯拷贝的操作,推荐使用字节流
   ​					单纯文本文件的读取操作,推荐使用字符流
   ​						一个中文字符使用gbk编码表,一个中文字符表示2个字节
   ​						一个中文字符使用utf-8编码表,一个中文字符表示3个字节
   ​						英文字符….一个字符表示一个字节
  ```

* 其他的流:
  ​		1.标准输入输出流:(指向控制台)
  ​					System.in:
  ​							public static final InputStream in:字节输入流,用来从控制台读入信息
  ​					System.out:
  ​							Public static final PrintStream out:打印出流,用来给控制台输出信息
  ​		2.转换流:(将字节流转换成字符流)
  ​					InputStreamRead:
  ​								输入流:属于字符流
  ​					OutputStreamWrite:
  ​								输出流:属于字符流
  ​					使用场景:
  ​							A:以指定的码表读取数据或者写出数据
  ​							B:如果我们在以后的知识中只能获取字节流,操作字符使用字符流更方便,也需要使用转换流
  ​		3.打印流:
  ​					printStream:字节打印流
  ​					printWriter:字符打印流
  ​							特点:可自动换行:使用println就可以自动换行
  ​								不能输出字节,但是可以输出其他任意类型
  ​								通过某些配置,可以实现自动刷新功能:通过在构造函数之后添加参数
  ​								也是包装流,不具备写出功能
  ​								可以把字节输出流转换成字符输出流
  ​					注意:只能输出不能输入
  ​		4.对象操作流:(操作的是对象)
  ​					ObjectOutputStream():
  ​							构造方法:
  ​									writeObject()
  ​									objectOutputStream(OutputStream)
  ​					ObjectInputStream():
  ​							构造方法:
  ​									readObject()
  ​									ObjectInputStream(InputStream)
  ​				注意:
  ​					使用对象输出流写对象,只能使用对象输入流来读取对象		
  ​				Serializable:序列号,是一个表示接口,只起表示作用
  ​				序列化:
  ​						向文件中写数据(持久化)
  ​				反序列化:
  ​						从文件中读取数据.
  ​				练习题:
  ​						需求:向对象中写多个学生对象
  ​							1.找对象,让对象帮我们做
  ​								ObjectOutputStream oos=new ObjectOutputStream(new FileOutputStream(File file))
  ​								//将多个学生对象封装到一个集合中
  ​								通过oos写出对象
  ​						需求:从文件中读文件	     
  ​		5.Properties类(集合类)
