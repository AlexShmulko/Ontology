# Модуль рекомендаций

Модуль принимает входной JSON с результатами теста/трекера, интерпретирует их через онтологию и возвращает JSON со списком рекомендаций.

На выходе возвращаются рекомендации трёх типов:

- `test`
- `practice`
- `theory`

Каждая рекомендация содержит:
- `type`
- `material_id`

## Структура

Для работы модуля нужны следующие файлы:

- `wellbeing_onto/__init__.py`
- `wellbeing_onto/recommendation_demo.py`
- `wellbeing_onto/recommender.py`
- `data/ontologies/wellbeing_app_demo_rules.owl`
- `requirements.txt`
- `user_data.json`

Во время работы автоматически создаются:
- `recommendations.json`
- `result.owl`

Файл `result.owl` является промежуточным артефактом для формирования итогового `recommendations.json`.

### Установка

Рекомендуется Python 3.11+.

Установка зависимостей:
`pip install -r requirements.txt`


#### Запуск

Запуск осуществляется через `python -m wellbeing_onto.recommendation_demo`