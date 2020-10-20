# Шифрование бакета

_Функциональность находится на [стадии Preview](../../../overview/concepts/launch-stages.md)._

В {{ objstorage-short-name }} есть возможность шифровать объекты в бакете с помощью [ключей {{ kms-short-name }}](../../../kms/concepts/key.md):
* [Добавьте шифрование бакету](#add), чтобы все новые объекты шифровались указанным ключом.
* Указывайте ключ шифрования при [загрузке объекта через API](../../s3/api-ref/object/upload.md).

{% note alert %}

Данные в {{ objstorage-short-name }} шифруются по схеме [envelope encryption](../../../kms/concepts/envelope.md). Удаление ключа равносильно уничтожению зашифрованных им данных.

{% endnote %}

## Добавить шифрование бакету {#add}

{% list tabs %}

- Консоль управления

    Чтобы добавить ключ {{ kms-short-name }}:
    1. В [консоли управления]({{ link-console-main }}) перейдите в бакет, для которого хотите настроить шифрование.
    2. В левой панели выберите **Шифрование**.
    3. В поле **Ключ {{ kms-short-name }}** выберите ключ.
    4. Нажмите кнопку **Сохранить**.

{% endlist %}

## Убрать шифрование бакета {#del}

{% list tabs %}

- Консоль управления

    Чтобы убрать шифрование, удалите ключ {{ kms-short-name }}:
    1. В [консоли управления]({{ link-console-main }}) перейдите в бакет, для которого хотите удалить шифрование.
    2. В левой панели выберите **Шифрование**.
    3. В поле **Ключ {{ kms-short-name }}** выберите **Без шифрования**.
    4. Нажмите кнопку **Сохранить**.

{% endlist %}