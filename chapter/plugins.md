# Plugins

**Управление Robots.txt с админки**

В дальнейшем это будет неплохо, если сеошник или владелец сайта смогут просто менять robots.txt. Я использую [https://wordpress.org/plugins-wp/wp-robots-txt/](https://wordpress.org/plugins-wp/wp-robots-txt/)

**Сброс и автогенерация изображений**

WP автоматически нарезает изображения под стандартные размеры (thumb, medium .. ) и кастомные, что можно задать через функцию [add_image_size()](https://developer.wordpress.org/reference/functions/add_image_size/). При перезаливке изображения под тем же именем или удалении кастомного размера - WP не делает пересборку нарезок. Еще один случай, когда добавили новый кастомный размер фото и надо применить его к уже загруженным ранее фотографиям. Для решения всех этих проблем нужно запустить пересборку всего медиа этим плагином
[Force regenerate thumbnails](https://wordpress.org/plugins/force-regenerate-thumbnails/)

**Клонирование постов/страниц**

Добавляем кнопку "Клонировать" для облегченного создания дублированного контента. [https://wordpress.org/plugins-wp/post-duplicator/](https://wordpress.org/plugins-wp/post-duplicator/)

**Исключаем автоформатирование от WordPress**

WP очень любит добавлять лишние `<p>` и удалять "лишние" `<div>`. Во избежание стоит установить [Raw HTML](https://wordpress.org/plugins-wp/raw-html/)

**Сжатие медиафайлов**

Для экономии нервов и места на сайте будет 100% надо установить [WP Smush](https://wordpress.org/plugins-wp/wp-smushit/)

**Конвертирование кириллических заголовков**

WP генерит ссылки от заданного заголовка, естественно, если заголовок написан кириллицей, то и ссылка будет кириллицей. Идеально, если кириллических ссылок не будет, очень идеально, если они будут прописаны руками на правильном английском. Очень идеально не выйдет, но с первым случаем поможет этот плагин [Cyr to Lat enhanced](https://ru.wordpress.org/plugins/cyr3lat/)
Будет конвертировать хотя бы в транслит на латинице

**Генерация форм**

[Contact Form 7](https://contactform7.com/)

**Developer

Плагин для отслеживания всех данных, которые есть на странице. (WMPL meta, database meta, user meta)
[Developer](https://ru.wordpress.org/plugins/developer/)
