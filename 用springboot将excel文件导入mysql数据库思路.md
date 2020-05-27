# 用springboot将excel文件导入mysql数据库

## 主要思路

### 第一个问题

如何excel文件读取到？

**解决**：可以利用POI读取excel文件，他是专门提供api给Java程序对Microsoft offic格式档案读写的功能。

主要可以有两个格式的excel

HSSF：是.xls的格式

XSSF：是.xlsx的格式

**解决步骤：**

①、获取文件输入流

用MultipartHttpServletRequest获取

②、获取excel工作薄对象	**Workbook类型**

③、获取excel工作表对象	**SheetAt类型**

④、开始循环读取表格的数据，存放在List<List<Object>>中

## 第二个问题

如何将excel中的数据导入到数据库中？

**解决：**建对应的数据库表，通过insert的方法，将excel每个单元格的数据绑定到对应的属性上。

需要解决的是将**对象类的数据**转为对应的数据类型，并传到数据库中。

**解决步骤：**

①、Controller中调用在service定义好的读取文件的方法

②、用for循环将对应的数据库到放到一个数组中

③、调用相应的insert方法，将数据插入到数据库中