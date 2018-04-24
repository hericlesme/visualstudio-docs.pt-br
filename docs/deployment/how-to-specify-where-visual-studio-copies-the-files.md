---
title: 'Como: especificar onde o Visual Studio copia os arquivos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b4e626253d9d07a9f263304d02739bdb3f4b012
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Como especificar onde o Visual Studio copiará os arquivos
Quando você publicar um aplicativo usando o ClickOnce, o `Publish Location` propriedade especifica o local onde os arquivos de aplicativo e manifesto são colocados. Isso pode ser um caminho de arquivo ou o caminho para um servidor FTP.  
  
 Você pode especificar o `Publish Location` propriedade o **publicar** página do **Project Designer**, ou usando o Assistente de publicação. Para obter mais informações, consulte [como: publicar um aplicativo ClickOnce usando o Assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Ao instalar mais de uma versão de um aplicativo usando o ClickOnce, a instalação moverá as versões anteriores do aplicativo para uma pasta chamada Arquivo, no local de publicação especificado. O arquivamento de versões anteriores dessa maneira mantém o diretório de instalação livre de pastas da versão anterior.  
  
### <a name="to-specify-a-publishing-location"></a>Para especificar um local de publicação  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  No **local publicar** , digite o local de publicação usando um dos seguintes formatos:  
  
    -   Para publicar em um caminho de disco ou compartilhamento de arquivo, insira o caminho usando um caminho UNC (\\\Server\ApplicationName) ou um caminho de arquivo (C:\Deploy\ApplicationName).  
  
    -   Para publicar em um servidor de FTP, insira o caminho usando o formato ftp://ftp.microsoft.com/ApplicationName.  
  
     Observe que o texto deve estar presente no **local de publicação** caixa para que o botão Procurar (**...** ) botão trabalhar.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)