# Стиль кодирования

### Обрамление PHP-кода
PHP-код должен всегда обрамляться полными PHP-тегами:
```php
<?php
 
?>
```

### Фигурные скобки
Фигурные скобки должны быть перемещены на новую строку с отступом на том же уровне, что и оператор управления (если это не наименование класса). Все содержимое между скобками пишется с отступом в четыре пробела.
```php
// Правильно
if ($a === $b)
{
    ...
}
else
{
    ...
}
 
// Не правильно
if ($a === $b) {
    ...
} else {
    ...
}
```

Фигурные скобки при объявлении класса/модели/трейда должны быть на той же строке. Перед открывающейся скобкой нужно поставить пробел
```php
// Правильно
class Foo {
 
// Не правильно
class Foo
{

// Не правильно
class Foo{
```

Если класс пустой, то между фигурными скобками не должно быть пробелов
```php
// Правильно
class Foo {}
 
// Не правильно
class Foo { }
```

### Строки
Для обрамления строк должны использоваться 'одинарные кавычки':
```php
$a = 'Обычная строка';
```

Когда строка сама содержит одинарные кавычки, разрешается для обрамления строки использовать "двойные кавычки". Это особенно актуально для SQL-запросов (синтаксис ниже является более предпочтительным, чем экранирование кавычек):
```sql
$sql = "SELECT `id`, `name` from `chocoaccount`.`users_data` WHERE `name`='Nikolay'";
```

Подстановка переменных разрешается в такой форме(без пробелов между "."):
```php
// Правильно:
$str = 'one'.$var.'two';

// Не правильно
$str = 'one'. $var .'two';
$str = 'one' . $var . 'two';
$str = 'one $var two';
$str = 'one {$var} two";
```

Строки должны объединятся с помощью оператора ".". Пробелы не нужно ставить до или после "."
```php
$str = 'One'.' '.'Two String';
```

Когда производится объединение строк с помощью оператора ".", разрешается разрывать выражение на несколько строк для улучшения читабельности. В этом случае, каждая следующая строка должна быть дополнена пробелами так, чтобы оператор "." был выровнен под оператором "=":
```php
$text = 'this is a long text block that is wrapped. Normally, we aim for '
      .'wrapping at 80 chars. Vertical alignment is very important for '
      .'code readability. Remember that all indentation is done with tabs,'
      .'but vertical alignment should be completed with spaces, after '
      .'indenting with tabs.';
```

### Массивы
* Отрицательные числа в качестве индексов запрещены.
* Хотя индекс массива может начинаться с любого неотрицательного числа, но не приветствуется и не рекомендуется начинать индексирование не с 0.

Создание массива желательно производить с помощью короткой записи(доступно с php версии 5.4):
```php
// Желательно:
$array = [];

// Не желательно
$array = array();
```

При ручном заполнении массива завершающий пробел должен быть добавлен после каждой запятой для улучшения читабельности:
```php
$array = [1, 2, 3, 'Chocolife', 'IT', 'Молодцы'];
```

При ручном заполнении многострочного массива начальный элемент может располагаться на следующей строке. В этом случае он должен быть сдвинут на один уровень отступа больше, чем строка содержащая объявление массива. Все последующие строки должны иметь аналогичный отступ. Закрывающая скобка должна быть на отдельной строке с уровнем отступа, что и строка, содержащая объявление массива:
```php
// Правильно
[
 1, 2, 3, 'Chocolife', 'Молодцы',
 56.44, $d, 500,
];

// Не правильно
[1, 2, 3, 'Chocolife', 'Молодцы',
                     56.44, $d, 500];
```

Когда определяется ассоциативный массив, приветствуется разделение выражения на несколько строк. В этом случае, каждая следующая строка должна быть дополнена с помощью пробелов так, чтобы и ключи и значения были выровнены:
```php
// Правильно
$array = [
          'a' => 'b', 
          'c' => 'd',
         ];

// Не правильно
$array = [
          'a' => 'b', 
'c' => 'd',
  ];
```

### Классы
* Каждый класс должен иметь блок документации (doc-блок) в соответствии со стандартом [PHPDoc]: http://www.phpdoc.org/.
* Код внутри класса должен иметь отступ в четыре пробела.
* Только один класс разрешен внутри одного PHP-файла.

```php
/**
* Doc-блок здесь
*/
class Sample_Class
{
    // содержимое класса должно быть
    // с отступом в четыре пробела
}
```

Классы, расширяющие другие классы или реализующие интерфейсы, должны объявлять свои зависимости на той же строке, если возможно.
```php
class Sample_Class extends Foo_Abstract {
}
```

Примеры

| Название класса  | Путь до файла |
| ------------- | ------------- |
| Controller_Template | classes/Controller/Template.php |
| Model_User  | classes/Model/User.php  |
| Model_BlogPost  | classes/Model/BlogPost.php |
| Database  | classes/Database.php |
| Database_Query | classes/Database/Query.php |
| Form  | classes/Form.php  |

Название классов необходимо указывать используя стиль "under_score". camelCase в названии классов запрещенно использовать.
camelCase используется только в моделях Doctrine и вызове методов Doctrine и ее моделей.
```php
// Controller class, используем Controller_ префикс
class Controller_Apple extends Controller {
 
// Model class, используем Model_ префикс
class Model_Cheese extends Model {
 
// Regular class
class Peanut {
```

Возвращаемое значение не должно обрамляться в круглые скобки, иначе это ухудшает читабельность, а также может нарушить код, если метод позже станет возвращать результат по ссылке.
```php
/**
* Doc-блок здесь
*/
class Foo_Bar {
    /**
     * Правильно
     */
    public function action_bar()
    {
        return $this->bar;
    }
 
    /**
     * Не правильно
     */
    public function action_bar()
    {
        return($this->bar);
    }
}
```


### Переменные и функции
Название функции должно быть в нижнем регистре, для разделения слов использовать символ "_"
```php
function drink_beverage($beverage)
{
   //
}
```

Аргументы функции разделяются одним завершающим пробелом после каждой запятой. Это пример допустимого вызова функции для функции, которая принимает три аргумента:
```php
three_arguments(1, 2, 3);
```

Функции внутри классов должны всегда определять свою область видимости с помощью одного из префиксов private, protected или public.

Фигурная скобка всегда пишется на следующей строке под именем функции. Пробелы между именем функции и круглой скобкой для аргументов не допускаются.
```php
/**
* Doc-блок здесь
*/
class Sample_Class {
    /**
     * Doc-блок здесь
     */
    public function action_bar()
    {
        // содержимое класса должно быть
        // с отступом в четыре пробела
    }
}
```

Название переменной должно быть в нижнем регистре, для разделения слов использовать символ "_"
```php
// Правильно
$foo = 'bar';
$long_example = 'uses underscores';
 
// Не правильно
$weDontWantThis = 'understood?';
```

### Управляющие структуры

Синтаксис if
```php
// Правильно:
if ($foo == $bar)
if ( ! $foo)
 
// Не правильно:
if($foo == $bar)
if(!$foo)
if ((int) $foo)
if ( $foo == $bar )
if (! $foo)
```

Управляющие структуры, основанные на конструкциях if и elseif, должны иметь один пробел до открывающей круглой скобки условия.
```php
if ($a != 2)
{
    $a = 2;
}
```

Однострочная запись (без использования фигурных скобок) "if" должны использоваться только тогда, когда возврат результата или "пропуск" или выкинуть эксепшн
```php
// Правильно
if ($foo == $bar)
    return $foo;
 
if ($foo == $bar)
    continue;
 
if ($foo == $bar)
    break;
 
if ($foo == $bar)
    throw new Exception('You screwed up!');
 
// Не правильно
if ($baz == $bun)
    $baz = $bar + 2;
```

Для выражения "if", включающего "elseif" или "else", форматирование должно быть таким, как в следующем примере:
```php
if ($a === $b)
{
    ...
}
else
{
    ...
}

if ($a === $b)
{
    ...
}
elseif ($a === $b)
{
    ...
}
```

Управляющие структуры, написанные с использованием "switch" конструкции, должны иметь один пробел до открывающей круглой скобки условного выражения.

Все содержимое между фигурными скобками пишется с отступом в четыре пробела. Содержимое каждого "case" выражения должно писаться с отступом в дополнительные четыре пробела. Ключевое слово default никогда не должно опускаться в выражении switch.
```php
switch ($numPeople)
{
    case 1:
        break;
 
    case 2:
        break;
 
    default:
        break;
}
```

Не нужно использовать краткую запись if/else
```php
// Не правильно
$foo = ($bar == $foo) ? $foo : $bar;
$foo = $bar ? $foo : $bar;
```

### Комментарии

Комментарии внутри кода классов должны соответствовать синтаксису комментариев [PHPDoc]: http://www.phpdoc.org.
Дополнительные комментарии, кроме тех, что предусмотрены PHPDoc, только приветствуются. Основное правило в данном случае — каждая часть кода повышенной сложности должна быть прокомментирована до того, как вы забыли как она работает.
Подходят комментарии в стилях C (/* */) и C++ (//). Использование комментариев в стиле Perl/shell (#) не рекомендуется.
После "тега комментария" необходимо поставить один пробел и комментарий начинать с большой буквы.
```php
// Правильно
 
//Неправильно
// не правильно
# Не правильно
```

### Дополнительно
Не использовать оператор echo для вывода html-тэгов, а использовать «встраивание» html-кода:
```php
// Не правильно
echo "<table>";
echo "<tr><td>Name</td><td>Position</td></tr>";
foreach ($employees as $employee) {
    echo "<tr><td>$employee[name]</td><td>$employee[position]</td></tr>";
}
echo "</table>";

// Правильно
<table>
  <tr><td>Name</td><td>Position</td></tr>
<?php foreach ($employees as $employee) { ?>
  <tr><td><?=$employee['name'];?></td><td><?=$employee['position'];?></td></tr>
<?php } ?>
</table>
```
Использование пустого пространства для усиления логической структуры кода
```php
// Не правильно
$lt = localtime();
$name = $_GET['name'];
$email = $_GET['email'];
$month = $lt['tm_mon'] + 1;
$year = $lt['tm_year'] + 1900;
$day = $lt['tm_day'];
$address = $_GET['address'];

// Правильно
$name    = $_GET['name'];
$email   = $_GET['email'];
$address = $_GET['address'];

$lt    = localtime();
$day   = $lt['tm_day'];
$month = $lt['tm_mon'] + 1;
$year  = $lt['tm_year'] + 1900;
```

При создании таблиц(не для special_projects) создавать Doctrine модели для облегчения работы и связки моделей
