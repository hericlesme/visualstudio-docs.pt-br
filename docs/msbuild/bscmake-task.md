---
title: Tarefa BscMake | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2308e1efecf01972dd494ce7ad4341e8e5d6d20e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="bscmake-task"></a>Tarefa BscMake
> [!IMPORTANT]
>  O bscmake não é usado pelo IDE do Visual Studio. Desde o Visual Studio 2008, as informações de procura são armazenadas automaticamente em um arquivo .sdf na pasta da solução.  
  
 Encapsula a ferramenta do Utilitário de Manutenção de Informações de Procura da Microsoft (bscmake.exe).  A ferramenta bscmake.exe cria um arquivo de informações de procura (.bsc) dos arquivos do navegador de origem (.sbr) que são criados durante o build. Use o **Pesquisador de Objetos** para exibir um arquivo .bsc. Para obter mais informações, consulte [referência BSCMAKE](/cpp/build/reference/bscmake-reference).  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa **BscMake**. A maioria dos parâmetros de tarefa corresponde a uma opção de linha de comando.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|**AdditionalOptions**|Parâmetro **String** opcional.<br /><br /> Uma lista de opções, conforme especificado na linha de comando. Por exemplo, "/*option1* /*option2* /*option#*". Use esse parâmetro para especificar opções não representadas por nenhum outro parâmetro da tarefa **BscMake**.<br /><br /> Para obter mais informações, consulte as opções em [Opções BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**OutputFile**|Parâmetro **String** opcional.<br /><br /> Especifica um nome de arquivo que substitui o nome de arquivo de saída padrão.<br /><br /> Para obter mais informações, consulte a opção **/o** em [Opções BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**PreserveSBR**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, ele forçará um build não incremental. Um build completo não incremental ocorre independentemente de existir um arquivo .bsc e impede que arquivos .sbr sejam truncados.<br /><br /> Para obter mais informações, consulte a opção **/n** em [Opções BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**Sources**|Parâmetro opcional **ITaskItem[]**.<br /><br /> Define uma matriz de itens de arquivo de origem do MSBuild que pode ser consumida e emitida por tarefas.|  
|**SuppressStartupBanner**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.<br /><br /> Para obter mais informações, consulte a opção **/NOLOGO** em [Opções BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**TrackerLogDirectory**|Parâmetro **String** opcional.<br /><br /> Especifica o diretório do log de rastreamento.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)