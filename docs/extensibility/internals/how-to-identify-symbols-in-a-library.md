---
title: "Como: identificar os símbolos em uma biblioteca | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 60365f3722ae4e2c1f8b52dacc3df03840fb3304
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-identify-symbols-in-a-library"></a>Como: identificar os símbolos em uma biblioteca
Ferramentas de navegação de símbolo exibem modos de exibição hierárquicos de símbolos. Os símbolos representam namespaces, objetos, classes, membros de classe e outros elementos de linguagem.  
  
 Cada símbolo na hierarquia pode ser identificado pelas informações de navegação passadas pela biblioteca de símbolo para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gerenciador de objeto através das seguintes interfaces:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 O local do símbolo na hierarquia distingue um símbolo. Ele permite que as ferramentas de navegação de símbolo navegar até um símbolo específico. O caminho exclusivo, totalmente qualificado para o símbolo determina o local. Cada elemento no caminho é um nó. O caminho começa com o nó de nível superior e termina com o símbolo específico. Por exemplo, se o método M1 é um membro da classe C1 e C1 está no namespace N1, o caminho completo do método M1 é N1. C1. M1. Esse caminho contém três nós: N1, C1 e M1.  
  
 As informações de navegação permite que o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gerenciador de objeto para localizar, selecionar e manter selecionado os símbolos na hierarquia. Ele permite navegar de uma ferramenta de navegação para outro. Ao usar **Pesquisador de objetos** para procurar símbolos em um [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projeto, pode ser um método de clique com botão direito e iniciar o **Pesquisador de chamadas** ferramenta para exibir o método em um gráfico de chamada.  
  
 Duas formas descrevem a localização do símbolo. A forma canônica baseia-se o caminho totalmente qualificado do símbolo. Representa uma posição exclusiva do símbolo na hierarquia. Ele é independente da ferramenta de pesquisa de símbolo. Para obter as informações de forma canônica, o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chamadas de Gerenciador de objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> método. O formato de apresentação descreve o local do símbolo em uma ferramenta de pesquisa de símbolo específico. É a posição do símbolo em relação à posição de outros símbolos no hierarchicy. Um determinado símbolo pode ter vários caminhos de apresentação, mas apenas um caminho canônico. Por exemplo, se C1 classe é herdada da classe C2 e ambas as classes no namespace N1, a **Pesquisador de objetos** exibe a árvore hierárquica do seguinte:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 O caminho canônico de classe de C2, neste exemplo, é N1 + C2. O caminho de apresentação de C2 inclui nós C1 e "Bases e Interfaces": N1 + C1 + "Bases e Interfaces" + C2.  
  
 Para obter as informações de formato de apresentação, as chamadas do Gerenciador de objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> método.  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Identifica um símbolo na hierarquia  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Para obter canônico e apresentação de informações de formulários  
  
1.  Implementar o método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> .  
  
     O Gerenciador de objetos chama esse método para obter a lista de nós contidos no caminho canônico do símbolo.  
  
    ```vb  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```csharp  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  Implementar o método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> .  
  
     O Gerenciador de objetos chama esse método para obter a lista de nós contidos no caminho de apresentação do símbolo.  
  
## <a name="see-also"></a>Consulte também  
 [Suporte a ferramentas de navegação de símbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Como: registrar uma biblioteca com o Gerenciador de objeto](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Como expor listas de símbolos fornecidos pela biblioteca ao Gerenciador de Objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)