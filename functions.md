1) Вывод ссылок с tel из одного поля
Делаем одно поле, где админ может вводить телефон в любом виде например `+38(095) 888-22-33`
С помощью функции `cleanPhone` убираем все символы и пробелы, оставляем только цифры

```
  function cleanPhone($string) {
    $string = preg_replace('/[^0-9]/', '', $string); // Removes special chars.

    return 'tel:' . $string;
  }
```

Наша ссылка с телефоном будет выглядеть так:
```
<a href="<?php echo cleanPhone(get_field('contacts_ph', 'option'));?>"><?php the_field('contacts_ph', 'option'); ?></a>
```
Где `get_field('contacts_ph', 'option')` - ACF поле на страничке опций
