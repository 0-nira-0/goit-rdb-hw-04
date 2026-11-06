# goit-rdb-hw-04

Домашнє завдання до Теми 4 курсу "Relational Databases for Data Science". Автор: Mykyta Oliinyk.

## Датасет

Brazilian E-Commerce Public Dataset by Olist.
Джерело: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

Вибірка не формується: використано повні таблиці з шести CSV (клієнти, замовлення, позиції, товари, продавці, відгуки). Файли датасету не зберігаються в репозиторії, notebook завантажує їх через `kagglehub`.

| Таблиця | Рядків |
| --- | ---: |
| `olist_customers` | 99441 |
| `olist_orders` | 99441 |
| `olist_order_items` | 112650 |
| `olist_products` | 32951 |
| `olist_sellers` | 3095 |
| `olist_order_reviews` | 99224 |

Під час перенесення з raw- у typed-таблиці рядки не втрачаються.

## Запуск

Google Colab: відкрити `hw_t4.ipynb` і виконати Restart & Run All. Залежності встановляться в першій клітинці з кодом. Якщо Kaggle вимагатиме доступ, налаштуйте credentials або покладіть CSV у `data/olist/` у робочій папці (у Colab це `/content/data/olist/`). У Colab потрібна версія середовища 2026.07 (Python 3.12): Runtime → Change runtime type → Runtime version, бо `pgserver` не має збірок для Python 3.13.

Локально потрібен Python 3.12, бо `pgserver` не має wheel для 3.14:

```bash
python3.12 -m venv .venv
source .venv/bin/activate
pip install pgserver psycopg2-binary "psycopg[binary]" sqlalchemy pandas kagglehub jupyter
jupyter nbconvert --to notebook --execute --inplace --ExecutePreprocessor.timeout=1800 hw_t4.ipynb
```

PostgreSQL запускається через `pgserver` у `/tmp/hw4_pg`, окремо встановлювати його не потрібно. Notebook можна запускати повторно: таблиці створюються заново через `DROP TABLE IF EXISTS`.

## Структура

```
hw_t4.ipynb         notebook з кодом, виводами й інтерпретацією
README.md           опис роботи
.gitignore          виключає дані й службові файли
```
