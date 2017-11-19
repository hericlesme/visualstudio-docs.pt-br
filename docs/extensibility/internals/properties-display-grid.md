---
title: "Grade de propriedades de exibição | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35b36c357c9b98d81627eea0d511b0b4fd49f693
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="properties-display-grid"></a>Grade de exibição de propriedades
O **propriedades** janela exibe campos dentro de uma grade. A coluna esquerda contém os nomes de propriedade; a coluna à direita contém os valores de propriedade.  
  
## <a name="working-with-the-grid"></a>Trabalhar com a grade  
 A lista de duas colunas mostra as propriedades de configuração independente que podem ser alteradas em tempo de design e suas configurações atuais. Observe que todas as propriedades não podem ser mostradas. Uma propriedade pode ser definida como oculto, por exemplo, Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> método. Especificamente, para ocultar propriedades que têm propriedades filho:  
  
1.  Definir o `pfDisplay` parâmetro em <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> para `FALSE`.  
  
2.  Definir o `pfHide` parâmetro em <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> para `TRUE`.  
  
 Informações de envio por push para o **propriedades** janela, o IDE usa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>é chamado pelo VSPackages para cada janela que contém objetos selecionáveis com propriedades relacionadas a serem exibidos no **propriedades** janela. **Gerenciador de soluções**da implementação de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> chamadas `GetProperty` usando <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> em sua hierarquia de projeto para adquirir os objetos navegáveis na hierarquia.  
  
 Se seu VSPackage não oferece suporte a <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, o IDE tenta usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> usando o valor de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> que fornecem o item de hierarquia ou itens.  
  
 Seu projeto VSPackage não precisa criar <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> porque o pacote de janela fornecida pelo IDE que implementa ele (por exemplo, **Solution Explorer**) constrói <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> em seu nome.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>consiste em três métodos são chamados pelo IDE:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>contém o número de objetos selecionados a serem exibidos no **propriedades** janela.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>Retorna o `IDispatch` objetos selecionados a serem exibidos no **propriedades** janela.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>permite que qualquer um dos objetos retornados por <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> para ser selecionado pelo usuário. Isso permite que o VSPackage visualmente Atualizar seleção exibida para o usuário na interface de usuário.  
  
 O **propriedades** janela extrai informações do `IDispatch` objetos para recuperar as propriedades que está sendo pesquisadas. O navegador de propriedades usa `IDispatch` perguntar quais propriedades de objeto, ele oferece suporte ao consultar `ITypeInfo`, que é obtido `IDispatch::GetTypeInfo`. O navegador usa esses valores para preencher o **propriedades** janela e alterar os valores de propriedades individuais são exibidos na grade. As informações de propriedades são mantidas dentro do próprio objeto.  
  
 Porque os objetos retornados suportam `IDispatch`, o chamador pode obter informações sobre como o nome do objeto chamando `IDispatch::Invoke` ou `ITypeInfo::Invoke` com um identificador de predefinidos distribuição (DISPID) que representa as informações desejadas. DISPIDs declarados são negativos para garantir que eles não entrem em conflito com os identificadores definidos pelo usuário.  
  
 O **propriedades** janela exibe tipos diferentes de campos dependendo dos atributos de propriedades específicas de um objeto selecionado. Esses campos incluem caixas de edição, listas suspensas e links para caixas de diálogo do editor personalizado.  
  
-   Os valores contidos em uma lista enumerada são recuperados por um <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> de consulta para `IDispatch`. Valores obtidos de uma lista enumerada podem ser alterados na grade de propriedades, clique duas vezes no nome do campo ou clicando no valor e selecionando o novo valor na lista suspensa. Para propriedades que têm configurações de lista enumerada predefinidas, duas vezes no nome da propriedade na lista de propriedades alterna entre as opções disponíveis. Para as propriedades predefinidas com apenas duas opções, como verdadeiro/falso, duas vezes no nome de propriedade para alternar entre as opções.  
  
-   Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> é `false`, indicando que o valor foi alterado, o valor é exibido em negrito. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>é usado para determinar se o valor pode ser redefinido para o valor original. Se assim, você pode alterar para o valor padrão, clicando duas vezes o valor e escolhendo **redefinir** no menu exibido. Caso contrário, você precisa alterar o valor para o valor padrão manualmente. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>também permite que você localize e ocultar os nomes das propriedades exibidas durante o tempo de design, mas não afeta os nomes de propriedade exibidos durante o tempo de execução.  
  
-   Clique no botão de reticências (...) exibe uma lista de valores de propriedade da qual o usuário pode selecionar (como um seletor de cores ou a lista de fontes). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>fornecer esses valores.  
  
## <a name="see-also"></a>Consulte também  
 [Estender as propriedades](../../extensibility/internals/extending-properties.md)