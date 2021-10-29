# Анализ внутренних пассажирских авиаперевозок

---

<p align="center">
  <img src="https://avatars.mds.yandex.net/get-zen_doc/2417786/pub_5ed9ee7575ee4029d02eea61_5ed9ee9f1cc9cb3b062c1d75/scale_1200" width=800 height=500 />
</p>

---

В ходе данного исследования необходимо выявить предпочтения пользователей, покупающих билеты на те или иные направления. Предстоит изучить базу данных российской авиакомпании, выполняющей внутренние пассажирские авиаперевозки, и проанализировать спрос пассажиров на рейсы в города, где проходят крупнейшие фестивали.

---

### Схема таблиц и описание данных

<p align="center">
  <img src="https://pictures.s3.yandex.net/resources/photo_2019-11-08_14-08-31_1573733426.jpg" width=800 height=500 />
</p>

База данных об авиаперевозках:

Таблица **`airports`** — информация об *аэропортах*:
* `airport_code` — трёхбуквенный код аэропорта,
* `airport_name` — название аэропорта,
* `city` — город,
* `timezone` — часовой пояс.

Таблица **`aircrafts`** — информация о *самолётах*:
* `aircraft_code` — код модели самолёта,
* `model` — модель самолёта,
* `range` — дальность полётов.

Таблица **`tickets`** — информация о *билетах*:
* `ticket_no` — уникальный номер билета,
* `passenger_id` — уникальный идентификатор пассажира,
* `passenger_name` — имя и фамилия пассажира.

Таблица **`flights`** — информация о *рейсах*:
* `flight_id` — уникальный идентификатор рейса,
* `departure_airport` — аэропорт вылета,
* `departure_time` — дата и время вылета,
* `arrival_airport` — аэропорт прилёта,
* `arrival_time` — дата и время прилёта,
* `aircraft_code` — уникальный идентификатор самолёта.

Таблица **`ticket_flights`** — стыковая таблица *«рейсы-билеты»*:
* `ticket_no` — номер билета,
* `flight_id` — уникальный идентификатор рейса.

Таблица **`festivals`** — информация о *фестивалях*:
* `festival_id` — уникальный номер фестиваля,
* `festival_date` — дата проведения фестиваля,
* `festival_city` — город проведения фестиваля,
* `festival_name` — название фестиваля.

---

### Задачи исследования


Проект состоит из двух частей: написание запросов в тренажёре и блокнот в Jupyter Notebook. Шаги 1, 2 и 3 выполнены в тренажёре, а шаги 4 и 5 — в данном ноутбуке.

* **Шаг 1**. Написан парсер для сбора с сайта https://code.s3.yandex.net/learning-materials/data-analyst/festival_news/index.html данных о *десяти крупнейших фестивалях 2018 года*. Данные сохранены в таблице `festivals`. <br/> <br/>

* **Шаг 2**. Исследовательский анализ данных
1. Определено количество рейсов с вылетом в *сентябре 2018 года* на каждой модели самолёта. Получившееся поле `flights_amount` и поле `model` сохранено в датасет ***query_1.csv***
2. Посчитано количество рейсов по всем моделям самолетов *Boeing* и *Airbus* в *сентябре* с сохранением в переменную `flights_amount`
3. Посчитано среднее количество прибывающих рейсов в день для каждого города за *август 2018 года*. Получившееся поле `average_flights`, со столбцом `city` сохранено в датасет ***query_3.csv*** <br/> <br/>
    
* **Шаг 3**. Подготовка данных о количестве рейсов во время фестивалей
1. Установлены фестивали, которые проходили с *23 июля по 30 сентября 2018 года* в *Москве*, и *номер недели*, в которую они проходили - `festival_name` и `festival_week`
2. Для каждой недели с *23 июля по 30 сентября 2018 года* посчитанно количество билетов, купленных на рейсы в *Москву* (номер недели `week_number` и количество рейсов `flights_amount`). Получена таблица, в которой содержится информация о *количестве купленных за неделю билетов*, *отметка, проходил ли в эту неделю фестиваль*, *название фестиваля* `festival_name` и *номер недели* `week_number` <br/> <br/>

* **Шаг 4**. Для двух наборов данных (***query_1.csv*** и ***query_3.csv***) необходимо:
1. Импортировать файлы
2. Изучить данные в них
3. Проверить типы данных на корректность
4. Выбрать топ-10 городов по количеству рейсов
5. Построить графики: модели самолетов и количество рейсов, города и количество рейсов, топ-10 городов и количество рейсов
6. Сделать выводы по каждому из графиков, пояснить результат <br/> <br/>

* **Шаг 5**. Формирование общего вывода исследования

---
