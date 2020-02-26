# 1,Vue--------学习笔记

## 1.1：【vue是什么】

​	1，是一个用于创建用户界面的开源javascript框架，也是一个创建单页应用的web应用框架

​	2，**MVVM**：是Model-View-ViewMdel的缩写，它是一种基于前端开发的架构模式，其核心是提供对View和	      ViewModel的双向数据绑定这使的ViewModel的状态改变可以自动传递给View，就是所谓的双向数据绑	     定

​	

## 1.2：【vue的特点】

​	1，响应式数据：数据驱动视图，可以让我们只关注数据的变化

​	2，MVVM的双向绑定：数据变化则视图变化，视图变化则数据变化

​	3，指令：增强了html功能的新特性，一个指令对应一种功能

​	4，组件化开发：提高复用性，解耦，提升未来的开发效率



## 1.3：【vue的三种安装方式】

​	1，采用本地文件引入的方式直接下载到目录中引入

​	2，采用在线cdn引入的方式：cdn相当于把一个文件放到了全国各地，然后你离那里近就从哪里调拨给你。

​	3，采用npm的安装方式



## 1.4：【vue的使用过程】

​	1，先创建一个vue的实例，接收一个对象作为参数，对象的第一个参数是el：用来管理页面中那一个元素的	      部分，值通常是id选择器，也可以是类选择器，或者其他选择器。但是管理的视图不能是body或者html。

​			

```javascript
		let vm = new Vue({
		
			el : "#app",
		});
```


​	  2，对象的第二个参数是data：存储的都是响应式数据。可以通过mv.$data访问原始数据对象，vue中所有		的原始数据都带$.vue的实例vm也代理了data对象上的所有的属性，因此访问vm.a等同于vm.$data.a。		视图中显示的数据必须保存在data对象中

​				

```javascript
		let vm = new Vue({

			el : "#app",
		
			data : {
				
				name : "hahah"
			}
		});
```
​	

​		3，对象的第三个参数methods：用来定位方法的。vm也代理$methods中的所有的方法。

​		

```javascript
		let vm = new Vue({

			el : "#app",
		
			data : {
				
				name : "hahah"
			},
			
			methods : {

				add() {
					
					console.log("aaa");
				}
			},

		});
```


## 1.5：【插值表达式】

​	1，**概念**：将绑定在data中的数据插入到页面中。通过{{ name }}形式来插进去。

​	2，**优点**：如果元素本身有内容的话不会覆盖掉，只会替换插值表达式部分

​	3，**缺点**：如果网速慢的话，请求vue没有响应，页面不会显示数据，而是会显示插值表达式



## 1.6：【指令】

​	1，概念：扩展html5的功能一个指令一个功能。指令一般都设置在元素的身上

​	2，v-text="表达式"：里面的表达式会被当做变量来解析。

​		

```html
		特点：如果元素中本身有内容，那么会覆盖原来的内容。并且他不能识别标签
			<p v-text="msg"></p>
```

​	3，v-html="表达式"：里面的表达式会被当做变量来解析。

​		

```html
		特点：如果元素中本身有内容，那么会覆盖原来的内容。并且他能识别标签
			<p v-html="msg"></p>
```

​	4，v-if="表达式"：根据表达式是true还是false决定元素是删除还是创建。

​		

```html
		缺点：有较高的性能切换开销
			<p v-if="flag">小明明明明明明明</p>
```

​	5，v-show="表达式"：根据表达式是true还是false决定元素是隐藏还是删除。

​		

```html
		缺点：有较高的初始渲染开销
			<p v-show="flag">哈啊啊啊啊啊啊啊啊啊啊啊啊啊啊</p>
```

​	6，v-on：特定事件的指令。用来绑定事件的他的值必须是一个函数

​		

```html
		格式：v-on:事件类型="事件处理程序"
			<button v-on:click="show" v-on:mouseover="run">登陆</button>


		简写：@事件类型="事件处理函数"
			<div id="app" @click="app">         
```

​	7，事件修饰符

​		

```javascript
		.stop：//阻止事件冒泡。格式：@事件类型.stop
		
		.prevent：//阻止元素的默认的行为，格式：@事件类型.prevent

		.capture（砍破吃）：//实现事件的捕获机制来执行事件处理程序。格式：@事件类型.capture，给最外面							的元素设置
        
        .self：//只有触发了当前事件才会执行，冒泡上去的不会执行。格式：@click.self

		.once：//事件只能触发一次。格式：@click.once

		.enter：//只有按下回车键才会触发该事件

		.tab：//只有按下tab才会触发该事件

		.space：//只有按下space才会触发该事件

			@keyup.space="事件函数"

		//自定义按键修饰符
        	
        	Vue.config.keyCodes.end = 13;
			
			@keyup.end="add"
```

​	8，获取事件对象的俩种方法

​		1，定义事件函数的时候，第一个参数指定event，在@click="click"调用的时候，不加小括号，第一个参		      数默认就是事件对象

​		2，定义定义事件函数的时候，第一个参数指定event，在@click="click($event)"调用的时候，第一个参		       数，加上$就是事件对象，如果不加就是普通的传参

​	

​	9，v-bind:属性="表达式"：把vue中的data对象的数据绑定到元素的属性中

​			

```html
		简写格式：:属性="表达式"
			<div v-bind:style="style" @click="parent">
            
        通过他绑定的class属性可以给他传入一个数组，每一项要用单引号引起来 ，也可以传入对象，还可以用三元		   表达式
        	<div id="div2" v-bind:class="['get','add','delete']">
            
        当flag为true的时候该类名可以使用，为false不可以使用
        	<div id="div2" v-bind:class="{'get' : flag,'add' : false}">
```

​	10，v-model="表达式"：可以实现数据的双向绑定，只能给表单元素设置

​		

```html
		<input type="text" v-model="msg">

		修饰符：
		
			.trim：去除俩边的空格

			.number：将用户输入的值转为数值类型

			.v-model.trim="msg"

```

​	11，v-for="(变量, 索引) in 要遍历的项"：如果不需要索引的话，可以把小括号去掉

```html
		遍历数组	
			<p v-for="user in list">{{user.name}}</p>

		
		遍历对象
			<p v-for="(val,key,i) in obj">
```

​	12，v-for""和key属性的使用：如果没有这个属性的时候vue就使用就地复用策略，列表里的顺序发生改变的		时候，vue为了提升性能，不去移动dom元素，只是更新相应元素的内容节点。值必须是字符串类型或者		number类型。

​	

```html
			<div v-for="item in listData" :key="item.id">

				<p>{{item.id}}====<input type="checkbox" />=={{item.name}}</p>

			</div>
```
​	13，v-once指令：如果给元素加上该指令表示该元素只能被操作一次

​		

```html
		<p v-once>{{msg}}</p>
```

​	14，当v-if和v-for相遇：v-for的优先级会大于v-if。



## 1.7：【过滤器】

​	    **概念**：必须有返回值的函数，用来过滤出想要的部分

​	     	格式：{{msg + 1 +2 +3 | 过滤器名字}}或者 v-bind:属性="表达式 |`过滤器名称"。|：被叫做管道



### 	1.7.1：【局部过滤器】

​		1，**概念**：在Vue的实例对象中使用filters对象，里面定义过滤器函数，函数的名字就是过滤器。只能给				  当前vue的实例使用

​		

```javascript
			filters {

				get(value) {}
		    }
```
### 	1.7.2：【全局过滤器】

​		1，概念：可以给任意多个Vue的实例使用

​		2，用法：Vue.filter("名字", callback(value))：第一个参数是过滤器的名字，第二个参数是回调函数，函		      数的第一个参数始终都是需要过滤的值，调用的时候不需要传值，如果需要传递其他的参数，调用		      的时候就带上小括号，里面传值。但是第一个参数，永远都是过滤器左边的值。如果有多个过滤器，		     在元素上使用 | 分开

## 1.8：【ref属性】

​		1，概念：用来操作DOM。给元素定义ref属性，然后通过this.$refs对象中包含了DOM元素和信息

​		

```html
			<input type="text" ref="myText">
			
			通过this.$refs.myText方法获取
```

## 1.9：【自定义指令】

### 	1.9.1：【全局自定义指令】

​			

​			1，概念：可以给任意多的vue实例对象使用我们自己定义的指令

​			2，格式：Vue.directive("名字",{})：对象里面接收以下的参数函数

​					参数：el和bindding参数说明：

​						el：当前DOM元素

​						bindding：是一个对象。记录了指令的名字，值等信息



​			3，bind(el, binding) {}：只调用一次，指令第一次绑定到元素上时使用，可以进行一次性初始化的			      设置

​			4，inserted(el, binding){}：被绑定的元素插入到父节点时使用，保证父节点存在就行，不一定非要			      插入。

​			5，update(el, binding){}：当元素的值被改变完成之前调用

​			6，componentUpdated(el, binding)：当元素的值改变完成之后调用

​			7，unbind(el, binding){}：当指令与元素解绑时调用，只调用一次

### 	1.9.2：【局部自定义指令】

​			1，概念：只能给当前vue实例对象使用

​			

```javascript
				格式：directives : {

                    指令的名字
                    get : {

                        （1）bind(el, binding) {}：//只调用一次，指令第一次绑定到元素上时使用，可							以进行一次性初始化的设置


                        （2）inserted(el, binding){}：//被绑定的元素插入到父节点时使用，保证父节							 点存在就行，不一定非要插入。


                        （3）update(el, binding){}：//当元素的值被改变的时候调用


                        （4）componentUpdated(el, binding)：//当元素的值改变完成的时候调用


                        （5）unbind(el, binding){}：//当指令与元素解绑时调用，只调用一次

                    }

			      }		
```

## 2.0：【计算属性】

​	1，概念：监视属性数据的变化，当某个属性数据变化之后需要重新计算，并且将重新计算后的结果返回

​	2，作用：可以在计算属性中定义方法，来完成这些复杂的逻辑，调用的时候，不要加小括号，当属性一样去	       使用

​		

​		

```javascript
        computed : {
            watchData () {
                return data.name
            }
        }
```

## 2.1：【axios插件】

​	1，概念：用来放松ajax请求，异步获取服务器的数据
​		

```javascript
		格式：
        
        	xios.get({}),
                
            axios.post({}),
                
            axios.put({}),
                
            axios.delete({})
		
		参数：
        	
        	url: //请求的地址
            method: //请求的类型（get, post）
			data：//请求参数（请求体的参数）
            params：//请求的参数（请求头中的参数）
```

## 2.2：【json-server】

​	1，概念：可以快速的帮我们搭建一个后端的接口

​	2，安装和使用：

​			安装：**npm i -g json-server**

​			使用：创建一个json文件，并且在该目录下运行命令 josn-server --watch data.json能够快速的产生			一个接口

​	3，获取数据的格式：

​			1，查询数据  GET  /brands 获取db.json下brands对应的所有数据列表

​			2，GET /brands/1 查询id=1数据单条

​			3，删除数据 DELETE/brands/1 删除id=1数据

​			4，修改数据 PUT/brands/1 请求体对象

​			5，上传/添加 POST/brands 请求体对象

​	4，json文件数据的格式：

​		

```json
        {
            "phone": [

                    {
                        "name": "西瓜",
                        "date": "2019-12-11T01:16:42.622Z",
                        "id": 15
                    },

                    {
                        "name": "鸭梨",
                        "date": "2019-12-11T01:25:00.802Z",
                        "id": 16
                    },
            ]
        }
```



## 2.3：【mounted】

​	1，概念：是一个事件函数，当vue实例对象加载完毕的时候调用



## 2.4：【Vue.set()】

​	1，参数：

​		第一个参数：要更改的数据源

​		第二个参数：要更改的具体的数据

​		第三个参数：重新改变的值

​	2，概念：假如我们的button元素的按钮没有在vue的控制范围，并且data的对象定义到全局，这个时候，在	      button事件函数里面访问data里面数组带有下标的值的时候，vue是检测不到的，所有需要通过Vue.set()	      方法来设置



## 2.5：【Vue.config.keyCodes】

​	1，概念：用来自定义键盘修饰符，自定义的键盘修饰符等于键盘码

​			

```javascript
		Vue.config.keyCodes.end = 13;
```



## 2.6：【watch】

​	1，概念：用来监视初始化data对象里面数据的变化，监视那个属性就写那个属性。

​		

```javascript
   		
        watch: {
            // 第一个参数是发生变化后的新数据，第二个参数是变化之前的旧数据
            msg (newVal, oldVal) {
                console.log(newVal)
            }
        }
```

​	2，当值是复杂数据类型的话：他存储的是地址，地址没有变的话是不会触发的，所以需要深度监听。设置	     deep属性为true就是深度监听

```javascript
		watch : {
				
				num : {

					handler(newVal, oldVal) {

					}

					immediate : true,	// 页面初始化完毕，就马上执行一次

					deep : true,	// 深度监听
				}

			}
```


## 2.7：【watch于computed区别】

​	1，watch用于观察和监听页面上的vue实例，当你需要在数据变化响应时，执行异步操作，高性能消耗的操		作，那么watch是最佳的选择

​	2，computed可以关联多个实时计算的对象，当这些对象中的其中一个改变时都会触发这个属性。而且他可	      以缓存数据，或者需要处理监听数据之后的返回值的话。



## 2.8：【component】

​	1，概念：vue自定义的标签，通过is属性来决定绑定那个组件显示出来。如果is的值不是变量是直接的组件名	      字，需要加上单引号，因为组件的名字是字符串

​			

```html
		<component :is="comName"></component>
		<script>
            import zujian from '组件的地址'
            data () {
                return {
                    comName: 'zujian'	// 组件的名字
                }
            }
		</script>
```


## 2.9：【组件】

### 	2.9.1：【组件的特点】

​			1，复用性高

​			2，代码容易维护

​	

### 	2.9.2：【创建组件的二种方法】

​			1，第一种创建组件的方法：第一个参数是组件的名字，第二个参数是组件的模板

​			

```javascript
				Vue.component("myCom", Vue.extend({

					template : '<a href="#">组件</a>'
				}));
```
​	

​			2，第二种创建组件的方法：使用的是对象字面量的方法

​			

```javascript
			Vue.component("myCom", {
			
				template : '<a href="#">字面量模板-----{{msg}}</a>',

			});
```
### 	2.9.3：【全局组件】

​			概念：可以被所有的vue实例对象使用



```javascript
		Vue.component("myCom", {

			template : '<a href="#">字面量模板-----{{msg}}</a>',

		);
```
### 	2.9.4：【局部组件】

​		概念：只能在当前vue实例对象中使用



```javascript
	components : {
			
			//组件的名字
			login : {

				template : '<a href="#">私有的组件</a>'
		 	},
		
		},
```
### 	2.9.5：【组件data必须是函数】

​		因为：每一个vue组件都是一个vue的实例，通过new Vue()，引向同一个对象，如果data直接是一个对			    象的话，，那么一旦修改其中一个组件的的数据，其他组件的数据也会把值改变。如果data是一			    个函数的话，每个vue组件的data都因为函数有了自己的局部作用域，互不干扰



### 	2.9.6：【组件的嵌套】

​			概念：将定义的组件，嵌套到另一个组件中



```javascript
			//将组件渲染到页面
			<dong></dong>


			//父组件
			Vue.component("dong", {
                
							//将子组件嵌套到父组件中
				template : "<div>哈哈哈哈<dong-child><dong-child><child></child></div>"
				
				//可以继续定义局部组件
				components : {

					"dongChild" : {

						template : "#com1-1",

					}
				},

			});

			
			//子组件
	
	
			Vue.component("child", {

				
				template : "<p>哈哈哈</p>"
	
			});
```
### 	2.9.7：【父组件给子组件传值】

​			概念：通过props来接收父组件的值，就是接收new Vue()中的data中的值，通过绑定属性的方法绑				    定的模板上去，属性的值必须是data中的属性

​			

```javascript
		//将组件渲染到页面通过绑定属性来传值
		<dong :name="msg"><dong>
            
		Vue.component("dong", {
			template : "<div>hahahha</div>"
			//通过他来接收父组件的传值，通过this.name来获取到
			props : ["name"]
		});

		let vm = new Vue({
			el : "app",

			data : {

				msg : "hahah"
			},

		});
```
### 	2.9.8：【子组件给父组件传值】

​		概念：子组件通过自定义事件将数据传入到函数中，父组件通过监听函数获取子组件传递的参数

​		

```html
	将组件渲染到页面中去
	<button @click="add"></button>

	<dong @type="fn"></dong>
	<script>
		Vue.component("dong", {	

			template : "<div>哈哈哈哈</div>",

			methods : {

				add() {

					//触发自定义事件，让父元素来追踪子元素的数据

					this.$emit("type", 传递过去的参数);
				}
	
			}
		});
        
        
        
        let vm = new Vue({
	
			el : "app",

			data : {
					
				msg : "hahah"
			},

			methods : {
	
				fn(传递过来的参数) {

					追踪子组件参数的函数
				
					console.log(传递过来的参数);
					
				}
			}
		});
	</script>
```
## 3.0：【spa(路由)】

​	1，概念：只有一个web页面的应用，是加载单个html页面，并在用户与应用程序交互时，动态更新该页面的		          web应用程序

​	

​	2，优点和缺点：



​		优点：

​			。减轻服务器端的压力

​			。提高了页面的渲染效果

​			。提高了用户的体验

​		

​		缺点：

​			。首次加载页面很慢

​			。SEO搜索引擎不友好

​	

### 	3.0.1：【spa实现原理】

​			1，浏览器中的哈希值与展示视图内容之间的对应规则。路由就是hash和component的对应关系

​		

### 	3.0.2：【vue-router】	

​			1，概念：是vue.js官方的路由管理器，第三方的插件

​			2，使用步骤：

​				

```html
				<div id="app">

			 		<!-- 第一步设置路由的导航 -->
                 	<router-link to="/food">食物</router-link>
                    
                  	<!-- 第二步设置一个容器，容器必须有 -->
    			 	<router-view></router-view>

				</div>
				<script>
                    //第三步实例化一个rooter路由对象
                    let router = new VueRouter({

                        //第四步配置路由列表

                        routes : [

                            {	
                                //path是路径

                                path : "/food", 

                                //组件

                                component : {

                                    template : `<div>猪肉鱼肉鸭头</div>`,
                                }

                            },

                        ]
                    });
                    
                    let vm = new Vue({

                        el : "#app",

                        data : {},

                        methods : {},

                        //最后将router的实例挂在vue实例上
                        router : router
                    });
	
                </script>
```

​		

### 	3.0.3：【动态路由】



​		1，概念：组件标签携带的参数不同，但是可以进入同一个组件，可以动态的控制组件。那么path路径就				  不能写死，如果要接收参数，在接收参数的部分加上:冒号，之后就是一个变量了，可以获取			          不同组件标签访问同一个路由，并且可以获取到他们传递过来的参数

​		

```html
			<div id="app">
	
                <router-link to="/city/上海">上海</router-link>

                <router-link to="/city/北京">北京</router-link>

                <router-link to="/city/张家口">张家口</router-link>

                <router-view></router-view>
            </div>

			<script>
                let router = new VueRouter({

                    routes : [

                        {	
                            //此时的name就成为了一个变量，可以接收组件标签传递过来的参数	

                            path : "/city/:name",

                            component : {

                                template : 

                                   ` <div>你点击的城市是{{$route.params.name}}</div>`
                            
                            }
                        }
                    ],
                });	
                
                let vm = new Vue({

                    el : "#app",

                    data : {},

                    methods : {},

                    router,
                });
	
			</script>
```
### 	3.0.4：【query接受和传参数】

```html
		<div id="app">

             <router-link to="/login?id=10&name='小美'">登录</router-link>

             <router-view></router-view>
		</div>	

		<script>
            let router = new VueRouter({

        		routes : [

            		{
                		path : "/login",
                		component : {

                    		template : "<div>{{$route.query.name}}组件</div>",

                    		created() {

                        		//第一种接收参数的方式

                        		console.log(this.$route);
                        		console.log(this.$route.query.id);

                 
                    		}

                		}

            		}

        		]
    		});
            
            let vm = new Vue({

        		el : "#app",

       			data : {},

        		methods : {},

        		router,
    		});
		</script>
```
### 	3.0.5：【props】

​			1，概念：使用props来实现路由传值和接收值：通过这种方式来实现传值刚方便，因为使用了			          	this.$route这种方式获取数据相当于和vue-router进行了耦合



​			2，路由组件：只要在配置路径的时候，设置props属性为true，路径后面要跟变量，通过props来			      获取，直接通过this.id获取

​			

```html
				<div>
 				 	<!--路由接收的参数是：{{ this.id }}-->
 				</div>
				<script>
                    export default {

                        data() {

                            return {

                            }
                        },

                        //接收每一个连接过来的组件，并且获取该参数

                        props : ['id'],

                    }
                </script>


				<!--连接到路由组件的组件：-->
				
                    <router-link to="/dong/冬哥">冬哥</router-link>

                    <router-link to="/dong/小颖">小颖</router-link>

                    <router-link to="/dong/小美">小美</router-link>
				

				<!--配置路由参数组件(index.js)：-->
			
				
					<script>
						{ path: "/dong/:id", props: true, component: childRouter }
					</script>
```

###  	3.0.6：【vue-router-to】	

​			1，路由组件标签vue-router-to属性赋值的几种方式：

​					1，普通字符串：就是死的路径，不能接收传递的参数

​						

```html
						<div id="app">
	
                            <router-link to="/city/name">上海</router-link>

                            <router-link to="/city/name">北京</router-link>

                            <router-link to="/city/name">张家口</router-link>

                            <router-view></router-view>
                        </div>

						<script>
                            
                            let router = new VueRouter({

                                routes : [

                                    {
                                        
                                     //此时的name就成为了一个变量，可以接收组件标签传递过来的参数	
                                        path : "/city/name",

                                        component : {

                                           template : `

                                             <div>你点击的城市是{{$route.params.name}}</div>
                                            `
                                        }
                                    }
                                ],
                            });		
                            
                            let vm = new Vue({

                                el : "#app",

                                data : {},

                                methods : {},

                                router,
                            });
						</script>
```
​						

​					2，对象形式

​						

```html
						<div id="app">
	
                            <router-link :to="{path : '/city/name'}">上海</router-link>

                            <router-link :to="{path : '/city/name'}">北京</router-link>

                            <router-link :to="{path : '/city/name'}">张家口</router-link>

                            <router-view></router-view>
                        </div>
						
						<script>
							
                            let router = new VueRouter({

                                routes : [

                                    {		
                                        
                                      //此时的name就成为了一个变量，可以接收组件标签传递过来的参数
                                        
                                        path : "/city/name",

                                        component : {

                                           template : `

                                             <div>你点击的城市是{{$route.params.name}}</div>
                                            `
                                        }

                                    }

                                ],

                            });	
                            
                            let vm = new Vue({

                                el : "#app",

                                data : {},

                                methods : {},

                                router,
                            });
						</script>
```
​					4，自定义属性：

​				

```html
						<div id="app">
	
                            <router-link :to="{name : 'abc'}">上海</router-link>

                            <router-link :to="{name : 'abc'}">北京</router-link>

                            <router-link :to="{name : 'abc'}">张家口</router-link>

                            <router-view></router-view>
                        </div>

						<script>
                            
                            let router = new VueRouter({

                                routes : [

                                    {		
                                        
                                      //此时的name就成为了一个变量，可以接收组件标签传递过来的参数

                                        path : "/city/name",

                                        name : "abc",						

                                        component : {

                                          template : `

                                             <div>你点击的城市是{{$route.params.name}}</div>
                                            `
                                        }
                                    }
                                ],
                            });		
                            
                            let vm = new Vue({

                                el : "#app",

                                data : {},

                                methods : {},

                                router,
                            });
						</script>
```

​					5，对象带参数：

​							

```html
						<div id="app">

                            <router-link
                            	:to="{name : abc, params : {name : "上海"}}"
                            >
								上海
							</router-link>

                            <router-view></router-view>

                        </div>

						<script>
							
                            let router = new VueRouter({

                                routes : [

                                    {		
                                        
                                      //此时的name就成为了一个变量，可以接收组件标签传递过来的参数	
                                        path : "/city/:name",					

                                        name : "index",

                                        component : {

                                          template : `

                                             <div>你点击的城市是{{$route.params.name}}</div>
                                            `
                                        }
                                    }
                                ],
                            });	
                            
                            let vm = new Vue({

                                el : "#app",

                                data : {},

                                methods : {},

                                router,
                            });
                            
						</script>
```
### 	3.0.7：【路由的重定向】

​			1，概念：当希望某个页面被强制中转时，可采用redirect进行路由重定向设置，在配置路由对象中			      设置，是一个属性，值是要强行跳转的地址

​			

```html
				<div id="app">
	
                    <router-link to="/city/sh">上海</router-link>

                    <router-link to="/city/bj">北京</router-link>

                    <router-link to="/city/zjk">张家口</router-link>

                    <router-view></router-view>

				</div>

				<script>
					
                    let router = new VueRouter({

                        routes : [

                            {
                                path : "/city/sh",

                                component : {

                                    template : "<div>您取得是上海<div>"
                                }
                            },

                            {
                                path : "/city/bj",

                                //设置重定向当路由到北京的时候拦截重定向到张家口

                                redirect : "/city/zjk",

                                component : {

                                    template : "<div>您取得是北京<div>"
                                }

                            },

                            {
                                path : "/city/zjk",

                                component : {

                                    template : "<div>您取得是张家口<div>"
                                }

                            }
                        ],
                    });			
                    
                    let vm = new Vue({

                        el : "#app",

                        data : {},

                        methods : {},

                        router,

                    });
				</script>
```
### 	3.0.8：【编程式导航】

​			1，概念：跟router-link一样，都能实现组件之间的跳转，router-link是根据a标签进行跳转的，而			      导航式通过绑定click事件，调用$router来进行跳转的。this.$router可以拿到当前路由的实例

​		

​			2，跳转的方法：

​			

```html
				。this.$router.push(path)：//往历史记录了推了一条记录，如果点击浏览器的返回上一页按				    钮，可以返回上一页

				。this.$router.replace(path)：//替换了当前的记录历史记录并没有多，但是地址会变

				。this.$router.go(number)：//代表是前进还是后退，数字大于0是前进，小于0是后退
                

                <div id="app">
			
                    容器必须有
                    <router-view></router-view>
                </div>

				<script>
                    
                    let objA = {

                        template : `<div>

                            我是A页面我要去B页面
                            <button @click="goB">去B页面</button>	
                        </div>`,

                        methods : {

                            goB() {

                                //使用push方法会有历史记录，可以返回到上一个页面
                                this.$router.push("/B");

                                //第二种方法

                                // router.push("/B");
                                console.log(this.$router);
                            }
                        }
                    }
                    
                    let objB = {

                        template : `

                            <div>我是B，我要去C

                                <button @click="goC">去C页面</button>
                            </div>
                        `,

                        methods : {

                            goC() {

                                // replace：替换当前的记录
                                this.$router.replace("/C");
                            }
                        }

                    }
                    
                    let objC = {

                        template : `<div>C页面，我要去A页面

                            <button @click="goA"></button>
                        </div>`,

                        methods : {

                            goA() {

                                // go：后退后退多少页，大于0是前进，小于0是后退
                                this.$router.go(-1);
                            }
                        }
                    }
                    
                    //配置路由表
                    let router = new VueRouter({

                        routes : [

                            {path : "/", redirect : "/A"},
                            {path : "/A", component : objA},
                            {path : "/B", component : objB},
                            {path : "/C", component : objC}
                        ],
                    });
				</script>
```

### 	3.0.9：【路由激活样式】

​			1，概念：可以改变当前点击组件的class样式

​			

```html
			<script>
				
                let router = new VueRouter({

                    //通过linkActiveClass可以改变组件标签的class属性
                    linkActiveClass : "dong",	

                    routes : [

                         //当点击北京的时候强制重定向到重庆

                        {path : "/bj", redirect : "cq", component : temp},

                        {path : "/sh", component : temp2},

                        {path : "/cq", component : temp3}

                    ]
                });
                
                let vm = new Vue({

                    el : "#app",

                    data : {},

                    methods : {},

                    router,
                });
			</script>
```
### 	3.0.10：【路由的嵌套】

​			1，概念：通过children可以在父级路由配置子级路由，他是一个数组，数值里面配置子路由的信息

​				

```javascript
						let router = new VueRouter({

                            routes : [

                                {
                                    path : "/city/bj",

                                    //设置二级路由导航

                                    children : [

                                        {
                                            path : "cp",

                                            component : {

                                                template : "<div>昌平区</div>"
                                            }
                                        },

                                        {
                                            path : "hd",

                                            component : {

                                                template : "<div>海淀区</div>"
                                            }
                                        },

                                        {
                                            path : "cy",

                                            component : {

                                                template : "<div>朝阳区</div>"
                                            }
                                        },

                                    ],

                                    component : {

                                        template : "<div>

                                            <p>这是北京</p>

                                            //设置二级组件标签
                                            <router-link to="cp">昌平</router-link>

                                            <router-link to="hd">海淀</router-link>

                                            <router-link to="cy">朝阳</router-link>

                                        </div>"
                                    }

                                }
                            ]
                        });

						let vm = new Vue({

                            el : "#app",

                            data : {},

                            methods : {},

                            router,
                        });
```
## 3.1：【命名视图】

​	1，概念：拥有多个视图容器(<router-view></router-view>)，布局页面就应该有很多的视图，在视图		          中防止其他的内容，这个时候就需要用到命名视图。简单说就是给容器加上name属components			  中定义的模板

​			

```javascript
			let header = {
    			template : "<div class='head'>头部</div>"
    		}
            
   			let nav = {
        		template : "<div class='nav'>导航条</div>"
   			}
            
   			let news = {
       			template : "<div class='news'>新闻部分</div>"
    		}
            
            let router = new VueRouter({

        			routes : [

            			{
               				path : "/",
                			components : {

                    			//default属性是vue自带的属性，其余的属性我们可以自己定义

                    			//通过name属性绑定到容器组件标签上。default属性表示是默认的意思

                    				"default" : header,

                    				"nav" : nav,

                    				"news" : news

                				}
            				}
        			]
   			});
			
			let vm = new Vue({

        		el : "#app",

       			data : {},

      			methods : {},

        		router

    		});
```
## 3.2：【vue-cli工具的介绍】

​	1，概念：是一个开发脚手架，是一个开发辅助工具用于自动生成**vue.js+webpack**的项目模板

​	2，安装方法：

​			。全局安装：**npm i -g @vue/cli** 默认的版本是4.0+

​			。补全2.0版本：**npm i -g @vue/cli-init** 把2.0的版本也补上

​	3，使用脚手架：

​			。使用2.0版本

​					1，**vue init webpack-simple** 项目名称    创建一个项目

​					2，**cd** 项目名称 切换到当前的项目

​					3，**npm i**   安装依赖

​					4，**npm run dev**   启动运行项目

​			。使用4.0版本

​					1，**vue create** 项目名称     创建项目

​					2，**cd** 项目名称     进入项目

​					3，**npm run serve**    启动项目

​		

​		4，项目目录的介绍：

​			。**bablelrc**：es6特性浏览器还没有全部支持，但是使用es6是大势所趋，

​						所以babel用来将es6代码转成浏览器能够识别的代码



​			。**editorconfig**：存放的是编译器的配置信息

​			。**gitignore**：可以添加一些不需要提交的项目的文件。

​			。**index.html** ：单页应用的html

​			。**package.json**：用于存放依赖信息及其它的项目信息

​			。**README.md**：项目的介绍信息

​			。**webpack.config.js**：wepack工具的配置文件。webpack是一个前端工程化的工具  

​								  编译代码 -压缩代码- 处理代码,其他....

​		

​			。**webpack**：代码编译,打包 压缩



## 3.3：【ES6模块的导入和导出】

​		1，模块的导入：import 变量 from 路径  来引入组件

​		2，使用export default来导出我们的组

​	

## 3.4：【vue单文件和入口解析】

​		1，**main.js**：整个项目的入口文件

​		2，**App.vue**：整个项目的根组件

​		3，**单文件组件**：一个.vue的文件就是一个组件

​		4，**注意**：vue选项中的render函数若是存在，则Vue构造函数不会从template`选项或通过 `el` 选项指定		                  的挂载元素中提取出的 HTML 模板编译渲染函数

​		5，**介绍**：

​			。在cli开发模式下，一个.vue就是一个文件就是一个组件

​			。template 组件的页面结构 代表它的 html 结构

​			。必须在里面放置一个 html 标签来包裹所有的代码

​			。我们在其他地方写好了一个组件，然后就可以在当前template中引入

​			。script ：组件的逻辑结构及数据对象

​			。style 组件的样式：就是针对我们的 template 里内容出现的 html 元素写一些样式



## 3.5：【vue的插槽】

### 	3.5.1：【匿名插槽】

​			1，概念：会将组件中的内容对应的放到定义插槽的位置，通过在子组件中定义solt标签，在父组件					  中引入子组件，在子组件中填入内容，就可以填到插槽里

​		

```html
			<!--子组件中：-->
                <div>

                    <p>今天是<slot></slot></p>

                </div>

			<!--父组件中：-->
				 <child>
					
					<!--在子组件中填值，会填入到子组件中定义的插槽-->

            		<span style="font-size: 20px;color: green;">你笑啥</span>

            		<span style="font-size: 20px;color: blue;">星期一</span>

            		<span style="font-size: 20px;color: red;">星期二</span>

        		 </child>
```


### 3.5.2：【默认值的插槽】

​	1，概念：就是插槽本身带有默认值，如果在父组件中引入，并且重新填值的话，那么插槽带有的默认值会被			  覆盖
​		

```html
		<!--子组件中：-->
            <slot>
                    <!--此时的子组件带有默认值-->

                    <span style="color: red;">高兴</span>

            </slot>
            
 		<!--父组件中：-->
			<div>	
				<!--没有填入值的子组件标签，使用的是默认值-->
				<child></child>

        		<child></child>

        		<child></child>
					
				<!--填入值的子组件标签使用的是填入放入值-->
        		<child>难过</child>

			</div>
```
### 	3.5.3：【具名插槽】

​		1，概念：可以自由的通过slot属性指向子组件中定义插槽带有name属性相匹配的值，可以自由的选择				  性，填插槽

​				

```html
			<!--子组件中：-->
			<div>

				<p><slot name="dong"></slot></p>

  					<p><slot name="xue"></slot></p>

 					<p><slot></slot></p>

			</div>
			
			<!--父组件中：-->
			<div>
			
				<child>
						
				   <!--通过slot的值和子组件中的插槽的name属性相对于的填值，slot属性要定义在标签上-->
					
            		<span slot="xue" style="font-size: 30px;color: red;">我是尉明慧</span>

            		<span slot="dong" style="font-size: 30px;color: blue;">我是尉明</span>

            		<span style="font-size: 30px;color: yellow;">冬哥</span>

        		</child>

			</div>
```
​	

### 	3.5.4：【作用域插槽】

​			1，概念：可以将子组件中定义的数据传入到父组件中。子组件中定义插槽的时候，可以绑定自定义					  属性，将data中的值，当做变量。在父元素中通过slot-scope属性来获取值他的属性值随					  便起，拿到是一个对象，也是要在标签上定义属性。

​			

```html
				<!--子组件中：-->

				<!--title属性和age属性就是要传过去的值-->

				<p>传给父元素的参数是：<slot name="name" :title="name" :age="age"></slot></p>
				
				<!--父组件中：-->
				 <child>
						
					<!--通过slot-scope属性获取值，再传回到子组件的插槽中-->

            		<span slot="name" slot-scope="obj">{{obj.title}}==={{obj.age}}</span>

        		</child>
```
​			2，注意点：如果在vue中使用console.log()方法报错的话，解决方法使用window.console.log()来					     解决。



## 3.6：【Element-UI】

​	1，概念：是一个基于vue的pc端的轻量级组件库

​	2，安装和使用：
​			

```javascript
		npm i element-ui -S

		import 'element-ui/lib/theme-chalk/index.css';

		// 按需加载引入使用
			
			//需要在babel.config.js配置以下
				
				plugins: [
                    [
                      'component',
                      {
                        'libraryName': 'element-ui',
                        'styleLibraryName': 'theme-chalk'
                      }
                    ]
                  ]
			
			// 然后安装以下使用
				
				import Vue from 'vue';
				import { Button, Select } from 'element-ui';
				
				Vue.use(Button)
				   .use(Select)
```


## 3.7：【Eslint插件】

​		1，概念：是用来统一javascript代码风格的工具，不包含html和css等，在vscode中安装此插件

​		2，使用：打开vscode配置文件 settings.json,配置这些数据，在首选项然后设置，上面有一个打开设置

​			

```javascript
			"eslint.enable": true,
			"eslint.autoFixOnSave": true,
			"eslint.run": "onType",
			"eslint.options": {
					"extensions": [".js",".vue"]
			},
			"eslint.validate": [
					{ "language": "html", "autoFix": true },
					{ "language": "javascript", "autoFix": true },
					{ "language": "vue", "autoFix": true }
			 ]
```


## 3.8：【项目中文件的介绍】

​		1，.**browserslistrc** ：该文件会被 Babel 和 Autoprefix 用来根据浏览器的版本确定需要转译的 							JavaScript 特性和 CSS 浏览器前缀

​		2，**.editorconfig** ：编辑器配置文件，编辑器会根据该文件选择编辑格式

​		3，**.eslintrc.js**： ESLint配置文件

​		4，**.gitignore**： Git忽略配置文件

​		5，**babel.config.js** ：Babel转码工具配置文件

​		6，**package-lock.json**： 包管理工具的锁定文件

​		7，**package.json**：包说明文件

​		8，**postcss.config.js**：postcss配置文件

​		9，**README.md**： 说明文档



## 3.9：【组件按需加载引入方式】

​		1，component: () => import('组件的名字')



## 4.0：【初始化git仓库】

​		1，首次提交：

​			。git remote add origin 远程仓库地址

​			。git push -u origin master   // -u 的意思是 记录当前的推送信息



## 4.1：【局部样式】

​		1，概念：因为在插件中设置样式都属于全局样式，若果其他的组件有相同的类名，样式就会冲突。所以				  需要设置局部样式。在style标签中设置lang属性值为less就可以使用less语法，在设置scoped				  属性为局部样式

​		

## 4.2：【install】

​		1，概念：设置全局组件。Vue.use()方法就是内部调用的这个方法它是一个函数，接收一个参数Vue，然				  后在他的内部注册组件，就可以在全局中访问到

​		

```javascript
				export default { 
                    install(Vue){
                    
                        Vue.component(组件名，组件)
                        Vue.component()
                    }
				}
```
  

## 4.3：【img的src属性问题】

​		1，如果给图片的src属性设置固定的值字符串，会将 img 的src属性值 编译成base64字符串，可以预览

​		2，如果img的属性是动态的值，变量再用三元表达式的时候判断的时候，再给另外一个路径的话是一个		      相对路径的话，那么这个路径不能让图片显示

​		3，使用 require导入图片的路径，赋值给一个属性，然后去做三元表达式判断



## 4.4：【导航守卫】

​		1，概念：从一个路由跳转到另一个路由的时候触发此守卫

​		2，router.beforeEach()：全局守卫。接收一个参数是函数，有三个参数，第一个参数（to）是要跳去的							     路由对象，第二个参数是from（要离开的路由对象）第三个参数是next是回							     调函数。必须调用否则就会死在这里。直接调用next()可以继续执行，如果里							     面传入参数路径的话，就是拦截在该路径中



```javascript
			import router from './router'

			// 全局前置守卫

			router.beforeEach(function (to, from, next) {
				// 判断 拦截的范围

  				if (to.path.startsWith('/home')) {
  					// 进入到了拦截范围

					// 判断是否登录 有token 就登录 没token就没登录

					let token = window.localStorage.getItem('user-token') // 获取token

						if (token) {

  							// 如果有token

  							next()

						} else {

  							next('/login') // 没有token 就跳转到登录页

						}
				} else {
					next() // 放行
				}
			})
			
			// 先导出
			export default router
```

  

## 4.5：【axios拦截器】

​	1，概念：项目中所有的请求，会先到拦截器中做处理，然后通过return的方式，再把请求放行到服务器中

​	2，作用：如果有很多的请求的参数一致的话，就不需要在每一个请求中设置相同的参数，在请求到拦截器的	      时候，统一的把参数注入

​	

​	3，**axios.interceptors(音特三坡特斯).request.use()**：第一个参数是一个成功的函数，请求的拦截器里面		函数接收一个参数config，包含了所有请求的信息，可以给他注入相同的请求参数，然后返回即可，第二		个函数时错误的函数	

​	4，**axios.interceptors.response.use()**：响应拦截，跟请求拦截的参数一样，请求回来的数据会先到拦截	      器里面，做相应的处理然后返回到请求中



## 4.6：【javascript大数字问题】

```javascript
		// 安装
			npm i json-bigint

		//引入使用
			import JSONBig from 'json-bigint'

		//在到达响应拦截之前设置修改响应数据
			axios.defaults.transformResponse: [function (data) {
    				// data 是响应回来的字符串
  				return jsonBigInt.parse(data)

  			}],
```

 

## 4.7：【EventBus】	

​		1，概念：公共事件池，如果使用this.$emit()只能在当前实例监听，无法让其他的组件监听，如果想要b				  组件监视a组件必须使用事件公共池

​		2，使用：

​			。先创建一个js文件，并且引入vue，然后将创建的vue的实例导出去

​			。在需要用到的组件中导入，导入的包名.emit(事件名，参数)

​			。接收方使用导入的包名.$on(传过来的事件名,callback)



## 4.8：【nprogress进度条】	

```javascript
	// 安装
		npm install --save nprogress

	//引入使用
		import nprogress from 'nprogress'
	
	// 引入样式
		import 'nprogress/nprogress.css'
	
	//使用插件：在导航守卫里面创建，当路由改变的时候触发

		//在beforeEach里面调用nprogress .start()开始，在afterEach里面调用nprogress .done()结束

	
```
 

## 4.9：【async和await】	

​		1，概念：解决ajax回调函数的问题await会造成代码的堵塞，必须要给父级函数设置async配合使用，				  await强制的把代码从异步变成了同步

​				

```javascript
			async delData (id) {

                await this.$confirm('真的要删除吗，删除之后无法找回？')

                await getIdArticleInfo(id, 'delete')

                // 重新渲染页面

                 this.packageFactorParams()

			},
```


## 5.0：【webpack】

​	1，概念：项目打包：npm run build使用这个命令可以对项目打包，出现一个dist文件夹，里面是打包好的js			  文件和css文件等



## 5.1：【动态添加响应式数据】

​		1，概念：就是数据是动态生成的，并没有在data函数中定义，但是动态添加的数据必须在必须在对象中

​		2，通过this.$set(父级对象，属性，初始值)方法

​		3，先使用this.obj.name = 值，然后调用this.$forceUpdate()强制更新视图



## 5.2：【this.$nextTick(callback】

​		1，概念：放在回调函数执行的代码是等到dom更新完成之后再执行



## 5.3：【Vuex的使用】

​		1，概念：

​			。是一个专为vue.js应用程序开发的状态管理模式，他采用集中式存储管理应用的所有组件的

​			。实现组件之间的通信，用来定义组件之间需要共享的数据

​		2，使用：

​			

```javascript
			// 安装vuex
				npm i vuex
            
            // 使用vuex的包：在一个单独的js文件中引入vuex的包，使用Vue.use()全局注册
                
            // 导出一个vuex的的实例对象：通过new Vuex.Store({})创建一个vuex的实例，然后挂到vue实例					上
                	
                	const store = new Vuex.Store({
  
                        //类似于组件中的 data

                        state: {
                                count: 0
                        }
                    });

                    export default store;
```
​		3，vuex的属性介绍：

​				。state: {}：用来定义共享的数据。在组件中使用：通过$store.state.定义的属性

​				。mutations: {}：用来定义函数逻辑，但是函数里面不能有异步的操作。函数的第一个参数永								远都是state通过他可以拿到state里面的值。在组件中使$store.commit('函								数的名称', 参数)，函数只能接受一个参数

​			

​				。actions: {}：用来定义函数函数里面定义异步操作，但是不能在actios里面的函数里面修改							  state里面的值，只能来调用mutations里面定义的函数。定义的函数的第一个							  参数永远都是store实例。在组件中使用：$store.dispatch("函数名", 参数)

​			

​				。geeter:{}：是vuex的计算属性

​				。modules: {}：模块化vuex，可以让每一个模块拥有自己的state、mutation、action、							     getters,使得结构非常清晰，方便管理。



## 5.4：【v-mode的高级使用】

​	1，使用：就是在组件中绑定v-model

​		。第一步相当于把父组件中的内容传递到子组件，子组件通过value来接收，:value="active"

​		。第二步会默认的接收一个input的自定义事件，子组件可以订阅这个事件，父组件通过@input来接收

​		。v-mode就是上面俩步的缩写，也就是子父组件之间的通信



## 5.5：【VeeValidate表单验证】

​	1，在vue.js的学习中的cookbook里面的表单验证部分

​	

```javascript
		// 安装
			npm install vee-validate --save
            
        // 需要以下的配置在单独的js文件中
           		import Vue from 'vue'

			// 加载需要使用的验证组件
				import { ValidationProvider, ValidationObserver, extend } from 'vee-validate'
			
			// 加载内置的验证规则
				import * as rules from 'vee-validate/dist/rules'
			
			// 加载中文语言包
				import { messages } from 'vee-validate/dist/locale/zh_CN.json'
			
			// 注册全局组件

			// 包裹每一个要验证的文本框,name属性用来写提示的字段 rules来写验证规则，有多个规则用|管道				符隔开,值都是字符串类型
				Vue.component('ValidationProvider', ValidationProvider)
			
			// 使用他来包裹整个表单元素
				Vue.component('ValidationObserver', ValidationObserver)
			
			// 配置验证规则和中文提示消息
                Object.keys(rules).forEach(rule => {

                    extend(rule, {

                            ...rules[rule],

                            message: messages[rule]
                    })
                })

			this.$refs.myForm.validate()：//通过他来手动验证是否通过
            
			this.$refs.myForm.errors：//可以获取到错误的信息，但是要放在一次性定时器中，因为有时间差										异，获取到的是数组
			
			//验证单个选项
                import { validate } from 'vee-validate'
	
			//第一个参数是验证的选项，第二个参数是验证规则，第三个参数里面是参数配置，可以配置name的字段				提示
                const validateRules = await validate(mobile, 'required|mobile', {

                        name: '手机号'
                })
            
            
            //自定义验证规则
                extend('mobile', {

                    validate: value => {

                            return /^1(3|5|6|7|8|9)\d{9}$/.test(value)

                    },

                    // {_field_}表示在ValidationProvider上面定义的name属性的值，要验证的字段值

                    message: '{_field_}格式有误'
                })
            
            

		// 官方文档：
		// https://logaretm.github.io/vee-validate/guide/rules.html#importing-the-rules

		
```


## 5.6：【lodash函数工具库】

​	1，官方文档：https://lodash.com/

​	2，翻译的中文文档：https://www.lodashjs.com/

​	3，优点：支持按需加载



## 5.7：【webSocket】

​	1，概念：是一种在单个TCP连接上进行全双工通信的协议。

​	2，作用：使得客户端和服务器之间的数据交换变得更加简单，允许服务器主动向客户端推送数据

​	3，优点：

​			。较少的控制开销

​			。在连接创建后，服务器和客户端交换数据时，用于协议控制的数据包头部较小

​			。可以支持扩展

​			。还有更好的压缩效果



## 5.8：【组件的缓存】

​	1，概念：需要将路由容器使用组件缓存组件包裹起来

​	2，使用：在vue中提供了一个组件<keep-alive></keep-alive>将路由容器包起来，可以将组件缓存起	      	    来，并且不会销毁，保存到了内存中

​	

​	3，有以下的属性配置：

​		。**include**：只有name名称匹配的组件会被缓存，他的值是一个数组或者对象，给组件设置name				      名将组件的name名称放的数组中即可

​		。**exclude**：用来匹配name名称的组件不会被缓存

​		。**max**：最多可以缓存多少组件实例

​	4，当组件在缓存组件中切换：他的activated和deactivated这俩个声明周期函数将会被执行



## 5.9：【打包发布】

​	1，npm run build或者yarn build

​	2，将dist目录放到web网中测试：

​			。安装：npm install -g serve

​			。使用：serve -s dist在当前目录下运行，默认的端口号为5000

​			。也可以自己使用node.js



## 6.0：【异步组件并且动态显示】

​	1，概念：点击那个异步组件那个异步组件加载，若果给<component></component>包上了组件缓存，只			  要退出页面组件就会被销毁，若果待在该页面就是缓存状态

​			

```javascript
		components: {
		
			// 异步组件

			userCollect: () => import('./components/user-collect'),

			userHistory: () => import('./components/user-history'),

			userWorks: () => import('./components/user-works')
         },
             
         
         // 动态显示		

		<component :is="arrayAssembly"></component>
		
		
		// 组件的名字

		computed: {

    			arrayAssembly () {

      				return ['userCollect', 'userHistory', 'userWorks'][this.active]

    			}

  		},
```

 

## 6.1：【prefetch】

​	1，概念：用来告诉浏览器页面加载完毕后，利用空余的时间提前获取用户访问的内容

​	2，简单的用法：

```html
		<link rel="prefetch" href="./h5.html">	
```
​	3，优点：可以利用空闲的时间去加载，其他的资源

​	4，缺点：会浪费用户很多的流量，因为用户并不需要访问很多的页面，但是全部加载好了，会消耗流量

​	5，如果不想要的话，在项目的根路径，需要参加vue.config.js然后配置以下内容

​			

```javascript
		module.exports = {
			chainWebpack: config => {
				// 移除 prefetch 插件

					config.plugins.delete('prefetch')

					// 或者

					// 修改它的选项：
					config.plugin('prefetch').tap(options => {

  						options[0].fileBlacklist = options[0].fileBlacklist || []

  						options[0].fileBlacklist.push(/myasyncRoute(.)+?\.js$/)

  						return options

					})
				}
		}
```

  		6，当 prefetch 插件被禁用时，你可以通过 webpack 的内联注释手动选定要提前获取的代码区块
			

​				import(/* webpackPrefetch: true */ './someAsyncComponent.vue')

​	

​		   7，注意：Prefetch 链接将会消耗带宽。如果你的应用很大且有很多 async chunk，而用户主要使用的			 是对带宽较敏感的移动端，那么你可能需要关掉 prefetch 链接并手动选择要提前获取的代码区块。

  			

## 6.2：【缓存和并处理】

​	1，概念：VueCLI 内置了cache-loader 会默认为 Vue/Babel/TypeScript 编译开启

​		文件会缓存在 node_modules/.cache 中——如果你遇到了编译方面的问题，记得先删掉缓存目录之后再		试试看。

​		thread-loader 会在多核 CPU 的机器上为 Babel/TypeScript 转译开启



## 6.3：【分析打包结果】

​	1，参考文档：https://cli.vuejs.org/zh/guide/cli-service.html#vue-cli-service-build

​	2，使用图形界面打包：执行命令vue ui打开图形化界面。再带项目的分析功能



## 6.4：【gzip压缩】

​	1，概念：HTTP协议上的GZIP编码是一种用来改进WEB应用程序性能的技术。大流量的WEB站点常常使用			 GZIP压缩技术来让用户感受更快的速度。这一般是指WWW服务器中安装的一个功能，当有人来访			 问这个服务器中的网站时，服务器中的这个功能就将网页内容压缩后传输到来访的电脑浏览器中显			 示出来，一般对纯文本内容可压缩到原大小的40%.这样传输就快了，效果就是你点击网址后会很快			 的显示出来.当然这也会增加服务器的负载.。一般服务器中都安装有这个功能模块的。

​	2，注意：文本文件压缩得非常好，通常会缩小两倍以上。另一方面，诸如JPEG或PNG文件之类的图像已经按			  其性质进行压缩，使用gzip压缩很难有好的压缩效果或者甚至没有效果。压缩文件会占用服务器资			  源，因此最好只压缩那些压缩效果好的文件。

​	3，开启gzip压缩：在打包的结果目录中执行下面的命令启动一个 HTTP 静态服务（默认开启 Gzip 压缩启动		服务）



​			命令：serve -s ./

​	4，禁用Gzip压缩：

​			使用 -u 参数禁用 Gzip 压缩

​			serve -s -u ./

​	5，压缩原理：

​		。不是每个浏览器都支持gzip的，如何知道客户端是否支持gzip呢，请求头中有个 Accept-Encoding 来		    标识对压缩的支持

​		。客户端http请求头声明浏览器支持的压缩方式，服务端配置启用压缩，压缩的文件类型，压缩方式

​		。当客户端请求到服务端的时候，服务器解析请求头，如果客户端支持gzip压缩

​			。响应时对请求的资源进行压缩并返回给客户端，浏览器按照自己的方式解析，在http响应头，

​			。我们可以看到 Content-encoding: gzip，这是指服务端使用了  gzip 的压缩方式。