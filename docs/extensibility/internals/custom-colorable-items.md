---
title: Itens personalizados de pode ser coloridos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b23ff39abcb9a1354ea28becab3b7df867378ddf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133359"
---
# <a name="custom-colorable-items"></a>Itens pode ser coloridos personalizados
Você pode substituir a lista de tipos para colorir, como palavras-chave e comentários, Implementando itens pode ser coloridos personalizados como parte de seu serviço de linguagem.  
  
## <a name="user-settings-of-colorable-items"></a>Configurações de usuário de itens pode ser coloridos  
 Você pode exibir o **fontes e cores** caixa de diálogo selecionando **opções** no **ferramentas** menu e selecionando **fontes e cores** em **ambiente**. Quando você seleciona uma exibição, como **Editor de texto** ou **janela comando**, o **exibir itens** caixa de listagem exibe todos os itens pode ser coloridos para essa exibição. Você pode exibir e alterar a fonte, tamanho, cor de primeiro plano e cor de plano de fundo para cada item pode ser colorido. As opções são armazenadas em cache no registro e acessadas pelo nome do item pode ser colorido.  
  
## <a name="presentation-of-colorable-items"></a>Apresentação de itens pode ser coloridos  
 Porque o IDE manipula substituições de usuário de itens pode ser coloridos o **fontes e cores** caixa de diálogo, é necessário apenas fornecer cada item pode ser colorido personalizado com um nome. Esse nome é o que aparece no **exibir itens** lista. Os itens pode ser coloridos aparecem em ordem alfabética. Para agrupar itens personalizados de pode ser colorido do seu serviço de idioma, você pode começar cada nome com o nome do idioma, por exemplo **NewLanguage - comentário** e **NewLanguage - palavra-chave**.  
  
> [!CAUTION]
>  Você deve incluir o nome do idioma no nome do item pode ser colorido para evitar colisões com nomes de item pode ser colorido existentes. Se você alterar o nome de um de seus itens pode ser coloridos durante o desenvolvimento, você deve redefinir o cache que foi criado na primeira vez em que foram acessados seus itens pode ser coloridos. Você pode redefinir o cache experimental com a ferramenta CreateExpInstance, que é instalado com o SDK do Visual Studio, normalmente no diretório  
>   
>  **C:\Program arquivos (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  Para redefinir o cache, chame `CreateExpInstance /Reset`. Para obter mais informações sobre CreateExpInstance, consulte [CreateExpInstance Utility](../../extensibility/internals/createexpinstance-utility.md).  
  
 O primeiro item na lista de itens pode ser coloridos nunca é referenciado. O primeiro item corresponde a um item pode ser colorido índice de 0, e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sempre fornece as cores padrão de texto e atributos para aquele item. A maneira mais fácil de lidar com esse item não referenciada é fornecer um item pode ser colorido do espaço reservado na sua lista como o primeiro item.  
  
## <a name="implementing-custom-colorable-items"></a>Implementação de itens pode ser coloridos personalizados  
  
1.  Defina o que deve ser colorido em seu idioma, por exemplo, palavra-chave, operador e identificador.  
  
2.  Crie uma enumeração desses itens pode ser colorido.  
  
3.  Associe os tipos de token retornados de um analisador ou scanner com valores enumerados.  
  
     Por exemplo, os valores que representam os tipos de token podem ser os mesmos valores na enumeração de itens pode ser colorido personalizados.  
  
4.  Na implementação do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método no seu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> de objeto, preencher a lista de atributos com os valores de enumeração pode ser colorido de itens personalizados correspondentes aos tipos de token retornados do analisador ou scanner.  
  
5.  Na mesma classe que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface, implemente o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interface e seus dois métodos, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6.  Implementar a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
7.  Se você deseja dar suporte a valores de cor de 24 bits ou alto, implementar também a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interface.  
  
8.  Em seu objeto de serviço de linguagem, crie uma lista que contém seu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> objetos, um para cada item pode ser colorido pode identificar o analisador ou scanner.  
  
     Você pode acessar cada item na lista usando o valor correspondente de enumeração de itens pode ser colorido personalizados. Use os valores de enumeração como um índice na lista. O primeiro item na lista nunca é acessado, pois ele corresponde ao texto padrão de estilo que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sempre trata em si. Você pode compensar isso inserindo um item pode ser colorido do espaço reservado no início da lista.  
  
9. Na implementação do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> método, retornar o número de itens na sua lista de itens pode ser colorido personalizados.  
  
10. Na implementação do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método, retornar o item pode ser colorido solicitado na sua lista.  
  
 Para obter um exemplo de como implementar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaces, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## <a name="see-also"></a>Consulte também  
 [Modelo de um serviço de linguagem herdado](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Cores de sintaxe no editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Cores de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementando a coloração de sintaxe](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Como usar itens de coloração internos](../../extensibility/internals/how-to-use-built-in-colorable-items.md)