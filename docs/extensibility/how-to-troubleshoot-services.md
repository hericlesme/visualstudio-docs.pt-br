---
title: "Como: solucionar problemas de serviços | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 71ac3cda8e3df935ab743fed7aa94a5152c152a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-troubleshoot-services"></a>Como: solucionar problemas de serviços
Há vários problemas comuns que podem ocorrer ao tentar obter um serviço:  
  
-   O serviço não está registrado com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   O serviço é solicitado pelo tipo de interface e não por tipo de serviço.  
  
-   O VSPackage solicitando o serviço não tem foi localizado.  
  
-   O provedor de serviço errada é usado.  
  
 Se o serviço solicitado não pode ser obtida, a chamada para <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> retorna nulo. Você sempre deve testar null depois de solicitar um serviço:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>Para solucionar problemas de um serviço  
  
1.  Examine o registro do sistema para ver se o serviço foi registrado corretamente. Para obter mais informações, consulte [como: fornece um serviço](../extensibility/how-to-provide-a-service.md).  
  
     O fragmento de arquivo. reg a seguir mostra como o serviço de SVsTextManager pode ser registrado:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     No exemplo acima, o número de versão é a versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], como 12.0 ou 14.0, a chave {F5E7E71D-1401-11d1-883B-0000F87579D2} é o identificador de serviço (SID) do serviço, SVsTextManager e o {de valor padrão F5E7E720-1401-11D1-883B-0000F87579D2} é o GUID do Gerenciador de texto VSPackage, que fornece o serviço do pacote.  
  
2.  Use o tipo de serviço e não do tipo de interface quando você chamar GetService. Ao solicitar um serviço de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> extrai o GUID do tipo. Um serviço não será encontrado se existem as seguintes condições:  
  
    1.  Um tipo de interface é passado para GetService em vez do tipo de serviço.  
  
    2.  Nenhum GUID seja atribuída explicitamente à interface. Portanto, o sistema cria um GUID de padrão de um objeto conforme necessário.  
  
3.  Certifique-se de que o VSPackage solicitando o serviço foi localizado. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]sites um VSPackage depois de construir a ele e antes de chamar <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Se você tiver código em um construtor VSPackage que precisa de um serviço, mova-o para o método Initialize.  
  
4.  Certifique-se de que você está usando o provedor de serviço correta.  
  
     Nem todos os provedores de serviço são iguais. O provedor de serviços que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passa uma janela de ferramenta é diferente daquele que ele passa para um VSPackage. O provedor de serviços de janela de ferramenta conhece <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, mas não sabe sobre <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Você pode chamar <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para obter um provedor de serviço VSPackage de dentro de uma janela de ferramenta.  
  
     Se uma janela de ferramentas hospeda um controle de usuário ou qualquer outro contêiner de controle, o contêiner será colocado no local pelo modelo de componente do Windows e não terá acesso a qualquer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] serviços. Você pode chamar <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> para obter um provedor de serviço VSPackage de dentro de um contêiner de controle.  
  
## <a name="see-also"></a>Consulte também  
 [Lista de serviços disponíveis](../extensibility/internals/list-of-available-services.md)   
 [Usando e fornecer serviços](../extensibility/using-and-providing-services.md)   
 [Fundamentos do serviço](../extensibility/internals/service-essentials.md)