# UseDesk
[![Swift Package Manager](https://img.shields.io/badge/Swift_Package_Manager-compatible-orange?style=flat-square)](https://img.shields.io/badge/Swift_Package_Manager-compatible-orange?style=flat-square)


- [Добавление библиотеки в проект](#добавление-библиотеки-в-проект)
- [Классы базы знаний](#классы-базы-знаний)
- [Документация](#Документация)


# Добавление библиотеки в проект:

### Swift Package Manager

```swift
.package(url: "https://github.com/usedesk/UseDeskSwift.git", from: "1.0.0")
```

## Подключение SDK 

- Выполняем операцию инициализации чата параметрами без GUI:

| Переменная  | Тип | Описание |
| -------------| ------------- | ------------- |
| CompanyID\* | String | Идентификатор компании. Как найти описано в [документации](https://docs.usedesk.ru/article/61) |
| ChanelId\* | String | Идентификатор канала (добавлен  в v1.1.5). Как найти описано в [документации](https://docs.usedesk.ru/article/10167) |
| UrlAPI\* | String | Адрес API. Стандартное значение `secure.usedesk.ru/uapi` |
| API Token\* | String | Личный API ключ |
| Url\* | String | Адрес сервера в формате - pubsubsec.usedesk.ru |
| Knowledge Base ID | String | Идентификатор базы знаний. Если не указан, база знаний не используется |
| Email | String | Почта клиента |
| Phone | String | Телефон клиента |
| UrlToSendFile | String | Адрес для отправки файлов. Стандартное значение `https://secure.usedesk.ru/uapi/v1/send_file`  |
| Port | String | Порт сервера  |
| Name | String | Имя клиента |
| NameOperator | String | Имя оператора |
| FirstMessage | String | Автоматическое сообщение. Отправиться сразу после иницилизации от имени клиента |
| Note | String | Текст заметки |
| AdditionalFields | [Int : String] | Массив дополнительный полей в формате - id : "значение". Для текстовых полей значение - строка, для списка - строка с точно совпадающим значением списка, для флага - строка "false" или "true" |
| AdditionalNestedFields | [[Int : String]] | Массив допл полей типа вложенный список. Каждый подмассив представляет один вложенный список. Формат фложенного списка - [id1: "значение", id2 : "значение", id3 : "значение"], где id1, id2, id3 идентификаторы значений по уровням вложенности |
| Token | String | Подпись, однозначно идентифицирующая пользователя и его чат на любых устройствах для сохранения истории переписки. (генерирует наша система,  ограничение не меньше 64 символа) |
| isSaveTokensInUserDefaults | Bool | Сохранять ли токен UserDefaults |

\* - обязательный параметр

#### Пример:
```swift
let usedesk = UseDeskSDK()
usedesk.startWithoutGUI(companyID: "1234567", chanelId: "1234", knowledgeBaseID: "1", api_token: "143ed59g90ef093s", email: "lolo@yandex.ru", phone: "89000000000", url: "pubsubsec.usedesk.ru", urlToSendFile: "https://secure.usedesk.ru/uapi/v1/send_file", port: "213", name: "Name", operatorName: "NameOperator", firstMessage: "message", note: "Note text", additionalFields: [1 : "value"], additionalNestedFields: [[1 : "value1", 2 : "value2", 3 : "value3"]], token: "Token", connectionStatus: { (success, error) in

})
```

### Блок возвращает следующие параметры:

#### СonnectionStatus:

| Тип | Описание |
| ------------- | ------------- |
| Bool | Успешность подключения к чату |
| UDFeedbackStatus | Статус показа формы обратной связи |
| String | Токен пользователя |

#### ErrorStatus:

| Тип | Описание |
| ------------- | ------------- |
| UDError | Задокументированый тип ошибки |
| UDFeedbackStatus | Описание ошибки |


# Документация:

Документация находится по адресу - http://sdk.usedocs.ru/

## Author

Сергей, kon.sergius@gmail.com

## License

UseDesk_SDK_Swift is available under the MIT license. See the LICENSE file for more info.

