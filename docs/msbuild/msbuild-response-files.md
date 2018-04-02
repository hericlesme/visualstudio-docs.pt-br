---
title: Arquivos de resposta do MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 3
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 40a9f7b6e1456c511e70937ac6a1cff23dad30d0
ms.sourcegitcommit: a80e7ef2f0a0f6d906a44f4d696aeb208bc1ad70
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2018
---
# <a name="msbuild-response-files"></a>Arquivos de resposta do MSBuild
Arquivos de resposta (.rsp) são arquivos de texto que contêm as opções de linha de comando MSBuild.exe. Cada opção pode estar em uma linha separada ou todas as opções podem estar em uma linha. As linhas de comentários são precedidas por um símbolo **#**. A opção **@** é usada para passar a outro arquivo de resposta para o MSBuild.exe.  
  
## <a name="msbuildrsp"></a>MSBuild.rsp
O arquivo de resposta automática é um arquivo .rsp especial que o MSBuild.exe usa automaticamente ao criar um projeto. Esse arquivo, o MSBuild.rsp, deve estar no mesmo diretório que MSBuild.exe, caso contrário, ele não será localizado. Você pode editar esse arquivo para especificar opções de linha de comando padrão para MSBuild.exe. Por exemplo, caso use o mesmo agente de log sempre que compilar um projeto, você pode adicionar a opção **/logger** para MSBuild.rsp, e o MSBuild.exe usará o agente de log sempre que um projeto for compilado.  

## <a name="directorybuildrsp"></a>Directory.Build.rsp
Na versão 15.6 e superiores, MSBuild pesquisará nos diretórios pai do projeto um arquivo chamado `Directory.Build.rsp`.  Isso pode ser útil em um repositório de código-fonte para fornecer argumentos padrão durante os builds de linha de comando.  Também pode ser usado para especificar os argumentos de linha de comando de builds hospedados.

## <a name="see-also"></a>Consulte também  
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)