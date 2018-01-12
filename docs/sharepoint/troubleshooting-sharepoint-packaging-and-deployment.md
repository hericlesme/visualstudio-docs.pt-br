---
title: "Solução de problemas do SharePoint empacotamento e implantação | Microsoft Docs"
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a2c9cbb7b0b9e7f0536fb393bcea3d0873e0d90a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="troubleshooting-sharepoint-packaging-and-deployment"></a>Solucionando problemas de pacote e implantação do SharePoint
  Este tópico abrange vários problemas que você pode encontrar ao empacotar e implantar soluções do SharePoint.  
  
## <a name="enabling-enhanced-debugging"></a>Habilitando Depuração Aperfeiçoada  
 Para diagnosticar entre o Visual Studio, SharePoint e outras camadas, você pode usar a chave de registro EnableDiagnostics para exibir o rastreamento de pilha. Para obter mais informações, consulte [soluções do SharePoint de depuração](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="adding-project-output-to-the-solution-package"></a>Adicionando Saída do Projeto ao Pacote de Solução  
 Você pode adicionar a saída do projeto para um pacote por meio do Designer de pacote. No entanto, quando você adiciona a saída do projeto, certifique-se de que a plataforma do projeto corresponda à plataforma da solução do SharePoint. Recomendamos que você use o **qualquer CPU** destino da plataforma para os assemblies que você deseja implantar em um servidor do SharePoint. Para obter mais informações, consulte [página de compilação, Designer de projeto &#40; Visual Basic &#41; ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) e [Avançado da caixa de diálogo de configurações de compilador &#40; Visual Basic &#41; ](/visualstudio/ide/reference/advanced-compiler-settings-dialog-box-visual-basic).  
  
## <a name="validation-warnings-and-errors"></a>Avisos e Erros de Validação  
 As ferramentas de desenvolvimento do SharePoint no Visual Studio executam etapas de validação para verificar se o pacote de solução está formado corretamente. Você também pode criar etapas de validação personalizada para seus recursos e pacotes. Para obter mais informações, consulte [como: Criar recurso de personalizada e regras de validação de pacote para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## <a name="deployment-conflict-resolution"></a>Resolução do Conflito de Implantação  
 Quando você implanta uma solução do SharePoint, você pode achar colisões quando um item no servidor tem o mesmo nome, URL ou ID como um item em seu pacote de solução. Você pode alterar o **resolução de conflitos de implantação** propriedade para resolver, relatório ou em Ignorar colisões de módulos, Web parts, listar as instâncias e tipos de conteúdo.  
  
 A tabela a seguir demonstra as configurações para o **resolução de conflitos de implantação** propriedade.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Automático|Detecta colisões e resolve os conflitos automaticamente.|  
|prompt|Detecta colisões e relatá-los para o desenvolvedor antes de resolver os conflitos.|  
|Nenhum|Não detecta colisões.|  
  
## <a name="differences-between-f5-deployment"></a>Diferenças entre a Implantação de F5  
 Quando você usa [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para implantar o projeto do SharePoint para o servidor local do SharePoint para teste e depuração, há algumas etapas adicionais que são executadas por [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
1.  Redefina o serviço de informações da Internet (IIS) durante a etapa da implantação.  
  
2.  Associe automaticamente os fluxos de trabalho.  
  
3.  Defina a ordem de ativação de recurso acordo com a hierarquia no Designer de pacote.  
  
 Você pode adicionar etapas de implantação personalizada para alterar o comportamento de F5. Para obter mais informações, consulte [passo a passo: Criando uma etapa de implantação personalizada para projetos SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="delay-displaying-sharepoint-page-when-deploying-visual-web-part"></a>Exibindo a Página do SharePoint com Atraso ao Implantar uma Web Part Visual  
 A página do SharePoint leva muito tempo para ser exibida durante a implantação de uma Web part Visual para a pasta Bin em [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], ou [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]. Se você alterar todos os arquivos em um nível superior [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] recompilações do diretório, como o diretório Bin, todo o aplicativo Web. Isso pode causar um atraso de até 25 segundos para a página do SharePoint para renderizar.  
  
### <a name="error-message"></a>Mensagem de erro  
 nenhuma.  
  
### <a name="resolution"></a>Resolução  
 Para contornar esse problema, execute as seguintes etapas:  
  
1.  Instalar a atualização KB967535 conforme descrito no artigo do Microsoft Support [corrigir: está disponível um hotfix para corrigir os dois problemas no ASP.NET no IIS 7.0 para Windows Vista e Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=179055).  
  
2.  Adicione a seguinte linha ao arquivo Web. config:  
  
    ```  
    <compilation batch="false" optimizeCompilations="true">  
    ```  
  
## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>Falha na Implantação do Projeto do SharePoint com o Erro "Falha na extração do arquivo de gabinete na solução”  
 Se o nome de qualquer item de projeto do SharePoint contém parênteses, sua solução falhar na implantação com um erro.  
  
### <a name="error-message"></a>Mensagem de erro  
 Ocorreu um erro na etapa de implantação adicionar solução: Falha ao extrair o arquivo cab da solução.  
  
### <a name="resolution"></a>Resolução  
 Para contornar esse problema, remova todos os parênteses nos nomes de itens de projeto do SharePoint.  
  
## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Erro Aparece ao Implantar uma Web Part Visual em um Site em um Aplicativo Web Diferente  
 Na primeira vez que você implante uma Web part visual em um site em um aplicativo Web diferente no qual ele está implantado atualmente (alterando a propriedade de SiteUrl da Web part visual), você receberá um erro.  
  
### <a name="error-message"></a>Mensagem de erro  
 Ocorreu um erro na etapa de implantação adicionar solução: um recurso com a ID [#] já foi instalado neste farm. Use o atributo de forçar explicitamente reinstalar o recurso.  
  
### <a name="resolution"></a>Resolução  
 Esse erro ocorre devido à maneira que recursos de Web part visual são cancelados no SharePoint. Para implantar com êxito a Web part visual, implante a solução novamente, escolha a tecla F5.  
  
## <a name="warning-appears-when-deploying-nested-user-controls"></a>Aviso Exibido ao Implantar Controles de Usuário Aninhados  
 Este aviso ocorre quando você implanta uma solução do SharePoint que tem controles de usuário aninhados, como uma Web part visual que contém um controle de usuário ou um controle de usuário que contém uma Web part visual ou outro controle de usuário. Este aviso ocorre se você adicionar um controle a um designer, arrastando-o na caixa de ferramentas ou usando o @Register diretiva na exibição da fonte.  
  
### <a name="error-message"></a>Mensagem de erro  
 Aviso 1 elemento ' [*nome do controle*]' não é um elemento conhecido. Isso pode ocorrer se houver um erro de compilação no site da Web ou o arquivo Web. config está ausente.  
  
### <a name="resolution"></a>Resolução  
 Se o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sistema de projeto não está ciente de um controle de usuário aninhados, ele não pode fornecer o Intellisense e emite o aviso. O sistema do projeto não fica ciente de um controle de usuário aninhados se o projeto não é compilado e o designer não está fechado e reaberto, ou se o cancele automaticamente opção estiver habilitada, que faz com que o controle de usuário deve ser cancelada na seção do SharePoint após a depuração.  
  
 Para remover esse aviso, compilar o projeto e, em seguida, feche e reabra o designer ou desabilitar a opção para o projeto de retirada automaticamente. Para fazer isso, desmarque o **cancele automaticamente após a depuração** caixa de seleção de **SharePoint** guia da caixa de diálogo Propriedades do projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
