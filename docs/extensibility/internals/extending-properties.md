---
title: Estendendo propriedades | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: abf254aa21be5ec4b7401e21afa5f9bcca00e011
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="extending-properties"></a>Estendendo propriedades
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **propriedades** janela é um navegador de propriedade universal para componentes COM e COM+ e dá suporte a todos os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] produtos. O **propriedades** janela funciona com `ITypeInfo` COM+ metadados para listar as propriedades de tempo de design para o objeto atualmente selecionado em qualquer outra janela no ambiente de desenvolvimento integrado (IDE) e informações de tipo.  
  
 O **propriedades** janela, que pode ser aberta pressionando F4 no teclado ou selecionando **janela propriedades** no **exibição** menu, é usado para exibir e editar Propriedades de configuração independente, o tempo de design e eventos dos objetos selecionados. Propriedades de configuração dependente, associadas com soluções e projetos, são exibidas em [páginas de propriedade](../../extensibility/internals/property-pages.md). Para obter mais informações, consulte [propriedades do projeto: NIB](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [opções de configuração do gerenciamento de](../../extensibility/internals/managing-configuration-options.md), e [gerenciamento NIB: Item em projetos](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Visão geral da janela propriedades](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Janela de Propriedades  
  
 Esta seção fornece informações detalhadas relacionadas a áreas individuais do **propriedades** janela e as interfaces que você deve implementar e chamada para preencher a janela.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral da janela de propriedades](../../extensibility/internals/properties-window-overview.md)  
 Explica a finalidade de **propriedades** janela relativa à janela de ferramenta e a janela do documento.  
  
 [Política de modelo e a janela Propriedades](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Discute como um projeto está contido em um projeto de modelo de empresa e como esse projeto de modelo de empresa pode impor a política.  
  
 [Interfaces e campos da janela Propriedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Explica a base para a seleção que determina quais informações são exibidas no **propriedades** janela.  
  
 [Lista de objetos da janela Propriedades](../../extensibility/internals/properties-window-object-list.md)  
 Descreve a finalidade do **propriedades** lista de objetos de janela, que descreve como, quando um objeto diferente da lista dispara uma chamada, o ambiente é informado de que um novo objeto foi selecionado.  
  
 [Botões da janela Propriedades](../../extensibility/internals/properties-window-buttons.md)  
 Explica a finalidade dos botões de quatro padrão exibidos no **propriedades** barra de ferramentas da janela.  
  
 [Grade de exibição de propriedades](../../extensibility/internals/properties-display-grid.md)  
 Explica onde os nomes de propriedade e os campos de valores de propriedade são encontrados na grade.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Tipos de projeto](../../extensibility/internals/project-types.md)  
 Discute projetos como os blocos de construção de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Compilando e criando](../../ide/compiling-and-building-in-visual-studio.md)  
 Descreve como você pode usar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plataforma para testar e depurar aplicativos ao criá-los continuamente.  
  
 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)  
 Descreve o `IDispatch` interface, que primeiro foi projetado para oferecer suporte a automação, fornecendo um mecanismo de associação tardia para acessar e recuperar informações sobre os métodos e propriedades de um objeto.  
  
 [Gerenciando configurações de aplicativo (.NET)](../../ide/managing-application-settings-dotnet.md)  
 Fornece uma visão geral das configurações do aplicativo que permitem que você configure seu aplicativo para que os valores de propriedade são armazenados no arquivo de configuração externo em vez do código compilado do aplicativo.  
  
 [Soluções e projetos](../../ide/solutions-and-projects-in-visual-studio.md)  
 Explica como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerencia com eficiência os itens como referências, conexões de dados, pastas e arquivos que são exigidos por seu esforço de desenvolvimento por meio de soluções e projetos.  
  
 [Estender outras partes do Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica como usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] services para criar elementos de interface do usuário que correspondem ao restante da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].