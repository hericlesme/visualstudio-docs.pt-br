---
title: Arquivos .Targets do WPF | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- combining tasks into a .targets file to build an MSBuild project [WPF MSBuild]
- WPF .targets files [WPF MSBuild], introduction
- WPF .targets files [WPF MSBuild]
ms.assetid: e85a3ff4-dedd-4ff4-9b22-3a1e94755362
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6f1fbf6f4a5e1cc0c49b6d7ad7513d17eb07b3c2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="wpf-targets-files"></a>Arquivos .targets do WPF
[!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)] estende o [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] adicionando um conjunto de tarefas específicas do [!INCLUDE[TLA2#tla_wpf](../msbuild/includes/tla2sharptla_wpf_md.md)] que são combinadas em um arquivo .targets especial, o **Microsoft.WinFX.targets**. Esse arquivo combina o conjunto de tarefas [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] necessárias para compilar um projeto [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] no [!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Arquivos .Targets](../msbuild/msbuild-dot-targets-files.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Como compilar um aplicativo WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)