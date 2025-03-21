# Проект: База данных для управления научной лабораторией

### Введение

#### ***Цель работы:***
Получение практических навыков работы с промышленными СУБД, проектирование базы данных (концептуальное, логическое,физическое)
\
Создание базы данных для управления научной лабораторией, которая позволит:
- Учитывать эксперименты, оборудование, материалы и сотрудников.
- Отслеживать использование ресурсов.
- Управлять проектами и анализировать результаты экспериментов.

---

#### ***Инструменты:***
- PostgreSQL 15

---

#### ***Описание проекта:***
Проект представляет собой базу данных для управления научной лабораторией. Основная цель — учет экспериментов, оборудования, сотрудников, материалов и отчетов. База данных позволяет отслеживать использование ресурсов, управлять проектами и анализировать результаты экспериментов.

---

### Предметная область и сущности

#### Сущности:
1. **Проекты (Projects)** — информация о научных проектах, включая название, даты начала и окончания, бюджет и описание.
2. **Эксперименты (Experiments)** — информация о проводимых экспериментах, включая даты начала и окончания, статус и описание.
3. **Сотрудники (Employees)** — информация о сотрудниках лаборатории, включая имя, должность, зарплату, отдел и даты начала/окончания работы.
4. **Оборудование (Equipment)** — информация об оборудовании лаборатории, включая название, местоположение и статус.
5. **Материалы (Materials)** — информация о материалах, используемых в экспериментах, включая название, количество, единицы измерения и даты начала/окончания использования.
6. **Отчёты (Reports)** — информация об отчётах, создаваемых по результатам экспериментов.
7. **Использование оборудования (Usage Equipment)** — информация об использовании оборудования в экспериментах.
8. **Использование материалов (Usage Materials)** — информация об использовании материалов в экспериментах.
9. **Активность сотрудников (Employees Activity)** — информация об активности сотрудников в проектах.

---

### Актуальность

Научные лаборатории играют ключевую роль в исследованиях и разработках. Управление ресурсами, проектами и экспериментами требует эффективного учета и анализа данных. База данных для научной лаборатории позволяет автоматизировать эти процессы, повышая эффективность работы и снижая вероятность ошибок.

---

### Модели базы данных

#### Концептуальная модель
![Концептуальная модель](./docs/conceptual-model.png)

#### Логическая модель
![Логическая модель](./docs/logical-model.png)

#### Физическая модель

### Проекты (Projects)

| Название      | Описание          | Тип данных      | Ограничения |
|---------------|-------------------|-----------------|-------------|
| project_id    | ID проекта        | INTEGER         | PK          |
| name          | Название проекта  | VARCHAR(200)    | NOT NULL    |
| start_date    | Дата начала       | TIMESTAMP       | NOT NULL    |
| end_date      | Дата окончания    | TIMESTAMP       |             |
| budget        | Бюджет проекта    | DECIMAL(15, 2)  |             |
| description   | Краткое описание  | VARCHAR(200)    | NOT NULL    |

### Эксперименты (Experiments)

| Название      | Описание          | Тип данных      | Ограничения |
|---------------|-------------------|-----------------|-------------|
| experiment_id | ID эксперимента   | INTEGER         | PK          |
| project_id    | ID проекта        | INTEGER         | FK          |
| start_time    | Дата начала       | TIMESTAMP       | NOT NULL    |
| end_time      | Дата окончания    | TIMESTAMP       |             |
| status        | Статус            | VARCHAR(200)    | NOT NULL    |
| description   | Краткое описание  | VARCHAR(200)    | NOT NULL    |

### Сотрудники (Employees)

| Название      | Описание          | Тип данных      | Ограничения |
|---------------|-------------------|-----------------|-------------|
| employee_id   | ID сотрудника     | INTEGER         | PK          |
| name          | Имя сотрудника    | VARCHAR(200)    | NOT NULL    |
| salary        | Зарплата          | DECIMAL(15, 2)  | NOT NULL    |
| department    | Отдел             | VARCHAR(200)    | NOT NULL    |
| position      | Должность         | VARCHAR(200)    | NOT NULL    |
| start_date    | Дата начала       | TIMESTAMP       | NOT NULL    |
| end_date      | Дата окончания    | TIMESTAMP       |             |
| is_current    | Текущий статус    | BOOLEAN         |             |

### Оборудование (Equipment)

| Название      | Описание          | Тип данных      | Ограничения |
|---------------|-------------------|-----------------|-------------|
| equipment_id  | ID оборудования   | INTEGER         | PK          |
| name          | Название          | VARCHAR(200)    | NOT NULL    |
| location      | Местоположение    | VARCHAR(200)    | NOT NULL    |
| status        | Статус            | VARCHAR(50)     | NOT NULL    |

### Материалы (Materials)

| Название      | Описание          | Тип данных      | Ограничения |
|---------------|-------------------|-----------------|-------------|
| material_id   | ID материала      | INTEGER         | PK          |
| name          | Название материала| VARCHAR(200)    | NOT NULL    |
| quantity      | Количество        | INT             | NOT NULL    |
| unit          | Единицы измерения | VARCHAR(200)    | NOT NULL    |
| start_date    | Дата начала записи| TIMESTAMP       | NOT NULL    |
| end_date      | Дата окончания    | TIMESTAMP       |             |
| is_current    | Текущий статус    | BOOLEAN         |             |

### Отчеты (Reports)

| Название      | Описание          | Тип данных      | Ограничения |
|---------------|-------------------|-----------------|-------------|
| report_id     | ID отчета         | INTEGER         | PK          |
| experiment_id | ID эксперимента   | INTEGER         | FK          |
| report_date   | Дата отчета       | TIMESTAMP       | NOT NULL    |

### Использованное оборудование (Usage Equipment)

| Название              | Описание          | Тип данных      | Ограничения |
|-----------------------|-------------------|-----------------|-------------|
| usage_equipment_id    | ID исп.оборудования | INTEGER       | PK          |
| experiment_id         | ID эксперимента   | INTEGER         | FK          |
| equipment_id          | ID оборудования   | INTEGER         | FK          |
| usage_date            | Дата использования| TIMESTAMP       | NOT NULL    |

### Использованные материалы (Usage Materials)

| Название              | Описание          | Тип данных      | Ограничения |
|-----------------------|-------------------|-----------------|-------------|
| usage_material_id     | ID исп.материала  | INTEGER         | PK          |
| experiment_id         | ID эксперимента   | INTEGER         | FK          |
| material_id           | ID материала      | INTEGER         | FK          |
| usage_date            | Дата использования| TIMESTAMP       | NOT NULL    |
| usage_quantity        | Использовано      | INT             |             |

### Активность сотрудников (Employees Activity)

| Название      | Описание          | Тип данных      | Ограничения |
|---------------|-------------------|-----------------|-------------|
| ea_id         | ID активности     | INTEGER         | PK          |
| project_id    | ID проекта        | INTEGER         | FK          |
| employee_id   | ID сотрудника     | INTEGER         | FK          |
| start_date    | Дата              | TIMESTAMP       | NOT NULL    |

---

#### ***Заключение***

Данная база данных позволяет эффективно управлять научной лабораторией, учитывая все аспекты её работы. Она обеспечивает целостность данных, поддерживает версионирование (SCD Type 2) и позволяет анализировать использование ресурсов.

---
