---
title: "Segurança para soluções do SharePoint | Microsoft Docs"
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
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 22ef16c40fb2d70ae7e1b835860b74843abe57d3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="security-for-sharepoint-solutions"></a>Segurança das soluções do SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]incorpora os seguintes recursos para ajudar a melhorar a segurança de aplicativos do SharePoint.  
  
## <a name="safe-control-entries"></a>Entradas de controle de segurança  
 Cada item de projeto do SharePoint criado na [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tem um **entradas de controle de segurança** coleção de controles de propriedade que representa um cofre. Seu **seguro** subpropriedade permite que você especifique os controles que você considerar seguros. Para obter mais informações, consulte [fornecendo empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) e [especificando seguro Web Parts](http://go.microsoft.com/fwlink/?LinkId=177521).  
  
## <a name="allowpartiallytrustedcallers-attribute"></a>Atributo AllowPartiallyTrustedCallers  
 Por padrão, somente aplicativos que são totalmente confiáveis pelo sistema de CAS (segurança) de acesso de código de tempo de execução podem acessar um assembly de código gerenciado compartilhado. Marcar um assembly totalmente confiável com o atributo AllowPartiallyTrustedCallers permite parcialmente confiáveis assemblies para acessá-lo.  
  
 O atributo AllowPartiallyTrustedCallers é adicionado a qualquer solução do SharePoint que não está implantada para o cache de assembly global do sistema ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Isso inclui soluções em modo seguro ou soluções implantadas para o diretório de Bin do aplicativo do SharePoint. Para obter mais informações, consulte [versão 1 alterações de segurança para o Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) e [implantação de Web Parts do SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
## <a name="safe-against-script-property"></a>Segurança em relação a propriedade de Script  
 *Injeção de script* é a inserção de códigos possivelmente mal-intencionados em controles ou páginas da Web. Para ajudar a proteger contra injeção de script de sites do SharePoint 2010, colaboradores não é possível exibir ou editar suas propriedades ou Web parts por padrão. Esse comportamento é controlado por um atributo SafeControl chamado SafeAgainstScript. Em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], defina este atributo em um item de projeto **entradas de controle de segurança** subpropriedade **seguro contra Script**. Para obter mais informações, consulte [fornecendo empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) e [como: marcar controles como controles seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md).  
  
## <a name="vista-and-windows-7-user-account-control"></a>Controle de conta de usuário 7 Vista e Windows  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporar um recurso de segurança, conhecido como controle de conta de usuário (UAC). Para desenvolver soluções do SharePoint na [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] sistemas, o UAC exige que você execute [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como um administrador do sistema. Do **iniciar** menu, abra o menu de atalho para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]e, em seguida, escolha **executar como administrador**.  
  
 Para configurar o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] atalho para sempre executar como administrador, abra o menu de atalho, escolha **propriedades**, escolha o **avançado** no botão de **propriedades**caixa de diálogo e, em seguida, selecione o **executar como administrador** caixa de seleção.  
  
 Para obter mais informações, consulte [Noções básicas e configurando o controle de conta de usuário no Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). e [controle de conta de usuário do Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## <a name="sharepoint-permissions-considerations"></a>Considerações das Permissões do SharePoint  
 Para desenvolver soluções do SharePoint, você deve ter permissões suficientes para executar e depurar soluções do SharePoint. Antes de você pode testar uma solução do SharePoint, execute as etapas a seguir para garantir que você tenha as permissões necessárias:  
  
1.  Adicione sua conta de usuário como um administrador do sistema.  
  
2.  Adicione sua conta de usuário como um administrador de Farm do SharePoint server.  
  
    1.  Na Administração Central do SharePoint 2010, escolha o **gerenciar o grupo de administradores de farm** link.  
  
    2.  No **os administradores de Farm** página, escolha o **novo** opção de menu  
  
3.  Adicione sua conta de usuário para ao grupo WSS_ADMIN_WPG.  
  
## <a name="additional-security-resources"></a>Recursos de segurança adicionais  
 Para obter mais informações sobre problemas de segurança, consulte o seguinte.  
  
### <a name="visual-studio-security"></a>Segurança do Visual Studio  
  
-   [Segurança e permissões de usuário](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [Segurança em código nativo e código do .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [Segurança no .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### <a name="sharepoint-security"></a>Segurança do SharePoint  
  
-   [Segurança e administração do Microsoft SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [Central de recursos de segurança do SharePoint](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [Protegendo as Web Parts do SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [Melhorar a segurança aplicativo Web: Ameaças e contramedidas](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### <a name="general-security"></a>Segurança geral  
  
-   [O ciclo de vida de desenvolvimento de segurança MSDN](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [Criando aplicativos do ASP.NET seguros: Autenticação, autorização e comunicação segura](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  