# DBLabs

# Функциональные требования:
1. Авторизация пользователей
2. Система ролей
3. Логгирование действий пользователей
4. Управление пользователями
5. Создание услуг
6. Создание заказов
7. Создание отзывов на услуги
8. Панель администратора :
  8.1. Изменение статуса заказа
  8.2. Создание и изменение услуг
  8.3. Создание и изменение запчастей

# Описание таблицы

# ServiceType - тип услуги

1. name - varchar(30) NOT NULL

# SparePartType - тип запчасти

1. name - varchar(30) NOT NULL

# User - пользователь

1. username - varchar(30) NOT NULL, UNIQUE
2. email - varchar(60) NOT NULL, must be valid email, UNIQUE
3. firstname - varchar(50) NOT NULL
4. lastname - varchar(50) NOT NULL
5. password - varchar(200) NOT NULL

# Employee - сотрудник

1. user - OtO(User)
2. photo - varchar(50) NOT NULL

# SparePart - запасные части для выполнения услуги

1. type - OtM(SparePartType)
2. name - varchar(30) NOT NULL, UNIQUE
3. price - float NOT NULL

# Service - услуга оказываемая клиентом

1. type - OtM(ServiceType)
2. name - varchar(30) NOT NULL, UNIQUE
3. description - varchar(200)
4. work_price - float NOT NULL

# Device - устройство пользователя

1. name - varchar(30) NOT NULL
2. owner - OtO(User)

# Task - задача

1. master - OtM(Employee)
2. service - OtM (Service)
3. device - OtM(Device)
4. sp - OtM(SparePArt)

# Order - Заказ

1. tasks - OtM(Task)
2. client - OtM(User)
3. contractDate - Date
4. deadline - Date

# Review - Отзыв на услугу

1. text = varchar(2000)
2. author = OtM(User)
3. date = Date
4. rate = int
5. service = MtM(Service)



	


	
