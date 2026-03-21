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
- `wellbeing_onto/api.py`
- `data/ontologies/wellbeing_app_demo_rules.owl`

### Установка

Установка зависимостей:
`pip install -r requirements.txt`

#### Запуск

Для работы необходимо сначал поднять сервис: `uvicorn wellbeing_onto.api:app --host 0.0.0.0 --port 8000`

##### Работа

Чтобы получить рекомендации от сервиса нужно отправить POST запрос на `http://localhost:8000/recommendations`

В теле запроса нужно отправить json структуру. Например: 

```bash -> (bash только только для подстветки синтаксиса)

{
  "test_id": "bc9f1204-ea5d-40b0-b367-359bf9b2cc21",
  "scale_results": [
    {
      "scale_title": "Stress",
      "score": 13
    },
    {
      "scale_title": "Anxiety",
      "score": 9
    },
    {
      "scale_title": "Depression",
      "score": 11
    }
  ]
}

```
В ответ придет:

```bash 

[
    {
        "type": "practice",
        "material_id": ""
    },
    {
        "type": "practice",
        "material_id": ""
    },
    {
        "type": "practice",
        "material_id": "9bfde30c-0aca-4ed8-abdf-b768b6b8f67f"
    },
    {
        "type": "test",
        "material_id": "f56b5284-323e-42db-bd74-c80e8a5dc29a"
    },
    {
        "type": "test",
        "material_id": "33d10952-aed7-4a4e-9e5a-dbd01b2f294d"
    },
    {
        "type": "test",
        "material_id": "3a9a3c8d-348e-4f0d-aefd-0feaa960ac25"
    },
    {
        "type": "practice",
        "material_id": "4e3f51e9-aad8-4a13-b4b7-d748e472d394"
    }
]

```