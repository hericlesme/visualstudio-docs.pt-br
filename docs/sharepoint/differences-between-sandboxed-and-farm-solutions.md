---
title: "Diferenças entre a área restrita e soluções em Farm | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d82bc012b2be9736b83fc07f7d0a83d354dda002
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Diferenças entre soluções de área restrita e de farm
  Quando você compila uma solução do SharePoint, implanta o servidor do SharePoint e anexa um depurador para depurá-lo. O processo usado para depurar a solução depende da configuração da propriedade solução em área restrita: solução em área restrita ou solução de farm.  
  
 Para obter mais informações, consulte [considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Soluções de farm  
 Soluções de farm, que são hospedadas no processo de trabalho do IIS (W3WP.exe), execute o código que pode afetar o farm inteiro. Quando você depurar um projeto do SharePoint cuja propriedade da solução em área restrita é definida como "solução de farm", o pool de aplicativos do IIS do sistema recicla antes do SharePoint retira ou implanta o recurso para liberar quaisquer arquivos bloqueados pelo processo de trabalho do IIS. Somente o pool de aplicativos do IIS que serve o URL do site do projeto do SharePoint é reciclado.  
  
## <a name="sandboxed-solutions"></a>Soluções em modo seguro  
 Soluções em modo seguro, que são hospedadas no processo de trabalho de solução de código do usuário do SharePoint (SPUCWorkerProcess.exe), execute o código que pode afetam apenas o conjunto de sites da solução. Como soluções de área restrita não executar no processo de trabalho do IIS, o pool de aplicativos do IIS e o servidor do IIS não reinicie. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]anexa o depurador ao processo SPUCWorkerProcess que o serviço SPUserCodeV4 no SharePoint aciona automaticamente e controles. Não é necessário para o processo de SPUCWorkerProcess reciclar para carregar a versão mais recente da solução.  
  
## <a name="either-type-of-solution"></a>O tipo de solução  
 Com qualquer tipo de solução, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] também anexa o depurador para o navegador para habilitar a depuração de script do lado do cliente. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]usa o mecanismo para essa finalidade de depuração de script. Para habilitar a depuração de script, você deve alterar as configurações do navegador quando for solicitado.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]anexa o depurador somente para os processos W3WP ou SPUCWorkerProcess executando o site atual. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]também anexa o gerenciado COM Plus e mecanismos de depuração de fluxo de trabalho.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando soluções do SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Compilando e depurando soluções do SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Considerações de solução em área restrita](../sharepoint/sandboxed-solution-considerations.md)  
  
  