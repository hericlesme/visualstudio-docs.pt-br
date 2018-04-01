---
title: Arquitetura de VSPackage de controle de origem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 25
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 002dea54b63a78975d56464319614d369a9b2318
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-vspackage-architecture"></a>Arquitetura de VSPackage de controle do código-fonte
Um pacote de controle de origem é um VSPackage que usa os serviços que o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE fornece. Em troca, um pacote de controle de origem fornece sua funcionalidade como um serviço de controle de origem. Além disso, um pacote de controle de origem é uma alternativa mais versátil que o plug-in para integrar o controle de origem em um controle de origem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Um plug-in para que implementa a API de plug-in de controle de origem de controle de origem age de acordo com um contrato estrito. Por exemplo, um plug-in não é possível substituir o padrão [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface do usuário (IU). Além disso, a API de plug-in de controle de origem não permite um plug-in implementar seu próprio modelo de controle de origem. No entanto, um pacote de controle de origem, supera essas limitações. Um pacote de controle de origem tem controle total sobre a experiência de controle de origem de um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usuário. Além disso, um pacote de controle de origem pode usar seu próprio modelo de controle de origem e lógica, e ele pode definir todas as interfaces de usuário relacionada ao controle de origem.  
  
## <a name="source-control-package-components"></a>Componentes de controle de origem do pacote  
 Conforme mostrado no diagrama da arquitetura, um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componente denominado o Stub de controle de origem é um VSPackage que integra um pacote de controle de origem com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Stub de controle de origem trata as seguintes tarefas.  
  
-   Fornece a interface do usuário comum que é necessário para registro de controle de origem do pacote.  
  
-   Carrega um pacote de controle de origem.  
  
-   Define um pacote de controle de origem como ativa/inativa.  
  
 Stub de controle do código-fonte procura o serviço ativo para o pacote de controle de origem e roteia entrada todas as chamadas de serviço do IDE para que o pacote.  
  
 O pacote de adaptador de controle de origem é um controle de fonte especial de pacote que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornece. Este pacote é o componente central para dar suporte a controle de origem plug-ins com base na API de plug-in de controle de origem. Quando um plug-in de controle de origem é o plug-in do ativo, o Stub de controle de origem envia seus eventos para o pacote de adaptador de controle de origem. Por sua vez, o pacote de adaptador de controle de origem se comunica com o plug-in de controle de origem usando a API de plug-in de controle de origem e também fornece uma interface do usuário que é comum para controle de origem todos os plug-ins padrão.  
  
 Quando um pacote de controle de origem é o pacote do ativo, por outro lado, o Stub de controle de origem se comunica diretamente com o pacote usando o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfaces de controle de origem de pacote. O pacote de controle de origem é responsável por hospedar seu próprio controle de origem da interface do usuário.  
  
 ![Gráfico de arquitetura de controle de origem](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 Para um pacote de controle de origem, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] não fornecer o código de controle de origem ou uma API para integração. Compare isso com a abordagem descrita [criar um plug-in de controle de origem](../../extensibility/internals/creating-a-source-control-plug-in.md) em que o plug-in de controle de origem precisa implementar um conjunto rígido de funções e retornos de chamada.  
  
 Como qualquer VSPackage, um pacote de controle de origem é um objeto COM que pode ser criado usando `CoCreateInstance`. O VSPackage se torna disponível para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE com a implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Quando uma instância tiver sido criada, um VSPackage recebe um ponteiro de site e um <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface que fornece o VSPackage acessem os serviços disponíveis e interfaces no IDE.  
  
 Gravar um pacote de controle de origem com base em VSPackage exige experiência de programação mais avançada que escrever uma API de plug-in de controle de origem com base em plug-in.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Introdução](../../extensibility/internals/getting-started-with-source-control-vspackages.md)