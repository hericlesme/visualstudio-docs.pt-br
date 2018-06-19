---
title: SDK do Azure para Python
description: O SDK do Azure para Python facilita o consumo de serviços do Microsoft Azure em aplicativos Python executados em qualquer plataforma.
ms.date: 01/22/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 58e7f6cd46293573f17c344ffba943d99b55f830
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031466"
---
# <a name="azure-sdk-for-python"></a>SDK do Azure para Python

O SDK do Azure para Python facilita o consumo e gerenciamento de serviços do Microsoft Azure em aplicativos executados no Windows, Mac OSX e Linux.

## <a name="installation"></a>Instalação

O SDK do Azure está instalado no [Índice de Pacote Python](https://pypi.python.org/pypi/azure).

Instale a **última versão estável** (dá suporte ao Python 2.7 e 3.x) da seguinte maneira:

```command
pip install azure
```

Também é possível seguir [Instalar o Python e o SDK](https://docs.microsoft.com/azure/python-how-to-install/) na documentação do Azure.

## <a name="documentation"></a>Documentação

A documentação pode ser encontrada em [azure-sdk-for-python.readthedocs.org](https://docs.microsoft.com/en-us/python/azure/?view=azure-python).

O [SDK do Azure para a Central de desenvolvedores do Python](http://azure.microsoft.com/develop/python/) também conta com diversos recursos úteis, incluindo vários tutoriais:

- Criando aplicativos Web com o [Django](/azure/app-service-web/web-sites-python-create-deploy-django-app), [Flask](/azure/app-service-web/web-sites-python-create-deploy-flask-app) e [Bottle](/azure/app-service-web/web-sites-python-create-deploy-bottle-app).
- [Armazenamento de Blobs](/azure/storage/storage-python-how-to-use-blob-storage)
- [Armazenamento de tabelas](/azure/storage/storage-python-how-to-use-table-storage)
- [Armazenamento de filas](/azure/storage/storage-python-how-to-use-queue-storage)
- [Azure Cosmos DB](/azure/cosmos-db/sql-api-python-application)
- [Filas do Barramento de Serviço](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Tópicos/assinaturas do Barramento de Serviço](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Gerenciamento de serviços](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Para as APIs públicas sem documentação, os testes de unidade no [repositório GitHub do SDK](https://github.com/Azure/azure-sdk-for-python) são uma boa fonte de informações:

- [Testes de unidade de Armazenamento](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Testes de unidade do Barramento de Serviço](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Testes de unidade de Gerenciamento de Serviços](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [Testes de unidade de Gerenciamento de Recursos](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>Suporte

O repositório Git do SDK está localizado em [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

[Registre problemas no repositório](https://github.com/Azure/azure-sdk-for-python/issues) se encontrar problemas ou tiver dúvidas relacionadas ao uso do SDK.
