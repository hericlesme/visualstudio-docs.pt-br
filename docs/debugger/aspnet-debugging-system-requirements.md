---
title: "Depuração de ASP.NET: Requisitos do sistema | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: 9cf9517775b5729507252a259485ad8d6cc276ff
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2018
---
# <a name="aspnet-debugging-system-requirements"></a>Depuração do ASP.NET: requisitos do sistema
Este tópico descreve os requisitos de software e segurança para [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] cenários de depuração:  
  
-   Depuração local, na qual o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e o aplicativo Web são executados no mesmo computador. Há duas versões do controle desse cenário:  
  
    -   O código do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] reside no sistema de arquivos.  
  
    -   O código do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] reside em um site do IIS.  
  
-   Depuração remota, na qual o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é executado em um computador cliente e depura um aplicativo Web que esteja em execução em um computador de servidor remoto.  
  
## <a name="security-requirements"></a>Requisitos de segurança  
 Para a depuração remota, os computadores locais e remotos devem estar em uma configuração de domínio ou em uma configuração de grupo de trabalho.  
  
 Para depurar o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o processo de trabalho (hospedado por um Pool de aplicativos), você deve ter permissão para depurar esse processo. Por padrão, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativos IIS 6.0 antes de executar como a **ASPNET** usuário. No IIS 6.0 e IIS 7.0, o **serviço de rede** conta é o padrão. Se o processo de trabalho está em execução como **ASPNET**, ou como **serviço de rede**, você deve ter privilégios de administrador para depurá-lo.

 > [!IMPORTANT]
 > A partir do Windows Server 2008 R2, é recomendável o uso do [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) como a identidade de cada pool de aplicativos.
  
 O nome do processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] varia de acordo com o cenário de depuração e a versão do IIS. Para obter mais informações, consulte [como: localizar o nome do processo do ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Você pode alterar o usuário da conta que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o processo de trabalho é executado, editando o arquivo Machine. config no servidor que está executando o IIS. A melhor maneira de fazer isso é usar o **serviços de informações da Internet (IIS) Manager**. Para obter mais informações, consulte [como: executar o trabalho processo em uma conta de usuário](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Se você alterar o processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para ser executado em sua própria conta de usuário, não precisará ser um administrador no servidor que está executando o IIS.  
  
> [!CAUTION]
>  Antes de alterar o processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para ser executado em uma conta diferente, considere as possíveis consequências se o processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] for invadido ao executar sob essa conta. As contas de usuário ASPNET and NETWORK SERVICE são executadas com as permissões mínimas, reduzindo o dano possível se o processo for invadido. Se você precisar alterar o processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para ser executado sob uma conta que tenha permissões maiores, o dano potencialmente será maior.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Como executar o processo de trabalho em uma conta de usuário](../debugger/how-to-run-the-worker-process-under-a-user-account.md)