---
title: "Fornecer um contexto de serviço de idioma usando a API herdado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79f58bf66e5d0a137738d0a2cc90f67a287246dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Fornecer um contexto de serviço de idioma usando a API herdado
Há duas opções para um serviço de linguagem fornecer o contexto de usuário usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor núcleo: fornecer contexto do marcador de texto ou fornecer todo o contexto de usuário. As diferenças entre cada um deles são descritas aqui.  
  
 Para obter mais informações sobre como fornecer contexto para um serviço de idioma que está conectado ao seu próprio editor, consulte [como: fornecer contexto para editores](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Fornecer o contexto do marcador de texto no Editor  
 Para fornecer contexto para erros de compilador indicados por marcadores de texto no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor de núcleo, implemente o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interface. Nesse cenário, o serviço de linguagem fornece contexto somente quando o cursor estiver em um marcador de texto. Isso permite que o editor fornecer a palavra-chave na posição do cursor para o **ajuda dinâmica** janela sem atributos.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Fornece todo o contexto de usuário para o Editor  
 Se você estiver criando um serviço de linguagem e estiver usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] principal editor, em seguida, você pode implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interface para fornecer contexto para o serviço de linguagem.  
  
 Para a implementação de `IVsLanguageContextProvider`, um recipiente de contexto (coleção) é anexado ao editor, que é responsável por atualizar o recipiente de contexto. Quando o **ajuda dinâmica** janela chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> interface esse recipiente de contexto em tempo ocioso, o recipiente de contexto consultará o editor para uma atualização. O editor notifica o serviço de linguagem que deve atualizar o editor e transmite um ponteiro para o recipiente de contexto. Isso é feito chamando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> método do editor para o serviço de linguagem. Usando o ponteiro para o recipiente de contexto, o serviço de linguagem pode adicionar e remover palavras-chave e atributos. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Há duas maneiras de implementar `IVsLanguageContextProvider`:  
  
-   Fornecer uma palavra-chave para o recipiente de contexto  
  
     Quando o editor é chamado para atualizar o recipiente de contexto, passar as palavras-chave e os atributos e, em seguida, retornar `S_OK`. Esse valor de retorno instrui o editor para manter seu contexto de palavra-chave e atributo em vez de fornecer a palavra-chave na posição do cursor para o recipiente de contexto.  
  
-   Obter a palavra-chave da palavra-chave na posição do cursor  
  
     Quando o editor é chamado para atualizar o recipiente de contexto, passe os atributos apropriados e, em seguida, retornar `E_FAIL`. Esse valor de retorno instrui o editor para manter seus atributos no recipiente de contexto, mas o recipiente de contexto de atualização com a palavra-chave na posição do cursor.  
  
 O diagrama a seguir demonstra como o contexto é fornecido para um serviço de linguagem que implementa `IVsLanguageContextProvider`.  
  
 ![Gráfico de LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
Contexto de um serviço de linguagem  
  
 Como você pode ver no diagrama, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor de texto principal tem um recipiente de contexto anexado a ele. Esse recipiente de contexto aponta para três pacotes de subcontexto separado: serviço de linguagem, o editor padrão e o marcador de texto. Os pacotes language service e texto marcador subcontexto contêm atributos e palavras-chave para o serviço de linguagem, se o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interface é implementada, marcadores de texto e se o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interface é implementada. Se você não implementar qualquer uma dessas interfaces, o editor fornece contexto para a palavra-chave na posição do cursor no recipiente de subcontexto de editor padrão.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Diretrizes de contexto para editores e Designers  
 Designers e editores devem fornecer uma palavra-chave geral do editor ou a janela do designer. Isso é feito para que exiba um tópico da Ajuda genérico, mas apropriado, para o designer ou editor quando o usuário pressionar F1. Um editor deve, além de isso, forneça a palavra-chave atual no cursor ou fornecer um termo-chave com base na seleção atual. Isso é feito para garantir que um tópico da Ajuda para o texto ou um elemento de interface do usuário apontada ou selecionada exibe quando o usuário pressiona F1. Um designer fornece contexto para um item selecionado em um designer, como um botão em um formulário. Editores e designers também devem se conectar a um serviço de idioma conforme descrito na [Essentials de serviço de linguagem herdado](../extensibility/internals/legacy-language-service-essentials.md).