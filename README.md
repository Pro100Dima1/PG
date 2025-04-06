### Задание 1
Этапы разработки:
1)	Анализ требований.
Используя подход shift-left testing, на этом этапе QA подключаются к анализу требований. Что б минимизировать затраты на фиксы ошибок. Для этого, когда требования будут собраны, но не зафиксированы, надо назначить встречу всей команды, что б каждый член команды мог проанализировать требования и уточнить непонятные моменты. Аналитик должен посвятить команду в тонкости техническую часть требований, а ПМ должен погрузить команду в бизнес процесс. Тогда QA смогут выделить критичные сценарии для бизнеса и в дальнейшем грамотнее выстраивать тестирование и тест дизайн. Так же на этой встрече могут быть заблаговременно выявлены логические, бизнесовые или технические ошибки в требованиях. Что значительно удешевит и ускорит их исправление. Так же по существующей аналитике пишутся чек листы, по которым в дальнейшем будут писаться тест кейсы. Пишется план тестирования в котором прописываются сроки, человекочасы, инструменты тестирования итд. (Ресурсы: 2 QA. Сроки:1 неделя на анализ и составление плана с чек листами)
2)	Проектирование
На данном этапе должны привлекаться опытные QA, которые могут знать особенности уже имеющейся архитектуры. Слабы места итд. Т.к. QA владеют довольно большими знаниями о проекте в целом, то они могут помочь указать на места где может быть высокая нагрузка на сервис. Может где то нелогично часто приходится ходить в разные БД для формирования простого запроса. Такие моменты могут подсветить опытные QA. Так же обсуждаются инструменты для выстраивания грамотного CI\CD. Что б QA и разработка были на одной волне.
(Ресурсы: 2QA. Сроки: 1-1,5 недели)
3)	Разработка
На этапе разработки QA приступают к написанию тестовой модели. Применяя техники тест дизайна :
- Предугадывание ошибки
- Таблица принятия решений
- Попарное тестирование
- Анализ граничных значений
- Классы эквивалентности
Создаются тестовые наборы API тесты, Интеграционные тесты, UI тесты, Е2Е. 
В API тестах пишется больше всего тестов. Пишутся контрактные тесты на проверку маппинга и валидацию посылаемых  и запрашиваемых данных.

В Интеграционных тестах пишутся тесты интеграций микросервисов друг с другом. Микросервисов с БД. UI части с бэкендом.
В UI тестах пишутся тесты на проверку всех UI элементов на всех экранах во всем флоу.
В Е2Е пишутся сквозные тесты, которые проходят по основному пользовательскому пути и проверяют, что весь сценарий работает целиком. Проверяются интеграции всего процесса, логи, метрики, записи\выгрузки БД и UI часть.
Заводятся остальные артефакты релиза. Подготавливается рыба отчета по тестированию. Заводится релиз. Уточняются сроки. 
Проводится настройка тестового стенда и подготовка тестовых данных.
Выстраивание метрик тестирования. На первом релизе важно покрыть как можно больше требований кейсами. Так что будем руководствоваться метрикой тестового покрытия требований что б понять. 
Т.к. ПО связанно с покупками, то нам важно не иметь критичных и серьезных багов. Поэтому за Quality Gate будем брать отсутствие критичных и серьезных багов. Допустимы тривиальные баги с низким приоритетом (не более 3 штук), которые попадают в техдолг и обязаны быть исправлены в следующем релизе\хотфиксе.
При получении промежуточных билдов, надо проверять интеграции, особенно внешние. Что б успеть отладиться к этапу тестирования.
(Ресурсы: 2-3 QA *Что б была возможность проводить ревью кейсов*. Сроки: 4-5 недели)
4)	Тестирование
На данном этапе проводится само тестирование. 
При получении сборки со всеми разработанными фичами, надо провести Smoke тестирование для проверки работоспособности всей системы. Следующей проверкой должен быть Critical path, что б проверить главный бизнесовый путь клиента.

Далее проводятся позитивные проверки критичного для бизнеса функционала. Дальше если нигде не заблокированы, то более опытные QA подключаются к проверкам E2E и интеграционных проверок. Менее опытные коллеги могут проверить маппинг в контрактных тестах API и экраны в UI.
Так же есть активность по заведению и актуализации багов. После успешного фикса багов заводится и проходится тестовый прогон с регрессионными кейсами.
Итогом тестирования является отчет о тестировании в котором указаны сроки тестирования, кто и что тестировал. Линкуются прогоны с пройденными тест кейсами и баги, как пофикшенные, так и пропущенные в релиз. Так же пишутся рекомендации по улучшению качества на следующей итерации.
(Ресурсы: 2-3 QA *Лучше пусть будет в запасе 1 человек, ибо первый запуск и нет понимания слабых мест и с какими трудностями придется столкнуться в ходе тестирования* Сроки: 4-5 недели с запасом.)

5)	Ввод в эксплуатацию и поддержка
На данном этапе происходит поддержка приложения. Происходит мониторинг действий пользователей. Сбор метрик, построение воронки. Анализ нагрузки и стабильности. Получение и разбор багов от 1-й линии поддержки и выкатка хотфиксов. Проведение регрессионного тестирования после каждого хотфикса.
(Ресурсы: 1 QA. Сроки: на протяжении всего времени эксплуатации)
