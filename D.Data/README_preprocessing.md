# 📄 README_preprocessing — Подготовка данных

## Общие этапы предобработки

Для всех ноутбуков выполняются следующие общие шаги предобработки данных:

- **Формирование целевой переменной:** `target = like + dislike` в тренировочном наборе.
- **Оптимизация памяти:**
  - Приведение типов данных (`category`, `int8`) для минимизации объёма данных.
- **Сохранение новых датасетов:**
  - После предобработки данные сохраняются для быстрой тренировки моделей.

Эти шаги выполняются в каждом ноутбуке для уменьшения размера данных и упрощения структуры.

---

## 📄 fv2 — Первичная предобработка

### Что сделано:
- **Дополнительные признаки:**
  - Добавлены признаки: `age`, `item_duration` через конфигурацию `CONFIG`.

---

## 📄 fv3 — Вторичная предобработка

### Что сделано:
- **Дополнительные признаки:**
  - Добавлены признаки: `age`, `gender`, `duration`, `source_id`.
  - Интеграция эмбеддингов содержимого клипа (`embeddings`) в тренировочные и тестовые данные.

---

## 📄 av1 — Расширенная предобработка

### Что сделано:
- **Дополнительные признаки:**
  - Добавлены признаки на уровне пользователей, видео и источников:
    - **Пользователи:** `age`, `gender`, `user_like_ratio`, `user_dislike_ratio`, `user_ignore_ratio`, `user_share_ratio`, `user_bookmark_ratio`, `user_avg_spent_time`, `user_view_ratio`, `user_full_view_ratio`.
    - **Видео:** `item_duration`, `item_like_ratio`, `item_dislike_ratio`, `item_ignore_ratio`, `item_share_ratio`, `item_bookmark_ratio`, `item_avg_spent_time_ratio`, `item_view_ratio`, `item_full_view_ratio`.
    - **Источник:** `source_id`, `source_like_ratio`, `source_dislike_ratio`, `source_ignore_ratio`, `source_share_ratio`, `source_bookmark_ratio`, `source_avg_spent_time_ratio`, `source_view_ratio`, `source_full_view_ratio`.
