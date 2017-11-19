---
title: "Como: abrir soluções do Office sem executar código | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
ms.assetid: a853d91c-9fd6-421a-b3a2-956b6b494b96
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74cc162e0323656bea9d48c8458eaf77519fdc14
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Como abrir soluções do Office sem executar código
  Uma solução do Microsoft Office criada com extensões de código gerenciado é executado, mesmo se a configuração de segurança no aplicativo do Office do usuário final é definida como alto. Isso ocorre porque a segurança de código do assembly .NET é gerenciada pelo Microsoft .NET Framework, não pelo Microsoft Office.  
  
 No entanto, há ocasiões quando você quiser abrir um documento sem executar o código. Por exemplo, código que é executado quando o documento for aberto pode alterar o conteúdo, mas você deseja atualizar a aparência do documento antes das alterações de código-lo. Ou talvez você queira enviar o documento com certas informações nela para outra, e você não deseja que o código para executar e possivelmente altere o conteúdo.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Há várias maneiras de abrir um documento ou a pasta de trabalho que contém as extensões de código gerenciado sem executar o código do assembly.  
  
### <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Para ignorar o assembly usando a tecla SHIFT  
  
-   Abrir documentos e pastas de trabalho de **arquivo** menu enquanto mantém pressionada a tecla SHIFT para impedir que o Word e Excel gerar eventos de inicialização, enquanto o documento será aberto.  
  
    > [!NOTE]  
    >  Se você abrir um documento ou a pasta de trabalho do **Introdução** painel de tarefas, mantendo pressionada a tecla SHIFT não ignora o código. Além disso, mantendo pressionada a tecla SHIFT não impede que eventos que está sendo gerado depois que o documento está aberto.  
  
     Esse método é útil se você quiser abrir um documento para fazer alterações sem o código em execução e alterar o documento primeiro.  
  
### <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Para ignorar um assembly renomeando ou removê-lo  
  
-   Se você tiver as permissões necessárias no computador onde o assembly está localizado, você pode renomear ou remover o assembly para que o documento ou a pasta de trabalho não é possível encontrá-lo. Isso resulta em um erro que está sendo gerado sempre que abrir o documento do Office.  
  
     Se a solução for usada por várias pessoas, esse método impede que a solução em execução para todos eles. Isso pode ser útil se um problema for encontrado no código ou um servidor referenciado e você deseja interromper a execução de todos os usuários.  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo soluções do Office](../vsto/securing-office-solutions.md)   
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)   
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifestos de aplicativo e implantação em soluções do Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  