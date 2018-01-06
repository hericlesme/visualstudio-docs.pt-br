---
title: "Guia de System. Activities, escolher a caixa de diálogo de itens de caixa de ferramentas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: ba4078a903c1e30b968928e13c8d160c898bbf0d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>O guia de System.Activities, escolher a caixa de diálogo dos itens da caixa de ferramentas
Esta guia, o **escolher itens da caixa de ferramentas** caixa de diálogo exibe uma lista de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] atividades, modelos e itens disponíveis para você. Para exibir essa lista, selecione **escolher itens da caixa de ferramentas** do **ferramentas** menu ou clicando com o **caixa de ferramentas** e selecionando **escolher itens**para exibir o **escolher itens da caixa de ferramentas** caixa de diálogo e, em seguida, selecione seu **System. Activities** guia. Inicialmente, a lista contém as atividades de fluxo de trabalho de assemblies de System. Activities, System.ServiceModel.Activities e System.Activities.Core.Presentation; No entanto, somente o fornecida pelo sistema mostradas de atividades e atividades adicionadas por meio de outros assemblies exibidos no **caixa de ferramentas** são selecionadas por padrão. Adicionado recentemente atividades são verificadas automaticamente e aparecem no **caixa de ferramentas** quando você clica em **Okey** na caixa de diálogo. Além disso, esses itens aparecem no **caixa de ferramentas** em uma nova categoria que corresponde ao namespace onde reside o atividade / / modelo de item.  
  
> [!WARNING]
>  Se você tentar adicionar um conjunto que não contém quaisquer atividades de fluxo de trabalho, uma caixa de diálogo de erro é exibida para explicar que o assembly não contém quaisquer atividades.  
  
 Essa caixa de diálogo é independente do projeto e, portanto, o **System. Activities** guia continua apareça em XAML autônomo ou um tipo de projeto de fluxo de trabalho não.  
  
 A filtragem é feita em cada guia. Isso significa que não é possível adicionar as atividades de fluxo de trabalho por meio de **componente .NET** guia. Eles precisam ser adicionados por meio de **System. Activities** guia em si.  
  
 Você pode desmarcar os itens que você não deseja ver no **caixa de ferramentas** nessa caixa de diálogo guia, ou como alternativa, você pode fazer isso usando o **excluir** opção de menu de contexto no **caixa de ferramentas** e desalocar fazendo referência a um assembly não remove o item do **caixa de ferramentas**.  
  
 Criando uma instância da atividade, arrastando e soltando-os ao designer adiciona o assembly que contém o item à lista de módulos (assemblies) referenciados automaticamente. Também se a atividade referencia um assembly C 2.0, C 2.0 não adiciona à lista de assembly referenciado. Assembly C deve estar no GAC ou no mesmo diretório que a atividade B. No caso de autônomo, o assembly deve ser no GAC ou os caminhos de investigação do VS. Somente então você pode arrastar e soltar a atividade na superfície de fluxo de trabalho.  
  
 **Caixa de ferramentas** por padrão, as configurações são salvas como opções de usuário, assim a próxima vez, quando você abre o **caixa de ferramentas**, ele exibe a lista personalizada de atividades de fluxo de trabalho. Um efeito colateral disto é que, se você tiver adicionado seus itens de domínio específico para o **caixa de ferramentas** por meio de **escolher itens da caixa de ferramentas** caixa de diálogo, você ainda continuar a ver esses itens quando você estiver trabalhando em um Fluxo de trabalho também aplicativo de Console. Se você não deseja vê-los, excluí-los usando o menu de contexto ou desmarque-as por meio de **escolher itens da caixa de ferramentas** caixa de diálogo, conforme observado anteriormente.  
  
 As colunas nesta caixa de diálogo contém as informações a seguir:  
  
 Nome  
 Lista os nomes das atividades de fluxo de trabalho registradas atualmente em seu computador local.  
  
 Namespace  
 Exibe a hierarquia de namespace de biblioteca de classes do.NET Framework que define a estrutura de atividade.  
  
 Nome do Assembly  
 Exibe o nome e a versão do assembly do.NET Framework que contém a atividade.  
  
 Diretório  
 Exibe o local do assembly do.NET Framework que contém as atividades de fluxo de trabalho. O local padrão para todos os assemblies é o cachê global de assemblies.  
  
 Para classificar os componentes listados, selecione todo o título de coluna.