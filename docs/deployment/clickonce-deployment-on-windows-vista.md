---
title: A implantação do ClickOnce no Windows Vista | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c546d7e4287fc47a3770baa306a43a1631be2f06
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31558926"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Implantação do ClickOnce no Windows Vista
Criando aplicativos no Visual Studio para controle de conta de usuário (UAC) no Windows Vista normalmente gera um manifesto inserido, como dados binários codificados XML no arquivo executável do aplicativo. Como aplicativos ClickOnce e COM sem registro exigem um manifesto externo, o Visual Studio gera um arquivo para esses tipos de projetos que contêm os dados UAC em vez de um manifesto inserido. Por padrão, o Visual Studio usa informações de um arquivo chamado App. manifest para gerar informações de manifesto de UAC externo (para implantação do ClickOnce e COM sem registro), ou para incorporá-lo no arquivo executável do aplicativo (para todos os outros casos). O Visual Studio fornece as seguintes opções de geração de manifesto:  
  
-   Use um manifesto inserido. Inserir dados UAC no arquivo executável do aplicativo e executar como usuário normal.  
  
     Essa é a configuração padrão (a menos que você usa o ClickOnce). Essa configuração oferecerá suporte da maneira normal, em que o Visual Studio funciona no Windows Vista; ou seja, a geração de um manifesto interno e externo, ambos usando `AsInvoker`.  
  
-   Use um manifesto externo. Gere um manifesto externo usando o App. manifest.  
  
     Isso gera somente o manifesto externo usando as informações no App. manifest. Quando você publicar um aplicativo usando o ClickOnce ou COM sem registro, o Visual Studio adiciona App para o projeto e essa opção.  
  
-   Não use nenhum manifesto. Crie o aplicativo sem um manifesto.  
  
     Essa abordagem também é conhecido como *virtualização*. Use esta opção para compatibilidade com aplicativos existentes de versões anteriores do Visual Studio.  
  
 As novas propriedades estão disponíveis no **aplicativo** página no Designer de projeto (Visual c# somente para projetos) e no formato de arquivo de projeto MSBuild.  
  
 Observe que o método para configurar a geração de manifesto UAC no IDE do Visual Studio é diferente dependendo do tipo de projeto (Visual c# e Visual Basic).  
  
 Para obter informações sobre como configurar projetos do Visual c# para geração de manifesto, consulte [página de aplicativo, Designer de projeto (c#)](../ide/reference/application-page-project-designer-csharp.md).  
  
 Para obter informações sobre como configurar projetos do Visual Basic para geração de manifesto, consulte [página de aplicativo, Designer de projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Consulte também  
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Permissões de usuário e o Visual Studio](http://msdn.microsoft.com/en-us/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Página Aplicativo, Designer de Projeto (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Página de Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)