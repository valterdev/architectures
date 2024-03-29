# Введение
Любому разработчику, закладывающему архитектуру для будущего проекта, предстоить решить - каким способом различные модули проекта будут взаимодействовать друг с другом. Тут должен работать принцип низкой связности и высокого уровня зацепления. Или другими словами, модули можно легко подменять и одновременно легко использовать из одного модуля функционал других модулей (не создавая прямых связей между этими модулями).

Решений этой проблемы существует множество. Ниже будут рассмотрены:
1. Dependency Injection (внедрение зависимости) по принципу инверсии зависимости. Это когда высокоровневый модуль не имеет ссылки на низкоуровневый, а низкоуровневые тем или иным способом получают ссылки на высокоровневые модули.
   - Базовый (через интерфейсы)
   - Через IoC контейнер
   - С использование Zenject (библиотека внедрения зависимостей)
2. Глобальное хранилище состояний с реактивной подпиской на изменения в модулях. (Event Driven подход - EDD)
3. Паттерн с шиной Event Bus - схож с предыдущем, но все таки это несколько иной подход через сообщения (бинарные / protobuf, текстовые / json / xml и прочее )
4. Command Pattern - тот же Event Bus, только с жестко запрограммированным форматом команд, в виде сущностей, с которыми напряму взаимодействуешь в коде.
5. База данных и обращение к ней. Это когда идет четкое раздение в приложении на отдельное хранилище данных, и модули которые взаимодействуют с этими данными через CRUD операции. 
6. Взыимодействие через модели данных и биндинги (улучшенная реактивность)
7. ECS Pattern - data driven подход. Где иначе смотрят на архитектуру приложений и где во главе угла становятся данные.

В реальных и сложных проектах могут использоваться более одного метода, для решения части задач (domain driven подход, не путать с data driven, т.к. абревиатуры одинаковые - DDD). Где задачи делятся на области применения и для них подбирается наиболее удачный способ решения проблемы связности модулей.