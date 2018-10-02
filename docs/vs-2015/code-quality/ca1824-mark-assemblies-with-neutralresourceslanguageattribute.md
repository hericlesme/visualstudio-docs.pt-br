---
title: 'CA1824: Marcar assemblies com NeutralResourcesLanguageAttribute | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d433208e9bb63d770feb00f7f659c9e469a0c4e9
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587029"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: marcar assemblies com NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1824: marcar assemblies com NeutralResourcesLanguageAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute).

|||
|-|-|
|NomeDoTipo|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um assembly contém um **ResX**-com base em recursos, mas não tem o <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> aplicado a ele.

## <a name="rule-description"></a>Descrição da Regra
 O **NeutralResourcesLanguage** atributo informa o **ResourceManager** da linguagem que foi usada para exibir os recursos de cultura neutra para um assembly. Quando ele procura recursos na mesma cultura que o idioma de recursos neutros, o **ResourceManager** usa automaticamente os recursos que estão localizados no assembly principal. Ele faz isso em vez de procurar por um assembly satélite que tem a cultura de interface do usuário atual do thread atual. Isso melhora o desempenho da pesquisa para o primeiro recurso carregado e pode reduzir o conjunto de trabalho.

## <a name="fixing-violations"></a>Corrigir violações
 Para corrigir uma violação dessa regra, adicione o atributo ao assembly e especificar o idioma dos recursos de cultura neutra.

## <a name="specifying-the-language"></a>Especificando o idioma

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Para especificar o idioma do recurso de cultura neutra

1.  Na **Gerenciador de soluções**, clique em seu projeto e, em seguida, clique em **propriedades**.

2.  Na barra de navegação à esquerda, selecione **Application**e, em seguida, clique em **informações de Assembly**.

3.  No **informações do Assembly** diálogo caixa, selecione o idioma do **linguagem neutra** lista suspensa.

4.  Clique em **OK**.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É permitido para suprimir um aviso nessa regra. No entanto, pode diminuir o desempenho da inicialização.



