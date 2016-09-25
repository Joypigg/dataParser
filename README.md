# dataParser
通用表格数据解析工具，目前支持xls、xlsx、csv、html、xml、txt形式的数据源。
> 支持jdk1.5及以上版本，jdk1.5需额外导入javax包，否则解析xlsx会报错。

##代码目录
1. lib：依赖的jar
* files：示例文件
* samples：示例代码

##更新日志
1. 20160925 新增支持txt数据解析（含示例代码及文件）

##示例
###待解析excel内容
<table>
  <tr>
  <th></th>
  <th>A</th>
  <th>B</th>
  <th>C</th>
  <th>D</th>
  <th>E</th>
  </tr>
  <tr>
  <td>1</td>
  <td>序号</td>
  <td>姓名</td>
  <td>性别</td>
  <td>年龄</td>
  <td>民族</td>
  </tr>
  <tr>
  <td>2</td>
  <td>1</td>
  <td>张三</td>
  <td>男</td>
  <td>20</td>
  <td>汉族</td>
  </tr>
  <tr>
  <td>3</td>
  <td>2</td>
  <td>李四</td>
  <td>女</td>
  <td>18</td>
  <td>汉族</td>
  </tr>
  <tr>
  <td>4</td>
  <td>3</td>
  <td>王二</td>
  <td>男</td>
  <td>30</td>
  <td>满族</td>
  </tr>
</table>

###java代码

    //xls格式文件解析
    File file = new File("test.xls");

    //使用列对应字母，数据从第1行开始（行从0开始计）
    IParserRule rule = new ParserRuleLetter(1,"A","E");

    IParser parser = ParserFactory.getInstance().getParser(file,rule);

    Block block = null;
    while(null!=(block = parser.nextBlock())){
      System.out.print(block.getItemContent("A"));
      System.out.print("\t");
      System.out.print(block.getItemContent("B"));
      System.out.print("\t");
      System.out.print(block.getItemContent("C"));
      System.out.print("\t");
      System.out.print(block.getItemContent("D"));
      System.out.print("\t");
      System.out.println(block.getItemContent("E"));
      System.out.println("_____________________________________");
    }

###输出结果

1 张三  男 20  汉族
_____________________________________
2 李四  女 18  汉族
_____________________________________
3 王二  男 30  满族
_____________________________________