---
title: Guia classe, caixa de diálogo de propriedades de janela | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a4be66a2eb725f2c81032b18414a2d6d624a0cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464645"
---
# <a name="class-tab-window-properties-dialog-box"></a>Guia Classe, Caixa de diálogo Propriedades da Janela
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [guia de classe, caixa de diálogo de propriedades de janela](https://docs.microsoft.com/visualstudio/debugger/class-tab-window-properties-dialog-box).  
  
Use o **classe** guia para exibir informações sobre a classe da janela selecionada. Para exibir o [janela caixa de diálogo de propriedades](../debugger/window-properties-dialog-box.md), mova o foco para o [modo de exibição do Windows](../debugger/windows-view.md) janela. Selecione qualquer nó de janela na árvore e escolha **propriedades** da **exibição** menu.  
  
 As seguintes configurações estão disponíveis sobre o **classe** guia:  
  
|Entrada|Descrição|  
|-----------|-----------------|  
|**Nome de Classe**|O nome (ou um número ordinal) dessa classe de janela.|  
|**Estilos de classe**|Uma combinação de códigos de estilo de classe.|  
|**Bytes de classe**|Dados de específicos do aplicativo associados a essa classe de janela.|  
|**Classe Atom**|O atom para a classe retornada pela **RegisterClass** chamar.|  
|**Identificador de instância**|O identificador da instância do módulo que registrou a classe. Identificadores de instância não são exclusivos.|  
|**Bytes de janela**|O número de bytes adicionais associados a cada janela dessa classe. O significado desses bytes é determinado pelo aplicativo. Expanda a caixa de lista para ver os valores de byte em formato DWORD.|  
|**Procedimento de janela**|O endereço atual do **WndProc** função para o windows dessa classe. Isso difere da **procedimento de janela** sobre o **geral** guia se a janela é uma subclasse.|  
|**Nome do menu**|O nome do menu principal que está associado com o windows dessa classe ("none" se não houver nenhum menu).|  
|**Identificador de ícone**|O identificador para o ícone que está associado com o windows dessa classe ("none" se não houver nenhum ícone).|  
|**Identificador de cursor**|O identificador para o cursor que está associado com o windows dessa classe ("none" se não houver nenhum cursor).|  
|**Pincel de plano de fundo**|O identificador para o pincel de plano de fundo que está associado com o windows dessa classe ou uma das COLOR_ * cores predefinidas para pintar a tela de fundo de janela ("none" se não houver nenhum pincel).|



