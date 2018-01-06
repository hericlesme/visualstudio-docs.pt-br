---
redirect_url: shell/distributing-isolated-shell-applications
title: "Distribuição de aplicativos do Shell isolado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 250f1d7769f6035e015eeb7247c439b27f913b78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="distributing-isolated-shell-applications"></a>Distribuição de aplicativos do Shell isolado
Você deve instalar o Visual Studio e o SDK do Visual Studio para criar um aplicativo de shell isolado. Para distribuir o aplicativo para as máquinas de outros usuários ou os clientes, você deve incluir um pacote redistribuível especial para o shell isolado.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Pré-requisitos para a distribuição de aplicativos do Shell isolado  
  
|Nome|Descrição|  
|----------|-----------------|  
|SDK do Visual Studio|O SDK, você deve ter para desenvolver e testar as extensões de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Você também pode usar o SDK para criar sua própria instância do shell do Visual Studio isolado.<br /><br /> O Visual Studio é um pré-requisito para o SDK.|  
|Microsoft Visual Studio Isolated Shell redistribuível|Os pacotes redistribuíveis do que você incluir em seu programa de instalação quando você cria um ambiente de ferramentas do Visual Studio isolada shell. O pacote redistribuível do Shell isolado inclui o .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Criando um programa de instalação para o aplicativo  
 Você deve criar um programa de instalação especiais para seu aplicativo de shell integrado ou isolado. Para obter mais informações, consulte [instalar um aplicativo de Shell isolado](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Permitir que as atualizações para seu aplicativo  
 O programa de instalação deve permitir a possibilidade de que seu aplicativo será atualizado, as atualizações da Microsoft ou atualizações da sua empresa. Para obter mais informações sobre atualizações, consulte [diretrizes de serviço para aplicativos do Shell isolado](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).