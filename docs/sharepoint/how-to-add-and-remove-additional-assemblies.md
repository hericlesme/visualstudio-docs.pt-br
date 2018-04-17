---
title: 'Como: adicionar e remover Assemblies adicionais | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
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
ms.openlocfilehash: cadfffb2dbf977e23a0edb082065125aea4f5940
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Como adicionar e remover assemblies adicionais
  Se um pacote do SharePoint depende de outros assemblies para funcionalidade ou dados, você pode adicionar os assemblies ao seu pacote de solução (. wsp). Dessa forma, o servidor do SharePoint assegura que os assemblies personalizados são instalados com um pacote.  
  
 Você também pode adicionar e alterar os controles seguros e arquivos de recurso de classe associados com os assemblies.  
  
## <a name="adding-additional-assemblies-safe-controls-and-class-resources"></a>Adicionando Assemblies adicionais, os controles de seguros e recursos de classe  
 Você pode adicionar assemblies adicionais para o pacote de solução do SharePoint. Implantar assemblies adicionais em uma solução em área restrita para o cache de assembly global, mas os itens de projeto do SharePoint em uma solução em área restrita serão adicionados para o banco de dados de conteúdo. Você também pode adicionar controles de seguros e recursos de classe para esses assemblies adicionais. Para obter mais informações sobre controles de seguras, consulte [fornecendo empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) ou "Criando uma entrada SafeControl" em [implantação de Web Parts do SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### <a name="to-add-an-existing-assembly"></a>Para adicionar um assembly existente  
  
1.  Abra o **pacote Designer**. Para obter mais informações, consulte [como: personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Escolha o **avançado** guia.  
  
3.  Escolha o **adicionar** botão e, em seguida, escolha **adicionar Assembly existente** da lista.  
  
     O **adicionar Assembly existente** caixa de diálogo é exibida.  
  
4.  Escolha o botão de reticências (![elipse ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipse ASP.NET Mobile Designer")) e, em seguida, escolha o assembly que você deseja adicionar. É recomendável usar um caminho relativo para o assembly selecionado para fins de portabilidade.  
  
5.  Para o **destino de implantação**, escolha o **GlobalAssemblyCache** botão de opção para implantar o assembly no cache de assembly global, ou escolha o **WebApplication** opção botão para implantar o assembly para a pasta de aplicativo Web no servidor que está executando o SharePoint.  
  
#### <a name="to-add-an-assembly-from-project-output"></a>Para adicionar um assembly de saída do projeto  
  
1.  Abra o **pacote Designer**.  
  
     Para obter mais informações, consulte [como: personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Escolha o **avançado** guia.  
  
3.  Escolha o **adicionar** botão e, em seguida, escolha **adicionar Assembly de saída do projeto** da lista.  
  
     O **adicionar Assembly de saída do projeto** caixa de diálogo é exibida.  
  
4.  No **projeto de origem** lista e escolha o projeto de origem que você deseja adicionar.  
  
5.  Para o **destino de implantação**, escolha o **GlobalAssemblyCache** botão de opção para implantar o assembly no cache de assembly global, ou escolha o **WebApplication** opção botão para implantar o assembly para a pasta de aplicativo Web no servidor que está executando o SharePoint.  
  
#### <a name="to-add-a-safe-control"></a>Para adicionar um controle de seguro  
  
1.  Abra o **Editar Assembly existente** caixa de diálogo. Para fazer isso, abra o Designer de pacote, escolha o **avançado** guia, escolha um assembly e, em seguida, escolha o **editar**botão.  
  
2.  No **controles seguros** painel, escolha o **clique aqui para adicionar um novo item** botão.  
  
3.  No **nome do Assembly** coluna, digite o nome do assembly.  
  
4.  No **Namespace** coluna, digite o nome do namespace para o controle de seguro.  
  
5.  No **nome do tipo** coluna, digite o nome do tipo.  
  
#### <a name="to-add-a-class-resource"></a>Para adicionar um recurso de classe  
  
1.  Abra o **Editar Assembly existente** caixa de diálogo. Para fazer isso, abra o Designer de pacote, escolha o **avançado** guia, escolha um assembly e, em seguida, escolha o **editar** botão.  
  
2.  No **recursos de classe** painel, escolha o **clique aqui para adicionar um novo item** botão.  
  
3.  No **nome de arquivo** coluna, escolha o botão de reticências (![elipse ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipse ASP.NET Mobile Designer")) e escolha o recurso de classe que você deseja adicionar.  
  
## <a name="deleting-custom-assemblies"></a>Excluindo Assemblies personalizados  
 Você pode excluir conjuntos de um pacote do SharePoint ou excluir recursos de classe e controles de seguros de assemblies existentes.  
  
#### <a name="to-delete-an-existing-assembly"></a>Para excluir um assembly existente  
  
1.  Abra o **pacote Designer**. Para obter mais informações, consulte [como: personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Escolha o **avançado** guia.  
  
3.  No **Assemblies adicionais** painel, escolha o assembly personalizado que você deseja excluir.  
  
4.  Escolha o **excluir** botão.  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Para excluir um controle de segurança para um assembly  
  
1.  Abra o **Editar Assembly existente** caixa de diálogo. Para fazer isso, abra o Designer de pacote, escolha o **avançado** guia, escolha um assembly e, em seguida, escolha o **editar** botão.  
  
2.  Escolha o controle de segurança que você deseja excluir.  
  
3.  Pressione a tecla Delete.  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Para excluir um recurso de classe para um assembly  
  
1.  Abra o **Editar Assembly existente** caixa de diálogo. Para fazer isso, abra o Designer de pacote, escolha o **avançado** guia, escolha um assembly e, em seguida, escolha o **editar** botão.  
  
2.  Escolha o recurso de classe que você deseja excluir.  
  
3.  Pressione a tecla Delete.  
  
## <a name="see-also"></a>Consulte também  
 [Criar recursos do SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Como: personalizar um recurso do SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Como adicionar e remover itens de funcionalidades do SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
  
  