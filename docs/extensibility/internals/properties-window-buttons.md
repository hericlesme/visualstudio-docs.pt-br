---
title: "Botões da janela de propriedades | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4cd83a8d8e72c18f8a6929e8985f7a8635a940d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="properties-window-buttons"></a>Botões da janela de propriedades
Dependendo do idioma de desenvolvimento e o tipo de produto, determinados botões são exibidos por padrão na barra de ferramentas para a **propriedades** janela. Em todos os casos, o **categorizado**, **Alphabetized**, **propriedades**, e **páginas de propriedade** botões são exibidos. Em Visual c# e Visual Basic, o **eventos** botão também é exibido. Em determinados projetos Visual C++, o **VC + + mensagens** e **VC substitui** botões são exibidos. Botões adicionais podem ser exibidos para outros tipos de projeto. Para obter mais informações sobre botões de **propriedades** janela, consulte [janela propriedades](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Implementação de botões de janela de propriedades  
 Quando você clica o **categorizado** botão, chamadas do Visual Studio a <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> interface no objeto que tem o foco para classificar suas propriedades por categoria. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>é implementado o `IDispatch` objeto que é apresentado para o **propriedades** janela.  
  
 Há 11 categorias de propriedade predefinidos, que têm valores negativos. Você pode definir as categorias personalizadas, mas é recomendável que você está atribuindo valores positivos para diferenciá-los a categorias predefinidas.  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> método retornará o valor de categoria de propriedade apropriada para a propriedade especificada. O <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> método retorna uma cadeia de caracteres que contém o nome da categoria. Você só precisa fornecer suporte para valores de categoria personalizada, como Visual Studio sabe os valores de categoria de propriedade padrão.  
  
 Quando você clica o **Alphabetized** botão, as propriedades são exibidas em ordem alfabética por nome. Os nomes são recuperados por `IDispatch` acordo com um algoritmo de classificação localizado.  
  
 Quando o **propriedades** janela é aberta, o **propriedades** botão automaticamente é mostrado como selecionado. Em outras partes do ambiente, o mesmo botão é exibido e clique nele para mostrar o **propriedades** janela.  
  
 O **páginas de propriedade** botão não estará disponível se `ISpecifyPropertyPages` não está implementado para o objeto selecionado. Páginas de propriedades exibe as propriedades de configuração dependente que são normalmente associadas com soluções e projetos, mas ser também podem ser associadas a itens de projeto (por exemplo, no Visual C++).  
  
> [!NOTE]
>  Não é possível adicionar botões de barra de ferramentas para a **propriedades** janela usando código não gerenciado. Para adicionar um botão de barra de ferramentas, você deve criar um objeto gerenciado que deriva de <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## <a name="see-also"></a>Consulte também  
 [Estender as propriedades](../../extensibility/internals/extending-properties.md)