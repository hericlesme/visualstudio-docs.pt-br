---
title: Implantação segura
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47cecda571a6826c2d7e845945c05d0264971134
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693325"
---
# <a name="secure-deployment"></a>Implantação segura
  Quando você cria uma solução do Office, seu computador de desenvolvimento é atualizado automaticamente para permitir que o código em seu projeto para ser executado. No entanto, quando você implanta sua solução, você deve fornecer evidências no qual basear uma decisão de confiança a solução com um certificado de assinatura, ou usando o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chave prompt da relação de confiança. Para obter mais informações, consulte [conceder confiança a soluções do Office](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Para personalizações no nível do documento, se você implantar o documento em um local de rede, você também deverá adicionar a localização do documento à lista de locais confiáveis na Central de confiabilidade do aplicativo do Office. Para obter mais informações sobre como definir permissões de usuário final computadores, consulte [conceder confiança a documentos](../vsto/granting-trust-to-documents.md).  
  
## <a name="prevent-office-solutions-from-running-code"></a>Impedir a execução de código de soluções do Office  
 Os administradores podem usar o registro para impedir que todas as soluções do Office em execução em um computador. Quando uma solução do Office que tem extensões de código gerenciado é aberto, o Visual Studio Tools para verificações de tempo de execução do Office se uma entrada com o nome `Disabled` existe em uma das seguintes chaves de registro no computador:  
  
-   **HKEY_CURRENT_USER\Software\Microsoft\VSTO**  
  
-   **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**  
  
 Para impedir a execução de código de soluções do Office, criar um `Disabled` entrada em uma ou ambas as chaves do registro e especifique um dos seguintes tipos de dados e valores para `Disabled`:  
  
-   Um REG_SZ ou REG_EXPAND_SZ é definido como qualquer cadeia de caracteres diferente de "0" (zero).  
  
-   Um REG_DWORD é definida como qualquer valor diferente de 0 (zero).  
  
 Para habilitar soluções do Office executar o código, defina ambos o `Disabled` entradas como 0 (zero), ou excluir as entradas do registro.  
  
## <a name="see-also"></a>Consulte também  
 [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)   
 [Preparar os computadores para executar ou hospedar soluções do Office](http://msdn.microsoft.com/en-us/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Proteger as soluções do Office](../vsto/securing-office-solutions.md)  
  
  