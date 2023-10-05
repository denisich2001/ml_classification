**Классификация товаров**

ML-алгоритм для классификации товаров

Сервис состоит из двух классов:
* DataHandler - все что касается обработки данных (удаление пропусков, выбросов)
* TNVEDClassifier - все что касается моделей: автоматический подбор гиперпараметров, обучение, предсказание, выбор лучшей.

Планы по разработке модели классификации:
I. Ресерч:
    1. Изучить данные (выделить проблемы)
    2. Выбрать метрику
    3. Вручную обучить модельки (логистическая регрессия, случайный лес(вероятно будет оптимален, т.к. много категорийных факторов), xgboost, catboost(?)), посмотреть как отрабатывают
    4. Что делать с дисбалансом?
    5. Что делать с пропусками?
    6. Как искать и что делать с выбросами?
    7. Что делать с кореелирующими столбцами
    8. Как обрабатывать текстовые данные, категорийные(как определять) и object?
    9. Как определять тип поля?
    10. Как делить автоматически на тестовую и обучающую? (если избавимся от дисбаланса, то рандомно)
    11. Как подбирать гиперпараметры, чтобы не переобучатьс, и не недообучаться

II. Работа с кодом:
    1. Реализовать автоматизированную обработку данных (вышеописанные проблемы)
    2. Реализовать автоматизированное обучение моделей:
        * Зарузка треинсета
        * Разбиение на train/test
        * Подбор гиперпараметров
        * Обучение модели
        * Проверка точности
        * Выбор оптимальной модели
        * Предсказание и возврат ответа


**Мемо по встрече 22.09.2023**:
* До 25.09 - 26.09 жду примеров датасетов для продолжения ресерча
* Пока решили, что вместе с датасетом на обучение, в систему будет передаваться файл с описанием типов данных колонок - число, категория, текст. В будущем рассматривается возможность автоматизирования определения типов данных
* Будет несколько столбцов с названиями вида: "ХК{число}", в которых будет написано название хакрактеристики, 
а в столбце "Значение_ХК{число}" - ее значение. Договорились, что пока не будем выделять эти характеристики в отдельные колонки, а то получатся очень разреженные таблички
* Должна отображаться надежность обучения модели (пока сам выбираю метрику и пороговое значение)
* Примерно: пропуски в числовых данных заполняем медианой(???), в категорийных - создаем категорию unknow, текстовые - ???
* Обученые модели должны сохраняться в БД, а также должна быть возможность переобучения 


Орг вопросы:
* Данные для классификации будут полные или с большим количеством пропусков (будет страдать точность) (если в примере классификации от клевера удалять поля с пропускаами в столбце ЭкоКласс, то у нас потеряется один из классов - 2710125100, и модель никогда не будет его предсказывать)?