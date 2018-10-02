---
title: 'Como: especificar arquivos de Log detalhados para implantações do ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: b30260267fca5b7de16316e84082fc3b464f7deb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47465017"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Como especificar arquivos de log detalhados para implantações do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: especificar arquivos de Log detalhado para implantações do ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-verbose-log-files-for-clickonce-deployments).  
  
[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] mantém os arquivos de log de atividades para todas as implantações. Esses logs documentar detalhes referentes à instalação, inicializando, atualizando e desinstalando uma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação. Para aumentar o detalhe que [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] gravações para esses arquivos de log, use o Editor do registro (**regedit.exe**) para especificar o nível de detalhamento.  
  
> [!CAUTION]
>  Se você usar o Editor do Registro incorretamente, poderá causar sérios problemas que talvez exijam a reinstalação do sistema operacional. Use o Editor do registro por seu próprio risco.  
  
 O procedimento a seguir descreve como especificar o nível de detalhamento para [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] arquivos de log para o usuário atual. Para reduzir o nível de detalhamento, remova esse valor do registro.  
  
### <a name="to-specify-verbose-log-files"></a>Para especificar os arquivos de log detalhados  
  
1.  Abra **Regedit.exe**.  
  
2.  Navegue até o nó `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Se necessário, crie um novo valor de cadeia de caracteres chamado `LogVerbosityLevel`.  
  
4.  Defina as `LogVerbosityLevel` valor `1`.  
  
## <a name="see-also"></a>Consulte também  
 [Solução de problemas de implantações ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)



