`$_REQUEST['data-text']` 获取前端给的请求参数  包含$_GET['A'] $_POST['A']两种请求  
`include_once` 若已被包含则不包含  
`define(string name,vale)` 返回值bool，value为int str float bool array  
`dirname(string $path)`  返回$path的父路径   
`intval（$a）` $a为array（）|| '',,,非空 返回`1`，失败返回`0`  
`2017-9`.`3` 其中`.`是连接符  
`$query_info = array('date'=>'$date','adid'=>'$adid');` 变量无需定义，这里的value强转为string了  
`$test = array();$test['k1']='v1';` 关联数组 同上    
`strlen($str)` 返回值某个字串长度  
`const a`   常量的值不能变    
`PIRECTORY_SEPARATOR` 生成系统反斜杠  
`$_SERVER['HTTP_HOST']` 当前请求头中host项的内容      
`$dist_type_interest['interest'] = $dist_type_interest['interest'] + $dist_type_app_interest['interest'];`
当数组中的key相同，array_merge会后者覆盖前者，为了不覆盖 可以直接用 + 号连接  

```
 intval('222')   --> int(222)
 intval('aaa')   --> int(0)
 
 
 is_numeric('22')  --> true 
 is_integer('22')  --> false      

```  
`array_keys($arr)`  返回，$arr数组的所有key，所以可以用个数组单独存起来  


`implode(",",$tmp)`  tmp是个一维数组，返回值是个字符串  

```
static $arr = array(); 
if(is_null($arr[$cust_id])){
coding...
}
静态数组，对单次查询有效，知识
当重复的访问同一个cust_id时候，为了更快速，可以这样。第二次开始就读静态数组了。


```   

`isset`  检查一个变量是否被设置了且不为null   
`is_null` 检查一个变量是否为null  
`empty` 检查当变量为"" "0" 0 0.00 null false array() $var;(即被定义但并未赋值)      

`array_push($arr,$item)` 返回值为个数  
`str_replace("e","s","hello")`  将hello中的e替换为s   

 

**namespace解决的问题**
```  
冲突：用户编写的代码与php内部命名的冲突。
可读性：为长标识符创建别名

namespace Parse\Lib   //目录为Lib/class Date{}  
include_once('ROOT_PATH',dirname(_DIR_));
use Parse\Lib\Date;    //写全  

```   

```
  public function abc () //默认是public,通过类的实例去访问，$a = new abc();$a -> test();
  public static function abc()  //通过类直接访问 classa::test();  
  
  self::test() // 继承时，self指向它的类
  static::test() //继承时，static动态指向定义它的类
```   

**一次操作，多次赋值**
```
  $array = array('a','b','c');
  list($a,$b,$c) = $array;
  相当于，$a = 'a';$b = 'b';$c  ='c';
```   


**几种测试数据结构** 

```markdown  
   gettype('adc') //string  
   var_dump('abc') //string(3) '123'  子元素value的数据类型，长度，值
   is_array() || is_int()  || is_bool() ...  
   json_encode($a) //编码 将任何数据类型(必须是utf-8编码，除了resource类型)转为json  
   json_decode($a,true) //解码 将json转为array(参数为true时)|| object(参数为false时)   
   print_r($arr);
   exit；
```  
`split('[:]',$value)` 正则，将$value以冒号为分割线，分割为数组   
`preg_match('/^rankIdx',$item)` 正则，返回值0(不匹配)||1(第一次匹配后会停止搜索)||false(发生错误)  
`echo "\n";` 换行  
`array_push($arr,$v1,$v2)` 数组压栈，普通数组，返回新数组的个数  
`$array[$son]=1`  关联数组，赋值才入栈生效，才key建立有效  
关联数组，被转化为`对象`  
普通数组，被转化成`数组`  
`foreach ($array as $key => $value)` 针对纯数组，直接as $items  
`array_key_exists($key,$value)` return bool;  
**进制运算**  

```  
  bin2hex(string)  //2-->16  ,pack()可以再转回去  
  hexdec(string)   //16-->10
```   
`fopen($GLOBALS['PASSWORD'],'r')` 以`特定方式`(只读)打开`特定文件`  
`$password = fgetcsv($file)` 读入文件，并解析csv文件（纯文本文件，存数据的），单个文件，方便  
**mysql常用**  

```   
$flag = mysql_connect();//成功，mysql连接标识；失败，false  
mysql_select_db('dbname',$flag);  //$flag可选，返回值bool
mysql_query("ser names utf8");//解决乱码  
$result = mysql_query($query,$connect);//成功，资源标识符(describe,show,select)||true(其他类型)；失败，false  
$row = mysql_fetch_assoc($result);// 返回，关联数组（从结果集中取出一行）|| false，无更多行   


$queryRows = mysql_num_rows($result);//仅select
$queryRows > 1 （多行结果，用mysql_fetch_array()）||  == 1 （一行结果，用mysql_fetch_assoc() ）|| == 0(空数据) 
$result == false ($query语句||$connect连接 出错)


if(is_bool($result)){
//返回值为true||1，表示，$result是bool型
}
else{
//返回值为true||1，表示，$result不是bool型
}

mysql_affected_rows($connect);//除了select
mysqli_affected_rows($connect);//all（含select）
```

`rm -rf 文件夹名`  强制删除非空文件夹，其中 -rf是做了递归处理  
`require_once('../config/config.php')` 同`require` 用法，但是会检查文件唯一性  
`ini_set('display_errors',0)` 设置配置项（是否将错误信息作为输出值得一部分打印到屏幕上）  
`date_default_timezone_set('Asia/Shanghai')` 设日期时间函数的默认时区   

`strtotime($date)`  将字符串(人类习惯读的，2017-05-01，tomorrow)解析为`时间戳` (unix可读的)  
`时间戳`  是种字符序列，表示具体事件发生的日期和时间  
`data("Ymd",strtotime($date))`  以`某种方式`格式化时间戳,返回值是易读的时间  

`$arr[$key][$q] = 'chu';`  若原来没有[$q]这个属性，则新增这个属性  

``` markdown  
$keys = array('0'=>'k1','1'=>'k2');
foreach ($keys as $key){
  echo $key; //'k1','k2'
}  
foreach ($keys as $key => $value){
  echo $key; //0,1
  echo $value; //'k1','k2'
}
```  
``` markdown  
$keys = array('k1'=>'','k2'=>'');
foreach ($keys as $key){
  echo $key; //''空值！！
}  
foreach ($keys as $key => $value){
  echo $key; //'k1','k2'
}
```  

``` markdown  
$keys = array('k1'=>'123','k2'=>'456');
foreach ($keys as $key){
  echo $key; //'k1','k2'
}  
```  

``` markdown  
$arr = array(
'k1' => 'v1',
'k1' => 'v2',
); 

当同key，后者会覆盖前者。解决方案，放到非关联数组中保存。
``` 



**时间戳 时间转换**  

```  
时间 --> 时间戳
var strtime = ‘2017-05-12 18:55:49’
var date = new Date(strtime);
var time1 = date.getTime();精确到毫秒
var time2 = date.valueOf();精确到毫秒
var time3 = Date.parse(date);精确到秒

时间戳 --> 时间
var date = new Date(戳);
Y = date.getFullYear()+'-' 
M = date.getMonth+1<10?'0'+(date.getMonth()+1) : date.getMonth()+1)+'-';

```   


`curl_post($url,$request)`post方式 通过`$_POST`能获取到，$url是请求地址，$request是传入的参数   

`http_build_query($params)`  生成 URL-encode 之后的请求字符串  ，$params可以是数组或包含属性的对象。  
`curl_post_contents($url,$params)`  自己写的。。。  
`$_SERVER`  各种信息  

`URI`    
URI = Universal Resource Identifier   统一资源标识符   
URL = Universal Resource Locator      统一资源定位符    
URN = Uniform Resource Name           统一资源名称    
 
关系：URL 和 URN 是 URI的子集  

`substr("abcdef",1)`  返回值，被切割后的字符串。1是索引值为1，即b。从b开始，切到最后全部（默认第三个参数为全部，可自控）              


```  
substr("abcdef",-1)  //f  
substr("abcdef",-2)  //ef    
substr("abcdef",-2,1)  //e  
substr("abcdef",-0)  //adcdef同0  

```   

`time()` 返回当前unix时间戳  
`error_reporting()` 设置应该报告何种 PHP 错误  
`setlocale()` 设置地区信息  
` $icon = "'fa fa-arrow-down icon-green'" ` 内部的字符串是值，外部的引号是作为字符串    
php-->html 的过程中的空格，回车会被转义，需要注意！  

`$_SERVER['PHP_SELF']` 当前执行脚本的文件名  
`$_SERVER['REQUEST_URI']` URI用来指定要访问的页面  
`parse_url($url)` 返回值是个关联数组，比如，['host'] = 'hostname';其中host是关键字。  
`parse_url($url,PHP_URL_HOST)` PHP_URL_HOST是关键字，提取上面的关联数组   
`trim($text)` 一般用于出去首尾空白字符  
`strpos($request,',')` 返回值，‘,’ 所在的索引值（false，代表未查找到）。  
`explode(',',$a)`返回值，array[0]是','分割后面的，[1]是分割前面的。    
`array_shift($arr)` 将数组第一项移出数组。返回值，被移后的新数组。  
`class_exists($a)` 检查这个$a类名是否已经定义  
`stripslashes` 反引用一个引用   
`microtime()` 返回当前unix时间戳和微秒数  ，传入参数为true，将返回一个float数    
`HDFS`是Hadoop Distribute File System    hadoop分布式文件系统  




## 日志等级  
`LOG_ERR`  可进行修复工作，以后也会出现  
`LOG_INFO` 有用的信息，给用户看明白，不可随便对待  
`LOG_DEBUG` 级别最低，可随意使用，为了了解系统的运行状态  




## 类与对象  
`astract` 抽象类  
`$a instanceof MyClass` 检查是否是某一类的实例  返回值是bool  
`Exception` 异常类 php内置的类，getCode() 获取异常代码。getMessage() 获取异常信息 。__toString()将异常对象转成字串。  
 
 
 **self** 
 类本身
 **$this**
 对象本身  
 若本身无期望函数，会找到父级  
 
 
 
 **parent**
 父类本身   
 只能访问static的  
 
 
 
 
 **static**
 可以用类名直接访问   
 静态方法，可以用对象访问  
 静态属性，不可以用对象访问  
 
 
 **protected**
其子类可以访问，外部类不能访问  

 
## 与ajax交互    
问题描述： 
PHP接收到的参数类型非预期  

解决方案1:  
`excodeURIComponent(JSON.stringify(~~))`  // 前端，手动编码  

`$parse = urldecode($parse)`  //后端，手动解码，解URL  
`json_decode($parse)`  //string --> obj  
`$obj -> adid_text`   //Array:arr[$key]   Obj:obj->key  

解决方案2:
前端修改ajax的contentType的值  我觉得并不能成功。  



## 关于继承

```    

            同类          子类       外部类
            
private     可以        不可以       不可以

protected   可以        可以         不可以

public      可以        可以         可以

```  


```  

除非子类覆盖了父类的方法，被继承的方法都会保留其原有功能
PHP只支持单继承，不允许多重继承。一个子类只能有一个父类，不允许一个类直接继承多个类，但一个类可以被多个类继承。
可以有多层继承，即一个类可以继承某一个类的子类，如类B 继承了类A，类C又继承了类B，那么类C也间接继承了类A
在子类里面允许重写（覆盖）父类的方法

```  
父类如何继承子类？  
```  
后期静态绑定，表示运行时最初调用的类来绕过限制
<?php
class A {
    public static function who() {
        echo __CLASS__;
    }
    public static function test() {
        static::who(); // 后期静态绑定从这里开始
    }
}

class B extends A {
    public static function who() {
        echo __CLASS__;
    }
}

B::test();  //  B  
?>


```  
或者使用多态性，抽象类  

```
abstract class whale
{

  function __construct()
  {
    // some code here
  }

  function myfunc()
  {
    $this->test();
  }

  abstract function test();
}


class fish extends whale
{
  function __construct()
  {
    parent::__construct();
  }

  function test()
  {
    echo "So you managed to call me !!";
  }

}


$fish = new fish();
$fish->test();
$fish->myfunc();

```  

## 关于异常错误   
`502` 重启下php-fpm  


















