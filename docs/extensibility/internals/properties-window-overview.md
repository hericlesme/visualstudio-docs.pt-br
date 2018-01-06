---
title: "Visão geral da janela Propriedades | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1f766fe903df4f7a7ea36fb4ec1654b889457f65
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="properties-window-overview"></a>Visão geral da janela Propriedades
O **propriedades** janela é usada para exibir as propriedades de objetos selecionados os dois tipos principais do windows disponíveis no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE). Esses dois tipos de janelas são:  
  
-   Janelas de ferramenta como Gerenciador de soluções, o modo de exibição de classe e o objeto de navegador  
  
-   Janelas de documentos que contém esses editores e designers como o designer de formulários, o editor de XML e o editor de HTML  
  
## <a name="using-the-properties-window"></a>Usando a janela Propriedades  
 O **propriedades** janela exibe as propriedades de um ou vários itens selecionados. Se forem selecionados vários itens, a interseção de todas as propriedades de todos os objetos selecionados será exibida.  
  
 Eventos relacionados a um objeto selecionado dentro de uma janela de design do formulário ou o editor de HTML usando metadados de COM+ são exibidos no **propriedades** janela. Por exemplo, você pode selecionar um botão e exibir seus eventos associados, como um `OnClick` evento, que pode ser vinculado a esse botão.  
  
 Os eventos exibidos no **propriedades** janela são usadas principalmente com objetos que estão vinculados ao código. Se você estiver editando um formato de arquivo que não tem nenhuma relação com o código, você não vai ter todos os eventos. Eventos só são exibidos no **propriedades** janela quando há uma associação entre executar código e certos eventos associados a objetos específicos. Um exemplo disso seria o código por trás de um objeto selecionado que é executado quando esse objeto é ativado.  
  
 A tabela a seguir lista as interfaces principais usadas pelo **propriedades** janela.  
  
|Nome da interface|Descrição|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fornece uma lista de categorias para o **propriedades** janela e mapeia cada propriedade para uma categoria.|  
|[Interface IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)|Expõe métodos e propriedades para ferramentas e outros aplicativos que oferecem suporte a automação de programação de um objeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Fornece os botões de reticências (...) chamados *construtores* que abrir janelas de caixa de diálogo modal implementadas pelo objeto em si. Usado quando um valor não é facilmente digitado pelo usuário em um campo de texto. Por exemplo, ele pode ser usado para abrir um seletor de cores que determina o valor RGB para você.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Fornece acesso a objetos usados para atualizar as informações exibidas no **propriedades** janela. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>é implementado por VSPackages para cada janela que contém objetos selecionáveis com propriedades relacionadas a ser exibido.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fornece informações sobre o tipo de um objeto como métodos de uma interface e campos de uma estrutura.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Habilita a VSPackages para receber notificações de eventos de seleção e recuperar informações sobre a hierarquia de projeto atual, item, o valor do elemento e o contexto do comando da interface do usuário.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fornece o ambiente com acesso a várias seleções.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Usado para fornecer nomes localizados em algumas propriedades exibidas no **propriedades** janela.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifica VSPackages registrados de alterações para a seleção atual, o valor do elemento ou contexto de interface do usuário do comando.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica o ambiente de uma alteração na seleção atual e fornece acesso às informações de hierarquia e o item relacionado à nova seleção.|  
  
 Para obter mais informações sobre `IDispatch`, consulte a biblioteca MSDN.  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo propriedades](../../extensibility/internals/extending-properties.md)   
 [Interfaces e campos da janela Propriedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)