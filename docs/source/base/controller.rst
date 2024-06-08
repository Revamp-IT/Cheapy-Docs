Контроллер
==========

Вот мы и подошли к основному компоненту фреймворка - контроллеру.

Создание контроллера
--------------------

Объявить контроллер довольно просто. Необходимо лишь создать файл в папке :code:`src/Controller`.

Давайте создадим контроллер, который будет обслуживать сущность продукта:

.. code-block:: PHP

    <?php

    // src/Controller/ProductController.php

    class ProductController extends AbstractController
    {
        // some code
    }

.. important:: Учтите, что указывать контроллер где-либо не нужно - **Cheapy** сам найдет все контроллеры и будет их
    учитывать

Наполнение контроллера
----------------------

Сейчас важно наполнить контроллер методами так, чтобы весь необходимый функционал был доступен клиенту.

.. important:: Пожалуйста, создавайте только один метод для каждого раздела функционала - получения, создания, обновления
    и удаления экземпляра сущности

.. code-block:: PHP

    <?php

    // src/Controller/ProductController.php

    class ProductController extends AbstractController
    {
        // some attributes
        public function getProducts(): void
        {
            // some code
        }

        // some attributes
        public function getProductById(): void
        {
            // some code
        }

        // some attributes
        public function createProduct(): void
        {
            // some code
        }

        // some code
    }