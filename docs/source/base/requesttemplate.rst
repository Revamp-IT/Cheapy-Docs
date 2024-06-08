Модель запроса
==============

Здесь я расскажу вам о том, как работать с моделями запросов в **Cheapy**

Объявление
----------

Для того, чтобы **Cheapy** понял, какие данные будут переданы с клиента - необходимо создать модель запроса.

Создадим модель для создания продукта:

.. code-block:: PHP

    <?php

    // src/Request/CreateProductRequest.php

    class CreateProductRequest extends AbstractRequest
    {
        public string $name;
    }

Использование
-------------

Привязать модель к методу контроллера еще проще, чем привязать роут. Используем атрибут :code:`#[Request]` с обязательным
аргументом :code:`requestTemplate` (компонент). Вот пример:

.. code-block:: PHP

    <?php

    // some controller file

    // some attributes
    #[Request(requestTemplate: CreateProductRequest::class)]
    public function createProduct(): void
    {
        $name = $this->request->name;
    }

