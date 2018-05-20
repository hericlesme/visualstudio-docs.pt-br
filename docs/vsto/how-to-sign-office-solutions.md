---
title: 'Como: assinar soluções do Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d5fa4a837de66a39502e2c9e2d8466f3998acc4d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-sign-office-solutions"></a>Como: assinar soluções do Office
  Se você assinar uma solução, você pode conceder confiança para a solução usando o certificado como evidência. Você pode usar o mesmo certificado para várias soluções e todas as soluções serão confiáveis sem atualizações de política de segurança adicional.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Se você editar manualmente o aplicativo e manifestos de implantação usando a ferramenta de edição e geração de manifesto (*mage.exe* e *mageui.exe*), você deve assinar novamente os manifestos antes que você pode usá-los. Para obter mais informações, consulte [como: assinar novamente os manifestos de aplicativo e implantação](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="sign-by-using-a-certificate"></a>Entre usando um certificado  
 Um certificado é um arquivo que contém uma chave exclusiva e a identidade do publicador de solução. Você pode comprar certificados de autoridade de certificação, ou criar seu próprio certificado e ter uma autoridade de certificação assiná-lo.  
  
 O Visual Studio assina soluções do Office com um certificado temporário para habilitar a depuração. Você não deve usar o certificado temporário em soluções implantadas como evidência.  
  
### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Assinar uma solução do Office usando um certificado  
  
1.  Sobre o **projeto** menu, clique em * SolutionName ***propriedades**.  
  
2.  Clique na guia **Assinatura**.  
  
3.  Selecione **assinar os manifestos ClickOnce**.  
  
4.  Localize o certificado clicando **selecionar no armazenamento de** ou **Selecione arquivo** e navegar para o certificado.  
  
5.  Para verificar se o certificado correto está sendo usado, clique em **mais detalhes** para exibir as informações do certificado.  
  
## <a name="see-also"></a>Consulte também  
 [Proteger as soluções do Office](../vsto/securing-office-solutions.md)   
 [Relação de confiança de concessão para soluções do Office](../vsto/granting-trust-to-office-solutions.md)   
 [Página de Assinatura, Designer de Projeto](/visualstudio/ide/reference/signing-page-project-designer)  
  
  