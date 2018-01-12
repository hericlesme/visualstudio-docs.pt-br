---
title: "Como: assinar soluções do Office | Microsoft Docs"
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
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2883f75c6ca75e1875621f9c6779db09722d6945
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-sign-office-solutions"></a>Como assinar soluções do Office
  Se você assinar uma solução, você pode conceder confiança para a solução usando o certificado como evidência. Você pode usar o mesmo certificado para várias soluções e todas as soluções serão confiáveis sem atualizações de política de segurança adicional.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Se você editar manualmente o aplicativo e manifestos de implantação usando a ferramenta de edição (mage.exe e mageui.exe) e geração de manifesto, deve assinar os manifestos novamente antes de você pode usá-los. Para obter mais informações, consulte [como: assinar novamente os manifestos de aplicativo e implantação](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="signing-by-using-a-certificate"></a>Usando um certificado de assinatura  
 Um certificado é um arquivo que contém uma chave exclusiva e a identidade do publicador de solução. Você pode comprar certificados de autoridade de certificação, ou criar seu próprio certificado e ter uma autoridade de certificação assiná-lo.  
  
 O Visual Studio assina soluções do Office com um certificado temporário para habilitar a depuração. Você não deve usar o certificado temporário em soluções implantadas como evidência.  
  
#### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Assinar uma solução do Office usando um certificado  
  
1.  Sobre o **projeto** menu, clique em *SolutionName***propriedades**.  
  
2.  Clique na guia **Assinatura**.  
  
3.  Selecione **assinar os manifestos ClickOnce**.  
  
4.  Localize o certificado clicando **selecionar no armazenamento de** ou **Selecione arquivo** e navegar para o certificado.  
  
5.  Para verificar se o certificado correto está sendo usado, clique em **mais detalhes** para exibir as informações do certificado.  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo soluções do Office](../vsto/securing-office-solutions.md)   
 [Concedendo confiança a soluções do Office](../vsto/granting-trust-to-office-solutions.md)   
 [Página de Assinatura, Designer de Projeto](/visualstudio/ide/reference/signing-page-project-designer)  
  
  