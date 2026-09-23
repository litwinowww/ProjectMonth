# Семантический поиск товаров по текстовому запросу (CalmFruits)

MVP системы поиска query-to-item: по текстовому запросу пользователя система возвращает топ-K релевантных карточек товаров. Сравниваем лексический baseline (TF-IDF) с семантическим поиском на эмбеддингах и проверяем гипотезы по улучшению качества. Качество оцениваем по синтетической разметке релевантности (0-3) метриками Precision@K, Recall@K, MRR, NDCG@K, HitRate@K.

## Структура репозитория

```
.
├── semantic_search_project.ipynb       # EDA, пайплайн поиска, оценка, эксперименты
├── semantic_search_project_workbook.md # рабочий документ: QA-сессия, наблюдения, выводы
├── check_mlflow.py                     # проверка эксперимента в MLflow
├── requirements.txt                    # зависимости
└── .env.example                        # шаблон переменных окружения
```

## Запуск

1. Создать и активировать виртуальное окружение, установить зависимости:

   ```bash
   python -m venv calmfruitsvenv
   calmfruitsvenv\Scripts\activate        # Windows
   source calmfruitsvenv/bin/activate     # Linux / macOS
   pip install -r requirements.txt
   ```

2. Скопировать `.env.example` в `.env` и заполнить доступы к S3 и MLflow.

3. Открыть и выполнить `semantic_search_project.ipynb` сверху вниз. Данные ноутбук берёт из папки `data/`, а если файла там нет - читает напрямую из бакета `s3-ds-source`.

4. Проверить эксперимент в MLflow:

   ```bash
   python check_mlflow.py wb-semantic-search
   ```
