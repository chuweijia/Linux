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





