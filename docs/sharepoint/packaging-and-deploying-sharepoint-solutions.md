---
title: "Empacotando e implantando soluções do SharePoint | Microsoft Docs"
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
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e25d0829305f414712590296b6121d62583736a2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="packaging-and-deploying-sharepoint-solutions"></a>Empacotando e implantando recursos do SharePoint
  Normalmente, uma solução do SharePoint é implantada para um servidor do SharePoint usando um arquivo de pacote (. wsp) da solução. Você pode usar o Visual Studio para organizar os itens de projeto do SharePoint em recursos e criar um pacote para implantar os recursos do SharePoint.  
  
 Este tópico fornece as seguintes informações:  
  
-   [Criação de recursos e pacotes](#Creating)  
  
-   [Recursos e suporte a ferramentas de empacotamento](#Tools)  
  
-   [Implantando soluções do SharePoint](#Deploying)  
  
-   [Implantando arquivos em soluções do SharePoint](#DeployingFiles)  
  
##  <a name="Creating"></a>Criação de recursos e pacotes  
 Você pode usar o Visual Studio para agrupar elementos relacionados do SharePoint em um *recurso*. Por exemplo, um recurso para uma definição de lista de contatos pode incluir a instância da lista e a definição de lista. Você pode combinar esses dois elementos em um único recurso para fins de implantação. Para obter mais informações sobre recursos, consulte [blocos de construção: recursos](http://go.microsoft.com/fwlink/?LinkID=169183).  
  
 Em seguida, você pode criar um pacote do SharePoint solução (. wsp) para agrupar vários recursos, definições de site, assemblies e outros arquivos em um único pacote, que armazena os arquivos em um formato que precisa do SharePoint para implantar os arquivos no servidor. Para obter mais informações, consulte [blocos de construção: soluções](http://go.microsoft.com/fwlink/?LinkID=169186).  
  
##  <a name="Tools"></a>Recursos e suporte a ferramentas de empacotamento  
 Você pode usar as ferramentas de desenvolvimento do SharePoint no Visual Studio para organizar rapidamente os arquivos do SharePoint em recursos e pacotes de solução para facilitar a implantação. Você pode usar as ferramentas a seguir para configurar o pacote de solução e de recurso.  
  
-   Designer de pacote e o Designer de recursos.  
  
-   Gerenciador de empacotamento, uma janela de ferramenta.  
  
-   Gerenciador de soluções.  
  
### <a name="feature-designer-and-package-designer"></a>Designer de recurso e o Designer de pacote  
 Você pode criar recursos, definir escopos e marcar outros recursos como dependências usando o Designer de recursos. O designer também exibe o arquivo final do XML que descreve cada recurso. Para obter mais informações, consulte [criar recursos do SharePoint](../sharepoint/creating-sharepoint-features.md).  
  
 Aplicar o recurso a um site específico ou um grupo de sites da Web, definindo seu *escopo* no Designer de recursos. Se um recurso é ativado para um site individual, o recurso só funciona no site da Web específico. Se um recurso é ativado para um conjunto de sites, os itens no recurso se aplicam à coleção de todo o site. Para obter mais informações, consulte [elemento escopo](http://go.microsoft.com/fwlink/?LinkID=169189).  
  
 Se o recurso depende de outros recursos, você pode definir um *dependência de ativação de recursos* para marcar os recursos dependentes antes de disponibilizar o recurso. Uma dependência de ativação de recurso verifica se os recursos dependentes já estiverem ativados nesse escopo. Para obter mais informações, consulte [dependências de ativação e escopo](http://go.microsoft.com/fwlink/?LinkID=169190).  
  
 No Designer de pacote, você pode agrupar os elementos do SharePoint em um pacote de solução único e configurar se deseja redefinir o servidor Web durante a implantação. Para definir o tipo de servidor de implantação, use o **propriedades** janela. O designer também gera o arquivo XML que descreve o conteúdo do pacote. Para obter mais informações, consulte [criando pacotes da solução SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).  
  
 Durante a implantação, o serviço de serviços de informações da Internet (IIS) é interrompido para copiar os arquivos de solução para o servidor do SharePoint. Usando o Designer de pacote no Visual Studio, você pode selecionar se o servidor Web deve ser reiniciado. Para configurar se a solução for implantada em um servidor Web front-end ou um servidor de aplicativos, use o **propriedades** janela. Para obter mais informações, consulte [elemento Solution (solução)](http://go.microsoft.com/fwlink/?LinkID=169191).  
  
### <a name="packaging-explorer"></a>Gerenciador de pacotes  
 Para complementar o Designer de pacote e o Designer de recursos, você pode usar o Packaging Explorer para agrupar arquivos do SharePoint para recursos e pacotes. Além disso, você pode ver a exibição hierárquica do projeto do SharePoint pacote, recursos, itens e arquivos. O Gerenciador de pacotes é uma janela de ferramenta que você pode usar para concluir as seguintes tarefas:  
  
-   Abrir itens de projeto do SharePoint e arquivos.  
  
-   Arrastar e soltar itens de projeto do SharePoint de um recurso para outro.  
  
-   Arrastar e soltar itens de projeto do SharePoint e recursos de um pacote para outro.  
  
-   Adicione um novo recurso a um pacote.  
  
-   Abra um designer de pacote ou de recurso.  
  
-   Valide recursos e pacotes.  
  
 As ferramentas de desenvolvimento do SharePoint no Visual Studio tem regras de validação para ajudar a garantir que o pacote de solução está formado corretamente. Além disso, as regras de verificam que o arquivo de solução. wsp pode ser implantado e com êxito ativado em um servidor do SharePoint. Para obter mais informações sobre o esquema XML para recursos, consulte [esquemas de recurso](http://go.microsoft.com/fwlink/?LinkID=169192).  
  
 Você pode adicionar funcionalidade personalizada e regras de validação de pacote para o sistema de projeto do SharePoint. Para obter mais informações, consulte [como: Criar recurso de personalizada e regras de validação de pacote para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
 Para obter mais informações sobre o Gerenciador de pacotes, consulte [como: adicionar e remover recursos e itens de um pacote usando o Packaging Explorer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
### <a name="solution-explorer"></a>Gerenciador de Soluções  
 Você pode usar o Gerenciador de soluções para navegar e abrir os arquivos do projeto do SharePoint. Use o menu de contexto no Gerenciador de soluções para adicionar recursos, receptores de evento de recurso e recursos de recursos. Além disso, você pode abrir o recurso Designers e Designers de pacote para configurar os recursos e pacotes de implantação de.  
  
##  <a name="Deploying"></a>Implantando soluções do SharePoint  
 Depois de personalizar os recursos e o pacote no Visual Studio, você pode criar um arquivo. wsp para implantar servidores do SharePoint. Você pode usar o Visual Studio para depurar e testar o. wsp somente no servidor do SharePoint no computador de desenvolvimento. Para obter mais informações sobre como implantar suas soluções do SharePoint em um servidor remoto do SharePoint, consulte [Implantando uma solução](http://go.microsoft.com/fwlink/?LinkID=169194).  
  
 Você também pode personalizar as etapas de implantação no computador de desenvolvimento. Para obter mais informações, consulte [atualizar os pacotes de solução do SharePoint, publicação e implantação](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
##  <a name="DeployingFiles"></a>Implantando arquivos em soluções do SharePoint  
 Normalmente, quando você adiciona um item de projeto do SharePoint para a solução do SharePoint, todos os arquivos necessários estão incluídos. Arquivos que podem ser compilados (arquivos de código) são incorporados ao assembly de saída da solução. No entanto, você também precisará adicionar arquivos não compilável, por exemplo,. XML,. txt ou arquivos de recurso para um projeto do SharePoint. Esses arquivos não são incluídos automaticamente em sua solução. Para garantir que eles são compactados, adicione os arquivos para uma pasta mapeada ou um item de projeto do SharePoint.  
  
 Arquivos adicionados a pastas mapeadas são copiados automaticamente para o hive do SharePoint quando a solução for implantada. Arquivos adicionados a um item de projeto do SharePoint são implantados para o local especificado no **local de implantação** propriedade para cada arquivo, que é parcialmente definido com base no **tipo de implantação** propriedade. Por padrão, o **tipo de implantação** é o valor da propriedade **NoDeployment**, o que significa que o arquivo não está implementado com a solução. Você deve definir outro valor para a propriedade incluir o arquivo do pacote.  
  
 Por exemplo, para adicionar um arquivo. XML para um projeto do SharePoint, execute uma destas ações:  
  
-   Adicione uma pasta do SharePoint "Layouts" mapeado para seu projeto. Isso cria no **Solution Explorer** uma pasta chamada **Layouts** que tem uma subpasta para o projeto. Adicione o arquivo. XML para a nova subpasta. Por padrão, o arquivo é implantado para o sistema de arquivos do SharePoint em... \TEMPLATE\LAYOUTS\\*nome da pasta*\\. Para obter informações sobre como adicionar pastas mapeadas, consulte [como: adicionar e remover pastas mapeadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
-   Adicionar o arquivo. XML para a pasta de um item de projeto do SharePoint e, em seguida, alterar o **tipo de implantação** propriedade do arquivo. XML do **NoDeployment** para outro, como configuração **RootFile** ou **ElementFile**. Apropriada **tipo de implantação** configuração depende do arquivo e o projeto. Para obter mais informações sobre o **tipo de implantação** configurações de propriedade, consulte [desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md).  
  
 Se um arquivo de inclusão não se aplica a qualquer projeto específico na solução, você pode adicionar um projeto vazio do SharePoint para sua solução e, em seguida, adicione os arquivos adicionais a ele. Outra alternativa para implantação de arquivos para o SharePoint, especialmente para o banco de dados de conteúdo, é adicionar um módulo ao projeto e, em seguida, adicione os arquivos para o módulo. Para obter mais informações, consulte [usando módulos para incluir arquivos na solução](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Compilando e depurando soluções do SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  