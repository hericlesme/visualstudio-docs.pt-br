---
title: "Exigiu alterações executar projetos do Office migrados para o .NET Framework 4 ou o .NET Framework 4.5 | Microsoft Docs"
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
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
ms.assetid: e2cd35cc-7731-428e-9046-34fc57a02c48
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2a037bd26eb3caa24c86fdba63753894b0bd1af3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Alterações necessárias para executar projetos do Office migrados para o .NET Framework 4 ou o .NET Framework 4.5
  Se a estrutura de destino de um projeto do Office será alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior de uma versão anterior do .NET Framework, você deve executar as seguintes tarefas para garantir que a solução pode ser executado no computador de desenvolvimento e em computadores de usuário final:  
  
-   Remover o <xref:System.Security.SecurityTransparentAttribute> do projeto se você atualizou do Visual Studio 2008.  
  
-   Executar um **limpar** comando no Visual Studio para poder executar ou depurar o projeto no computador de desenvolvimento.  
  
-   Atualize o .NET Framework pré-requisitos para o projeto.  
  
-   Os usuários finais também deverá reinstalar a solução se tiver implantado usando o ClickOnce antes de alterar a estrutura de destino.  
  
 Para obter mais informações sobre cada uma dessas tarefas, consulte as seções correspondentes abaixo.  
  
## <a name="removing-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Removendo o atributo SecurityTransparent de projetos que você atualiza do Visual Studio 2008  
 Se você atualizar um projeto do Office do Visual Studio 2008 e a estrutura de destino do projeto subsequentemente altera para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve remover o <xref:System.Security.SecurityTransparentAttribute> do projeto. O Visual Studio não remove automaticamente esse atributo para você. Se você não remover esse atributo, você receberá uma mensagem de erro quando você compilar o projeto.  
  
 Para obter mais informações sobre as condições na qual o Visual Studio pode alterar a estrutura de destino de um projeto atualizado para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consulte [atualizando e Migrando soluções do Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### <a name="to-remove-the-securitytransparentattribute"></a>Para remover o SecurityTransparentAttribute  
  
1.  Com o projeto aberto no Visual Studio, abra **Gerenciador de soluções**.  
  
2.  Sob o **propriedades** nó (c#) ou o **meu projeto** nó (para Visual Basic), clique duas vezes o arquivo de código AssemblyInfo para abri-lo no editor de códigos.  
  
    > [!NOTE]  
    >  Em projetos do Visual Basic, você deve clicar no **Mostrar todos os arquivos** no botão **Solution Explorer** para ver o arquivo de código AssemblyInfo.  
  
3.  Localize o <xref:System.Security.SecurityTransparentAttribute> e removê-lo do arquivo ou comente-o.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## <a name="performing-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Executar o comando Limpar depurar ou executar um projeto no computador de desenvolvimento  
 Se um projeto do Office foi criado antes que a estrutura de destino do projeto é alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve executar uma **limpar** de comando e, em seguida, recompile o projeto depois que a estrutura de destino é alterada. Se não executar um **limpar** de comando, você receberá um <xref:System.Runtime.InteropServices.COMException> quando você tenta depurar ou executar o projeto redirecionado.  
  
 Para obter mais informações sobre o **limpar** command, consulte [criando soluções do Office](../vsto/building-office-solutions.md).  
  
## <a name="updating-the-prerequisites-for-deployment"></a>Os pré-requisitos para implantação de atualização  
 Quando você redirecionar um projeto do Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você também deve atualizar os pré-requisitos do .NET Framework correspondente no **pré-requisitos** caixa de diálogo. Caso contrário, a implantação do ClickOnce ou o projeto do InstallShield Limited Edition verifica e instala uma versão anterior do .NET Framework.  
  
 Para obter mais informações sobre como atualizar os pré-requisitos para implantação em computadores de usuário final, consulte [como: instalar pré-requisitos em computadores de usuário final para executar soluções do Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## <a name="reinstalling-solutions-on-end-user-computers"></a>Reinstalar as soluções em computadores de usuário final  
 Se você usar o ClickOnce para implantar uma solução do Office que tem como alvo o .NET Framework 3.5 e, em seguida, você pode redirecionar o projeto para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, os usuários finais deve desinstalar a solução e, em seguida, reinstalar a solução após você republicá-lo. Se você publicar novamente a solução redirecionada e a solução é atualizada nos computadores de usuário final, os usuários finais receberão um <xref:System.Runtime.InteropServices.COMException> quando executarem a solução atualizada.  
  
## <a name="see-also"></a>Consulte também  
 [Migrando soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  