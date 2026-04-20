# Життєвий цикл Pull Request (PR): Стандарти та Процеси

Цей документ описує еталонний процес розробки через Pull Request (PR), що забезпечує високу якість коду, безпеку та ефективну співпрацю в команді.

---

## 1. Концептуальна схема процесу

Процес PR — це механізм контролю якості, який дозволяє перевірити зміни в коді перед їх об'єднанням з основною гілкою проєкту.

### Діаграма послідовності (Sequence Diagram)

```mermaid
sequenceDiagram
    participant D as Розробник
    participant G as Git-репозиторій
    participant CI as CI/CD Pipeline
    participant R as Рецензент (Reviewer)
    participant M as Main Branch

    D->>G: Створення гілки (feature-branch)
    D->>G: Робота над кодом та Commit
    D->>G: Push гілки на сервер
    D->>G: Відкриття Pull Request
    G->>CI: Автоматичний запуск тестів
    CI-->>G: Результат (Pass/Fail)
    G->>R: Запит на перегляд коду
    R->>D: Коментарі та зауваження
    D->>G: Виправлення (Updates)
    R-->>G: Схвалення (Approve)
    G->>M: Злиття (Merge) та видалення гілки
```

## Стани Pull Request

```mermaid
stateDiagram-v2
    [*] --> Draft: Створення PR
    Draft --> Open: Готовність до перегляду
    Open --> InReview: Розпочато перегляд
    InReview --> ChangesRequested: Знайдено помилки
    ChangesRequested --> InReview: Виправлення внесено
    InReview --> Approved: Перевірку пройдено
    Approved --> Merged: Злиття з Main
    Open --> Closed: Відхилено/Дублікат
    Merged --> [*]
```
