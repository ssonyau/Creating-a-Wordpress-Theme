# Створення теми Wordpress
#### 1) Відкриваємо Диск(С:), заходимо в нашу папку xampp, потім у папку htdocs, Wordpress, і створитюєм в ній нову папку з назвою майбутньої теми. У мене ж це папка з назвою theme-tutor.

![](https://github.com/ssonyau/Creating-a-Wordpress-Theme/blob/main/Screenshot%202023-04-17%20133319.png)

#### 2) Кожна тема обов'язково містить два файли: index.php і style.css, Для початку досить просто створити ці файли в будь-якому текстовому редакторі. у мене ж це блокнот, а потім зайнятися їх наповненням.

![](https://github.com/ssonyau/Creating-a-Wordpress-Theme/blob/main/Screenshot%202023-04-17%20140002.png)

#### 3) Відкриваємо файл style.css та пропишемо там основні пункти опису: 
```
/* 
    Theme Name: назва теми
    Theme URI: 
    Author: автор
    Author URI: 
    Description: опис
    Version: 0.0.1
*/
```
![](https://github.com/ssonyau/Creating-a-Wordpress-Theme/blob/main/Screenshot%202023-04-17%20140417.png)

#### 4) У файл index.php ми підключимо всі файли нашої теми, і виведемо пости, щоб було цікавіше.
#### Приклад кода: 
```
<php? get_header(); ?>
<main> 
  <div class="content">
<h1> Main Contents </h1>
<?php if (have_posts()) : while (have_posts()) : the_post(); ?>
<hl> <?php the_title(); ?> </h1>
<h4>Posted on <?php the_time ('F iS, Y') ?> </h4> 
<p> <?php the_content (_('(more...)')) ; ?></p>
<hr> <?php endwhile;else: ?>

<p> <?php _e('Sorry, no posts'); ?></p> <?php endif; ?>
</div>
<?php get_sidebar(); ?> 
</main> 
<div class="delimetr"></div> 
<?php get_fidebar(); 7>
```

#### 5) Далі розділяємо index.php на окремі файли. Файл index.php містить загальну інформацію про сайт. У ній прописані елементи, які повторюються для кожної сторінки. Для коректної роботи всього вмісту потрібно створити окремі файли для header.php, sidebar.php, footer.php. 

![](https://github.com/ssonyau/Creating-a-Wordpress-Theme/blob/main/Screenshot%202023-04-20%20115125.png)

#### 6) Далі у файл header.php потрібно виділити та скопіювати рядки, що стосуються заголовка з index.php:

```
  <!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Document</title>
  <link rel="stylesheet" href="<?php bloginfo('stylesheet_url');?>"/>
</head>
<body>
 <div class="wrapper">
  <header>
    <h1>Header</h1>
  </header>
  ```
#### Це повний вміст header.php. Такі ж дії потрібно зробити з іншими файлами.

#### 7) Відкриваємо наш файл sidebar.php, у цьому файлі ми використовуємо внутрішні функції Wordpress для відображення категорій та архівів зображень. Функція повертає їх до елементів списку:
```
<div class="sidebar">
  <h2> <?php _e('Categories'); ?></h2>
<ul> 
 <?php wp_list_cats('sort_column=name&optioncount=1&hierarchial=0'); ?>
</ul>
 <h2> <?php _e('Archives'); ?></h2>
  <ul>
   <?php wp_get_archives('type-monthly'); ?>

</ul>
 </div>
 ```   
#### 8) У файлі footer.php будуть такі рядки:
```
<footer>
    <h1>Footer</h1>
</footer>
</div>
</body>
</html>
 ``` 
#### Їх можна доповнювати та редагувати на свій розсуд.

#### 9) Тепер додамо небагато стилізації у нашу папку style.css:
```
*{
    margin: 0;
    padding: 0;
}

header{
    width: 100%;
    background: yellow;
    padding: 40px;
}

main{
    display: flex;
    justify-content: center;
    height: 70px;
}

footer{
    background: blue;
    padding: 40px;
}
```

#### 10) Після цього переходимо назад до адмінки, і бачимо, що у нас з'явилася тема, яку ми щойно створили, після цього натискаємо на кнопку Активувати.

![](https://github.com/ssonyau/Creating-a-Wordpress-Theme/blob/main/Screenshot%202023-04-17%20142401.png)
 
#### Після активації ми можемо одразу перейти на сайт.

![](https://github.com/ssonyau/Creating-a-Wordpress-Theme/blob/main/Screenshot%202023-04-17%20142903.png )

#### Ось такий простий сайт на Wordpress у нас виходить.

![](https://github.com/ssonyau/)
