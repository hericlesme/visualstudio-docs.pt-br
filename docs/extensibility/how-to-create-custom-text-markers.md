---
title: 'Como: criar marcadores de texto personalizado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5c44a507cc291b203fc9ba330b248a854f61b81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132245"
---
# <a name="how-to-create-custom-text-markers"></a>Como: criar marcadores de texto personalizado
Se você quiser criar um marcador de texto personalizado para enfatizar ou organizar o código, você deve executar as etapas a seguir:  
  
-   Registrar o novo marcador de texto, de forma que outras ferramentas podem acessá-lo  
  
-   Fornecer uma implementação padrão e a configuração do marcador de texto  
  
-   Criar um serviço que pode ser usado por outros processos para fazer uso do marcador de texto  
  
 Para obter detalhes sobre como aplicar um marcador de texto para uma região de código, consulte [como: usar marcadores de texto](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Para registrar um marcador personalizado  
  
1.  Crie uma entrada de registro da seguinte maneira:  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versão >* \Text Editor\External marcadores\\*\<MarkerGUID >*  
  
     *\<MarkerGUID >* é um `GUID` usado para identificar o marcador que está sendo adicionado  
  
     *\<Versão >* é a versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], por exemplo 8.0  
  
     *\<PackageGUID >* é o GUID do VSPackage que implementa o objeto de automação.  
  
    > [!NOTE]
    >  O caminho raiz de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versão >* pode ser substituído por uma raiz alternativa quando o shell do Visual Studio é inicializado, para obter mais informações, consulte [De linha de comando](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2.  Criar quatro valores em HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versão >* \Text Editor\External marcadores\\*\<MarkerGUID >*  
  
    -   (Padrão)  
  
    -   Serviço  
  
    -   DisplayName  
  
    -   Pacote  
  
    -   `Default` é uma entrada opcional do tipo REG_SZ. Quando definido, o valor da entrada é uma cadeia de caracteres que contém algumas informações de identifica útil, por exemplo "marcador de texto personalizado".  
  
    -   `Service` é uma entrada do tipo REG_SZ que contém a cadeia de caracteres do GUID do serviço que fornece o marcador de texto personalizado por proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. O formato é {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
    -   `DisplayName` é uma entrada do tipo REG_SZ que contém a ID de recurso do nome do marcador de texto personalizado. O formato é #YYYY.  
  
    -   `Package` entrada de tipo REG_SZ contendo o `GUID` de VSPackage que fornece o serviço listado sob o serviço. O formato é {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Para criar um marcador de texto personalizado  
  
1.  Implementar a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     A implementação desta interface define o comportamento e a aparência do seu tipo de marcador personalizado.  
  
     Essa interface é chamada quando  
  
    1.  Um usuário inicia o IDE pela primeira vez.  
  
    2.  Um usuário seleciona o **Redefinir padrões** botão sob o **fontes e cores** página de propriedades no **ambiente** pasta, localizada no painel esquerdo do  **Opções de** caixa de diálogo obtido o **ferramentas** menu do IDE.  
  
2.  Implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> método, especificando que `IVsPackageDefinedTextMarkerType` implementação deve ser retornada com base no tipo de marcador GUID especificado na chamada do método.  
  
     O ambiente chama o método primeiro momento o tipo de marcador personalizado é criado e especifica um GUID que identifica o tipo de marcador personalizado.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Para proffer o tipo de marcador, como um serviço  
  
1.  Chamar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> método para <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> é retornado.  
  
2.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> método, especifica o GUID que identifica o serviço do tipo de marcador personalizado e fornecendo um ponteiro para a implementação do <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface. O <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implementação deve retornar um ponteiro para a implementação do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> interface.  
  
     Um cookie exclusivo que identifica que o serviço será retornado. Mais tarde você pode usar esse cookie revogue o seu serviço de tipo de marcador personalizado chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> método o <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface especificando o valor do cookie.  
  
## <a name="see-also"></a>Consulte também  
 [Usar marcadores de texto com a API herdado](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Como: adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md)   
 [Como: implementar marcadores de erro](../extensibility/how-to-implement-error-markers.md)   
 [Como: usar marcadores de texto](../extensibility/how-to-use-text-markers.md)