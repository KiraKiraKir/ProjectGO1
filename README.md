Итоговая задача модуля 1 Яндекс лицея

Этот проект реализует веб-сервис, принимающий выражение через Http запрос и возвращабщий результат вычислений

Инструкция по запуску:

Убедитесь, что у вас установлен Go (версия 1.16 или выше).

Скопируйте репозиторий(через git bash):

git clone https://github.com/KiraKiraKir/ProjectGO1

cd Module1

Запустите сервер:

go run ./cmd/calc_service/main.go

Сервер будет доступен по адресу http://localhost:8080.

У меня чтобы дальше работали запросы нужно перезапустить консоль git bash, затем опять открыть путь вводом cd Module1 и после этого можно вводить запросы

Примеры использования:

Успешный запрос:

curl --location 'http://localhost:8080/api/v1/calculate' \
--header 'Content-Type: application/json' \
--data '

{ "expression": "2*2+2" }'

Ответ:

{ "result": "6" }

Ошибка 422 (невалидное выражение):

curl --location 'http://localhost:8080/api/v1/calculate' \
--header 'Content-Type: application/json' \
--data '

{ "expression": "2+a" }'

Ответ: { "error": "Expression is not valid" }

Ошибка 500 (внутренняя ошибка сервера):

curl --location 'http://localhost:8080/api/v1/calculate' \
--header 'Content-Type: application/json' \
--data '

{ "expression": "2/0" }'

Ответ: { "error": "Internal server error" }