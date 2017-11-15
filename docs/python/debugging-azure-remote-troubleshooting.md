---
title: "Solução de problemas de depuração remota do Azure para Python no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b723b343-dffb-457e-9af7-ee48c1451e30
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 5f8c27eb0c1360e2bd0fcf0593a8438383b6fd69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Solução de problemas da depuração remota para o Python e o Azure

O Visual Studio não consegue se anexar a um [Serviço de Aplicativo do Azure para depuração remota](debugging-azure-remote.md) por um dos seguintes motivos:

| Motivo | Resolução |
| --- | --- |
| Você não tem o Visual Studio 2013 Atualização 4 ou posterior instalado. | Instale uma versão adequada de [visualstudio.com](https://www.visualstudio.com/downloads/). | 
| O projeto implantado no Serviço de Aplicativo não corresponde ao que está aberto no Visual Studio. | Carregue o projeto correto no Visual Studio. |
| O projeto não foi implantado com a configuração Depuração. | Reimplante o aplicativo clicando com o botão direito do mouse no projeto, no Gerenciador de Soluções e selecionando **Publicar**. Na guia **Configurações**, verifique se **Depuração** é a configuração selecionada. |
| O Serviço de Aplicativo não está em execução. | Inicie-o no Gerenciador de Servidores do Visual Studio ou no portal do Azure. |
| O Serviço de Aplicativo não está configurado para soquetes da Web. | Acesse o [portal do Azure](https://portal.azure.com), navegue até o Serviço de Aplicativo, abra a folha **Configurações > Configurações de aplicativo**, defina **Configurações gerais > Soquetes da Web** como **Ativado** e selecione **Salvar**. (Observe que as opções **Depuração** mostradas nessa folha *não* se aplicam à depuração do Python.) |
| `web.debug.config` foi modificado para desabilitar o proxy de depuração. | Exclua o arquivo e republique o projeto no Serviço de Aplicativo; durante esse tempo, o Visual Studio recriará o arquivo. |

Confira também: 

- [Depuração remota do Azure para o Python](debugging-azure-remote.md)
