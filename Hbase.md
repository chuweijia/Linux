**thrift各个接口**  
`TScan` 对查询多行多列进行了封装  
```markdown
$scan = new TScan();  
$scan -> startRow;
$scan -> stopRow;
$scan -> columns = $columnArray; 

3=> array(
'var'=>'columns',
'elem' => array('class' => 'TColumn')
)
```  

`TColumn` 列族key
```markdown 
1 => array('var' => 'family' string)
2 => array('var' => 'qualifier' string)
3 => array('var' => 'timestamp')
```  

`TResult` 数组，对单行（Row）及其查询结果（若干columnvalue）的封装
```markdown 
$scanId = $client -> openScanner($tableName,$scan);$client -> openScanner($tableName,$scan);
$scanRets = $client -> getScannerRows($scanId,$num); // 返回值类型是TResult  

foreach ($scanRets as $scanRet){
  $scan_row = $scanRet -> row;  
  $scan_cols = $scanRet -> columnValues; 
}

1 => array('var' => 'row' string)
2 => array( 
        'var' => 'columnValues'
        'elem' => array('class' => 'TColumnValue')
     )
```  

`TColumnValue` 列族value
```markdown 
1 => array('var' => 'family' string)
2 => array('var' => 'qualifier' string)
3 => array('var' => 'value' string) 

new HBaseTypes.TColumnValue(family:'info',qualifier:'hobbies',value:'music');
```   

**cronTab linux自动执行脚本**   
`yum install crontabs`  在指定`docke`r中下载  
`crond -i` 初始化 仅需一次  
`cd /etc/cron.d`  默认生成路径   
`vi test.cron`  新建并编辑脚本  
`*/10 * * * * root /usr/bin/php  /www/svn_chu/printCron.php >> /www/svn_chu/show.txt 2>&1`  

**讲解**  
`*/10 * * * * `  五列，表示分钟(1～59)，小时（1～23，0表示子夜），日（1～31），月（1～12），星期（0～6，0表示周日）  
`root` 表示启动脚本的权限  
`/usr/bin/php` php命令  
`urlA >> urlB` A中内容以`累加`方式输出到B中（单个`>`表示以`覆盖`方式） 
`2>&1`1标准输出 2错误输出    
2>&1 是将错误输出重定向到标准输出。 然后将标准输入重定向到文件log.txt。  
&1 表示的是文件描述1，表示标准输出，如果这里少了&就成了数字1，就表示重定向到文件1。  


**hbase shell的使用**  
`describe '数据表名' `  查看数据表结构  
`scan '表名',{STARTROW => '0_1*',ENDROW => '0_3'}` STARTROW`支持通配符且是前缀通配匹配`，ENDROW不支持  
`scan '表名',{LIMIT => 10}` 扫描表前十条数据  
`count'表名',{INTERVAL => 100,CACHE => 500}` 查询表行数，每100行打印一次，缓存区是500条  
`get '表名','rowkey值','info:win_hits'` 获取指定rowkey的某行  


`scan '表名',{STARTROW => '0_1',FILTER => "PrefixFilter('条件')"}` 其中`PrefixFilter`前缀过滤 只能这个！！   









