---
title: Usando o Designer de fluxo de trabalho herdado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a042d98019b7f618792f7a9104d262362a4e6e3d
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
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

## <a name="see-also"></a>Consulte também

- [Fluxos de trabalho de desenvolvimento](http://go.microsoft.com/fwlink?LinkID=65010)