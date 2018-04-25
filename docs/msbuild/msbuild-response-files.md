---
title: Arquivos de resposta do MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f685364bbcf69b8d4b91635cb42079f3f06e5311
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
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