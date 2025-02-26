# Платежный аккаунт находится в статусе `PAYMENT_NOT_CONFIRMED`


## Описание проблемы {#issue-description}

* Платежный аккаунт находится в статусе `PAYMENT_NOT_CONFIRMED`;
* Использование платежного аккаунта и создание новых ресурсов в привязанном к нему облаке недоступно.

## Решение {#issue-resolution}

Статус `PAYMENT_NOT_CONFIRMED` означает, что требуется подтверждение аккаунта.

Проверьте адрес электронной почты, указанный в аккаунте Яндекса или {{ yandex-360 }}.

Для подтверждения учетной записи необходимо отправить в ответ на это письмо следующие документы:

1. Копию свидетельства о регистрации юридического лица.
1. Копию решения или протокола о назначении генерального директора, если вы являетесь генеральным директором.
1. Копию доверенности представителя юридического лица, если вы являетесь представителем.

Не забудьте указать полное название организации и [идентификатор облака]({{ link-console-cloud }}). После проверки документов ваш платежный аккаунт может быть активирован и вы сможете начать пользоваться {{ yandex-cloud }}.

## Если проблема осталась {#if-issue-still-persists}

Если вышеописанные действия не помогли решить проблему, [создайте запрос в техническую поддержку]({{ link-console-support}}). При создании запроса укажите следующую информацию:

1. Идентификатор платежного аккаунта со статусом `PAYMENT_NOT_CONFIRMED`.  Он имеет вид `d2nXXXXXXXXXXXXXXXXX`.  Его можно найти [на странице с данными по платежному аккаунту]({{ link-console-billing }}).
1. Описание проблемы.