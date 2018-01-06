---
title: "Introdução a personalizações no nível do documento da programação para Word | Microsoft Docs"
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
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
ms.assetid: 30593c47-1658-4fca-b9a9-36fbdf73c901
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 12265c725480324c396d59d848e5269432bb5d6e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-programming-document-level-customizations-for-word"></a>Introdução a personalizações no nível de documento da programação para Word
  Se você estiver apenas começando criar personalizações no nível de documento para o Microsoft Office Word usando o Visual Studio, aqui está o que você precisa saber.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understanding-how-document-level-customizations-for-word-work"></a>Noções básicas sobre personalizações como nível de documento para o trabalho do Word  
 Cada personalização do Word que você criar baseia-se em um único documento. Para começar a usar a personalização, o usuário final abre o documento ou cria o documento de um modelo do Word. Eventos do documento, por exemplo, mover o cursor para áreas específicas ou clicar em itens de menu e botões podem chamar métodos de manipulação de eventos no assembly. Quando o documento é fechado, os recursos fornecidos pela personalização não estão mais disponíveis no Word.  
  
 Para obter mais informações, consulte [arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="creating-document-level-projects-for-word"></a>Criando projetos no nível de documento para Word  
 Para criar uma personalização de nível de documento para Word, use o modelo de projeto de documento do Word ou o modelo do Word no **novo projeto** caixa de diálogo. Esses modelos incluem referências de assembly necessárias e os arquivos de projeto.  
  
 Para obter mais informações sobre como criar um projeto de nível de documento para Word, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obter mais informações sobre os modelos de projeto, consulte [visão geral de modelos de projeto do Office](../vsto/office-project-templates-overview.md).  
  
## <a name="programming-word-documents-by-using-host-items-host-controls"></a>Documentos do Word programação por meio de controles de Host de itens de Host  
 *Itens de host* e *hospedar controles* são classes que fornecem o modelo de programação para personalizações no nível do documento.  
  
 Itens de host fornecem um ponto de entrada para o seu código, e eles também podem atuar como contêineres para controles de host e controles de formulários do Windows. Em projetos de nível de documento para Word, o item de host é representado pela `ThisDocument` classe.  
  
 Controles de host são baseados em objetos nativos do Word, como controles de conteúdo, indicadores e os nós XML. Controles de host fornecem funcionalidade semelhante aos objetos de palavra nativo, mas também têm novos eventos, o suporte ao designer e o recurso de associação de dados. Elas são exibidas como objetos de primeira classe no seu código de projeto e do IntelliSense, o que torna mais fácil para se referir a objetos específicos diretamente no seu código sem precisar navegar o modelo de objeto do Word.  
  
 Para mais informações, consulte os seguintes tópicos:  
  
-   [Programando personalizações no nível do documento](../vsto/programming-document-level-customizations.md)  
  
-   [Automatizando o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Visão geral dos Controles de Host e dos Itens de Host](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customizing-the-user-interface-of-word"></a>Personalizando a Interface do usuário do Word  
 A maioria das soluções do Microsoft Office modificar a interface do usuário (IU) do aplicativo do Office para fornecer alguma forma para os usuários interajam com a solução. Há muitas maneiras em que você pode modificar a interface do usuário do Word usando uma personalização no nível do documento. Por exemplo, você pode adicionar controles à faixa de opções, e você pode exibir um painel de ações. Para obter mais informações, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
 Você também pode abrir o documento que está associado ao seu projeto diretamente no Visual Studio. Quando o documento é aberto no Visual Studio, você pode modificar o documento usando a interface de usuário do Word. Você também pode usar o documento como uma superfície de design, o que permite que você arraste os controles para ele. Para obter mais informações, consulte [projetos do Office no ambiente do Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="binding-controls-to-data"></a>Associando controles a dados  
 Os controles de conteúdo e o <xref:Microsoft.Office.Tools.Word.Bookmark> controle estão na lista de controles que você pode arrastar o **fontes de dados** janela. Adicionando controles de conteúdo e indicadores na forma automaticamente associa a fonte de dados que você deseja configurar usando a janela. Sem gravar nenhum código, você pode exibir dados de bancos de dados, serviços e objetos comerciais. Para obter mais informações, consulte [vinculação de dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Próximas etapas  
 Para saber como criar uma personalização de nível de documento para Word, consulte [passo a passo: Criando seu primeiro nível do documento personalização para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Este passo a passo apresenta as ferramentas de desenvolvimento do Office no Visual Studio e o modelo de programação para personalizações de nível de documento do Word.  
  
 Para obter uma lista de tópicos que mostram algumas das tarefas comuns em projetos do Word, consulte [tarefas comuns na programação do Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Personalizações no nível do documento da programação](../vsto/programming-document-level-customizations.md)   
 [Soluções do Word](../vsto/word-solutions.md)   
 [Passo a passo: Criando a primeira personalização no nível do documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Explicações passo a passo usando o Word](../vsto/walkthroughs-using-word.md)   
 [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)   
 [Escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md)  
  
  