---
title: "Atualizando e Migrando soluções do Office | Microsoft Docs"
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
- Office applications [Office development in Visual Studio], upgrading
- Office projects [Office development in Visual Studio], upgrading
- upgrading applications [Office development in Visual Studio]
- upgrading Office solutions in Visual Studio
- migrating Office solutions in Visual Studio
ms.assetid: cc60cdcb-593d-498a-8358-f1f3ac673fe1
caps.latest.revision: "105"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8189032a38aba69b63cb96f824c973b0d41a1aad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="upgrading-and-migrating-office-solutions"></a>Atualizando e migrando soluções do Office
  Se você tiver um projeto do Microsoft Office que foi criado em uma versão anterior do Visual Studio, você deve atualizar o projeto para usá-lo nas versões atuais do Visual Studio. Para atualizar um projeto do Microsoft Office, abra-o em uma versão do Visual Studio que inclui o Microsoft Office developer tools. Para obter mais informações sobre as versões do Visual Studio que incluem o Microsoft Office developer tools, consulte [Configurando um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
> [!NOTE]  
>  Interessado em desenvolvimento de soluções que estendem a experiência do Office em [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com suplementos do VSTO e soluções, e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  
  
> [!NOTE]  
>  O Visual Studio não pode atualizar os projetos de modelo de formulário do InfoPath que foram criados em versões anteriores do Visual Studio. Esses tipos de projetos não são suportados na versão atual do Visual Studio.  
  
## <a name="changes-to-upgraded-projects"></a>Alterações nos projetos atualizados  
 Quando você atualizar um projeto do Microsoft Office, o Visual Studio modifica o projeto para direcionar os itens a seguir:  
  
-   O Visual Studio 2010 Tools for Office Runtime. Para obter mais informações, consulte [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   As referências de assembly atual.  
  
-   Uma versão do .NET Framework que é compatível com o tipo de projeto (quando você atualiza para o Visual Studio 2013 somente).  
  
-   Uma versão do Microsoft Office que há suporte para o tipo de projeto (quando você atualiza para o Visual Studio 2013 somente).  
  
## <a name="assembly-references"></a>Referências de Assembly  
 O Visual Studio atualiza as seguintes referências de assembly no projeto:  
  
-   Microsoft Office assemblies de interoperabilidade primários (PIAs).  
  
-   Assemblies de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Para obter mais informações sobre esses assemblies, consulte [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Versões novas ou atualizadas de assemblies dependentes.  
  
## <a name="targeted-net-framework"></a>Destino do .NET Framework  
 Ao atualizar um projeto para o Visual Studio 2013, Visual Studio modifica o projeto para direcionar o o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ou [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. A versão do .NET framework buscada pelo projeto depende de qual versão do Office está instalada no seu computador. Se [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] é instalado, o Visual Studio modifica o projeto de destino a [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Caso contrário, o Visual Studio modifica o projeto de destino a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
> [!NOTE]  
>  Talvez seja necessário executar algumas etapas adicionais para executar uma solução redirecionada no desenvolvimento e computadores de usuários finais e seu projeto não serão mais compilados se usar determinados recursos. Para obter mais informações, consulte [Migrando soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Se você destinar a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior em um projeto do Office, você pode usar alguns recursos que não estão disponíveis quando você direcionar o .NET Framework 3.5. Para obter mais informações, consulte [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="targeted-office-application"></a>Aplicativo de destino do Office  
 Quando você atualizar um projeto do Office para Visual Studio 2013, Visual Studio modifica o projeto para direcionar uma versão do Microsoft Office que é compatível com o tipo de projeto, como um projeto de personalização no nível do documento ou um projeto de suplemento do VSTO.  
  
 Projetos do Office no Visual Studio 2013 podem direcionar [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplicativos. O Visual Studio modifica o projeto para a versão mais recente do office que você instalou o de destino. Se nenhuma dessas versões do Office estiverem instaladas, o Visual Studio não atualiza o projeto.  
  
> [!NOTE]  
>  Se você atualizar um projeto de suplemento do VSTO para destino [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou posterior, certifique-se de que o `ThisAddIn_Startup` manipulador de eventos do suplemento do VSTO não contém código que acessa um documento no aplicativo. Para obter mais informações, consulte [acessar um documento quando o Office aplicativo inicia](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Para personalizações no nível do documento, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] converte documentos em um projeto que têm um formato binário, como documentos que tenham uma extensão. xls ou. doc, para o formato do Office Open XML. Para obter mais informações sobre Open XML, consulte [Introdução às novas extensões de nome de arquivo e formatos XML abertos](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).  
  
> [!NOTE]  
>  As marcas inteligentes foram preteridas no Excel 2010 e o Word 2010. Portanto, se sua solução usar marcas inteligentes, você deve removê-los antes de testar e depurá-lo no Visual Studio 2013 ou o Visual Studio 2015.  
  
## <a name="upgrading-microsoft-office-2003-projects"></a>Atualizando projetos do Microsoft Office 2003  
 Há algumas considerações adicionais para atualizar as personalizações no nível do documento e suplementos do VSTO que se destinam a Microsoft Office 2003.  
  
### <a name="document-level-projects"></a>Projetos no nível de documento  
 Se o documento no projeto contém controles de formulários do Windows, você também deve ter o Visual Studio 2005 Tools para Office segunda edição em tempo de execução instalado antes de atualizar o projeto. Se esta versão do tempo de execução não está instalado no computador de desenvolvimento antes de atualizar o projeto, o projeto atualizado pode conter compilação ou erros de tempo de execução. Depois de terminar de atualizar o projeto, você pode desinstalar o Visual Studio 2005 Tools para Office Runtime segundo de edição de computador de desenvolvimento, se ele não está sendo usado por outras soluções do Office. Esta versão do tempo de execução está disponível como um pacote redistribuível do Microsoft Download Center em [Microsoft Visual Studio 2005 Tools para Office Runtime segundo da edição (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
### <a name="vsto-add-in-projects"></a>Projetos de suplemento do VSTO  
 Se o arquivo de solução para o seu projeto original incluído um projeto de instalação ou o InstallShield Limited Edition que foi configurado para instalar o suplemento do VSTO, o Visual Studio atualiza o projeto, mas não faz outras alterações ao projeto. Se você quiser continuar usando um arquivo do Windows Installer para implantar o suplemento do VSTO, você deve modificar o projeto de instalação ou o InstallShield Limited Edition para instalar os pré-requisitos de novo, como o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], o Visual Studio 2010 Tools for Office Runtime e, opcionalmente, os assemblies de interoperabilidade primária referenciados por seu suplemento do VSTO. Para obter mais informações, consulte [Implantando uma solução do Office usando o Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
 Se você quiser usar o ClickOnce para implantar o suplemento do VSTO, você pode excluir o projeto de instalação ou o InstallShield Limited Edition inteiramente. Para obter mais informações sobre a implantação de suplementos do VSTO usando ClickOnce, consulte [implantar uma solução Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: atualizar soluções do Office](http://msdn.microsoft.com/en-us/a269e539-b717-4680-a568-2152b070347e)   
 [Migrando soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Atualização do Projeto, Caixa de Diálogo Opções](../vsto/project-upgrade-options-dialog-box.md)  
  
  