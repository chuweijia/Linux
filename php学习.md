`$_REQUEST['data-text']` 获取前端给的请求参数  
`intval（$a）` $a为array（）|| '',,,非空 返回`1`，失败返回`0`  
`2017-9`.`3` 其中`.`是连接符  
`$query_info = array('date'=>'$date','adid'=>'$adid');` 变量无需定义，这里的value强转为string了  
`$test = array();$test['k1']='v1';` 关联数组 同上  

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
$result = mysql_query();//成功，资源标识符(describe,show,select)||true(其他类型)；失败，false  
$row = mysql_fetch_assoc($result);// 返回，关联数组（从结果集中取出一行）|| false，无更多行   

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















