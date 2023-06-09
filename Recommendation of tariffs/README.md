# Определение перспективного тарифа для телеком компании

## Описание проекта
Клиентам предлагают два тарифных плана: «Смарт» и «Ультра». 
Мне предстоит сделать предварительный анализ тарифов на небольшой выборке клиентов. В моем распоряжении данные 500 пользователей «Мегалайна»: кто они, откуда, каким тарифом пользуются и т.д. за 2018 год. Нужно проанализировать поведение клиентов и сделать вывод — какой тариф лучше, чтобы скорректировать рекламный бюджет, коммерческий департамент компании «Мегалайн» хочет понять, какой тариф приносит больше денег.
## Описание тарифов

- Тариф «Смарт»
    - Ежемесячная плата: 550 рублей
    - Включено 500 минут разговора, 50 сообщений и 15 Гб интернет-трафика
    - Стоимость услуг сверх тарифного пакета:
      - минута разговора: 3 рубля
      - сообщение: 3 рубля
      - 1 Гб интернет-трафика: 200 рублей  

- Тариф «Ультра»
    - Ежемесячная плата: 1950 рублей
    - Включено 3000 минут разговора, 1000 сообщений и 30 Гб интернет-трафика
    - Стоимость услуг сверх тарифного пакета:
      - минута разговора: 1 рубль
      - сообщение: 1 рубль
      - 1 Гб интернет-трафика: 150 рублей


## Описание данных

- Таблица users (информация о пользователях):
    - user_id — уникальный идентификатор пользователя
    - first_name — имя пользователя
    - last_name — фамилия пользователя
    - age — возраст пользователя (годы)
    - reg_date — дата подключения тарифа (день, месяц, год)
    - churn_date — дата прекращения пользования тарифом (если значение пропущено, то тариф ещё действовал на момент выгрузки данных)
    - city — город проживания пользователя
    - tariff — название тарифного плана  


- Таблица calls (информация о звонках):
    - id — уникальный номер звонка
    - call_date — дата звонка
    - duration — длительность звонка в минутах
    - user_id — идентификатор пользователя, сделавшего звонок  


- Таблица messages (информация о сообщениях):
    - id — уникальный номер сообщения
    - message_date — дата сообщения
    - user_id — идентификатор пользователя, отправившего сообщение  


- Таблица internet (информация об интернет-сессиях):
    - id — уникальный номер сессии
    - mb_used — объём потраченного за сессию интернет-трафика (в мегабайтах)
    - session_date — дата интернет-сессии
    - user_id — идентификатор пользователя  


 - Таблица tariffs (информация о тарифах):
    - tariff_name — название тарифа
    - rub_monthly_fee — ежемесячная абонентская плата в рублях
    - minutes_included — количество минут разговора в месяц, включённых в абонентскую плату
    - messages_included — количество сообщений в месяц, включённых в абонентскую плату
    - mb_per_month_included — объём интернет-трафика, включённого в абонентскую плату (в мегабайтах)
    - rub_per_minute — стоимость минуты разговора сверх тарифного пакета (например, если в тарифе 100 минут разговора в месяц, то со 101 минуты будет взиматься плата)
    - rub_per_message — стоимость отправки сообщения сверх тарифного пакета
    - rub_per_gb — стоимость дополнительного гигабайта интернет-трафика сверх тарифного пакета (1 гигабайт = 1024 мегабайта) 

## Общий вывод
В ходе данного проекта были выполнены следующие шаги:
1. Изучены исходные данные
2. Разбиты данные в отношение 3:1:1
3. Исследованы и найдены оптимальные гиперпараметры следующих моделей:
* Решающее дерево
* Случайный лес
* Логистическая регрессия
4. Оценена точность для лучших моделей
5. Проверена адекваптность модели

Наилучшей моделью оказался случайный лес с Accuracy на тестовой выборке: 0.80, при
* Критерий: gini
* Число признаков для выбора расщепления: sqrt
* Максимальная глубина: 14
* Количество деревьев: 71

Проверка на адекватность была проведена путем сравнения Accuracy при заполнении случайными значениями, и моя модель спарвилась значительно лучше(на 30%)
