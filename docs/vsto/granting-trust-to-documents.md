---
title: Conceder confiança a documentos
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f95887d5d540fd1acd95b8af1275c4b4054c8764
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2018
---
# <a name="grant-trust-to-documents"></a>Conceder confiança a documentos
  Um projeto no nível do documento tem os mesmos requisitos de segurança como projetos no nível de aplicativo: os manifestos com um certificado de assinatura ou clicando em prompt de confiança. Além disso, o documento ou a pasta de trabalho deve estar localizada em um diretório que é designado como um local confiável.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>Locais confiáveis  
 Aplicativos no [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e Office 2010 têm os centros de confiança em que os usuários podem configurar as configurações de segurança e privacidade, como locais confiáveis. Para soluções do Office, o computador local é considerado um local confiável. No entanto, devido a um risco maior, há determinadas pastas que já não são confiáveis, como as pastas temporárias para o sistema, para cada usuário e para o Internet Explorer.  
  
 Para obter mais informações sobre a Central de confiabilidade, consulte [segurança e políticas e configurações no Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202). Para obter mais informações sobre como criar, gerenciar, remover e configurar pastas confiáveis, consulte [configurar locais confiáveis e configurações de editores confiáveis no sistema Office 2007](http://go.microsoft.com/fwlink/?LinkId=89203) e [criar, remover ou alterar um confiável local para os arquivos](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="security-considerations-for-office-solutions"></a>Considerações sobre segurança para soluções do Office  
 Há várias questões de segurança quando você considerar quais pastas adicionar aos locais confiáveis:  
  
-   Pastas locais são consideradas mais seguro e são implicitamente confiáveis. Locais remotos, como compartilhamentos de arquivos devem ser designados como locais confiáveis.  
  
-   Quando você adiciona um diretório a locais confiáveis, essa ação concede confiança total não apenas para soluções do Office, mas também para o código VBA e ActiveX. Por esse motivo, o diretório raiz e o *Meus documentos* pastas não devem ser designadas como confiáveis.  
  
-   Embora o próprio documento é confiável por meio de locais confiáveis, permissões adicionais são necessárias para a personalização de relação de confiança. Você pode conceder confiança total para a personalização usando os manifestos com um certificado de assinatura, clicando em prompt de confiança ou instalar a solução do Office para o *arquivos de programa* directory.  
  
-   Você pode armazenar o documento ou a pasta de trabalho de uma solução de nível de documento no mesmo diretório que o assembly ou em um diretório diferente. Por exemplo, o documento pode ser localizado em um servidor do SharePoint e o assembly pode estar localizado em um compartilhamento de arquivos de rede. Para obter mais informações, consulte [como: publicar uma solução de nível de documento em um servidor do SharePoint usando o ClickOnce](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## <a name="see-also"></a>Consulte também  
 [Relação de confiança de concessão para soluções do Office](../vsto/granting-trust-to-office-solutions.md)   
 [Solucionar problemas de segurança de solução do Office](../vsto/troubleshooting-office-solution-security.md)   
 [Proteger as soluções do Office](../vsto/securing-office-solutions.md)  
  
  