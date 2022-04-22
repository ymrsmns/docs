---
title: "Yandex Monitoring. Ответы на вопросы"
description: "Как мне поставлять в Yandex Monitoring метрики своего приложения? Как мне поставлять в Yandex Monitoring метрики сторонних приложений? Ответы на эти и другие вопросы в данной статье."
---

# Общие вопросы про {{ monitoring-name }}

{% include [qa-logs.md](../../_includes/qa-logs.md) %}

#### Как посмотреть сервисные дашборды? {#dont-see-dashboards}

Сервисные дашборды создаются автоматически после создания ресурсов в {{ yandex-cloud }}. Добавьте необходимый ресурс и обновите [главную страницу](https://monitoring.cloud.yandex.ru) сервиса {{ monitoring-name }}.

#### Почему пропали старые данные графиков в {{ monitoring-name }}? {#lost-data-graphs}

Метрики, для которых не поступали новые значения в течение 30 дней, автоматически удаляются из {{ monitoring-name }}. Подробнее в разделе [{#T}](../concepts/ttl.md).

Существует также ненастраиваемый [механизм прореживания](../concepts/decimation.md) данных, сокращающий их объем в хранилищах.