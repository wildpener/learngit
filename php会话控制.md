##cookie��session

###6.1cookie���

Cookie�Ǵ洢�ڿͻ���������е����ݣ�����ͨ��Cookie��������洢�û����ݡ�һ������£�Cookieͨ��HTTP headers�ӷ���˷��ص��ͻ��ˡ�����web����֧��Cookie�Ĳ�������ΪCookie�Ǵ�����HTTP�ı�ͷ֮�У����Ա�����������Ϣ�����ǰ�������ã�������header������ʹ�����ơ�

PHPͨ��setcookie��������Cookie�����ã��κδ���������ص�Cookie��PHP�����Զ��Ľ����洢��$_COOKIE��ȫ�ֱ���֮�У�������ǿ���ͨ��$_COOKIE['key']����ʽ����ȡĳ��Cookieֵ��

PHP�е�Cookie���зǳ��㷺��ʹ�ã����������洢�û��ĵ�¼��Ϣ�����ﳵ�ȣ�����ʹ�ûỰSessionʱͨ��ʹ��Cookie���洢�Ựid��ʶ���û���Cookie�߱���Ч�ڣ�����Ч�ڽ���֮��Cookie���Զ��Ĵӿͻ���ɾ����ͬʱΪ�˽��а�ȫ���ƣ�Cookie�������������·����

###6.2����cookie

PHP����Cookie��õķ�������ʹ��setcookie������setcookie����7����ѡ���������ǳ��õ���Ϊǰ5����

name�� Cookie��������ͨ��$_COOKIE['name'] ���з���
value��Cookie��ֵ��
expire������ʱ�䣩Unixʱ�����ʽ��Ĭ��Ϊ0����ʾ������رռ�ʧЧ
path����Ч·�������·������Ϊ'/'����������վ����Ч
domain����Ч��Ĭ��������������Ч�����������'\www.Internet.com',��ֻ��www��������Ч��

```php
$value = 'test';
setcookie("TestCookie", $value);
setcookie("TestCookie", $value, time()+3600);  //��Ч��һСʱ
setcookie("TestCookie", $value, time()+3600, "/path/", "Internet.com"); //����·������
```

PHP�л���һ������Cookie�ĺ���setrawcookie��setrawcookie��setcookie����һ����Ψһ�Ĳ�ͬ����valueֵ�����Զ��Ľ���urlencode���������Ҫ��ʱ��Ҫ�ֶ��Ľ���urlencode��

```php
setrawcookie('cookie_name', rawurlencode($value), time()+60*60*24*365); 
```

��ΪCookie��ͨ��HTTP��ͷ�������õģ�����Ҳ����ֱ��ʹ��header�����������á�

```php
header("Set-Cookie:cookie_name=value");
```

###6.3cookie��ɾ�������ʱ��

�˽�������cookie�ĺ�������������ȴ����php��û��ɾ��Cookie�ĺ�������PHP��ɾ��cookieҲ�ǲ���setcookie������ʵ�֡�

```php
setcookie('test', '', time()-1); 
```

���Կ�����cookie�Ĺ���ʱ�����õ���ǰʱ��֮ǰ�����cookie���Զ�ʧЧ��Ҳ�ʹﵽ��ɾ��cookie��Ŀ�ġ�֮������ô�������Ϊcookie��ͨ��HTTP�ı�ͷ�����ݵģ��ͻ��˸��ݷ���˷��ص�Set-Cookie��������cookie�����ã����ɾ��cookie��Ҫʹ���µ�Del-Cookie��ʵ�֣���HTTPͷ�ͻ��ø��ӣ�ʵ���Ͻ�ͨ��Set-Cookie�Ϳ��Լ����˵�ʵ��Cookie�����á�������ɾ����

�˽�ԭ���Ժ�����Ҳ����ֱ��ͨ��header��ɾ��cookie��

```php
header("Set-Cookie:test=1393832059; expires=".gmdate('D, d M Y H:i:s \G\M\T', time()-1));
```

�����õ���gmdate���������ɸ������α�׼ʱ�䣬�Ա��ų�ʱ���Ӱ�졣

###6.4cookie����Ч·��

cookie�е�·�������������õ�cookie���ĸ�·������Ч��Ĭ��Ϊ'/'��������·���¶��У����趨������·��֮����ֻ���趨��·���Լ���·������Ч�����磺

```php
setcookie('test', time(), 0, '/path');
```

��������û�ʹtest��/path�Լ���·��/path/abc�¶���Ч�������ڸ�Ŀ¼�¾Ͷ�ȡ����test��cookieֵ��

һ������£������ʹ������·���ģ�ֻ���ڼ����������������ʱ�򣬻�����·�������������ֻ��ָ����·���вŻᴫ��cookieֵ�����Խ�ʡ���ݵĴ��䣬��ǿ��ȫ���Լ�������ܡ�

��������������Ч·����ʱ�򣬲��ڵ�ǰ·����ʱ���򿴲�����ǰcookie��

```php
setcookie('test', '1',0, '/path');  
var_dump($_COOKIE['test']); 
```

###6.5session��cookie����ͬ

cookie�����ݴ洢�ڿͻ��ˣ��������û��������֮�����ϵ��ͨ�����Խ���ܶ����⣬����cookie��Ȼ����һЩ���ޣ�

cookie��Բ���̫��ȫ�����ױ����õ���cookie��ƭ
����cookie��ֵ���ֻ�ܴ洢4k
ÿ������Ҫ�������紫�䣬ռ�ô���

session�ǽ��û��ĻỰ���ݴ洢�ڷ���ˣ�û�д�С���ƣ�ͨ��һ��session_id�����û�ʶ��PHPĬ�������session id��ͨ��cookie������ģ���˴�ĳ�̶ֳ�����˵��seesion������cookie�����ⲻ�Ǿ��Եģ�session idҲ����ͨ��������ʵ�֣�ֻҪ�ܽ�session id���ݵ�����˽���ʶ��Ļ��ƶ�����ʹ��session��

###6.6ʹ��session

��PHP��ʹ��session�ǳ��򵥣���ִ��session_start��������session��Ȼ��ͨ��ȫ�ֱ���$_SESSION����session�Ķ�д��

```php
session_start();
$_SESSION['test'] = time();
var_dump($_SESSION);
```

session���Զ��Ķ�Ҫ���õ�ֵ����encode��decode�����session����֧�������������ͣ��������������ȡ�

```php
session_start();
$_SESSION['ary'] = array('name' => 'jobs');
$_SESSION['obj'] = new stdClass();
var_dump($_SESSION);
```

Ĭ������£�session�����ļ���ʽ�洢�ڷ������ϵģ���˵�һ��ҳ�濪����session֮�󣬻��ռ���session�ļ��������ᵼ�µ�ǰ�û����������������޷�ִ�ж��ȴ������Բ��û���������ݿ����ʽ�洢�����������⡣

###6.7ɾ��������session

ɾ��ĳ��sessionֵ����ʹ��PHP��unset������ɾ����ͻ��ȫ�ֱ���$_SESSION��ȥ�����޷����ʡ�

```php
session_start();
$_SESSION['name'] = 'jobs';
unset($_SESSION['name']);
echo $_SESSION['name']; //��ʾname������
```

���Ҫɾ�����е�session������ʹ��session_destroy�������ٵ�ǰsession��session_destroy��ɾ���������ݣ�����session_id��Ȼ���ڡ�

```php
session_start();
$_SESSION['name'] = 'jobs';
$_SESSION['time'] = time();
session_destroy();
```

ֵ��ע����ǣ�session_destroy����������������ȫ�ֱ���$_SESSION�е�ֵ��ֻ�е��´��ٷ��ʵ�ʱ��$_SESSION��Ϊ�գ���������Ҫ��������$_SESSION������ʹ��unset������

```php
session_start();
$_SESSION['name'] = 'jobs';
$_SESSION['time'] = time();
unset($_SESSION);
session_destroy(); 
var_dump($_SESSION); //��ʱ��Ϊ��
```

�����Ҫͬʱ����cookie�е�session_id��ͨ�����û��˳���ʱ����ܻ��õ�������Ҫ��ʽ�ĵ���setcookie����ɾ��session_id��cookieֵ��

###6.8ʹ��session���洢�û��ĵ�¼��Ϣ

session���������洢�������͵����ݣ���˾��кܶ����;���������洢�û��ĵ�¼��Ϣ�����ﳵ���ݣ�����һЩ��ʱʹ�õ��ݴ����ݵȡ�

�û��ڵ�¼�ɹ��Ժ�ͨ�����Խ��û�����Ϣ�洢��session�У�һ��Ļᵥ���Ľ�һЩ��Ҫ���ֶε����洢��Ȼ�����е��û���Ϣ�����洢��

```php
$_SESSION['uid'] = $userinfo['uid'];
$_SESSION['userinfo'] = $userinfo;
```

һ����˵����¼��Ϣ�ȿ��Դ洢��sessioin�У�Ҳ���Դ洢��cookie�У�����֮��Ĳ������session���Է���Ĵ�ȡ�����������ͣ���cookieֻ֧���ַ������ͣ�ͬʱ����һЩ��ȫ�ԱȽϸߵ����ݣ�cookie��Ҫ���и�ʽ������ܴ洢����session�洢�ڷ������ȫ�Խϸߡ�

```php
session_start();
//�����û���¼�ɹ�����������û�����
$userinfo = array(
    'uid'  => 10000,
    'name' => 'spark',
    'email' => 'spark@Internet.com',
    'sex'  => 'man',
    'age'  => '18'
);
header("content-type:text/html; charset=utf-8");

/* ���û���Ϣ���浽session�� */
$_SESSION['uid'] = $userinfo['uid'];
$_SESSION['name'] = $userinfo['name'];
$_SESSION['userinfo'] = $userinfo;

//* ���û����ݱ��浽cookie�е�һ���򵥷��� */
$secureKey = 'Internet'; //������Կ
$str = serialize($userinfo); //���û���Ϣ���л�
//�û���Ϣ����ǰ
$str = base64_encode(mcrypt_encrypt(MCRYPT_RIJNDAEL_256, md5($secureKey), $str, MCRYPT_MODE_ECB));
//�û���Ϣ���ܺ�
//�����ܺ���û����ݴ洢��cookie��
setcookie('userinfo', $str);

//����Ҫʹ��ʱ���н���
$str = mcrypt_decrypt(MCRYPT_RIJNDAEL_256, md5($secureKey), base64_decode($str), MCRYPT_MODE_ECB);
$uinfo = unserialize($str);
echo "���ܺ���û���Ϣ��<br>";
print_r($uinfo);
```
