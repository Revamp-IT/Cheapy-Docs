Модель ответа
=============

Здесь я расскажу вам о том, как работать с моделями ответов в **Cheapy**

Объявление
----------

Для того, чтобы **Cheapy** понял, какие данные необходимо отформатировать в JSON и отдать клиенту - необходимо создать
модель ответа.

Создадим модель для получения продукта:

.. code-block:: PHP

    <?php

    // src/Response/GetProductByIdResponse.php

    class GetProductByIdResponse extends AbstractResponse
    {
        public string $name;
    }

.. important:: Учтите, что :code:`id` элемента из базы данных указывать не нужно - **Cheapy** сделает это автоматически

Использование
-------------

Привязать модель к методу контроллера еще проще, чем привязать роут. Используем атрибут :code:`#[Response]` с обязательным
аргументом :code:`responseTemplate` (компонент). Вот пример:

.. code-block:: PHP

    <?php

    // some controller file

    // some attributes
    #[Response(responseTemplate: GetProductByIdResponse::class)]
    public function createProduct(): void
    {
        $this->response->name = 'Product Name';
    }

.. important:: Учтите, что передавать свойство контроллера :code:`response` никуда не надо - **Cheapy** сделает это сам,
    вам необходимо только заполнить его согласно указанной модели ответа

