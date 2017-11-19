---
title: "Configuração de projeto para gerenciar a implantação | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87098c362e5b37690e2ab3116ffca431d58f129d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="project-configuration-for-managing-deployment"></a>Configuração de projeto para gerenciar a implantação
Implantação é o ato de mover fisicamente os itens de saída de um processo de compilação para o local esperado para a instalação e a depuração. Por exemplo, um aplicativo Web pode criado em um computador local e colocado no servidor.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dá suporte a duas maneiras de projetos pode estar envolvida na implantação:  
  
-   Como o assunto do processo de implantação.  
  
-   Como o Gerenciador do processo de implantação.  
  
 Antes de soluções podem ser implantadas, primeiro adicione um projeto de implantação para configurar as opções de implantação. Se o projeto de implantação ainda não existir, será perguntado se deseja criá-lo quando você selecionar **implantar solução** do **criar** menu ou botão direito do mouse a solução. Clicando em **Sim** abre o **adicionar novo projeto** caixa de diálogo com o **Assistente de implantação remota** projeto selecionado.  
  
 O Assistente de implantação remota solicita o tipo de aplicativo (Windows ou Web), os grupos de saída do projeto para incluir, quaisquer arquivos adicionais que você deseja incluir e o computador remoto que você deseja implantar. A última página do assistente exibe um resumo das opções selecionadas.  
  
 Os projetos que são o assunto de um processo de implantação produzem itens de saída devem ser movidos para um ambiente alternativo. Esses saída itens descritos como parâmetros para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interface, cujo principal objetivo se permitir que os projetos para o grupo de saídas. Para obter mais informações relacionadas à implementação de `IVsProjectCfg2`, consulte [configuração do projeto para a saída](../../extensibility/internals/project-configuration-for-output.md).  
  
 Projetos de implantação, que gerencia o processo de implantação, habilite o comando implantar e respondem quando esse comando é selecionado. Projetos de implantação implementam o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interface para realizar a implantação e fazer chamadas para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> interface para o relatório implantar eventos de status.  
  
 As configurações podem especificar as dependências que afetam as suas operações de compilação ou implantação. Compilar ou implantar as dependências são projetos que devem ser compilados ou implantados antes ou depois que as configurações se são criadas ou implantadas. Dependências de compilação entre os projetos são descritas com o <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> interface e implantar as dependências com o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interface. Para obter mais informações, consulte [configuração do projeto para criar](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciar opções de configuração](../../extensibility/internals/managing-configuration-options.md)   
 [Configuração de projeto para criação](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuração do projeto para saída](../../extensibility/internals/project-configuration-for-output.md)