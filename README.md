# Стиль кодирования

### Обрамление PHP-кода
PHP-код должен всегда обрамляться полными PHP-тегами:
```php
<?php
 
?>
```

### Фигурные скобки
Фигурные скобки должны быть перемещены на новую строку с отступом на том же уровне, что и оператор управления (если это не наименование класса).
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
* Каждый класс должен иметь блок документации (doc-блок) в соответствии со стандартом PHPDocumentor.
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

Название классов

| Название класса  | Путь до файла |
| ------------- | ------------- |
| Controller_Template | classes/Controller/Template.php |
| Model_User  | classes/Model/User.php  |
| Model_BlogPost  | classes/Model/BlogPost.php |
| Database  | classes/Database.php |
| Database_Query | classes/Database/Query.php |
| Form  | classes/Form.php  |
