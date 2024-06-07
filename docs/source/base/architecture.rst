Архитектура
===========
Страница посвящена сущностям, которые существуют в **Cheapy**

Роут
----

**Роут** - главное свойство любого метода контроллера, объявляется атрибутом :code:`#[Route]` и содержит в себе
:code:`URI` и методы, которые будут доступны

Модель запроса
--------------

Все запросы c методами :code:`POST`, :code:`UPDATE` и :code:`DELETE` должны соответствовать указанной модели запроса для
того, чтобы исключить ручную проверку наличия пришедших данных. Если каких либо данных не хватает - ответ будет
экземпляром :code:`JsonError` с кодом ответа :code:`400` и шорткодом ошибки :code:`R2`. Модель запроса указывается
аттрибутом :code:`#[Request]` в контроллере. Атрибут содержит в себе :code:`requestTemplate`. Вот пример модели запроса:

.. code-block:: PHP

   <?php

   // Request/Deal/CreateDealRequest.php

   class CreateDealRequest extends AbstractRequest
   {
       public string $name;
   }

Модель ответа
-------------

Все запросы с методом :code:`GET` должны соответствовать указанной модели ответа для того, чтобы исключить ручную
проверку пришедших данных на клиенте. При ошибках в заполнении модели - ответ будет предоставлен с кодом :code:`500` и
шорткодом ошибки :code:`R3`. Модель ответа указывается атрибутом :code:`#[Response]` в контроллере. Атрибут содержит в
себе :code:`responseTemplate`. Вот пример модели ответа:

.. code-block:: PHP

    <?php

    // Response/Deal/GetDealByIdResponse.php

    class GetDealByIdResponse extends AbstractResponse
    {
        public string $name;
    }

Контроллер
----------

Если вы не знакомы с другими фреймворками, то приведу краткое пояснение. Все запросы пришедшие с клиента попадают в
контроллеры. Обработкой запроса занимается метод, в котором шаблон :code:`URI` и поддерживаемые методы совпали с
предоставленными. Вот пример контроллера:

.. code-block:: PHP

    <?php

    // Controller/DealController.php

    class DealController extends AbstractController
    {
        #[Route(uri: '/deals/{id}', methods: ['GET'])]
        // some attributes
        public function getDealById(): void
        {
            // some code
        }
    }

Сущность базы данных
--------------------

Если вы знакомы с другими фреймворками, то наверняка знаете, что такое сущность базы данных. В **Cheapy** они называются
:code:`DataMap`. Каждый :code:`DataMap` объект содержит в себе колонки таблицы. Название используемой таблицы в базе
данных такое же, какое и у названия класса :code:`DataMap`. Вот пример сущности:

.. code-block:: PHP

    <?php

    // DataMap/Deal.php

    class Deal extends AbstractDataMap
    {
        // some attributes
        public string $name;

        // some attributes
        public int $age;
    }