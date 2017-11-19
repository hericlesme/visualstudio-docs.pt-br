---
title: "Vários DSLs em uma única solução | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: "3"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: b55d1d5ec8e84c8d16681ffd0ac738291e1bc39d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="multiple-dsls-in-one-solution"></a>Várias DSLs em uma mesma solução
É possível empacotar diversas DSLs como parte de uma única solução para serem instaladas juntas.  
  
 É possível usar diversas técnicas para integrar múltiplas DSLs. Para obter mais informações, consulte [integrar modelos usando o Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) e [como: adicionar um manipulador de arrastar e soltar](../modeling/how-to-add-a-drag-and-drop-handler.md) e [Personalizando comportamento de cópia](../modeling/customizing-copy-behavior.md).  
  
### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Compilar mais de uma DSL na mesma solução  
  
1.  Crie duas ou mais soluções DSL e um projeto VSIX e adicione todos os projetos a uma única solução.  
  
    -   Para criar um novo projeto do VSIX: no **novo projeto** caixa de diálogo, selecione **Visual C#**, **extensibilidade**, **projeto VSIX**.  
  
    -   Crie duas ou mais soluções DSL no diretório da solução VSIX.  
  
         Abra uma nova instância do Visual Studio para cada DSL. Crie a nova DSL e especifique a mesma pasta da solução que a solução VSIX.  
  
         Certifique-se de criar cada DSL com uma extensão de nome de arquivo diferente.  
  
    -   Alterar os nomes do **Dsl** e **DslPackage** projetos para que eles sejam diferentes. Por exemplo: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.  
  
    -   Em cada **DslPackage\*\source.extension.tt**, atualize esta linha para o nome de projeto de Dsl correto:  
  
         `string dslProjectName = "Dsl2";`  
  
    -   Na solução VSIX, adicione o Dsl * e DslPackage\* projetos.  
  
         É aconselhável colocar cada par em sua própria pasta da solução.  
  
2.  Combine os manifestos VSIX das DSLs:  
  
    1.  Abra *YourVsixProject***\source.extension.manifest**.  
  
    2.  Para cada DSL, escolha **adicionar conteúdo** e adicionar:  
  
        -   `Dsl*`um projeto como um **MEF componente**  
  
        -   `DslPackage*`um projeto como um **MEF componente**  
  
        -   `DslPackage*`um projeto como um **pacote VS**  
  
3.  Compile a solução.  
  
 O VSIX resultante instalará as duas DSLs. Você pode testá-las usando F5 ou implantar *YourVsixProject***\bin\Debug\\\*.vsix**.  
  
## <a name="see-also"></a>Consulte também  
 [Integração de modelos usando o Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Como: adicionar um manipulador de arrastar e soltar](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Personalizando o comportamento de cópia](../modeling/customizing-copy-behavior.md)