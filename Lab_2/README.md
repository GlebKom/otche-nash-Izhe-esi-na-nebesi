# Пишем плохой Dockerfile

![img.png](img.png)

Плохие практики:
1. Использование образа Ubuntu, вместо образа OpenJDK
2. Использование latest, вместо конкретных версий
3. Использование apt get upgrade

Сколько контейнер собирался:
![2.png](Screenshots/2.png)

Размер контейнера:
![3.png](Screenshots/3.png)

Запуск контейнера:
![4.png](Screenshots/4.png)

Проверка работы программы при помощи Postman:
![5.png](Screenshots/5.png)


# Пишем хороший Dockerfile

![10.png](Screenshots/10.png)

Что исправлено:
1. Вместо образа ubuntu используется openjdk
2. Вместо latest указана конкретная версия opendjkd:17
3. Не используется apt get upgrade

Сколько контейнер собирался:
![6.png](Screenshots/6.png)

Размер контейнера:
![7.png](Screenshots/7.png)

Запуск контейнера:
![8.png](Screenshots/8.png)

Проверка программы при помощи Postman:
![9.png](Screenshots/9.png)