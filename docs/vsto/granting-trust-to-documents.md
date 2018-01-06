---
title: "Concedendo confiança a documentos | Microsoft Docs"
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
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
ms.assetid: 16893647-501e-4836-98af-a79a1e9de3ee
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 31fd8ba79218c6844e8fc5af33a81ce1c95a8abf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="granting-trust-to-documents"></a>Concedendo confiança a documentos
  Um projeto no nível do documento tem os mesmos requisitos de segurança como projetos no nível de aplicativo: os manifestos com um certificado de assinatura ou clicando em prompt de confiança. Além disso, o documento ou a pasta de trabalho deve estar localizada em um diretório que é designado como um local confiável.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>Locais confiáveis  
 Aplicativos no [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e Office 2010 têm os centros de confiança em que os usuários podem configurar as configurações de segurança e privacidade, como locais confiáveis. Para soluções do Office, o computador local é considerado um local confiável. No entanto, devido a um risco maior, há determinadas pastas que já não são confiáveis, como as pastas temporárias para o sistema, para cada usuário e para o Internet Explorer.  
  
 Para obter mais informações sobre a Central de confiabilidade, consulte [segurança e políticas e configurações no Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202). Para obter mais informações sobre como criar, gerenciar, remover e configurar pastas confiáveis, consulte [configurar locais confiáveis e configurações de editores confiáveis no sistema Office 2007](http://go.microsoft.com/fwlink/?LinkId=89203) e [criar, remover ou alterar um confiável local para os arquivos](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="security-considerations-for-office-solutions"></a>Considerações sobre segurança para soluções do Office  
 Há várias questões de segurança quando você considerar quais pastas adicionar aos locais confiáveis:  
  
-   Pastas locais são consideradas mais seguro e são implicitamente confiáveis. Locais remotos, como compartilhamentos de arquivos devem ser designados como locais confiáveis.  
  
-   Quando você adiciona um diretório a locais confiáveis, essa ação concede confiança total não apenas para soluções do Office, mas também para o código VBA e ActiveX. Por esse motivo, o diretório raiz e Meus documentos pastas não devem ser designadas como confiam.  
  
-   Embora o próprio documento é confiável por meio de locais confiáveis, permissões adicionais são necessárias para a personalização de relação de confiança. Você pode conceder confiança total para a personalização usando os manifestos com um certificado de assinatura, clicando em prompt de confiança ou instalar a solução do Office para o diretório de arquivos de programa.  
  
-   Você pode armazenar o documento ou a pasta de trabalho de uma solução de nível de documento no mesmo diretório que o assembly ou em um diretório diferente. Por exemplo, o documento pode ser localizado em um servidor do SharePoint e o assembly pode estar localizado em um compartilhamento de arquivos de rede. Para obter mais informações, consulte [como: publicar uma solução de nível de documento em um servidor do SharePoint pelo ClickOnce usando](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## <a name="see-also"></a>Consulte também  
 [Concedendo confiança a soluções do Office](../vsto/granting-trust-to-office-solutions.md)   
 [Solucionando problemas de segurança de solução do Office](../vsto/troubleshooting-office-solution-security.md)   
 [Protegendo soluções do Office](../vsto/securing-office-solutions.md)  
  
  