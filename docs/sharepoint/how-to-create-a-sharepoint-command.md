---
title: 'Como: criar um comando do SharePoint | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 9afdf3c26d059a7593d21eb7844f8a1b45cc9d01
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-a-sharepoint-command"></a>Como criar um novo comando do SharePoint
  Se você quiser usar o modelo de objeto de servidor em uma extensão de ferramentas do SharePoint, você deve criar um personalizado *comando SharePoint* para chamar a API. Você pode definir o comando do SharePoint em um assembly que pode chamar diretamente o modelo de objeto do servidor.  
  
 Para obter mais informações sobre a finalidade de comandos do SharePoint, consulte [chamando os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-create-a-sharepoint-command"></a>Para criar um comando do SharePoint  
  
1.  Crie um projeto de biblioteca de classe que tem a seguinte configuração:  
  
    -   Tem como alvo o .NET Framework 3.5. Para obter mais informações sobre como selecionar a estrutura de destino, consulte [como: uma versão do .NET Framework de destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
    -   Tem como alvo o AnyCPU ou x64 plataforma. Por padrão, a plataforma de destino para projetos de biblioteca de classe é AnyCPU. Para obter mais informações sobre como selecionar a plataforma de destino, consulte [como: configurar projetos para destinar plataformas](../ide/how-to-configure-projects-to-target-platforms.md).  
  
    > [!NOTE]  
    >  Você não pode implementar um comando do SharePoint no mesmo projeto que define uma extensão de ferramentas do SharePoint, pois o destino de extensões de ferramentas do .NET Framework 3.5 e do SharePoint de destino de comandos do SharePoint a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Você deve definir os comandos do SharePoint que são usados por sua extensão em um projeto separado. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
2.  Adicione referências aos assemblies a seguir:  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft. SharePoint  
  
3.  Em uma classe no projeto, crie um método que define o comando do SharePoint. O método deve estar de acordo com as diretrizes a seguir:  
  
    -   Ele pode ter um ou dois parâmetros.  
  
         O primeiro parâmetro deve ser um <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> objeto. Esse objeto fornece o Microsoft.SharePoint.SPSite ou Microsoft.SharePoint.SPWeb no qual o comando é executado. Ele também fornece um <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> objeto que pode ser usado para gravar mensagens para o **saída** janela ou **lista de erros** janela no Visual Studio.  
  
         O segundo parâmetro pode ser um tipo de sua escolha, mas esse parâmetro é opcional. Você pode adicionar esse parâmetro ao comando do SharePoint se você precisar passar dados de sua extensão de ferramentas do SharePoint para o comando.  
  
    -   Ele pode ter um valor de retorno, mas isso é opcional.  
  
    -   O segundo valor de retorno e de parâmetro deve ser um tipo que pode ser serializado pelo Windows Communication Foundation (WCF). Para obter mais informações, consulte [tipos suportados pelo serializador de contrato de dados](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) e [usando a classe XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).  
  
    -   O método pode ter qualquer visibilidade (**pública**, **interno**, ou **privada**), e pode ser estático ou não-estático.  
  
4.  Aplicar o <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> para o método. Esse atributo especifica um identificador exclusivo para o comando. Esse identificador não precisa corresponder ao nome do método.  
  
     Quando você chama o comando de sua extensão de ferramentas do SharePoint, você deve especificar o mesmo identificador exclusivo. Para obter mais informações, consulte [como: executar um comando SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra um comando do SharePoint que tem o identificador `Contoso.Commands.UpgradeSolution`. Esse comando usa as APIs no modelo de objeto de servidor para atualizar para uma solução de implantação.  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]  
  
 Além do primeiro implícita <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parâmetro, esse comando também tem um parâmetro de cadeia de caracteres personalizada que contém o caminho completo do arquivo. wsp que está sendo atualizado para o site do SharePoint. Para ver esse código no contexto de um exemplo maior, consulte [passo a passo: Criando uma etapa de implantação personalizada para projetos SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer referências para os seguintes assemblies:  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft. SharePoint  
  
## <a name="deploying-the-command"></a>Implantando o comando  
 Para implantar o comando, inclua o assembly de comando na mesma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) com o assembly de extensão que usa o comando. Você também deve adicionar uma entrada para o assembly de comando no arquivo extension.vsixmanifest. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [A chamada para os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Como: executar um comando do SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Instruções passo a passo: estendendo o Gerenciador de Servidores para exibir Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  