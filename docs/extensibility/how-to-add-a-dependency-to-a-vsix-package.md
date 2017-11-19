---
title: "Como: adicionar uma dependência a um pacote do VSIX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3f3b54e19d8418f35a733b73ea0616b53bd42ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Como: adicionar uma dependência a um pacote do VSIX
Você pode configurar uma implantação de pacote VSIX que instala todas as dependências que não ainda estão presentes no computador de destino. Para fazer isso, inclua as dependências do VSIX para o arquivo source.extension.vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Para adicionar uma dependência  
  
1.  Abra o arquivo source.extension.vsixmanifest no **Design** exibição. Vá para o **dependências** guia e clique em **novo**.  
  
2.  Para adicionar uma extensão instalada: no **adicionar nova dependência** caixa de diálogo, selecione **extensão instalada** e, em seguida, para o **nome**, selecione uma extensão na lista.  
  
3.  Para adicionar outro VSIX que não está instalado:: no **adicionar nova dependência** caixa de diálogo, selecione **arquivo no sistema de arquivos** e, em seguida, use o **procurar** para selecionar o VSIX.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema 1.0 de extensão do VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparar extensões para a implantação do Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)