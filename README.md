# lesson-9

#MySQL

##Часть 1. 
Установить MySQL

Работа с консолью: 
( XAMPP does not have a pre build console to run php or mysql commands, so, you have to add to windows PATH environment variables, these 2: ;C:\xampp\mysql\bin;C:\xampp\php; )

1. Установить пароль для root-юзера ( XAMP - https://www.apachefriends.org/ru/faq_windows.html )

2. Создать базу данных для своего проекта ( utf8mb4 - http://dev.mysql.com/doc/refman/5.7/en/charset-database.html )

3. Создать юзера для своего проекта и предоставить права для использования базы (#2) ( http://dev.mysql.com/doc/refman/5.7/en/adding-users.html )

4. Создать таблицы InnoDB в бд (#2) с такой структурой:
( * создание таблиц: http://dev.mysql.com/doc/refman/5.7/en/create-table.html )
Таблицы:

1. `categories`:<br/>
`id`: primary, autoincrement<br/>
`title`: varchar 255<br/>

2. `products`:<br/>
`id`: primary, autoincrement<br/>
`title`: varchar 255<br/>
`description`: text 5000<br/>
`price`: integer 11<br/>
`category_id`: integer 11 (id-шка категории)<br/>

3. `users`:<br/>
`id`: primary, autoincrement<br/>
`name`: varchar 155<br/>
`role`: enum (‘admin’,‘customer’)<br/>
`email`: varchar 155<br/>
`password`: varchar 255<br/>
`login`: varchar 255<br/>
`last_activity`: datetime<br/>

4. `orders`:<br/>
`id`: primary, autoincrement<br/>
`user_id`: integer 11 (id-шка юзера)<br/>
`product_id`: integer 11 (id-шки продукта)<br/>
`created_at`: datetime<br/>
`delivered_at`: datetime default: null<br/>
`status`: enum (‘open’,’in progress’,’closed’)<br/>
`total_price`: integres 11<br/>

5. `reviews`:<br/>
`id`: primary, autoincrement<br/>
`user_id`: integer 11 (id-шка юзера)<br/>
`product_id`: integer 11 (id-шки продукта)<br/>
`created_at`: datetime<br/>
`text`: text 5000<br/>
`rating`: smallInt<br/>

Установить phpMyAdmin ( на XAMPP есть ):

1. Включить режим аутентификации через логин форму: http://stackoverflow.com/questions/17759776/how-to-get-login-option-for-phpmyadmin-in-xampp

2. Ознакомиться с интерфейсом

##Часть 2. 

Подключить базу к проекту.<br/>
Создать php-скрипт чтобы заполнить таблицы произвольными данными (fake data).<br/>
Создать роут для каталога и вывести категории (ссылками) и каждая категория должна вести на страницу с ее товарами.<br/> 
Создать роут для товаров. Добавить кнопку покупки для товаров в каталоге и на странице товара.<br/>
Создать механизм аутентификации юзеров на основе бд: `users` (вместо файлов, как раньше): страницу логина и регистрации.<br/> 
Создать механизм корзины на основе сессии. Создать роут для корзины, где выводить добавленные в нее товары и кнопку оформить заказ.<br/>
Если юзер не залогинянный, показывать форму для контактных данных. Иначе, сразу оформлять и брать данные юзера с бд.<br/>
Оформление - бутстрап.<br/>

##Часть 3.

Создать CRUD админку с аутентификацией:<br/>
Каталог: категории и товары<br/>
Юзеры<br/>
Отзывы<br/>
Заказы<br/>
