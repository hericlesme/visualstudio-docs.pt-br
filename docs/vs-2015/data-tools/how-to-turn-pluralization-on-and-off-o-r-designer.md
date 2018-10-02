---
title: 'Como: ative em pluralization e off (Object Relational Designer) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 02fa8b50b28f967a0835f68e85d146ca1eea514b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47476344"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Como: ative em pluralization e off (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: ative em pluralization e off (Object Relational Designer)](https://docs.microsoft.com/visualstudio/data-tools/how-to-turn-pluralization-on-and-off-o-r-designer).  
  
  
Por padrão, quando você arrasta objetos de banco de dados que têm nomes que terminam em s ou em ies de **Gerenciador de servidores**/**Database Explorer** até a [ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), os nomes das classes de entidade gerados são alterados de plural a única. Isso é feito a representa mais precisamente o fato que a classe instanciado de entidade mapeia para um único registro de dados. Por exemplo, adicione uma tabela de clientes para os resultados de [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] em uma classe de entidade chamada Cliente porque a classe conterá dados para apenas um único cliente.  
  
> [!NOTE]
>  Pluralization está ativada por padrão somente na versão de língua inglesa do Visual Studio.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>Para desativar o pluralization e sobre  
  
1.  No menu **Ferramentas**, clique em **Opções**.  
  
2.  No **opções** diálogo caixa, expanda **ferramentas de banco de dados**.  
  
> [!NOTE]
>  Selecione **Mostrar todas as configurações** se o **ferramentas de banco de dados** nó não está visível.  
  
1.  Clique em **Relational Designer**.  
  
2.  Definir **Pluralização de nomes** para **Enabled** = **False** para definir o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] para que ele não altera os nomes de classe.  
  
3.  Definir **Pluralização de nomes** para **Enabled** = **True** para aplicar regras de pluralization os nomes de classe de objetos adicionados ao [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

