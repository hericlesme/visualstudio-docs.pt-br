---
title: 'Como: criar um pacote de solução do SharePoint usando tarefas do MSBuild | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 629b63b8645f1b5ebd84d25a04a4cec4e8bca6a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Como criar um pacote de soluções do SharePoint usando tarefas do MSBuild
  Você pode compilar, limpar e validar um pacote do SharePoint (. wsp) usando as tarefas de linha de comando do MSBuild em um computador de desenvolvimento. Você também pode usar esses comandos para automatizar o processo de compilação usando o Team Foundation Server em um computador de compilação.  
  
## <a name="building-a-sharepoint-package"></a>Criar um pacote do SharePoint  
  
#### <a name="to-build-a-sharepoint-package"></a>Para criar um pacote do SharePoint  
  
1.  No Windows **iniciar** menu, escolha **todos os programas**, **Acessórios**, **Prompt de comando**.  
  
2.  Altere para o diretório onde se encontra o projeto do SharePoint.  
  
3.  Digite o seguinte comando para criar um pacote para o projeto. Substituir *ProjectFileName* com o nome do projeto.  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Por exemplo, você pode executar um dos seguintes comandos para um projeto do SharePoint chamado ListDefinition1 do pacote.  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="cleaning-a-sharepoint-package"></a>Limpeza de um pacote do SharePoint  
  
#### <a name="to-clean-a-sharepoint-package"></a>Para limpar um pacote do SharePoint  
  
1.  Abra uma janela do prompt de comando.  
  
2.  Altere para o diretório onde se encontra o projeto do SharePoint.  
  
3.  Digite o seguinte comando para limpar um pacote para o projeto. Substituir *ProjectFileName* com o nome do projeto.  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Por exemplo, você pode executar um dos comandos a seguir para limpar um projeto do SharePoint chamado ListDefinition1.  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validating-a-sharepoint-package"></a>Validar um pacote do SharePoint  
  
#### <a name="to-validate-a-sharepoint-package"></a>Para validar um pacote do SharePoint  
  
1.  Abra uma janela do prompt de comando.  
  
2.  Altere para o diretório onde se encontra o projeto do SharePoint.  
  
3.  Digite o comando a seguir para validar um pacote para o projeto. Substituir *ProjectFileName* com o nome do projeto.  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Por exemplo, você pode executar um dos comandos a seguir para validar um projeto do SharePoint chamado ListDefinition1.  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="setting-properties-in-a-sharepoint-package"></a>Definindo propriedades em um pacote do SharePoint  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Para definir uma propriedade em um pacote do SharePoint  
  
1.  Abra uma janela do prompt de comando.  
  
2.  Altere para o diretório onde se encontra o projeto do SharePoint.  
  
3.  Digite o seguinte comando para definir uma propriedade em um pacote para o projeto. Substituir *PropertyName* com a propriedade que você deseja definir.  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     Por exemplo, você pode executar o comando a seguir para definir o nível de aviso.  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Criar recursos do SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Como: personalizar um recurso do SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Como adicionar e remover itens de funcionalidades do SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  