# Классификация токсичных комментариев 


## Описание проекта
Интернет-магазин «Викишоп» запускает новый сервис. Теперь пользователи могут редактировать и дополнять описания товаров, как в вики-сообществах. То есть клиенты предлагают свои правки и комментируют изменения других. Магазину нужен инструмент, который будет искать токсичные комментарии и отправлять их на модерацию.
Обучите модель классифицировать комментарии на позитивные и негативные. В вашем распоряжении набор данных с разметкой о токсичности правок.

## Описание данных

- text - содержит текст комментария
- toxic - целевой признак

## Вывод
В ходе данного проекта я анализировал отзывы на токсичность. Для этого использовалась tf_idf модель представления языка.
1. Сначала я очистил и лемматизировал изначальный текст.
2. Затем я поделил датасет на трейн и тес, используя аргумент stratify для сохранения распредления токсичных отзывов.
2. Далее я изучил гиперпараметры для двух моделей.

LinearSVC дал лучшие результаты на кросс-валидации. На тесте LinearSVC значение **f1 = 0.786**, что является приемлимым результатом в рамках этого проекта
