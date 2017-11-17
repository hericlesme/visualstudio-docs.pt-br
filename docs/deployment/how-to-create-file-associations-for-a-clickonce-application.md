---
title: "Como: criar associações de arquivos para um aplicativo ClickOnce | Microsoft Docs"
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
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: "7"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 491de73e97bf44ea54d5ccdfb604924ff26c9530
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Como criar associações de arquivo para um aplicativo ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplicativos podem ser associados uma ou mais extensões de nome de arquivo, para que o aplicativo será iniciado automaticamente quando o usuário abre um arquivo desses tipos. Adicionando suporte à extensão de nome do arquivo para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é simples.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Para criar associações de arquivo para um aplicativo ClickOnce  
  
1.  Criar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo normalmente, ou use existente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
2.  Abra o manifesto do aplicativo com um editor de texto ou XML, como o bloco de notas.  
  
3.  Encontre o elemento `assembly`. Para obter mais informações, consulte [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md) (Manifesto do aplicativo ClickOnce).  
  
4.  Como um filho de `assembly` elemento, adicionar um `fileAssociation` elemento. O `fileAssociation` elemento tem quatro atributos:  
  
    -   `extension`: A extensão de nome de arquivo que você deseja associar o aplicativo.  
  
    -   `description`: Uma descrição do tipo de arquivo, que será exibido no shell do Windows.  
  
    -   `progid`: Uma cadeia de caracteres que identifica exclusivamente o tipo de arquivo, para marcá-la no registro.  
  
    -   `defaultIcon`: Um ícone a ser usado para este tipo de arquivo. O ícone deve ser adicionado como um recurso de arquivo no manifesto do aplicativo. Para obter mais informações, consulte [Como incluir um arquivo de dados em um aplicativo ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Para obter um exemplo de `file` e `fileAssociation` elementos, consulte [ \<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Se você deseja associar mais de um tipo de arquivo com o aplicativo, adicione adicionais `fileAssociation` elementos. Observe que o `progid` atributo deve ser diferente para cada um.  
  
6.  Depois de terminar com o manifesto do aplicativo, assinar novamente o manifesto. Você pode fazer isso na linha de comando usando Mage.exe.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Para obter mais informações, consulte [Mage.exe (ferramenta de edição e geração de manifesto)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>Consulte também  
 [\<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)