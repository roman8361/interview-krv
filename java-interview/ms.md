[Вопросы для собеседования](README.md)

# Микросервисы
+ [Что характеризует МС](ms.md#Что-характеризует-МС)
+ [Какие есть плюсы и минусы микросервесно архитектуры?](ms.md#Какие-есть-плюсы-и-минусы-микросервесно-архитектуры?)

## Что характеризует МС
* Микро не значит что маленький это значит что их много
* МС должне быть автономен
* Изменения в МС должны минимально влиять на связанные с ним компоненты
* МС может быть свободно заменен на другой ЯП с соблюдением контрактов по API
* МС должен иметь свою БД


## Какие есть плюсы и минусы микросервесно архитектуры?

__ПЛЮСЫ:__

* Изменение в одном месте МС не ведут к необходимости редеплоя
* Порог вхождения в предметную область ниже
* Разграничение зон ответсвенности для разработки
* Тестирование облегчается
* В МС можно поменять ЯП
* Вертикальная и горизонтальная массштабируемость
* Код МС не связан с кодом другого МС
* Каждый МС имеет строгоограниченный функционал

__МИНУСЫ:__

* Требуется детальное проектирование архитектуры
* Низкая связанность данных (и плюс и минус)
* Возможность хранения в БД не консистентных данных
* Усложняется процесс CI / CD
* Увеличивается время на отладку межсервисных взаимодействий