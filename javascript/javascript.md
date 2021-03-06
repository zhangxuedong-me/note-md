# 		javascript----学习笔记





## 1.0：【javascript介绍】

​	1，概念：是一门运行在浏览器端的语言。用来响应用户的操作，和用户来交互。

​	2，javascript的三种引入方式：

​		。**内嵌式**：在页面引入script标签，在head标签里和body标签里引入都可以

​		。**外联式**：在页面引入script标签加入属性src表示要引入的外部js的文件路径

​		。**行内式**：在行内使用javascript，但是并不建议使用

​	3，javascript由三部分组成：

​		。BOM

​		。DOM

​		。ECMAScript





## 1.1：【console对象】

```javascript
        console.log()：//输出打印，打印在控制台上（console）

        alert()：//弹出一个警告框

        prompt（铺ruang他）()：//弹出一个引导用户填写相应的内容框，会把用户填写的内容返回

        console.dir()：//用来打印复杂数据类型。	

        console.info()：//和console.log()一样，只不过名字不一样

        console.warn(wo 嗯)：//输出的时候前面会有一个黄色小图标。会有堆栈内存依次调用运行的方法名及其它等信息

        console.error()：//输出的时候前面会有一个红色的小图标，会有堆栈内存依次调用运行的方法名及其它等信息

        console.trace（吹斯）()：//不仅会打印函数调用栈信息，同时也会显示函数调用中各参数的值

        console.count（考恩特）()：//可以放在一个方法中，，每次调用都会加1，更好显示方法被调用了多少次

        console.time()：//需要和console.timeEnd()要同时使用。同时传入相同的字符串，会返回毫秒值

        console.assert（啊色特）()：//一般俩个参数，第一个参数是boolean类型参数，后面是要输出的内容

        console.clear()：//清空console的输出信息

        console.table()：//将数组形式的变量打印成了表格的形式
```


## 1.2：【注释】

​	1，概念：用来分析逻辑，分析步骤，注释不会被javascript执行

​	

```javascript
	//：单行注释。只能注释一行内容
			
	/**/：多行注释，可以写入多行注释

	/***/：当项目部署上线之后，对该项目版本，开发人员，和公司，和该项目的一些介绍，然后将其编译成一个文档
```


## 1.3：【var变量】

​	1，声明变量的关键字：var。声明的变量会暂时存储到栈内存中

​	2，变量的命名规范：

​		。不能以数字开头

​		。以英文或者美元符或者带有下划线的方式命名

​		。严格区分大小写

​		。变量命名不能使用javascript里面的关键字和保留字



## 1.4：【基本数据类型】

​	1，Number：类型，就是数值（整数）。如果打印Number类型返回NaN的话，表示返回的不是某个数值

​	2，String：就是字符串。字符串需要用双引号或者单引号来括起来

​		。特点：

​			任何数据类型与字符串相加，会先被转成字符串然后进行拼接

​			大量的字符串拼接会影响性能问题

​	3，Boolean：逻辑类型。有俩个值，true（真），false（假）来判断某个件事情是否成立

​	4，undefined：表示没有初始化的值

​	5，null：空。表示对象的引用



## 1.5：【基本数据类型的相互转换】

​	1，转成字符串类型：使用String()方法。但是undefined和null没有这个方法，可以使用.toString()方法来解	      决这个问题

​	2，转成Number类型：

```javascript
		Number()：//能转字符串形式的数字，和Boolean类型
	
		parseInt()：//用来转整数的，能转字符串形式的数字。但是不能转Boolean类型。
	
		parseFloat()：//用来转小数的，能转字符串形式的数字。但是不能转Boolean类型。
```
​	3，转成Boolean类型：使用Boolean()方法：除了（0）（NaN）（""）（undefined）（null）会转成false						之外，其他的都会转成true



## 1.6：【算数操作符】

​	1，**+加**：任何数据类型和字符串相加，最后会形成字符串的拼接，js会隐式把其他数据类型转成字符串再和字			符串相加

​	2，**-减号**：如果字符串与整数相减的话，会先把字符串转成整数再相减，包括Boolean类型。如果是字符串和			   字符串相减会先把他们都转成数值类型

​	3，***乘号**：和减号对字符串处理的性质一样

​	4，**\除号**：和减号对字符串处理的性质一样

​	5，**%取模**：对俩个数进行取余数，对字符串的处理和加减乘除一样先转成数值类型

​	6，**++自增**：一元操作符，如果++位于操作数之前并且有多步运算，那么就是先加一之后再输出加一之后的			      数。如果位于操作数之后的话，那么就是先输出原来的数再加一。

​	7，**--自减**：和自增的用法一样



## 1.7：【比较操作数】

​	1，概念：会返回Boolean类型的值。就是比较大于或者小于或者等于。注意在比较运算符中俩个等于号是等			  于，一个等于号是赋值



## 1.8：【逻辑操作符】

​	1，&&：并且的意思，如果符号俩边的表达式都为true，那么结果才为true，否则就是false

​	2，||：或者的意思，如果符号俩边的表达式只要有一边的表达式为true，那么结果就为true，否则就是false

​	3，!：取反的意思，就是将true取反为false，将false取反为true



## 1.9：【运算符的一些特殊用法】

​	1，+=：表示当前的数等于当前的数加上另一个数

​	2，-=：表示当前的数等于当前的数减去另一个数

​	3，*=：表示当前的数等于当前的数乘以另一个数

​	4，/=：表示当前的数等于当前的数除以另一个数

​	5，%=：表示当前的数等于当前的数取余另一个数



## 2.0：【优先级的分布】

​	1，有括号要先算括号里面的

​	2，其次是++运算符

​	3，再次是比较符：<=，==，>

​	4，然后是逻辑运算符：&&，||

​	5，最后是赋值：=



## 2.1：【流程控制】

​	1，概念：对代码的执行过程进行控制



## 2.2：【结构】

​	1，顺序结构：就是从上到下依次执行代码

​	2，分支结构：通过不同的分支判断，进入不同的执行环境

​	3，循环结构：执行需要重复的事情



### 	2.2.1：【分支结构】

​		1，概念：通过不同的分支，执行不同作用域中的代码

​			

```javascript
		            
			//if语句
			if(条件表达式){

                //当表达式为true的时候需要执行的代码语句
            }

            if(条件表达式){

                //当表达式为true的时候需要执行的代码}else{当表达式为false的时候需要执行的代码
            }

            if (条件表达式){

                //当表达式为true的时候需要执行的代码

            } else if (条件表达式){

                //当表达式为true的时候需要执行的代码

            } else if (条件表达式){

                //当表达式为true的时候需要执行的代码

            } else{

                //以上判断如果都不通过，就指向他
            }



			//switch-case语句：通过判断case里面不同的值执行相应的case，如果以上的case都不满足就走								   default相当于if语句中的else，加上break的意思是不满足条件的都直接跳								出不执行

					
					switch(需要判断的变量或者数据){
				
                        case 固定值:

                            //执行代码

                            break
                        case 固定值:

                            //执行代码

                            break

                        default（第否特） :

                            //执行代码
                            break
                      }
		
```


### 	2.2.2：【循环结构】

​		1，只要有需要重复执行的事情可以使用循环

```javascript
		// 如果表达式一直为true的话就会一直执行循环体，只到为false的话推出循环体
		while (表达式) {循环体}
	
		for (初始化表达式;条件表达式;自增表达式){循环体}
		
		// 他的好处就是无论条件表达式是否为true至少执行一次。
		do {循环体} while (条件表达式)：
```


## 2.3：【三元表达式】

​	1，概念：代码有三个操作数参加了运算。如果表达式为true的话，返回表达式1，如果为false的话返回表达			  式2



​			。格式：**表达式1 （比较运算符） 表达式2 ? 表达式1 : 表达式2**



## 2.4：【断点调试】

​	1，概念：查看代码执行的过程

​	2，使用步骤：

​		。F12打开开发者工具，点击sources（骚赛斯）（资源）选项

​		。在左边找到代码所在文件，双击打开

​		。代码中找到相应的行数，点击行数的数字，F5刷新，进入断点调试



## 2.5：【break和continue】

​	1，**break**：当满足一些条件后，跳出循

​	2，**continue**：当满足一些条件之后，跳出本次循环



## 2.6：【数组】

​	1，概念：复杂的数据类型，用来储存大量的数据，并且是有顺序的，可以通过索引也叫下标或者角标来提取			  数据，数组的索引是从0开始的。数组可以存储任何数据类型

​	2，如何定义：

​		。字面量 [ ]：以逗号来分割开每一项的数据

​		。new Array()来声明：通过这种构造函数创建对象的方式来声明

​	3，特点：

​		。通过声明数组的，变量[index]来取出数据

​		。通过数组的length（数组的长度）属性，可以获取数组的长度

​		。遍历数组：通过for循环的方式来遍历出数组中的每一项

​		。当需要使用数组的过程执行完毕之后，把数组的引用指引为null，方便垃圾回收机制把该变量回收

​	4，数组中的方法：

```javascript
		concat（康凯特）()//拼接数组，参数接收一个数组，将数组中的每一项拼接到旧的数组中，会返回一个新的							数组。

		push()：//向数组的最后面添加数据
		
		pop（爬铺）()：//删除数组的最后一项，并且将这一项返回，会重新修改原数组的长度。
		
		unshift()：//向数组的最前面添加数据
		
		shift(晒父特)：//删除数组的第一项，并且返回删除的数组项，重新修改原数组的长度。
		
		splice（私拍赖斯）()：//第一个参数从什么位置开始，第二个参数删除多少个，第三个参数添加多少个。
		
		join()：//将数组的中的每一项拼接成字符串。
		
		indexOf()：//获取数组中是否包含某一项，如果包含会返回包含项的角标，否则返回-1，第二个参数指定从						什么位置开始查找
		
		lastIndexOf()：//跟indexOf()的用法相同，只不过他是从最后面开始查找的
		
		slice（斯来丝）()：//截取方法：第一个参数是从什么位置开始截取，第二个参数是到什么位置结束。参数							如果是负数的话就会加上数组的长度。
		
		sort()：//数组的排序方法，如果只调用方法是给字符串进行排序的。如果要给数值进行排序的话，需要传入				一个匿名函数，函数有俩个参数。第一个参数代表数组中的第一个值，第二个参数代表第二个值，通				过判断大于还是小于，返回1，或者-1，或者0，来进行排序。

		reverse()：将数组中的数据进行反转。
```
​	5，数组中的迭代方法：

```javascript
		forEach()：//方法迭代数据，接收一个匿名函数，函数有三个参数，第一个参数是每一项数据，第二个参数						是每一项数据的角标，第三个参数是当前数组。
		
		filter（fiu 特）()：//筛选满足一定条件的元素，组成一个新的数组并且返回。接收一个匿名函数，函数								有三个参数，第一个参数是每一项数据，第二个参数是每一项数据的角标，第三									个参数是当前数组。
		
		reduce（瑞丢斯）()：//会迭代数组中的所有的项，然后构建一个最终的返回值，他接收一个匿名参数，函数								有四个参数，第一个参数是当前项的下一项，第二个参数是当前项，第三个参数									是每一项的索引，第四个参数是当前的数组。
		
		reduceRight()：//和reduce()的用法一样，只不过他是从最后一项开始遍历的。
```


## 2.7：【Date日期对象】

​	1，定义：通过new Date()来创建日期对象

​		。对象.getFullYear()：获取当前年份

​		。对象.getMonth（毛特）()：获取当前月份，月份是从0开始的

​		。对象.getDate()：获取当前日

​		。对象.getHours()：获取当前小时

​		。对象.getMinutes()：获取当前分钟

​		。对象.getSeconds()：获取当前秒

​		。对象.getDay()：获取当前星期几

​		。对象.getMilliseconds（猫音三坑的）()：获取毫秒值

​	

​	2，获取1970年1月1日到现在的总毫秒数（时间戳）通过以下方法获取

​		。对象.valueOf()

​		。对象.getTime()



## 2.8：【函数】

​	1，**函数的特点**

​		。函数如果只定义，而不调用的话是没有任何意义的。函数可以在任何的地方调用

​		。函数的格式：(声明函数)**function (函数名)fn(形参列表) {函数体}**

​	2，**函数的参数**

​		。形参：就是声明函数的时候，函数名括号里的参数，他用来接收调用函数的时候传递过来的实参

​		。实参：就是调用函数的时候，传递过来的真实参与运算的参数

​		。函数的参数让函数变得更加的灵活

​	3，**函数不传值**

​		。如果函数的形参有参数，而不传递实参的话，那么形参就是undefined的

​		。如果函数有返回值不打印也不接收的话什么也打印不出来

​	4，**函数的重载问题**：重载就是函数名字相同函数的参数个数不同和数据类型不同，调用的函数就不同。在js	     中没有函数重载的概念，在java和c语言中有



​	5，**函数的返回值**

​		。return：可以把函数内部的任何值返回，外部定义变量接收，但是在函数内部return下面的语句不会				   执行

​	6，**arguments**

​		。arguments（奥丢们次）：代码函数的实参的个数，通过arguments.length，在不确定函数的参数的								  个数的情况下可以使用，是一个伪数组可以循环遍历

​		。arguments.callee()：调用的是当前函数

​	7，**函数表达式**

​		1，概念：就是将等号右边的匿名函数赋值给左边的变量

```javascript
				var fn = function () {}
            
            //匿名函数
            	(function () {})()
```

​		

​	8，**作用域**

​		。**全局作用域**：能在script标签里的任何地方都可以访问到

​		。**局部作用域**：在快级作用域里面声明的变量叫做局部变量，在全局作用域中访问不到局部变量

​	9，**预解析**：将函数的声明和变量的声明不包括赋值，提升到当前作用域的最顶端



## 2.9：【对象】

​	1，介绍

​		。使用属性来描述事物的特征，使用方法来描述功能

​		。属性和方法的集合体

​	2，对象的俩种方式

​		。内置对象：就是通过创建一个对象，对象里面封装方法属性。



​		。实例对象：实例对象的方法，都被保存在每一个实例化的对象中，所有只能通过new关键字，实例化				       对象之后来调用方法。实例对象是通过面向对象的构造函数模板创建的。



​	3，对象添加数据的方法

```javascript
		obj["name"] = "aa";
	
        obj.name = "aa";
        
        var obj = {
           name : "aaa"
        }
```

​	4，获取对象数据的方法

```javascript
        obj["name"]

        obj.name
```


## 3.0：【基本数据类型和复杂数据类型】

​	1，**基本数据类型**

​		。基本数据类型保存在内存中的栈内存

​		。基本数据类型的赋值只是把当前的数据赋值了一份给了第二个变量，第二个变量再去如何操作这个值		    不会影响到第一个变量

​	2，**复杂数据类型**

​		。复杂数据类型保存到内存中的堆内存

​		。复杂数据类型的赋值，只是把对象的地址复制给了第二个变量，第二个变量操作这个对象，在第一个		    变量中也会体现出来



## 3.1：【Math对象】

​	1，方法：

```javascript
		// 随机向下取整
			Math.floor()

		// Math的其他方法
			Math（慢死）.round（软奥的）()：// 将小数四舍五入
            
            Math.ceil（赛奥）()：//向上取整
            
            Math.abs（啊不斯）()：//转成绝对值，将负数转成正数
            
            Math.max()：//求一列数的最大的那个数
```



## 3.2：【基本类型的包装】

​	1，概念：使用基本包装类型不能动态的添加属性，因为当前代码只在执行的一瞬间有效，所以如果添加属性			  的话并且返回的话会返回undefined。

​	

​	2，String()类型：

​		。不可变特点：定义一个变量给他赋值字符串，到下一步给他赋值为一个新的字符串，那么旧的字符串					   不会被覆盖，这样会影响性能问题

​		

​		。方法：

```javascript
			indexOf()：//查找字符串如果有就返回字符串的位置，如果没有就返回-1.
			
			lastIndexOf()：//跟indexOf()用法一样，只不过他是从最后一项开始查找的

			charAt()：//输入一个角标，返回角标位置的字符串
			
			charCodeAt()：//输入一个角标，返回角标位置的字符串的Ascroll码表的值
	
			split()：//以什么符号来对字符串进行分割，返回一个新的数组
			
			substring()：//截取字符串，第一个参数是从什么位置开始截取，第二个参数是截取到什么位置结束
			
			substr()：//截取字符串，第一个参数是从什么位置开始截取，第二个参数是截取多少个字符串。
			
			trim（踹木）()：//返回的是字符串的副本，会将字符串俩端的空格全部去掉
			
			replace()：//替换。第一个参数是要替换的字符串，第二个参数是要替换成新的字符串。第一个参数还							可以是一个正则表达式。
            
            padStart()：//字符串补全长度的功能，第一个参数是字符串的长度，第二个参数是如果不够长度用什							么去补全，在开头补全
            
            padEnd()：//字符串补全长度的功能，第一个参数是字符串的长度，第二个参数是如果不够长度用什么							去补全，在结尾补全
            
            trimStart()，trimEnd()：//一个是去除开头的空格，一个是去除结尾的空格，他们不会修改原来的										字符串，会返回新的字符串
```