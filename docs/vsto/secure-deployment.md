---
title: "Implantação segura | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
ms.assetid: c5ba86b1-e87f-4508-8c5a-1295681a9590
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: cace0c9826a76a4a8341c6b85e1219dcf287e80a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="secure-deployment"></a>Implantação segura
  Quando você cria uma solução do Office, seu computador de desenvolvimento é atualizado automaticamente para permitir que o código em seu projeto para ser executado. No entanto, quando você implanta sua solução, você deve fornecer evidências no qual basear uma decisão de confiança a solução com um certificado de assinatura, ou usando o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chave prompt da relação de confiança. Para obter mais informações, consulte [concedendo confiança a soluções do Office](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Para personalizações no nível do documento, se você implantar o documento em um local de rede, você também deverá adicionar a localização do documento à lista de locais confiáveis na Central de confiabilidade do aplicativo do Office. Para obter mais informações sobre como definir permissões de usuário final computadores, consulte [concedendo confiança a documentos](../vsto/granting-trust-to-documents.md).  
  
## <a name="preventing-office-solutions-from-running-code"></a>Impedindo a execução de código de soluções do Office  
 Os administradores podem usar o registro para impedir que todas as soluções do Office em execução em um computador. Quando uma solução do Office que tem extensões de código gerenciado é aberto, o Visual Studio Tools para verificações de tempo de execução do Office se uma entrada com o nome `Disabled` existe em uma das seguintes chaves de registro no computador:  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 Para impedir a execução de código de soluções do Office, criar um `Disabled` entrada em uma ou ambas as chaves do registro e especifique um dos seguintes tipos de dados e valores para `Disabled`:  
  
-   Um REG_SZ ou REG_EXPAND_SZ é definido como qualquer cadeia de caracteres diferente de "0" (zero).  
  
-   Um REG_DWORD é definida como qualquer valor diferente de 0 (zero).  
  
 Para habilitar soluções do Office executar o código, defina ambos o `Disabled` entradas como 0 (zero), ou excluir as entradas do registro.  
  
## <a name="see-also"></a>Consulte também  
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)   
 [Preparando computadores para executar ou hospedar soluções do Office](http://msdn.microsoft.com/en-us/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Protegendo soluções do Office](../vsto/securing-office-solutions.md)  
  
  