###1、介绍JavaScript的基本数据类型。
        答：
             1. Number 数字类型
             2. String 字符串类型
             3. Boolean 布尔类型
             4. Function 函数
             5. Object 对象
             6. Null
             7. Undefined 没有定义类型
###2、说说写JavaScript的基本规范？
        答：
          1、命名规范：
             1-1，javascript文件：js后缀为.js中，尽量减少html中的js代码。因为存在js代码会明显增加文件大
             小，且不能对其进行缓存和压缩。
             1-2，缩进单位是4个空格。避免使用tab键来缩进。因为tab始终没有统一tab长短标准，空格会增加文
             件的大小，但是可以忽略。
             1-3,每行长度不超过80个字符。
             1-4。注释，让注释有意义
             1-5，变量声明。所有变量必须在使用前通过var进行申明。
             1-6，函数声明。所有函数在使用前进行声明。
             1-7，命名。大小写字母，10个数字和下划线组成。

          2、封装技巧
              js是脚本语言。基于ECMA脚本设计的语言，还能巧妙的设计实现一些面向对象语言的基本特性。
              例如：
              类，多态，继承。。。。

             2.1类：静态类和普通类
                2.1.1静态类
                通过一个简单的object对象来模拟一个静态类。
                //定义静态类
                var
                2.1.2普通类
                普通类通过function来模拟的，我们通过new关键字来实现当前类的一个实例。

                区别：静态类和普通类差别除了声明上和访问上不同外，普通类还有一个特点就是我们可以定义访问类
                中的成员的访问级别。而静态类中所有的成员都是public。

            2.2继承
            js中继承是通过他本身的原型机制实现的，js下的继承分为：原型继承和原型子类继承。
                2.2.1原型继承
                2.2.2原型子类继承
            2.3重载
            由于js的方法名如果相同，方法被覆盖，所以我们只能变相实现重载。
###3、JavaScript原型，原型链？有什么特点？
        答：
           原型：
              我们创建的每个函数都有一个prototype（原型）属性。这个属性是一个指针，指向一个对象，而这个对象的用途是包含
              可以有特定类型的所有实例共享的属性和方法。
           原型链：
              用来继承和共享属性的对象组成的（优先的）对象链。
           特点：
              （1）ECMAScript只支持实现继承，而且其实现继承主要是依靠原型链来实现的。
              （2）只要是原型链中出现过的原型，都可以说是该原型链所派生的实例的原型。
              （3）不能用字面量创建原型的方法，这样做会重写原型链。
              （4）不要在原型对象中定义属性的，否则会被所有实例共享。
###4、JavaScript有几种类型的值？（堆：原始数据类型和 栈：引用数据类型），你能画一下他们的内存图吗？
        答：
             基本数据类型存储在栈中，引用数据类型（对象）存储在堆中，指针放在栈中。
             两种类型的区别是：
             存储位置不同；原始数据类型直接存储在栈(stack)中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所
             以放入栈中存储；引用数据类型存储在堆(heap)中的对象,占据空间大、大小不固定,如果存储在栈中，将会影响程序运
             行的性能；引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其
             在栈中的地址，取得地址后从堆中获得实体。
###5、Javascript如何实现继承？
        答：
              构造继承，原型继承，（实例继承，拷贝继承）。构造函数继承可以将构造函数的属性拷贝给实例（＊.call(this,[])）。
              但是缺点是无法实现函数复用。原型继承可以实现函数复用，但是所有实例共享一个属性，任意一个实例改变原型属性都会改
              变其它实例的属性值。推荐采用构造函数继承传递属性（拷贝），原型继承传递方法。
###6、Javascript创建对象的几种方式？
        答：
              1.对象字面量的方式，var obj={};{}是字面量，可以立即求值；
              2.用function来模拟无参的构造函数，再定义属性；
              3.用function模拟构造函数，利用this；function Rectangle(w,h){this.width=w;this.height=h;}
                var rect=new Rectangle(4,8); 
              4.利用工厂方式（内置对象Object，本质是方法），var obj=new Object();；
              5.利用原型方式来创建；
              6.混合方式来创建。
###7、JavaScript作用链域？
        答：   
              当代码在一个环境中执行时，会创建变量对象的一个作用域链。如果是个函数，则将其活动对象作为变量对象。活动对象
              在最开始只包含一个arguments对象。而下一个变量对象则来自下一个包含环境。如此一直延续到全局执行环境，这种
              组织形式即为作用域链。内部函数可访问外部变量，外部变量无法访问内部函数。
          注意：
              js没有块级作用域，若要形成块级作用域，可通过（function（）｛｝）（）；立即执行的形式实现
###8、谈谈this对象的理解。
        答：
            （1）this总是指向函数的直接调用者（而非间接调用者）
            （2）如果有new关键字，this指向new出来的那个对象
            （3）在事件中，this指向触发这个事件的对象，特殊的是IE的attachEvent中的this总是指向全局对象window。
###9、eval是做什么的？
        答：   
             计算某个字符串，并执行其中的js代码。eval（string），这样避免使用eval，不安全，耗性能。由json字符串转换成
             json对象可以使用eval，var obj=eval('('+ str +')')
###10、什么是window对象？什么是document对象？
        答：
              window对象代表浏览器中打开的一个窗口。
              document对象代表整个html文档。
              实际上，document对象是window对象的对象属性。
###11、null，undefined的区别？
        答：
              null表示一个对象被定义了，但存放了空指针。
              undefined表示这个值不存在。typeof(null)--object;typeof(undefined)--undefined
###12、写一个通用的事件侦听器函数(机试题)。
        答：
              // event(事件)工具集，来源：github.com/markyun
              markyun.Event = {
              // 页面加载完成后
              readyEvent : function(fn) {
              if (fn==null) {
              fn=document;
              }
              var oldonload = window.onload;
              if (typeof window.onload != 'function') {
                  window.onload = fn;
              } else {
              window.onload = function() {
              oldonload();
              fn();
              };
              }
              },
              // 视能力分别使用dom0||dom2||IE方式 来绑定事件
              // 参数： 操作的元素,事件名称 ,事件处理程序
              addEvent : function(element, type, handler) {
              if (element.addEventListener) {
              //事件类型、需要执行的函数、是否捕捉
              element.addEventListener(type, handler, false);
              } else if (element.attachEvent) {
              element.attachEvent('on' + type, function() {
              handler.call(element);
              });
              } else {
              element['on' + type] = handler;
              }
              },
              // 移除事件
              removeEvent : function(element, type, handler) {
              if (element.removeEnentListener) {
              element.removeEnentListener(type, handler, false);
              } else if (element.datachEvent) {
              element.detachEvent('on' + type, handler);
              } else {
              element['on' + type] = null;
              }
              },
              // 阻止事件 (主要是事件冒泡，因为IE不支持事件捕获)
              stopPropagation : function(ev) {
              if (ev.stopPropagation) {
              ev.stopPropagation();
              } else {
              ev.cancelBubble = true;
              }
              },
              // 取消事件的默认行为
              preventDefault : function(event) {
              if (event.preventDefault) {
              event.preventDefault();
              } else {
              event.returnValue = false;
              }
              },
              // 获取事件目标
              getTarget : function(event) {
              return event.target || event.srcElement;
              },
              // 获取event对象的引用，取到事件的所有信息，确保随时能使用event；
              getEvent : function(e) {
              var ev = e || window.event;
              if (!ev) {
              var c = this.getEvent.caller;
              while (c) {
              ev = c.arguments[0];
              if (ev && Event == ev.constructor) {
              break;
              }
              c = c.caller;
              }
              }
              return ev;
              }
              };
###13、["1","2","3"].map(parseint)答案是多少？
        答：
              为何返回不是 [1,2,3] 却是 [1,NaN,NaN]？原因：parseInt接收的是两个参数，map传递的是3个参数。
              (1)parseInt函数：parseInt(string, radix);string: 需要转化的字符，如果不是字符串会被转换，忽视空格符。
              radix：数字2-36之前的整型。默认使用10，表示十进制。需要注意的是，如果radix在2-36之外会返回NaN。
             （2）map函数：arr.map(callback[,thisArg]);
###14、关于事件，IE与火狐的事件机制有什么区别？ 如何阻止冒泡？
        答：    
              IE为事件冒泡，Firefox同时支持事件捕获和冒泡事件。但并非所有浏览器都支持事件捕获。jQuery中使用
              event.stopPropagation()方法可阻止冒泡;（旧ie的方法 ev.cancelBubble = true;）
###15、什么是闭包（closure），为什么要用它？
        答：
              闭包指的是一个函数可以访问另一个函数作用域中变量的函数。常见的构造方法，是在一个函数内部定义另外一个函数。内部函数
              可以引用外层的参数和变量；参数和变量不会被垃圾回收机制回收。注意，闭包的原理是作用域链，所以闭包访问的上级作用域中
              的变量是个对象，其值为其运算结束后的最后一个值。除非用立即执行函数来解决。
###16、javascript 代码中的"use strict";是什么意思 ? 使用它区别是什么？
        答：
              除了正常模式运行外，ECMAscript添加了第二种运行模式：“严格模式”。
           区别：
             （1）消除js不合理，不严谨地方，减少怪异行为
             （2）消除代码运行的不安全之处，
             （3）提高编译器的效率，增加运行速度
             （4）为未来的js新版本做铺垫。
###17、如何判断一个对象是否属于某个类？
        答：
              使用instanceof 即if(a instanceof Person){alert('yes');}
###18、new操作符具体干了什么呢?
        答：
              1、创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。p._proto_ =Base.prototype;
              2、属性和方法被加入到 this 引用的对象中。Base.call(p/this)
              3、新创建的对象由 this 所引用，并且最后隐式的返回 this 。
###19、用原生JavaScript的实现过什么功能吗？
        答：
            （1）显示和隐藏
             jq：
             $(el).show();
             $(el).hide();

             js：
             el.style.display = '';
             el.style.display = 'none';
            （2）淡入淡出
             jq：$(el).fadeIn();　　
             js：function fadeIn(el) {
             var opacity = 0;

             el.style.opacity = 0;
             el.style.filter = '';

             var last = +new Date();
             var tick = function() {
             opacity += (new Date() - last) / 400;
             el.style.opacity = opacity;
             el.style.filter = 'alpha(opacity=' + (100 * opacity)|0 + ')';

             last = +new Date();

             if (opacity < 1) {  
             (window.requestAnimationFrame && requestAnimationFrame(tick)) || setTimeout(tick,
             16);
             }
             };

             tick();
             }

             fadeIn(el);
###20、Javascript中，有一个函数，执行时对象查找时，永远不会去查找原型，这个函数是？
        答：
             Object.hasOwnProperty(proName)：是用来判断一个对象是否有你给出名称的属性或对象。不过需
             要注意的是，此方法无法检查该对象的原型链中是否具有该属性，该属性必须是对象本身的一个成员。
             判断对象是否有某个特定的属性。必须用字符串指定该属性。（例如，o.hasOwnProperty("name")）。
