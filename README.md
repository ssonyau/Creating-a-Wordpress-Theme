# Створення теми Wordpress
#### 1) Відкриваємо Диск(С:), заходимо в нашу папку xampp, потім у папку htdocs, Wordpress, і створитюєм в ній нову папку з назвою майбутньої теми. У мене ж це папка з назвою theme-tutor.

![](https://github.com/ssonyau/Creating-a-Wordpress-Theme/blob/main/Screenshot%202023-04-17%20133319.png)

#### 2) Кожна тема обов'язково містить два файли: index.php і style.css, Для початку досить просто створити ці файли в будь-якому текстовому редакторі. у мене ж це блокнот, а потім зайнятися їх наповненням.

![](https://github.com/ssonyau/Creating-a-Wordpress-Theme/blob/main/Screenshot%202023-04-17%20140002.png)

#### 3) Відкриваємо файл style.css та пропишемо там основні пункти опису: 
/* 
    Theme Name: назва теми
    Theme URI: 
    Author: автор
    Author URI: 
    Description: опис
    Version: 0.0.1
*/

![](https://github.com/ssonyau/Creating-a-Wordpress-Theme/blob/main/Screenshot%202023-04-17%20140417.png)

#### 4) У файл index.php додаємо код із простим змістом для теми з шапкою, підвалом, основним постом та сайдбаром.
#### Приклад кода: 
```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Мой блог</title>
  <link href="style.css" rel="stylesheet" type="text/css" />
</head>
<body>
  <div id="header">
    <div id="logo">
      <a href="index.html"><img src="images/shapka.png" alt="" title=""/></a>
    </div>
    <ul id="menu">
      <li><a href="#">Главная</a></li>
      <li><a href="#">О нас</a></li>
      <li><a href="#">Каталог товаров</a></li>
      <li><a href="#">Контакты</a></li>
    </ul>
  </div>
  <div id="content-main">
    
    <div id="content">
      <div class="post-content">
        <div class="post-img"><a href="#"><img width="275" height="230" src="images/mini.jpg" alt="Миниатюра поста"/></a></div>
        <h1 class="note-title"><a href="#">Заголовок</a></h1>
        <div class="post-text">Основной текст</div>
        <div class="readmore"><a href="#">Читать далее</a></div>
      </div>
    </div>
 
    <div id="sidebar">
      <div class="widget-title">Популярное на сайте</div>
      <div class="widget">
        <ul>
          <li><a href="#">Новости</a></li>
          <li><a href="#">Комментарии</a></li>
          <li><a href="#">Отзывы</a></li>   
        </ul>
      </div>
    </div>
  </div>
  <div id="footer">
    <p>Копирование информации запрещено</p>
  </div> 
</body>
</html>
```
#### Також до цього файлу можна додавати будь-які елементи, які вам хотілося б бачити на сайті.

#### 5) Далі розділяємо index.php на окремі файли. Файл index.php містить загальну інформацію про сайт. У ній прописані елементи, які повторюються для кожної сторінки. Для коректної роботи всього вмісту потрібно створити окремі файли для header.php, sidebar.php, footer.php. 

![](https://github.com/ssonyau/Creating-a-Wordpress-Theme/blob/main/Screenshot%202023-04-20%20115125.png)

#### 6) Далі у файл header.php потрібно виділити та скопіювати рядки, що стосуються заголовка з index.php.

  <!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Мой блог</title>
  <link href="style.css" rel="stylesheet" type="text/css" />
</head>
<body>
<div id="header">
    <div id="logo">
      <a href="index.html"><img src="images/shapka.png" alt="" title=""/></a>
    </div>
    <ul id="menu">
      <li><a href="#">Главная</a></li>
      <li><a href="#">О нас</a></li>
      <li><a href="#">Каталог товаров</a></li>
      <li><a href="#">Контакты</a></li>
    </ul>
  </div>
  
#### Це повний вміст header.php. Такі ж дії потрібно зробити з іншими файлами.

#### 7) Відкриваємо наш файл sidebar.php та прописуємо там наступні рядки:

<div id="sidebar">
      <div class="widget-title">Популярное на сайте</div>
      <div class="widget">
        <ul>
          <li><a href="#">Новости</a></li>
          <li><a href="#">Комментарии</a></li>
          <li><a href="#">Отзывы</a></li>   
        </ul>
      </div>
    </div>
    
#### 8) У файлі footer.php будуть такі рядки:

<div id="footer">
    <p>Копирование информации запрещено</p>
  </div>
  
#### Їх можна доповнювати та редагувати на свій розсуд.

#### 9) Далі, щоб шапка, сайдбар та футер коректно відображалися, необхідно зв'язати їх окремі файли з основним (індексом). Для цього на початку файлу index.php потрібно додати рядок:

<?php get_header(); ?>

#### А в кінці файлу ці рядки:

<?php get_sidebar(); ?>
<?php get_footer(); ?>

#### В результаті після перенесення даних шапки, сайдбару та футера залишиться така інформація:

<?php get_header(); ?>
<div class="content-main">
  <div class="content">
    <?php if ( have_posts() ) : while ( have_posts() ) : the_post(); ?>
    <div class="post-content">
      <div class="post-img"><a href="<?php the_permalink(); ?>"><?php the_post_thumbnail('full'); ?></a></div>
      <h2 class="post-title"><a href="<?php the_permalink(); ?>"><?php the_title(); ?></a></h2>
      <div class="post-text"><?php the_excerpt(); ?></div>
      <div class="readmore"><a href="<?php the_permalink(); ?>">Читать далее</a></div>
    </div>
    <?php endwhile; ?>
    <?php else: ?>
    <?php endif; ?>
  </div>
  <?php get_sidebar(); ?>
</div>
<?php get_footer(); ?>

#### Все, що залишається після перенесення ділянок коду, є чистий файл index.php. За бажанням, можна створювати додаткові файли та розділи для відображення на сайті різної інформації.

#### 10) Після цього переходимо назад до адмінки, і бачимо, що у нас з'явилася тема, яку ми щойно створили, після цього натискаємо на кнопку Активувати.

![](https://github.com/ssonyau/Creating-a-Wordpress-Theme/blob/main/Screenshot%202023-04-17%20142401.png)
 
#### Після активації ми можемо одразу перейти на сайт.

![](https://github.com/ssonyau/Creating-a-Wordpress-Theme/blob/main/Screenshot%202023-04-17%20142903.png )

