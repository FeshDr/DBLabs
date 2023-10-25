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
  1. Изменение статуса заказа
  2. Создание и изменение услуг
  3. Создание и изменение запчастей

# Описание таблицы

# ServiceType - тип услуги

name - varchar(30) NOT NULL

# SparePartType - тип запчасти

name - varchar(30) NOT NULL

# User - пользователь

username - varchar(30) NOT NULL, UNIQUE
email - varchar(60) NOT NULL, must be valid email, UNIQUE
firstname - varchar(50) NOT NULL
lastname - varchar(50) NOT NULL
password - varchar(200) NOT NULL

# Employee - сотрудник

user - OtO(User)
photo - varchar(50) NOT NULL

# SparePart - запасные части для выполнения услуги

type - OtM(SparePartType)
name - varchar(30) NOT NULL, UNIQUE
price - float NOT NULL

# Service - услуга оказываемая клиентом

type - OtM(ServiceType)
name - varchar(30) NOT NULL, UNIQUE
description - varchar(200)
work_price - float NOT NULL

# Device - устройство пользователя

name - varchar(30) NOT NULL
owner - OtO(User)

# Task - задача

master - OtM(Employee)
service - OtM (Service)
device - OtM(Device)
sp - OtM(SparePArt)

# Order - Заказ

tasks - OtM(Task)
client - OtM(User)
contractDate - Date
deadline - Date

# Review - Отзыв на услугу

text = varchar(2000)
author = OtM(User)
date = Date
rate = int
service = MtM(Service)



	


	
