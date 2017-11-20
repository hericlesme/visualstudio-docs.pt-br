---
title: 'Passo a passo: Criando um instalador personalizado para um aplicativo ClickOnce | Microsoft Docs'
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
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: "34"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 3b6a7069b520c1c4834ee3ca1a5824660803a665
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>Instruções passo a passo: criando um instalador personalizado para um aplicativo ClickOnce
Qualquer aplicativo ClickOnce com base em um arquivo .exe pode ser instalado e atualizado por um instalador personalizado silenciosamente. Um instalador personalizado pode implementar a experiência do usuário personalizada durante a instalação, incluindo caixas de diálogo personalizadas para operações de segurança e manutenção. Para executar operações de instalação, o instalador personalizado usa o <xref:System.Deployment.Application.InPlaceHostingManager> classe. Este passo a passo demonstra como criar um instalador personalizado que instala silenciosamente um aplicativo ClickOnce.  
  
## <a name="prerequisites"></a>Pré-requisitos  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>Para criar um instalador de aplicativo personalizado do ClickOnce  
  
1.  Em seu aplicativo ClickOnce, adicione referências ao deployment e System.  
  
2.  Adicionar uma nova classe ao seu aplicativo e especificar qualquer nome. Este passo a passo usa o nome `MyInstaller`.  
  
3.  Adicione o seguinte `Imports` ou `using` instruções na parte superior da sua nova classe.  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Adicione os seguintes métodos para sua classe.  
  
     Chamam esses métodos <xref:System.Deployment.Application.InPlaceHostingManager> métodos para baixar o manifesto de implantação, declare as permissões apropriadas, solicitará ao usuário permissão para instalar e, em seguida, baixar e instalar o aplicativo para o cache do ClickOnce. Um instalador personalizado pode especificar que um aplicativo ClickOnce previamente confiável, ou pode adiar a decisão de confiança para o <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> chamada de método. Esse código previamente confia no aplicativo.  
  
    > [!NOTE]
    >  Permissões atribuídas pelo previamente confiável não podem exceder as permissões do código do instalador personalizado.  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  Para tentar a instalação do seu código, chame o `InstallApplication` método. Por exemplo, se você nomeou sua classe `MyInstaller`, você pode chamar `InstallApplication` da seguinte maneira.  
  
    ```vb  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```csharp  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
    ```  
  
## <a name="next-steps"></a>Próximas etapas  
 Um aplicativo ClickOnce também pode adicionar lógica de atualização personalizada, incluindo uma interface de usuário personalizada para mostrar durante o processo de atualização. Para obter mais informações, consulte <xref:System.Deployment.Application.UpdateCheckInfo>. Um aplicativo ClickOnce também pode suprimir a entrada de menu de início padrão, o atalho e a entrada de adicionar ou remover programas usando um `<customUX>` elemento. Para obter mais informações, consulte [ \<entryPoint > elemento](../deployment/entrypoint-element-clickonce-application.md) e <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint > elemento](../deployment/entrypoint-element-clickonce-application.md)