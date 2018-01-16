---
title: Modelos do Visual Studio para projetos e arquivos | Microsoft Docs
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3959b01fdfc0ff77bdd5a3ffa0c96366b9da87d7
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2018
---
# <a name="project-and-item-templates"></a>Modelos de projeto e de item

Os modelos de projeto e de item fornecem stubs reutilizáveis que oferecem aos usuários uma estrutura e um código básico que eles podem personalizar para suas próprias finalidades.

## <a name="visual-studio-templates"></a>modelos do Visual Studio

Vários modelos de itens e de projetos predefinidos são instalados com o Visual Studio. Por exemplo, os modelos **Aplicativo do Windows Forms** e **Biblioteca de Classes** do Visual Basic e do C# que são mostrados na caixa de diálogo **Novo Projeto** são modelos de projeto. Os modelos de item são mostrados na caixa de diálogo **Adicionar Novo Item** e incluem itens como arquivos de código, arquivos XML, páginas HTML e folhas de estilo.

Esses modelos fornecem um ponto de partida para os usuários começarem a criar projetos ou expandir projetos existentes. Os modelos de projeto fornecem os arquivos que são necessários para um tipo de projeto específico, incluem referências de assembly padrão e definem opções de compilador e propriedades de projeto padrão. Os modelos de item podem variar em complexidade desde apenas um arquivo vazio com uma extensão de nome de arquivo correta até um item multiarquivos contendo, por exemplo, arquivos de código-fonte com código de stub, arquivos de informações do designer e recursos inseridos.

Além dos modelos instalados nas caixas de diálogo **Novo Projeto** e **Adicionar Novo Item**, você pode criar seus próprios modelos ou baixar e usar modelos criados pela comunidade. Para obter mais informações, consulte [Como criar modelos de projeto](../ide/how-to-create-project-templates.md) e [Como criar modelos de item](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Conteúdo de um modelo

Todos os modelos de projeto e de item, sejam eles instalados com o Visual Studio ou criados por você, funcionam usando os mesmos princípios e têm conteúdo semelhante. Todos os modelos contêm os seguintes itens:

- Os arquivos a serem criados quando o modelo é usado. Isso inclui arquivos de código-fonte, recursos inseridos, arquivos de projeto e assim por diante.

- Um arquivo .vstemplate. Esse arquivo contém os metadados que fornecem as informações necessárias para exibir o modelo nas caixas de diálogo **Novo Projeto** e **Adicionar Novo Item** e para criar um projeto ou um item do modelo. Para obter mais informações sobre arquivos .vstemplate, consulte [Parâmetros de modelo](../ide/template-parameters.md).

Quando esses arquivos são compactados em um arquivo .zip e colocados na pasta correta, o Visual Studio exibe-os automaticamente nos seguintes locais:

- Os modelos de projeto aparecem na caixa de diálogo **Novo Projeto**.

- Os modelos de item aparecem na caixa de diálogo **Adicionar Novo Item**.

Para obter mais informações sobre pastas de modelo, consulte [Como localizar e organizar modelos](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="starter-kits"></a>Kits de Início

Kits de início são modelos avançados que podem ser compartilhados com outros membros da comunidade. Um kit de início inclui exemplos de código que são compilados, documentação e outros recursos para ajudar os usuários a aprenderem novas ferramentas e técnicas de programação enquanto que compilam aplicativos úteis e reais. Os conteúdos e procedimentos básicos dos Kits de início são idênticos aos dos modelos. Para obter mais informações, consulte [Como criar kits de início](../ide/how-to-create-starter-kits.md).

## <a name="see-also"></a>Consulte também

[Como criar modelos de projeto](../ide/how-to-create-project-templates.md)  
[Como criar modelos de item](../ide/how-to-create-item-templates.md)  
[Parâmetros de modelo](../ide/template-parameters.md)  
[Personalizando modelos](../ide/customizing-project-and-item-templates.md)  
[NuGet Packages in Visual Studio templates](/nuget/visual-studio-extensibility/visual-studio-templates) (Pacotes do NuGet em modelos do Visual Studio)