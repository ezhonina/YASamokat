Дипломный проект - Яндекс самокат 
1. Тестирование функциональности веб-приложения
Написан чек-лист на функциональность «Сделать заказ», 
на «Для кого самокат»,а также тесты на логику для форм "Для кого самокат" и "Про аренду"
Написаны и приложены баг-репорты в YouTrack.
2. Ретест багов в мобильном приложении
Проведен ретест багов, написаны баг-репорты в YouTrack.
3. Регрессионное тестирование мобильного приложения по готовым тест-кейсам
Выполнено регрессионное тестирование, написаны баг-репорты в YouTrack.
4. Работа с базой данных
Запросы составлены в файле SQL:
Задание 1
      SELECT c.login, COUNT(o.id) AS "deliveryCount" 
      FROM "Couriers" AS c 
      LEFT JOIN "Orders" AS o ON c.id = o."courierId" 
      WHERE o."inDelivery" = true 
      GROUP BY c.login;
Задание 2
       SELECT track, CASE 
        WHEN finished = true THEN 2 
        WHEN cancelled = true THEN -1 
        WHEN "inDelivery" = true THEN 1 
        ELSE 0 END AS status 
        FROM "Orders";
5. Автоматизация теста к API
URLстенда  https://933d3f13-af9d-46b0-9481-a2882ff5e51b.serverhub.praktikum-services.ru
Шаги автотеста:
Выполнить запрос на создание заказа
Сохранить номер трека заказа
Выполнить запрос на получение заказа по треку заказа
Проверить, что код ответа равен 200
Тип запроса – POST.
Эндпоинт 
/api/v1/orders
Успешное создание заказа
HTTP/1.1 201 Created {
    track: 124124 }
Тип запроса - GET
Эндпоинт 
/api/v1/orders/track
Успешное получение заказа по его номеру
HTTP/1.1 200
Созданы файлы: configuration.py, data.py, sender_stand_request.py, test,py
Для запуска тестов устанавливаем pytest и requests через команду pip install
