---
title: 'Como: especificar onde o Visual Studio copiará os arquivos | Microsoft Docs'
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
ms.openlocfilehash: 2b2a4d642bc551127f34fe7a64ec01665b7ace70
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078622"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Como: especificar onde o Visual Studio copiará os arquivos
Quando você publica um aplicativo usando o ClickOnce, o `Publish Location` propriedade especifica o local onde os arquivos de aplicativo e manifesto são colocados. Isso pode ser um caminho de arquivo ou o caminho para um servidor FTP.  
  
 Você pode especificar o `Publish Location` propriedade no **Publish** página da **Designer de projeto**, ou usando o Assistente de publicação. Para obter mais informações, consulte [como: publicar um aplicativo ClickOnce usando o Assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Ao instalar mais de uma versão de um aplicativo usando o ClickOnce, a instalação moverá as versões anteriores do aplicativo para uma pasta chamada Arquivo, no local de publicação especificado. O arquivamento de versões anteriores dessa maneira mantém o diretório de instalação livre de pastas da versão anterior.  
  
### <a name="to-specify-a-publishing-location"></a>Para especificar um local de publicação  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  No **local de publicação** , insira o local de publicação usando um dos seguintes formatos:  
  
    -   Para publicar em um caminho de disco ou compartilhamento de arquivo, insira o caminho usando um caminho UNC (*\\\Server\ApplicationName*) ou um caminho de arquivo (*C:\Deploy\ApplicationName*).  
  
    -   Para publicar em um servidor FTP, insira o caminho usando o formato *ftp://ftp.microsoft.com/\<ApplicationName >*.  
  
     Observe que o texto deve estar presente na **local de publicação** caixa para que o botão Procurar (**...** ) botão funcione.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como: publicar um aplicativo ClickOnce usando o Assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)