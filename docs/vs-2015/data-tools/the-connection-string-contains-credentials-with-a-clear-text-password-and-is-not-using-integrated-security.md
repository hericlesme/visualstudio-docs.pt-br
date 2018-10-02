---
title: A cadeia de caracteres de conexão contém credenciais com uma senha de texto não criptografado e não está usando segurança integrada | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6d1be15ffdc204512c3034662b6ca24955869f5c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464516"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>A cadeia de conexão contém credenciais com uma senha de texto não criptografado e não estiver usando segurança integrada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [a cadeia de caracteres de conexão contém credenciais com uma senha de texto não criptografado e não está usando segurança integrada](https://docs.microsoft.com/visualstudio/data-tools/the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security).  
  
  
Deseja salvar a cadeia de conexão no arquivo DBML atual e nos arquivos de configuração do aplicativo com essas informações confidenciais?  Clique em Não para salvar a cadeia de conexão sem as informações confidenciais.  
  
 Ao trabalhar com conexões de dados que incluem informações confidenciais (senhas que são incluídas na cadeia de conexão), você tem a opção de salvar a cadeia de conexão no arquivo DBML de um projeto e o arquivo de configuração do aplicativo com ou sem informações sigilosas.  
  
> [!WARNING]
>  Definir explicitamente o **Conexão** propriedades **configurações do aplicativo** propriedade a ser **False** adicionará a senha para o arquivo DBML.  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Para salvar a cadeia de conexão com informações sigilosas nas configurações de aplicativo do projeto  
  
-   Clique em **Sim**.  
  
     A cadeia de conexão é armazenada como uma configuração de aplicativo. A cadeia de conexão inclui informações sigilosas em texto sem formatação. O arquivo DBML não contém informações sigilosas.  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Para salvar a cadeia de conexão sem informações sigilosas nas configurações de aplicativo do projeto  
  
-   Clique em **Não**.  
  
     A cadeia de conexão é armazenada como uma configuração de aplicativo, mas a senha não é incluído.  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

