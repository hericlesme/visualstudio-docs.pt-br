---
title: Usando o Designer de fluxo de trabalho herdado | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: eda078bdfc0eae8861ac4e70b0f1f73a399f994c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="using-the-legacy-workflow-designer"></a>Usando Designer de Fluxo de Trabalho herdado
[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado fornecido por [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] pode ser usado para direcionar [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Que são acessadas selecionando o **.NET Framework 3.0** opção ou o **.NET Framework 3.5** opção no menu suspenso na parte superior da lista da **novo projeto** janela. A opção padrão na [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] é **.NET Framework 4** que é usada para criar [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplicativos voltados para o [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].  
  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] fornece uma maneira de criar aplicativos graficamente de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] usando a interface do usuário e de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . aplicativos de[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] são compostos das etapas do processo de fluxo de trabalho chamadas atividades. Para criar um fluxo de trabalho, compor as atividades na superfície de design arrastando seus designers de atividade do respectivos de **caixa de ferramentas** na superfície de design.  
  
 A tabela a seguir lista os principais recursos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para Windows Workflow Foundation.  
  
|Recurso|Descrição|  
|-------------|-----------------|  
|Arrastar e soltar de atividades|Arraste as atividades do **caixa de ferramentas** na superfície de design para criar um fluxo de trabalho.|  
|Pesquisador de Propriedades|O padrão **propriedades** janela no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é usado para configurar as propriedades de uma atividade.|  
|Aplicar Zoom|Os binóculos **nível de Zoom** ícone está localizado abaixo da barra de rolagem vertical no lado direito da superfície de design. Clique nos binóculos e selecione uma porcentagem de zoom para fazer com que o elemento gráfico de fluxo de trabalho ampliar ou reduzir fora. Você também pode usar o **panorâmica** opções de cursor do ícone de lupa para ampliar e reduzir.|  
|Panorâmica|O **panorâmica** ícone, um círculo que contém quatro transversais setas apontando em quatro direções, está localizada abaixo da barra de rolagem vertical no lado direito da superfície de design, logo abaixo do ícone de zoom binóculos. Se você clicar no ícone de bandeja, oferece de um menu pop-up as seguintes opções de cursor:<br /><br /> -A **ampliar** cursor Lupa permite ampliar clicando na superfície de design.<br />-A **zoom** Lupa cursor permite reduzir clicando na superfície de design.<br />-A **ferramenta navegação** cursor mão permite "capturar" e alternar o modo de exibição de um fluxo de trabalho na superfície de design.<br />-A **padrão** cursor seta permite que você alterne de cursores de volta para o cursor de seta padrão.|  
|Rolagem automático|Se você tiver um grande fluxo de trabalho, convém colocar uma atividade além de exibição da área visível de superfície de design. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite que você arraste uma atividade para a borda da superfície de design mais próximo a onde você deseja colocar a atividade. A superfície de design de exibição os rola automaticamente naquela direção.|  
|Marcas inteligentes|As atividades que não são configuradas completamente ou não são configuradas não válida são marcadas com um ícone de ponto de exclamação. Você pode clicar no ícone e ver uma lista suspensa das necessidades de configuração que existem na atividade. Você pode usar o **propriedades** janela para configurar a atividade adequadamente. Quando todas as propriedades são válidos para atividades, o ícone de ponto de exclamação desaparece.|  
  
## <a name="in-this-section"></a>Nesta seção  
 [Janelas de fluxo de trabalho do Visual Studio (herdado)](../workflow-designer/visual-studio-workflow-windows-legacy.md)  
  
 [Criando projetos herdados de fluxo de trabalho](../workflow-designer/creating-legacy-workflow-projects.md)  
  
 [Exibições de fluxo de trabalho sequencial (herdado)](../workflow-designer/sequential-workflow-views-legacy.md)  
  
 [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)  
  
 [Usando temas em fluxos de trabalho (herdado)](../workflow-designer/using-themes-in-workflows-legacy.md)  
  
 [Usando o Designer de Fluxo de Trabalho da máquina de estado herdado](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)  
  
 [Usando o designer de atividade herdado](../workflow-designer/using-the-legacy-activity-designer.md)  
  
 [Designer herdado para a ajuda da interface do usuário do Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)  
  
## <a name="see-also"></a>Consulte também  
 [Fluxos de trabalho de desenvolvimento](http://go.microsoft.com/fwlink?LinkID=65010)