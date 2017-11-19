---
title: 'CA1824: Marcar assemblies com NeutralResourcesLanguageAttribute | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c1d2138065946bfd14abfedbbffdd2dc5b433d89
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: marcar assemblies com NeutralResourcesLanguageAttribute
|||  
|-|-|  
|NomeDoTipo|MarkAssembliesWithNeutralResourcesLanguage|  
|CheckId|CA1824|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um assembly contém um **ResX**-com base em recursos, mas não tem o <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> aplicada a ele.  
  
## <a name="rule-description"></a>Descrição da Regra  
 O **NeutralResourcesLanguage** atributo informa o **ResourceManager** do idioma usado para exibir os recursos de cultura neutra para um assembly. Ao procurar os recursos da cultura mesmo como o idioma de recursos neutros, o **ResourceManager** usa automaticamente os recursos que estão localizados no assembly principal. Ele faz isso em vez de procurar por um assembly satélite com a cultura de interface do usuário atual do thread atual. Isso melhora o desempenho da pesquisa para o primeiro recurso carregado e pode reduzir o conjunto de trabalho.  
  
## <a name="fixing-violations"></a>Corrigir violações  
 Para corrigir uma violação desta regra, adicione o atributo para o assembly e especificar o idioma dos recursos de cultura neutra.  
  
## <a name="specifying-the-language"></a>Especificar o idioma  
  
#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Para especificar o idioma do recurso de cultura neutra  
  
1.  Em **Solution Explorer**, clique com o botão direito e, em seguida, clique em **propriedades**.  
  
2.  Na barra de navegação à esquerda, selecione **aplicativo**e, em seguida, clique em **informações de Assembly**.  
  
3.  No **informações de Assembly** caixa de diálogo, selecione o idioma do **neutralidade de idioma** lista suspensa.  
  
4.  Clique em **OK**.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É permitido para suprimir um aviso dessa regra. No entanto, pode diminuir o desempenho de inicialização.