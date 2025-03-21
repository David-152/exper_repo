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
| dwscription   | Краткое описание  | VARCHAR(200)    | NOT NULL    |

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
| experment_id  | ID эксперимента   | INTEGER         | FK          |
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
