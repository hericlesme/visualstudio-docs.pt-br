---
title: Registrando uma janela de ferramentas | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79a2d2f1e9dc130fc280ce61ec282f30e55024ae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="registering-a-tool-window"></a>Registrando uma janela de ferramenta
Você pode registrar as janelas de ferramenta usando <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> e<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## <a name="example"></a>Exemplo  
  
```csharp  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 No código acima, o <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registra as janelas de ferramentas PersistedWindowPane e DynamicWindowPane com o Visual Studio. A janela da ferramenta persistente é encaixada e com guias com **Solution Explorer**, e a janela dinâmica recebe um inicial posição e o tamanho padrão. A janela dinâmica é feita transitória, que indica que ele não será criado na inicialização. Grava um valor de DontForceCreate na chave ToolWindows no registro do sistema. Para obter mais informações, consulte [configuração de exibição da janela de ferramenta](../extensibility/tool-window-display-configuration.md).