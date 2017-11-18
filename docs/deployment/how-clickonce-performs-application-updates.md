---
title: "Como o ClickOnce executa atualizações de aplicativos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 32e0b56ab5d4507c971948b98c8f7660650e70cc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-clickonce-performs-application-updates"></a>Como o ClickOnce executa atualizações de aplicativos
ClickOnce usa as informações de versão do arquivo especificadas no manifesto de implantação do aplicativo para decidir se deseja atualizar os arquivos do aplicativo. Depois que uma atualização começa, o ClickOnce usa uma técnica chamada *patch de arquivo* para evitar o download redundante dos arquivos de aplicativo.  
  
## <a name="file-patching"></a>Patch de arquivo  
 Ao atualizar um aplicativo, ClickOnce não baixará todos os arquivos para a nova versão do aplicativo, a menos que os arquivos foram alterados. Em vez disso, ele compara as assinaturas de hash dos arquivos especificados no manifesto do aplicativo para o aplicativo atual em relação as assinaturas no manifesto para a nova versão. Se as assinaturas de um arquivo forem diferentes, o ClickOnce baixa a nova versão. Se as assinaturas forem correspondentes, o arquivo não foi alterado de uma versão para a próxima. Nesse caso, o ClickOnce copia o arquivo existente e utiliza a nova versão do aplicativo. Essa abordagem impede que o ClickOnce precisar baixar todo o aplicativo novamente, mesmo que apenas um ou dois arquivos foram alterados.  
  
 Patch de arquivo também funciona para assemblies que são baixados sob demanda usando o <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> e <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> métodos.  
  
 Se você usar o Visual Studio para compilar o aplicativo, ele irá gerar novas assinaturas de hash para todos os arquivos sempre que você recompile o projeto inteiro. Nesse caso, todos os assemblies serão baixados para o cliente, embora apenas alguns assemblies podem ter sido alterado.  
  
 Patch de arquivo não funciona para arquivos que são marcados como dados e armazenados no diretório de dados. Estes são sempre baixadas, independentemente de assinatura de hash do arquivo. Para obter mais informações sobre o diretório de dados, consulte [acesso Local e remoto de dados em aplicativos ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Consulte também  
 [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)