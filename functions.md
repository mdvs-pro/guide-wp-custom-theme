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

2) Полностью кастомный вывод меню


Данная функция разбирает стандартную функцию вывода меню на отдельные элементы и группирует их в массив

```
function wp_get_menu_array($current_menu) {
		$locations = get_nav_menu_locations();
		$menu = get_term( $locations[$current_menu], 'nav_menu' );

    $array_menu = wp_get_nav_menu_items($menu->term_id);

    $menu = array();
    foreach ($array_menu as $m) {
        if (empty($m->menu_item_parent)) {
            $menu[$m->ID] = array();
            $menu[$m->ID]['ID']      =   $m->ID;
            $menu[$m->ID]['title']       =   $m->title;
            $menu[$m->ID]['url']         =   $m->url;
            $menu[$m->ID]['children']    =   array();
        }
    }
    $submenu = array();
    foreach ($array_menu as $m) {
        if ($m->menu_item_parent) {
            $submenu[$m->ID] = array();
            $submenu[$m->ID]['ID']       =   $m->ID;
            $submenu[$m->ID]['title']    =   $m->title;
            $submenu[$m->ID]['url']  =   $m->url;
            $menu[$m->menu_item_parent]['children'][$m->ID] = $submenu[$m->ID];
        }
    }
    return $menu;

}
```
Применять её просто, вот простейшая версия вывода уже в своем варианте
```
<?php $menu_items = wp_get_menu_array('menu-1');
    foreach ($menu_items as $item) {
        $actual_link = "http://$_SERVER[HTTP_HOST]$_SERVER[REQUEST_URI]";
        
        if ($actual_link == $item['url']){
            $actual_link = 'active';
        } else {
            $actual_link = '';
        };
        
        echo '<li class="'. $actual_link .'">';
        printf( '<a href="%1$s" class="%3$s">%2$s</a></li>',
          esc_url( $item['url'] ),
          esc_html( $item['title'] ),
          'menu__link'
        );
        
        echo '</li>';
    }
?>
```

• Проверка является ли пункт меню активным сейчас и добавление класса `active`
```
$actual_link = "http://$_SERVER[HTTP_HOST]$_SERVER[REQUEST_URI]";      
if ($actual_link == $item['url']){
    $actual_link = 'active';
} else {
    $actual_link = '';
};
```        
