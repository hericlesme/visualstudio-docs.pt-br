---
title: Criando pacotes de solução do SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e67073d1a12a9412b153adc0c06471c4d39ff15a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="creating-sharepoint-solution-packages"></a>Criando pacotes de soluções do SharePoint
  Usando o Designer de pacote, você pode criar e personalizar pacotes de implantação. Por exemplo, você pode adicionar itens de projeto do SharePoint e recursos, redefina o servidor IIS, definir escopos de ativação de recurso e identificar as dependências de recurso. O designer também gera um manifesto de um arquivo XML que descreve cada pacote.  
  
## <a name="packaging-tools"></a>Ferramentas de empacotamento  
 Você pode usar o **Package Designer** para personalizar o pacote e gerar o manifesto. Você pode incluir itens de projeto do SharePoint, configure se o servidor Web deve ser redefinido e defina o tipo de servidor de implantação. Para obter mais informações, consulte [como: adicionar e remover recursos e itens de um pacote usando o Designer de pacote](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
 Como alternativa, você pode usar o **Packaging Explorer** para modificar os recursos e itens de seu arquivo de pacote (. wsp). Para obter mais informações, consulte [como: adicionar e remover recursos e itens de um pacote usando o Packaging Explorer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
 Você pode usar o Visual Studio e o MSBuild para criar arquivos de pacote (. wsp) para implantar a solução do SharePoint. Esse processo gera os arquivos de manifesto necessários para a implantação do SharePoint. Para obter mais informações, consulte [como: criar um pacote do SharePoint](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b) e [como: criar um pacote de solução do SharePoint usando tarefas do MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).  
  
## <a name="package-designer-options"></a>Opções do Designer de pacote  
 A tabela a seguir mostra as propriedades que você pode personalizar os pacotes do SharePoint com o **Package Designer**.  
  
|Propriedade do Designer de pacote|Descrição da configuração padrão|  
|-------------------------------|------------------------------------|  
|Nome|Necessário. O nome padrão do pacote é definido como *ProjectName*.|  
|Redefinir o servidor Web|Opcional. Selecione se deseja reiniciar o servidor Web depois que o arquivo. wsp é instalado no servidor do SharePoint.|  
|Tipo de servidor de implantação|Necessário. Por padrão, o escopo é definido como ApplicationServer.<br /><br /> ApplicationServer: Descreve um servidor que hospeda os serviços.<br /><br /> WebFrontEnd: Descreve um servidor que hospede sites da Web.|  
|Itens da solução|Todos os itens de projeto do SharePoint e recursos que podem ser adicionados ao pacote.|  
|Itens do pacote|Opcional. Todos os itens do SharePoint e recursos que você deseja implantar no pacote.|  
  
## <a name="configuring-the-packaging-process"></a>Configurando o processo de empacotamento  
 Depois de desenvolver soluções do SharePoint no Visual Studio, você pode personalizar como os projetos são empacotados.  
  
 A tabela a seguir mostra os dois destinos do MSBuild que você pode usar para personalizar como o arquivo. wsp é criado.  
  
|Destino|Descrição|  
|------------|-----------------|  
|BeforeLayout|O destino que executa tarefas imediatamente antes dos arquivos são copiados para um diretório intermediário. Você pode modificar os arquivos antes de criar um arquivo de pacote (. wsp).|  
|AfterLayout|O destino que executa tarefas imediatamente depois que os arquivos são copiados para um diretório intermediário.|  
  
 Para obter mais informações, [como: personalizar um pacote de solução do SharePoint, usando destinos do MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).  
  
## <a name="packaging-architecture"></a>Arquitetura de empacotamento  
 As etapas a seguir ocorrem quando você cria um pacote (. wsp) do SharePoint no Visual Studio.  
  
1.  Os recursos e pacotes são validados para garantir que a estrutura física e semântica do pacote está correta.  
  
2.  Os recursos, itens de projeto e arquivos de pacote no pacote são enumerados. Arquivos de manifesto para pacotes e recursos são transformados para incluir todas as informações necessárias para a implantação e ativação. Os tokens são substituídos com o valor totalmente qualificado.  
  
3.  O destino do BeforeLayout MSBuild personalizável é executado. Você pode criar essa etapa para fazer modificações personalizadas para o pacote antes do arquivo. wsp é criado.  
  
4.  Os arquivos enumerados são copiados para um diretório intermediário.  
  
5.  O destino do MSBuild AfterLayout personalizável é executado. Você pode criar essa etapa para fazer modificações personalizadas para o pacote antes do arquivo. wsp é criado.  
  
6.  Os arquivos no diretório intermediário são adicionados ao arquivo. wsp.  
  
## <a name="package-folder-structure"></a>Estrutura de pasta do pacote  
 Quando você empacotar o projeto do SharePoint, um arquivo. wsp é criado para você no SolutionFolder\bin\\*BuildConfiguration* pasta. Por exemplo, se sua solução está em *unidade*: \Visual Studio 2013\Projects\ListDefinition1 e sua configuração de compilação é definida como versão, o arquivo. wsp está localizado em *unidade*: \Visual Studio 2013\ Projects\ListDefinition1\bin\Release.  
  
## <a name="see-also"></a>Consulte também  
 [Como personalizar um pacote de soluções do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Como: adicionar e remover recursos e itens de um pacote usando o Designer de pacote](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [Como: criar um pacote do SharePoint](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)   
 [Como: criar um pacote de solução do SharePoint usando tarefas do MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Como personalizar um pacote de soluções do SharePoint usando destinos do MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
  