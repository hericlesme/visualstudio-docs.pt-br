---
title: "Adicionar parâmetros de nome em modelos de projeto e de item no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ecdd277a36cb1c074653edb2af7f1882e6d25ede
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Como substituir parâmetros em um modelo

Os parâmetros de modelo permitem que você substitua identificadores como nomes de classes e namespaces, quando um arquivo é criado usando um modelo. Você pode adicionar parâmetros de modelo em modelos existentes ou criar seus próprios modelos com os parâmetros de modelo.

Parâmetros de modelo são escritos no formato $*parâmetro*$. Para obter uma lista completa dos parâmetros de modelo, consulte [Parâmetros de modelo](../ide/template-parameters.md).

A seção a seguir mostra como modificar um modelo para substituir o nome de um namespace pelo "nome seguro do projeto".

## <a name="to-use-a-parameter-to-replace-the-namespace-name"></a>Para usar um parâmetro para substituir o nome do namespace

1. Insira o parâmetro em um ou mais dos arquivos de código no modelo. Por exemplo:

    ```csharp
    namespace $safeprojectname$
    ```

1. No arquivo .vstemplate do modelo, localize o elemento `ProjectItem` que inclui esse arquivo.

1. Defina o atributo `ReplaceParameters` como `true` para o elemento `ProjectItem`:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Consulte também

[Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)  
[Parâmetros de modelo](../ide/template-parameters.md)  
[Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)  
[Elemento ProjectItem (Modelos de item do Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)