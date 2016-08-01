##�����������

###3.1 ��Ͷ���
����������������ƵĻ������ͨ�׵��������Ƕ���ʵ��ĳһ������Ķ����ĳ��� �����������Գ���Ϊһ���࣬����ӵ�����֡���̥���ٶȡ����������ԣ������л�����ǰ�������˵Ȳ���������

ͨ������һ��������ķ���Ϊ��
```php
class Car {
    $name = '����';
    function getName() {
        return $this->name;
    }
}
```

����һ�ණ���Ľṹ����������������һ�ණ����һ������ʵ������������������ʿ������Ϊ���������࣬��������������һ���������������

����ͨ��new�ؼ��ֽ���ʵ������

```php
$car = new Car();
echo $car->getName();
```

������������Ƚ����ƣ���ʵ�����б��ʵ��������ǳ���ĸ�������Ǿ����ʵ���������ʹ������п������ԡ�

###3.2 ����һ������

��ͨ���ؼ���class��ͷ��Ȼ���������뻨���ţ��ڻ������ж�����������뷽����������������ĸ���»��߿�ͷ������������ɸ���ĸ�����ֻ��»��ߣ���������ܹ����⣬���Բ������ʻ���Ӣ�ĵ��ʡ�

```php
//����һ����
class Car {
    //��������
    public $name = '����';

    //���巽��
    public function getName() {
        //�����ڲ�����ʹ��$thisα�������ö�������Ի��߷���
        return $this->name;
    }
}
```

Ҫ����һ�����ʵ��������ʹ��new�ؼ��ִ���һ������

```php
$car = new Car();
//Ҳ���Բ��ñ���������
$className = 'Car';
$car = new $className();
```

###3.3 �������

�����ж���ı�����֮Ϊ���ԣ�ͨ�����Ը����ݿ��е��ֶ���һ���Ĺ��������Ҳ���Գ������ֶΡ��������������ɹؼ��� public��protected ���� private ��ͷ�������һ����ͨ�ı�����������ɡ����Եı����������ó�ʼ����Ĭ��ֵ��Ĭ��ֵ�����ǳ�����

���ʿ��ƵĹؼ��ִ��������Ϊ��

public��������
protected���ܱ�����
private��˽�е�

```php
class Car {
    //���幫������
    public $name = '����';

    //�����ܱ���������
    protected $corlor = '��ɫ';

    //����˽������
    private $price = '100000';
}
```

Ĭ�϶�Ϊpublic���ⲿ���Է��ʡ�һ��ͨ��->��������������ʶ�������Ի��߷��������ھ�̬������ʹ��::˫ð�Ž��з��ʡ��������Ա�����ڲ����õ�ʱ�򣬿���ʹ��$thisα�������õ�ǰ��������ԡ�

```php
$car = new Car();
echo $car->name;   //���ö��������
echo $car->color;  //���� �ܱ��������Բ������ⲿ����
echo $car->price;  //���� ˽�����Բ������ⲿ����
```

�ܱ�����������˽�����Բ������ⲿ���ã�����ĳ�Ա�����ڲ��ǿ��Ե��õġ�

```php
class Car{
    private $price = '1000';
    public function getPrice() {
        return $this->price; //�ڲ�����˽������
?    }
}
```

###3.4 ������ķ���

�������������е�function���ܶ�ʱ�����Ƿֲ��巽���뺯����ʲô�����������̵ĳ��������function���������������������function�򱻳�֮Ϊ������

ͬ����һ������ķ���Ҳ����public��protected �Լ� private �ķ��ʿ��ơ�

���ǿ����������巽����

```php
class Car {
    public function getName() {
        return '����';
    }
?}
$car = new Car();
echo $car->getName();
```

ʹ�ùؼ���static���εģ���֮Ϊ��̬��������̬��������Ҫʵ�������󣬿���ͨ������ֱ�ӵ��ã�������Ϊ˫ð��::��

```php
class Car {
    public static function getName() {
        return '����';
    }
?}
echo Car::getName(); //���Ϊ��������
```

###3.5 ���캯������������

PHP5����������ʹ��__construct()����һ�����캯�������й��캯�����࣬����ÿ�ζ��󴴽���ʱ����øú�������˳������ڶ��󴴽���ʱ�����һЩ��ʼ��������

```php
class Car {
   function __construct() {
       print "���캯��������\n";
   }
}
$car = new Car(); //ʵ������ʱ�� ���Զ����ù��캯��__construct����������һ���ַ���
```

�����������������__construct�򲻻���ø����__construct�������Ҫͬʱ���ø���Ĺ��캯������Ҫʹ��parent::__construct()��ʽ�ĵ��á�

```php
class Car {
   function __construct() {
       print "���๹�캯��������\n";
   }
}
class Truck extends Car {
   function __construct() {
       print "���๹�캯��������\n";
       parent::__construct();
   }
}
$car = new Truck();
```

ͬ����PHP5֧������������ʹ��__destruct()���ж��壬��������ָ���ǵ�ĳ��������������ñ�ɾ�������߶�����ʽ������ʱ��ִ�еĺ�����

```php
class Car {
   function __construct() {
       print "���캯�������� \n";
   }
   function __destruct() {
       print "�������������� \n";
   }
}
$car = new Car(); //ʵ����ʱ����ù��캯��
echo 'ʹ�ú�׼������car���� \n';
unset($car); //����ʱ�������������
```

��PHP����ִ������Ժ󣬻��Զ����������ٶ������һ������²���Ҫ��ʽ��ȥ���ٶ���

###3.6 Static��̬�ؼ���

��̬�����뷽�������ڲ�ʵ�����������µ��ã�ֱ��ʹ������::�������ķ�ʽ���е��á���̬���Բ��������ʹ��->���������á�

```php
class Car {
    private static $speed = 10;
    
    public static function getSpeed() {
        return self::$speed;
    }
}
echo Car::getSpeed();  //���þ�̬����
```

��̬����Ҳ����ͨ�����������ж�̬����

```php
$func = 'getSpeed';
$className = 'Car';
echo $className::$func();  //��̬���þ�̬����
```

��̬�����У�$thisα����������ʹ�á�����ʹ��self��parent��static���ڲ����þ�̬���������ԡ�

```php
class Car {
    private static $speed = 10;
    
    public static function getSpeed() {
        return self::$speed;
    }
    
    public static function speedUp() {
        return self::$speed+=10;
    }
}
class BigCar extends Car {
    public static function start() {
        parent::speedUp();
    }
}

BigCar::start();
echo BigCar::getSpeed();
```

###3.7 ���ʿ���

���ʿ���ͨ���ؼ���public��protected��private��ʵ�֡�������Ϊ���е����Ա�������κεط������ʡ�������Ϊ�ܱ��������Ա����Ա��������Լ�������͸�����ʡ�������Ϊ˽�е����Ա��ֻ�ܱ��䶨�����ڵ�����ʡ�

�����Ա��붨��Ϊ���С��ܱ�����˽��֮һ��Ϊ����PHP5��ǰ�İ汾��������� var ���壬����Ϊ���С�

```php
class Car {
    $speed = 10; //���� ���Ա��붨����ʿ���
    public $name;   //���干������
}
���еķ������Ա�����Ϊ���С�˽�л��ܱ��������û��������Щ�ؼ��֣���÷���Ĭ��Ϊ���С�

class Car {
?    //Ĭ��Ϊ���з���
    function turnLeft() {
    }
}
```

������캯���������˽�з�����������ֱ��ʵ���������ˣ���ʱ��һ��ͨ����̬��������ʵ�����������ģʽ�лᾭ��ʹ�������ķ��������ƶ���Ĵ��������絥��ģʽֻ������һ��ȫ��Ψһ�Ķ���

```php
class Car {
    private function __construct() {
        echo 'object create';
    }

    private static $_object = null;
    public static function getInstance() {
        if (empty(self::$_object)) {
            self::$_object = new Car(); //�ڲ��������Ե���˽�з��������������Դ�������
        }
        return self::$_object;
    }
}
//$car = new Car(); //���ﲻ����ֱ��ʵ��������
$car = Car::getInstance(); //ͨ����̬���������һ��ʵ��
```

###3.8 ����̳�

�̳�����������������г��õ�һ�����ԣ�������һ���Ƚϴ���࣬����Ҳ���Գ�֮Ϊ���࣬����֮�⣬��������Ϊ�������γ������硢����ȣ���Ϊ��Щ������кܶ���ͬ�����Ժͷ��������Բ��ü̳���������������Щ�����뷽����ʵ�ִ���ĸ��á�

```php
class Car {
    public $speed = 0; //��������ʼ�ٶ���0
    
    public function speedUp() {
        $this->speed += 10;
        return $this->speed;
    }
}
//����̳���Car��Truck��
class Truck extends Car{
    public function speedUp(){
        $this->speed=parent::speedUp()+50;
    }
}

$car = new Truck();
$car->speedUp();
echo $car->speed;
```

###3.9 ����

PHP�е�����ָ���Ƕ�̬�Ĵ��������뷽������ͨ��ħ��������ʵ�ֵġ����Ե�����ͨ��__set��__get��__isset��__unset���ֱ�ʵ�ֶԲ��������Եĸ�ֵ����ȡ���ж������Ƿ����á��������ԡ�

```php
class Car {
    private $ary = array();
    
    public function __set($key, $val) {
        $this->ary[$key] = $val;
    }
    
    public function __get($key) {
        if (isset($this->ary[$key])) {
            return $this->ary[$key];
        }
        return null;
    }
    
    public function __isset($key) {
        if (isset($this->ary[$key])) {
            return true;
        }
        return false;
    }
    
    public function __unset($key) {
        unset($this->ary[$key]);
    }
}
$car = new Car();
$car->name = '����';  //name���Զ�̬��������ֵ
echo $car->name;
```

����������ͨ��__call��ʵ�֣������ò����ڵķ�����ʱ�򣬽���תΪ��������__call�����������ò����ڵľ�̬����ʱ��ʹ��__callStatic���ء�

```php
class Car {
    public $speed = 0;
    
    public function __call($name, $args) {
        if ($name == 'speedUp') {
            $this->speed += 10;
        }
    }
}
$car = new Car();
$car->speedUp(); //���ò����ڵķ�����ʹ������
echo $car->speed;
```

###3.10 ����ĸ߼�����

����Ƚϣ���ͬһ���������ʵ�����������Զ����ʱ������ʹ�ñȽ������==�����жϣ�����Ҫ�ж����������Ƿ�Ϊͬһ�����������ʱ������ʹ��ȫ�������===�����жϡ�

```php
class Car {
}
$a = new Car();
$b = new Car();
if ($a == $b) echo '==';   //true
if ($a === $b) echo '==='; //false
�����ƣ���һЩ��������£�����ͨ���ؼ���clone������һ��������ʱ__clone�����ᱻ���ã�ͨ�����ħ���������������Ե�ֵ��

class Car {
    public $name = 'car';
    
    public function __clone() {
        $obj = new Car();
        $obj->name = $this->name;
    }
}
$a = new Car();
$a->name = 'new car';
$b = clone $a;
var_dump($b);
```

�������л�������ͨ��serialize�������������л�Ϊ�ַ��������ڴ洢���ߴ������ݣ�Ȼ������Ҫ��ʱ��ͨ��unserialize���ַ��������л��ɶ������ʹ�á�

```php
class Car {
    public $name = 'car';
}
$a = new Car();
$str = serialize($a); //�������л����ַ���
echo $str.'<br>';
$b = unserialize($str); //�����л�Ϊ����
var_dump($b);
```