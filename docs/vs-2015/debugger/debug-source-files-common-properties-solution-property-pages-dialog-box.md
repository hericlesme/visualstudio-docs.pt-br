---
title: Caixa de diálogo de páginas de propriedade do código-fonte arquivos, propriedades comuns, solução de depuração | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b94306c44b8a19d1fbf924fe361d317dd911110b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462483"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Caixa de diálogo Depurar Arquivos de Origem, Propriedades Comuns, Páginas de Propriedades da Solução
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [depurar arquivos de origem, propriedades comuns, caixa de diálogo de páginas de propriedades de solução](https://docs.microsoft.com/visualstudio/debugger/debug-source-files-common-properties-solution-property-pages-dialog-box).  
  
Esta página de propriedades especifica onde o depurador procurará arquivos de origem ao depurar a solução.  
  
 Para acessar o **depurar arquivos fonte** página de propriedades, o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **propriedades** no menu de atalho. Expanda o **propriedades comuns** pasta e clique no **depurar arquivos fonte** página.  
  
 **Diretórios que contêm o código-fonte**  
 Contém uma lista de diretórios nos quais o depurador procura arquivos de origem ao depurar a solução. Os subdiretórios dos diretórios especificados também são pesquisados.  
  
 **Não procure esses arquivos de origem**  
 Insira os nomes de todos os arquivos que você não deseja que o depurador leia. Se o depurador encontrar um desses arquivos em um dos diretórios especificados acima, ele o ignorará. Se o **Localizar origem** caixa de diálogo aparece durante a depuração, e você clicar em **Cancelar**, o arquivo que você estava procurando é adicionado a essa lista para que o depurador não continuará a procurar o arquivo.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)



