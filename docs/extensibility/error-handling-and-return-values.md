---
title: Tratamento de erros e valores de retorno | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cfbeef2de041cfd71fbf163d7860d903a6cb59e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="error-handling-and-return-values"></a>Tratamento de erros e valores de retorno
VSPackages e COM usam a mesma arquitetura de erros. O `SetErrorInfo` e `GetErrorInfo` funções fazem parte da interface de programação de aplicativo (API) do Win32. Qualquer VSPackage no ambiente de desenvolvimento integrado (IDE) pode chamar essas APIs do Win32 global para registrar informações de erros completa ao receber uma notificação de erro. O [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornece assemblies de interoperabilidade para gerenciar informações de erro.  
  
## <a name="interop-methods"></a>Métodos de interoperabilidade  
 Como uma conveniência, o IDE oferece um método, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, para usar em vez de chamar as APIs do Win32. Em código gerenciado uso <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. Quando um erro `HRESULT` chega no nível de onde a mensagem de erro deve ser exibida (geralmente, esse é o objeto implementando um <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> manipulador de comando), o IDE usa outro método, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, para exibir a caixa de mensagem apropriado. Em uso de código gerenciado a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método.  
  
 Como um implementador VSPackage, os objetos COM normalmente implementam `ISupportErrorInfo`. O `ISupportErrorInfo` interface garante que as informações de erros podem mover verticalmente a cadeia de chamada. Devem oferecer suporte a objetos que podem ser usados em processos ou threads `ISupportErrorInfo` para garantir que as informações de erros completa corretamente realizar marshaling de volta para o chamador.  
  
 Todos os objetos que estão relacionados a VSPackages e que são envolvidos em estender o IDE, incluindo as fábricas de editor, editores, hierarquias, oferecidos serviços, devem oferecer suporte para as informações de erros. Embora o IDE não exija que esses objetos VSPackage implementar `ISupportErrorInfo`, ele sempre é incentivado.  
  
 O IDE é responsável por relatar informações de erro e exibi-los para um usuário do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sempre que um `HRESULT` é propagada para o IDE. O IDE também é o mecanismo para a criação de `ErrorInfo` objetos.  
  
## <a name="general-guidelines"></a>Diretrizes gerais  
 Você pode usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> métodos para definir e relatar os erros que são internos a implementação do VSPackage. No entanto, como regra geral, siga estas diretrizes para lidar com mensagens de erro no seu VSPackage:  
  
-   Implementar `ISupportErrorInfo` no seu VSPackage objetos.  
  
-   Criar um erro relatando o mecanismo que chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método em objetos que implementam <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
-   Permitir que o IDE exibir erros aos usuários por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método.  
  
## <a name="error-information-in-the-ide"></a>Informações de erro no IDE  
 As regras a seguir indicam como lidar com informações de erro no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:  
  
-   Como uma estratégia de defesa para garantir que informações de erro obsoletos não é relatada para os usuários, funções que chamam o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método primeiro deve chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método. Passar `null` para limpar as mensagens de erro em cache antes de chamar qualquer coisa que pode definir novas informações de erro.  
  
-   Funções que não relatam diretamente as mensagens de erro são permitidas apenas para chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método se eles estão retornando um erro `HRESULT`. É permitido para limpar o `ErrorInfo` na entrada para uma função ou ao retornar <xref:Microsoft.VisualStudio.VSConstants.S_OK>. A única exceção a essa regra é quando uma chamada retornará um erro `HRESULT` do que o destinatário pode recuperar explicitamente ou ignorar com segurança.  
  
-   Todas as pessoas que explicitamente ignora o erro `HRESULT` deve chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método com <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Caso contrário, o `ErrorInfo` objeto pode ser acidentalmente usado quando outro participante gera um erro sem fornecer suas próprias `ErrorInfo`.  
  
-   Todos os métodos que se originam erro `HRESULT` são incentivados a chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método para fornecer as informações de erros. Se retornado `HRESULT` é especial `FACILITY_ITF` erro e, em seguida, o método é necessário para fornecer apropriadas `ErrorInfo`objeto. Se o erro retornado é um erro de sistema padrão (por exemplo, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>e assim por diante) é aceitável para retornar o código de erro sem chamar explicitamente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método. Como uma defesa estratégia de codificação, quando um erro de origem `HRESULT` (incluindo erros de sistema), sempre chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método, seja com `ErrorInfo` descrevendo a falha em maiores detalhes, ou `null`.  
  
-   Todas as funções que retornam um erro foi originado por outra chamada deve passar as informações que foram recebidos de falha do chamam no `HRESULT` sem modificar o `ErrorInfo` objeto.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (automação de componente)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [Interface ISupportErrorInfo](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)