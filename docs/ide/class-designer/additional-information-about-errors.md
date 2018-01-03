---
title: "Informações adicionais sobre erros do Designer de Classe | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 53b61b1fa49ffcbc047d47dd26586b45ae883c5f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="additional-information-about-class-designer-errors"></a>Informações adicionais sobre erros do Designer de Classe
O Designer de Classe não controla o local dos arquivos de origem, de forma que modificar a estrutura do projeto ou mover os arquivos de origem no projeto pode fazer com que o Designer de Classe perca o controle do tipo (especialmente o tipo de origem de um typedef, classes base ou tipos de associação). É possível receber um erro como **O Designer de Classe não pode exibir este tipo**. Se você fizer isso, arraste o código-fonte realocado ou modificado para o diagrama de classe, para exibi-lo novamente.  
  
Você pode obter ajuda com outros erros e avisos nos seguintes recursos:  
  
[Trabalhando com código do Visual C++](working-with-visual-cpp-code.md)  
Inclui informações de solução de problemas sobre como exibir o C++ em um diagrama de classe.  
  
[Fórum do Designer de Classe do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754)  
Fornece um fórum para perguntas e problemas com o Designer de Classe.  
  
## <a name="see-also"></a>Consulte também
[Projetando e exibindo classes e tipos](designing-and-viewing-classes-and-types.md)