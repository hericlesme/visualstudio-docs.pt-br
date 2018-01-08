---
title: "Caixa de diálogo de páginas de propriedade do origem arquivos, propriedades comuns, solução de depuração | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: aa83025b15fe3773220a2b27394890318d60c850
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2018
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Caixa de diálogo Depurar Arquivos de Origem, Propriedades Comuns, Páginas de Propriedades da Solução
Esta página de propriedades especifica onde o depurador procurará arquivos de origem ao depurar a solução.  
  
 Para acessar o **depurar arquivos de origem** página de propriedades, clique com botão direito em sua solução em **Solution Explorer** e selecione **propriedades** no menu de atalho. Expanda o **propriedades comuns** pasta e clique no **depurar arquivos de origem** página.  
  
 **Diretórios que contêm o código-fonte**  
 Contém uma lista de diretórios nos quais o depurador procura arquivos de origem ao depurar a solução. Os subdiretórios dos diretórios especificados também são pesquisados.  
  
 **Não procure esses arquivos de origem**  
 Insira os nomes de todos os arquivos que você não deseja que o depurador leia. Se o depurador encontrar um desses arquivos em um dos diretórios especificados acima, ele o ignorará. Se o **Localizar origem** caixa de diálogo é exibida enquanto você está depurando e clicar em **Cancelar**, o arquivo que você estava procurando é adicionado a essa lista para que o depurador não continuará a pesquisa do arquivo.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)