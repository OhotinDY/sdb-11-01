# Домашнее задание к занятию «Базы данных, их типы»

### Задание 1. СУБД

### Кейс
Крупная строительная компания, которая также занимается проектированием и девелопментом, решила создать 
правильную архитектуру для работы с данными. Ниже представлены задачи, которые необходимо решить для
каждой предметной области. 

Какие типы СУБД, на ваш взгляд, лучше всего подойдут для решения этих задач и почему? 
 
1.1. Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков.
СУБД должна гарантировать целостность и чёткую структуру данных.

1.1.* Хеширование стало занимать длительно время, какое API можно использовать для ускорения работы? 

1.2. Под каждый девелоперский проект создаётся отдельный лендинг, и все данные по лидам стекаются в CRM к 
маркетологам и менеджерам по продажам. Какой тип СУБД лучше использовать для лендингов и для CRM? 
СУБД должны быть гибкими и быстрыми.

1.2.* Можно ли эту задачу закрыть одной СУБД? И если да, то какой именно СУБД и какой реализацией?

1.3. Отдел контроля качества решил создать базу по корпоративным нормам и правилам, обучающему материалу 
и так далее, сформированную согласно структуре компании. СУБД должна иметь простую и понятную структуру.

1.3.* Можно ли под эту задачу использовать уже существующую СУБД из задач выше и если да, то как лучше это 
реализовать?

1.4. Департамент логистики нуждается в решении задач по быстрому формированию маршрутов доставки материалов 
по объектам и распределению курьеров по маршрутам с доставкой документов. СУБД должна уметь быстро работать
со связями.

1.4.* Можно ли к этой СУБД подключить отдел закупок или для них лучше сформировать свою СУБД в связке с СУБД 
логистов?

1.5.* Можно ли все перечисленные выше задачи решить, используя одну СУБД? Если да, то какую именно?

## Ответ

1.1. Для бюджетирования проектов, формирования финансовых аналитических отчётов и прогнозирования рисков, подходят реляционные СУБД. Они обеспечивают целостность данных и имеют чёткую структуру. Некоторые из популярных реляционных СУБД, которые могут быть подходящими: MySQL, PostgreSQL.

1.2. Для лендингов и CRM, которые требуют гибкости и быстрой работы, можно использовать как реляционные, так и NoSQL СУБД. Реляционные СУБД хорошо подходят для структурированных данных, а NoSQL СУБД, такие как MongoDB или Cassandra, могут быть полезны, если необходимо обрабатывать большие объемы неструктурированных данных или если требуется гибкая схема данных.

1.3. Для отдела контроля качества, требующего простой и понятной структуры базы данных, рекомендуется использовать реляционную СУБД.

1.3. Можно. В этом случае, необходимо создать новые таблицы или модели данных, соответствующие структуре и требованиям отдела контроля качества.

1.4. Для данных задач можно использовать, как реляционные, так и NoSQL, но с тем условием, что необходимо будет внедрить поддержку пространственных данных. (PostgreSQL с расширением PostGIS или MongoDB с географическими индексами)

1.5. Скорее всего нет, т.к. задачи под каждым вопросом обладают своей спецификой. В данном случае скореее всего придется комбинировать реляционные и NoSQL СУБД.

---

### Задание 2. Транзакции

2.1. Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы 
транзакция завершилась успешно. Ориентируйтесь на шесть действий.

2.1.* Какие действия должны произойти, если пополнение счёта телефона происходило бы через автоплатёж?

## Ответ

- аутентификация
- выбор способа оплаты
- выбор суммы пополнения
- проверка возможности пополнения (наличия необходимой суммы)
- транзакция
- пополнение баланса

---

### Задание 3. SQL vs NoSQL

3.1. Напишите пять преимуществ SQL-систем по отношению к NoSQL. 

## Ответ

SQL-системы предоставляют более расширенные возможности сложных запросов, в отличии от NoSQL-систем, где запросы ориентированы на простые операции чтения и записи.

В SQL присутствует стандартизация в отличии от NoSQL-систем, где нет единого стандарта языка запросов или схемы данных.

Транзакционная поддержка. В большинстве NoSQL-систем отсутствует полная поддержка ACID-транзакций.

Гибкость схемы данных. NoSQL-системы обычно предлагают гибкость схемы данных, позволяя хранить разнородные данные. Однако, это может привести к трудностям в поддержке и обеспечении целостности данных, особенно при изменении схемы или выполнении сложных операций связи данных.

SQL-системамы больше сообществ пользователей и разработчиков, а также большее количество инструментов и ресурсов для разработки и управления базами данных.

---

### Задание 4. Кластеры

Необходимо производить большое количество вычислений при работе с огромным количеством данных, под эту задачу 
выделено 1000 машин. 

На основе какого критерия будете выбирать тип СУБД и какая модель *распределённых вычислений* 
здесь справится лучше всего и почему?

## Ответ

При выборе типа СУБД и модели распределенных вычислений для обработки большого объема данных на 1000 машинах, следует учитывать следующие критерии (полагаю, это самые важные критерии при любом раскладе:

- Масштабируемость, то есть возможность эффективно работать с большим количеством машин.

- Распределение данных, чтобы снизить нагрузку.

- Быстрота обработки запросов (выбор СУБД)

Относительно модели, гугл говорит, что круто использовать их же фрэймворк MapReduce + неизвестную мне СУБД от Apache.
Я же склонен предположить, что в наших реалиях, мы можем взять NoSQL СУБД MongoDB, которая обеспечивает горизонтальное масштабирование и хранение данных в формате JSON-подобных документов. Она позволяет распределить данные по кластеру машин и обеспечивает высокую производительность и отказоустойчивость.
