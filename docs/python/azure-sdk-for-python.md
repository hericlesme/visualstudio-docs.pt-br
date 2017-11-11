---
title: SDK do Azure para Python | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d30fddae-8e2f-4f50-90d3-8ed2cd35c7a6
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: c00adbbabf0d3b82acb17f4a269dfc693246bc69
ms.openlocfilehash: 89de0d11791dbf13b9d4fcfcea8168b443d2777b
ms.contentlocale: pt-br
ms.lasthandoff: 08/01/2017

---

# <a name="azure-sdk-for-python"></a>SDK do Azure para Python

O SDK do Azure para Python facilita o consumo e gerenciamento de serviços do Microsoft Azure em aplicativos executados no Windows, Mac OSX e Linux.

## <a name="installation"></a>Instalação

O SDK do Azure está instalado no [Índice de Pacote Python](https://pypi.python.org/pypi/azure).

Instale a **última versão estável** (dá suporte ao Python 2.7 e 3.3+) da seguinte maneira:

```bash
pip install azure
```

Também é possível seguir [Instalar o Python e o SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/) na documentação do Azure.

## <a name="documentation"></a>Documentação

A documentação pode ser encontrada em [azure-sdk-for-python.readthedocs.org](http://azure-sdk-for-python.readthedocs.org/en/latest/index.html).

O [SDK do Azure para a Central de desenvolvedores do Python](http://azure.microsoft.com/develop/python/) também conta com diversos recursos úteis, incluindo vários tutoriais, como:

  - Criando aplicativos Web com o [Django](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-django-app), [Flask](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-flask-app) e [Bottle](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-bottle-app).
  - [Armazenamento de Blobs](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-blob-storage)
  - [Armazenamento de tabelas](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-table-storage)
  - [Armazenamento de filas](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-queue-storage)
  - [DocumentDB](https://docs.microsoft.com/azure/documentdb/documentdb-python-application)
  - [Filas do Barramento de Serviço](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
  - [Tópicos/assinaturas do Barramento de Serviço](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
  - [Gerenciamento de serviços](https://docs.microsoft.com/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Para as APIs públicas sem a documentação, os testes de unidade no [repositório GitHub do SDK](https://github.com/Azure/azure-sdk-for-python) são uma boa fonte de informações:

- [Testes de unidade de Armazenamento](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Testes de unidade do Barramento de Serviço](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Testes de unidade de Gerenciamento de Serviços](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [Testes de unidade de Gerenciamento de Recursos](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>Suporte

O repositório Git do SDK está localizado em [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

[Registre problemas no repositório](https://github.com/Azure/azure-sdk-for-python/issues) se encontrar problemas ou tiver dúvidas relacionadas ao uso do SDK.
