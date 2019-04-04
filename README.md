# submenu-output-WP

<h2>Вывод только подпункта меню</h2>
<p>Допустим, есть первый уровень и у каждого из элементов первого уровня, есть свое подменю. Нам нужно вывести такое подменю у пункта с классом menu-item-135:</p>

```php
## Вырезаем все LI нужного submenu и выводим их в своем UL блоке
$menu = wp_nav_menu( array(
	'theme_location'  => 'header_menu',
	'container'       => '',
	'echo'            => 0,
) );
$regex_part = preg_quote('menu-item-135');
// выведем подменю пункта "gotovye-resheniya"
preg_match('~'. $regex_part .'.*sub-menu[^>]+>(.*?)</ul>~s', $menu, $mm );
if( !empty($mm[1]) ) echo "<ul>$mm[1]</ul>";
```
