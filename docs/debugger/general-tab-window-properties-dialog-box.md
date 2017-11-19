---
title: "Guia geral, caixa de diálogo de propriedades de janela | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b26896ce119e49ec2d001a0b09bc7b563bd7cac
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="general-tab-window-properties-dialog-box"></a>Guia Geral, Caixa de diálogo Propriedades da Janela
Use o **geral** guia para mostrar informações sobre a janela selecionada. Para exibir o [caixa de diálogo de propriedades de janela](../debugger/window-properties-dialog-box.md), move o foco para o [exibição Windows](../debugger/windows-view.md) janela. Selecione qualquer nó de janela na árvore e escolha **propriedades** do **exibição** menu.  
  
 As configurações a seguir estão disponíveis no **geral** guia:  
  
|Entrada|Descrição|  
|-----------|-----------------|  
|**Legenda da janela**|O texto na legenda da janela, ou o texto contido em uma janela se ele é um controle.|  
|**Identificador de janela**|A ID exclusiva desta janela. Os números de identificador de janela são reutilizados; eles identificarem uma janela somente para o tempo de vida da janela.|  
|**Procedimento de janela**|O endereço virtual da função de procedimento de janela para esta janela. Esse campo indica também se essa janela é uma janela de Unicode, e se ele é subclasse.|  
|**Retângulo**|O retângulo delimitador da janela. O tamanho do retângulo também é exibido. As unidades são pixels em coordenadas da tela.|  
|**RET restaurado.**|O retângulo delimitador para a janela restaurado. O tamanho do retângulo também é exibido. Rect restaurado será diferente de retângulo somente quando a janela é minimizada ou maximizada. As unidades são pixels em coordenadas da tela.|  
|**Cliente Rect**|O retângulo delimitador para a área cliente da janela. O tamanho do retângulo também é exibido. As unidades são pixels relativos à parte superior esquerda da área de cliente da janela.|  
|**Identificador de instância**|O identificador de instância do aplicativo. Identificadores de instância não são exclusivos.|  
|**ID de controle ou o identificador do Menu**|Se a janela que está sendo exibida é um filho, o rótulo da ID do controle é exibido. ID do controle é um inteiro que identifica ID de controle. desta janela filho Se a janela que está sendo exibida não é uma janela filho, o rótulo de identificador de Menu é exibido. O identificador do menu é um inteiro que identifica o identificador de menu associado a esta janela.|  
|**Dados de usuário**|Dados específicos do aplicativo que estão associados a essa estrutura de janela.|  
|**Bytes de janela**|O número de bytes adicionais associadas a esta janela. O significado desses bytes é determinado pelo aplicativo. Expanda a caixa de lista para ver os valores de byte em formato DWORD.|