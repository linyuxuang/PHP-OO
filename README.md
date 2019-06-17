# PHP-OO
PHP面向对象

php面向对象-类的声明-创建对象_魔术方法

  类的声明
    1. 你要开发的是什么， 确定写什么类
    2. 类中的成员一定要属于这个类
    电话的类
 
    [修饰类的关键字] class 类名{
 	 成员属性：外观、颜色、电池容量、屏幕尺寸 ....  
 	 成员方法：打电话、发信息、播放音乐、拍照 .... 
    }
     
    在类中声明成员属性时： 前面必须有修饰词,当不知道使用那个时，就使用var,如果知道使用那一个修饰关键字，就不使用var了
 
    类中的成属性，如果创建多个对象时，每个对象有不同的属性值时，不要直接组初值
 
    在创建好对象之后再给值
     
    一个文件只保存一个类， 文件名中包含类名， 文件：类名.class.php
    自动加载
    aaa bbb ccc 
    变量: aaaBbbCcc
    函数：aaaBbbCcc
    常量：AAABBBCCC
    类名：AaaBbbCcc
 
    一定要有意义
 
   通过类来实例化对象
   	1. 使用的是new 新建一个对象，加上类名，就是创建那个类的对象
   		$对象引用=new 类名;
   	2. 只要有一个new 关键字就是创建一个对象，创建一个对象就在内存中分配了一个空间
 
   只有对象才在内存有存储空间
 
   对象在内存中的分配
 
   对象的使用
 
   对象中的成员必须通过对象的引用来访问
 
   对象->成员
 
   对象->成员属性=新值
   echo 对象->成员属性
   对象->成员方法
 
   类的声明
 
   类中成员属性
 
   类中成员方法
 
   对象的创建（对象实例化）
 
   对象中成员的访问形式
 
 
 
  例子：   类的声明--->创建对象
  
  
        class Person {
                var $name;
                var $age;
                var $sex;

                function say(){

                }

                function eat(){

                }

                function run(){


                }	
                }

                $p1=new Person;
                $p2=new Person;
                $p3=new Person;

                $p1->name="zhasan";

                echo $p1->name;

                $p2->say();




            
  1. 对象中成员的访问（就是在一个对象的内部方法中，去访问本对象中的其它方法和成员属性）
 
  2. 在对象中的方法中都默认有一个$this关键字， 这个关键字代表调用这个方法的对象
 
  3. 第一人称代词：我
   
   构造方法， 构造器
 
     1. 是对象创建完成以后，“第一个” “自动调用”的方法
     2. 构造方法的定义， 方法名一个固定的，
     	 在PHP4中 和类名相同的方法就是构造方法
     	 在PHP5中 构造方法选择使用 魔术方法 __construct() 所有类中声明构造方法都使用这个名称
         	 	优点： 在改变类名时，构造方法不用改变 
       作用：就是为成员属性初使化；
     	
 
魔术方法：

     		在类中写出了某个魔术方法， 这个方法对象的功能 就会添加上
 
     		方法名称都固定的（都是系统给我们提供好），没有自己定义的， 
 
     		每一个魔术方法， 都是在不同时刻为了完成某一功能自动调用的方法
     		不同的魔术方法有不同调用 时机
 
     		都是以 __开头的方法
 
 
 
           		__construct();
           		__destruct();
       
           		__set();
           		__get();
           		__isset();
           		__unset();
       
           		__clone();
       
           		__call();
       
           		__sleep();
       
           		__weakup();
       
           		__toString()
       
           		... 
       
                __autoload();
   
   析构方法：
 
   	1. 当对象被释放之前最后一个 “自动”调用的方法
 
     	  使用垃圾回收器（java PHP）而C++手动的释放
 
 	      作用：关闭一些资源， 作一些清理的工作
 
          __destruct();
 
 
                          class Person {
                            var $name;
                            var $age;
                            var $sex;

                        function __construct($name="", $age=0, $sex="男"){
                          $this->name=$name;
                          $this->age=$age;
                          $this->sex=$sex;
                        }


                        function say(){
                          echo "我的名字：{$this->name}，我的年龄：{$this->age}，我的性别：{$this->sex}。<br>";
                          $this->eat();
                        }

                        function run(){

                        }

                        function eat(){

                        }

                        function __destruct(){
                          echo $this->name."再见！<br>";
                        }
                      }

                    $p1=new Person("zhangsan", 20, "女");
                    $p2=new Person("lisi", 25);
                    $p3=new Person("wangwu");

                    $p1->say();
                    $p1=null;
                    $p2->say();
                    $p3->say();
   
   
   
   
            
 *封装性： 面向对象的三大特性之一
 
    1. 就是把对象的成员（属性，方法）结合成一个独立的相同单位，并尽可能隐藏对象的内部细节
 
     public  protected  
 
    private 私有的， 用这个关键字修饰的成员，只能在对象内部访问（只有用$this访问），不能在对象外部使用
 
    属性可以封装：
    
    		只要一个变量，需要在多个方法使用，就将这个方法声明为成员属性，可以直接在这个对象中的所有方法中使用
 
    		成员属性，就相当于这个对象中的全局变量
 
    		成员属性都会在方法中使用， 成员属性值的变化其实就是在改变方法的执行行为， 也就是改变了对象的功能
 
  		  成员属性的值如果不正常， 方法执行的功能也就不正常 了
 
 
 		作用：不需要在对象外部改变或读取它的值
 
 			1. 封装

            再提供一个公有的方法(经过方法对象成员属性进行赋值和取值就可以控制)
            方法也可以封装：
 
       	作用：
    
            1. 使用private修饰使用其只能在内部使用
            2. 一个类中有100个方法， 封装了95个（为另外的5个服务的方法）， 只有5个方法可以使用
            100成员属性，都让取值，值都不可以改值, 有个别的还不想让人知道真实的值
 
 
       和封装有关的魔术方法：
 
            __set()：是直接设置私有成员属性值时，自动调用的方法
            __get()：是直接获取私有成员属性值时，自动调用的方法
            __isset(); 是直接isset查看对象中私有属性是否存时自动调用这个方法
            __unset(); 是直接unset删除对象中私有属性时，自动调用的方法          


  private  模块
  
 
         private，__get，__set，__isset，的使用

                        class Person{
                          private $name;
                          private $age;
                          private $sex;

                        function __construct($name,$age,$sex){
                          $this->name=$name;
                          $this->age=$age;
                          $this->sex=$sex;
                        }

                          在直接获取私有属性值的时候，自动调用了这个__get()方法 
                         private function __get($names){
                          return $this->$names;
                         }

                         或(可以控制age)

                        private function __get($bane_s){
                            if($bane_s=='age'){
                              if($this->age>40){
                                return $this->age-10;
                              }else{
                              return $this->age-20;	
                              }
                            }
                           }

                          __set()方法用来设置私有属性 
                          function __set($name_s,$val_s){

                            在直接设置私有属性值的时候，自动调用了这个__set()方法为私有属性赋值
                            $this->$name_s=$val_s;
                          }

                        或者 (控制某一项)
          
                       function __set($name_s,$val_s){
                            if($name_s=='age'){
                              if($val_s>100||$val_s<0){
                                return;
                              }
                            }
                            $this->$name_s=$val_s;
                          }

                          __isset 直接isset查看对象中私有属性是否存时自动调用这个方法
                         private function __isset($name_v){
                            return isset($this->$name_v);
                         }

                        function text1(){
                          echo	"我的名子：{$this->name}，我的年龄：{$this->age}，我的性别：{$this->sex}<br>";
                          $this->text2();
                          $this->text3();
                        }

                       private	function text2(){
                          echo "000000<br>";

                        }
                        private function text3(){
                          echo "111111111<br>";
                            }

                        }

                     $p1=new Person('zhangsan',90,'男');



                        直接获取私有属性的值，会自动调用__get()方法，返回成员属性的值 
                        echo "年龄：".$p1->name."<br>";
                        echo "年龄：".$p1->age."<br>";
                        echo "年龄：".$p1->sex."<br>";


                        直接为私有属性赋值的操作，会自动调用__set()方法进行赋值(改变原属性成员的值) 
                          $p1->name='蔺相如';
                          $p1->age=27;
                          $p1->sex='男';


                         $p1->text1();

                        注意这里如果name不是私有变量，结果就是 “存在该变量”   注意上面定义了__isset() 方法这里就可以访问私有变量
                         if(isset($p1->name)){
                          echo '存在该变量';
                         }else{
                          echo "不存在该变量";
                         }




继承性： 

  
          1. 他也是面向对象的三大特性之一
          2. 开放性、可扩充性
          3. 增加代码的重用性
          4. 提高了软件的可维护性
          5. 继承就是用子类去”扩展“父类
 


       C++ 属于多继承, 同一个类可以有多个父类
 
       PHP和Java属于单继承， 同一个类只能有一个父类
 
       不管多继承的还是单继承的都可以有多个子类
 
       只要你在设计两个类时，有可以共享的成员，就将可以共享的内容拿出来，单独作为一个基类使用
 
       父类--基类
       子类--派生类
 

   作用：
 
 
  一、类继承的应用
 
 	 1. 	声明一个子类，使用 extends 关键字 去继承（扩展）一个父类
 
  	2.  子类可以从父类，继承所有的内容，包括成员属性，成员方法， 构造方法 ..., 在子类中都可以直接使用
 
  	3. 父之间的层次关系设计好
 
  二、访问类型控制
  	虽然子类可以从父类中继承所有内容，但private的成员， 只能在本类中使用， 子类中也不能使用
 
  	封装时，即可以让自己类的内部可以访问，也让子类可以用，但类的外部不能使用， private --> protected
 
  三、子类中重载父类的方法
 
    1. 子类可以声明和父类相同的方法名，即子类覆盖了父类中同名的方法
 
    鸟类---鸵鸟（飞方法）， 在鸵鸟类中将 “飞的方法改写”
 
    子类的方法对父方法的扩展
 
    在子类中 调用 父类中 被覆盖的方法  
 	
 	对象->成员  类::成员
 
    	父类名::方法名()
    	parent::方法名()
 
 
    在子类中编写构造方法，如果父中也有构造方法一定要去调用一次父类中被覆盖的那个构造方法
 
    注意： 子类中重载的方法，不能低于父类中访问权限， （子类可以访大权限，但不能缩小权限）
 
 
                     class Person1 {
                            protected $name;
                            protected $age;
                            protected $sex;

                            function __construct($name, $age, $sex){
                              $this->name=$name;
                              $this->sex=$sex;
                              $this->age=$age;

                              echo "###################<br>";
                            }


                            protected function say(){
                              echo "我的名-{$this->name}：，我的年龄：{$this->age}，我的性别：{$this->sex}.<br>";
                            }

                             function eat(){
                              echo "wwwwwwwwwwwwwwww";
                            }

                            function run(){

                            }
                            }

                   class Student extends Person1 {
                              var $school;
                            function __construct($name, $age, $sex, $school){
                              parent::__construct($name, $age, $sex);
                              $this->school=$school;
                            }
                            function study(){
                              echo "{$this->name}在学习.<br>";

                              $this->eat();
                            }

                            public function say(){
                              parent::say();
                              echo "我所在的学校{$this->school}<br>";
                            }

                            }

                            $s=new Student("lisi", 20, "男", "QingHua");

                             $s->say();














