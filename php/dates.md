## Работа с датами в PHP

В PHP довольно много разных способов работы с датами, если открыть официальную документацию, можно запутаться в колчестве встроенных функций.
Рекомендуем использовать класс `DateTime` или его неизменяемую версию  `DateTimeImmutable`.


### Работа с DateTime
Показать текущую дату и время:
```php
$date = new \DateTime();

echo $date->format('Y-m-d H:i'); // 2022-10-06 10:37
echo $date->format(\DateTimeInterface::ATOM); // 2022-10-06T10:39:29+06:00
```

Создать объект с установленным временем и датой:
```php
$date \DateTime::createFromFormat('Y-m-d H:i', '2022-10-01 10:10');
```

Посчитать и вывести возраст:
```php
$birthday     = '1996-01-19';
$birthDate    = \DateTime::createFromFormat('Y-m-d', $birthday);
$currentTime  = new \DateTime();
$difference   = $currentTime->diff($birthDate);
$formattedAge = $difference->format('Ваш возраст: %Y лет %m месяцев и %d дней');

echo $formattedAge // Ваш возраст: 26 лет 8 месяцев и 18 дней
```

### Часовые пояса
По умолчанию используется часовой пояс UTC. Для установки своего, можно воспользоваться функцией:
```php
date_default_timezone_set('Asia/Almaty');
```

Работа с часовыми поясами часто нетривиальна и может приводить к трудноотлавливаемым ошибкам, следует быть вниматеьными при работе с ними.
Хранить даты лучше в UTC, и уже при выводе приводить к нужному часовому поясу.

###Полезные ссылки:
- [Дата и время](https://www.php.net/manual/ru/book.datetime.php)
- [Класс DateTime](https://www.php.net/manual/ru/class.datetime.php)
- [Класс DateInterval](https://www.php.net/manual/ru/class.dateinterval.php)
- [Форматирование дат](https://www.php.net/manual/ru/datetime.format.php)
- [Функция time()](https://www.php.net/manual/ru/function.time.php)
- [Функция microtime()](https://www.php.net/manual/ru/function.microtime)
- [Форматы даты](https://www.php.net/manual/ru/datetime.formats.date.php)
- [Форматы времени](https://www.php.net/manual/ru/datetime.formats.time.php)