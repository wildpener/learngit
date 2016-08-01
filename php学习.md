# 这里写一些学习php时的问题及需要注意的细节（不定时更新）
## PHP是弱类型语言！[弱类型语言](http://blog.csdn.net/wildpen/article/details/51996890)
1. 搭好环境后推荐使用Notepad++（windows下）和vim（linux下）；
2. 注意设置编码格式 utf-8格式编码；
3. php中输出字符串时 单引号“'” 会原样输出字符串，而双引号“"” 会其中的变量自动替换成实际数值；
4. 使用界定付输出时，结束标识符必须单独起一行，并且不允许带有空格。在标识符前后有其它符号或字符，也会发生错误；
5. 如果给定的数值超出了int型所能表示的最大范围，将会被当做float型处理，这种情况称为***整数溢出***。
6. 浮点型的数值只是一个近似值，所以要尽量避免浮点型数值之间比较大小，因为最后的结果往往是不准确的。
7. ***php数组声明后还可以自由更改元素的个数！***
8. 类型转换时，转换成布尔型，null,0,和未赋值的变量或数组会被转换为false，其他的为true。
9. php echo 1+1; 直接显示结果 '2' 而不是 '1+1'

##函数
2.1 自定义函数

PHP内置了超过1000个函数，因此函数使得PHP成为一门非常强大的语言。大多数时候我们使用系统的内置函数就可以满足需求，但是自定义函数通过将一组代码封装起来，使代码进行复用，程序结构与逻辑更加清晰。

PHP函数的定义方式：
    1.使用关键字“function”开始
    2.函数名可以是字母或下划线开头：function name()
    3.在大括号中编写函数体：
	
```php
function name() {
    echo 'Eric';
}
```

通过上面的步骤，我们就定义了一个简单的函数，当我们需要的时候，就可以在代码中调用这个函数，调用方法为函数名+参数，例如：name();

2.2 函数的参数

PHP的函数可以没有参数，也可以有若干个参数，多个参数称之为参数列表，采用逗号进行分割，参数类似于一个变量，调用时用来传递数据到函数体中。通过传递参数可以使函数实现对参数的运算，得到我们想要的结果。

参数的变量名可以自由指定，但最好能够表达相关的意思，常用的设定参数的方法为：

```php
function sum($a, $b) { 
    return $a+$b; 
}
```

2.3 函数的返回值

使用return关键字可以使函数返回值，可以返回包括数组和对象的任意类型，如果省略了 return，则默认返回值为 NULL。

```php
function add($a) {
    return $a+1;
}
$b = add(1);
```

返回语句会立即中止函数的运行，并且将控制权交回调用该函数的代码行，因此下面函数的返回值跟上面的函数是一样的。

```php
function add($a) {
    return $a+1;
    $a = 10;
    return $a+20;
}
$b = add(1);
```

函数不能返回多个值，但可以通过返回一个数组来得到类似的效果。

```php
function numbers() {
    return array(1, 2, 3);
}
list ($one, $two, $three) = numbers();
```

2.4 可变函数

所谓可变函数，即通过变量的值来调用函数，因为变量的值是可变的，所以可以通过改变一个变量的值来实现调用不同的函数。经常会用在回调函数、函数列表，或者根据动态参数来调用不同的函数。可变函数的调用方法为变量名加括号。

```php
function name() {
    echo 'jobs';
}
$func = 'name';
$func(); //调用可变函数
```

可变函数也可以用在对象的方法调用上。

```php
class book {
    function getName() {
        return 'bookname';
    }
}
$func = 'getName';
$book = new book();
$book->$func();
```

2.5 内置函数

内置函数指的是PHP默认支持的函数，PHP内置了很多标准的常用的处理函数，包括字符串处理、数组函数、文件处理、session与cookie处理等。

我们先拿字符串处理函数来举例，通过内置函数str_replace可以实现字符串的替换。下面的例子将“jobs”替换成“steven jobs”：

```php
$str = 'i am jobs.';
$str = str_replace('jobs', 'steven jobs', $str);
echo $str; //结果为“i am steven jobs”
```

另外一些函数是通过其他扩展来支持的，比如mysql数据库处理函数，GD图像处理函数，邮件处理函数等，PHP默认加载了一些常用的扩展库，我们可以安装或者加载其他扩展库来增加PHP的处理函数。

2.6 判断函数是否存在

当我们创建了自定义函数，并且了解了可变函数的用法，为了确保程序调用的函数是存在的，经常会先使用function_exists判断一下函数是否存在。同样的method_exists可以用来检测类的方法是否存在。

```php
function func() {
}
if (function_exists('func')){
    echo 'exists';
}
```

类是否定义可以使用class_exists。

```php
class MyClass{
}
// 使用前检查类是否存在
if (class_exists('MyClass')) {
    $myclass = new MyClass();
}
```

PHP中有很多这类的检查方法，例如文件是否存在file_exists等。

```php
$filename = 'test.txt';
if (!file_exists($filename)) {
    echo $filename . ' not exists.';
}
```
