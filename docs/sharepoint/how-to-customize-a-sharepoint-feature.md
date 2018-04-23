---
title: 'Como: personalizar um recurso do SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f22ec947e9aa3cae15427915bd5aff4122a67797
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Como personalizar uma funcionalidade do SharePoint
  Você pode criar e personalizar os recursos do SharePoint usando o Designer de recursos no Visual Studio. Por exemplo, você pode definir o escopo do recurso e adicionar outros recursos como dependências. Por padrão, o Designer de recursos é aberto quando você adiciona um novo recurso no Gerenciador de soluções ou o Gerenciador de pacote do SharePoint.  
  
## <a name="opening-the-feature-designer"></a>Abrir o Designer de recursos  
 Você pode adicionar ou remover itens de projeto do SharePoint para um recurso usando o Designer de recursos.  
  
#### <a name="to-open-the-feature-designer"></a>Para abrir o Designer de recursos  
  
1.  Em **Solution Explorer**, expanda **recursos**.  
  
2.  Clique duas vezes o *Feature1* item ou abra o menu de atalho para o *Feature1* item e, em seguida, escolha **Designer de exibição**.  
  
## <a name="viewing-the-packaged-manifest-file"></a>Exibindo o arquivo de manifesto de pacote  
 Você pode usar o Designer de recursos para modificar e gerar o arquivo de manifesto de pacote para o recurso (Feature). Em seguida, você pode exibir o código XML para este arquivo no Visual Studio.  
  
#### <a name="to-view-the-packaged-manifest-file"></a>Para exibir o arquivo de manifesto de pacote  
  
1.  No **recurso Designer**, escolha o **manifesto** guia.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Para exibir o arquivo de manifesto de pacote usando o Gerenciador de soluções  
  
1.  Em **Solution Explorer**, escolha o **Mostrar todos os arquivos** ícone.  
  
2.  Expanda recursos, expanda o nome do recurso, expanda FeatureName.feature e, em seguida, abra o *FeatureName*. Arquivo de Template.  
  
    > [!NOTE]  
    >  Quando você abre o arquivo XML de manifesto do modelo de recurso, os arquivos são validados automaticamente e os avisos que aparecem na janela lista de erros podem ser ignorados.  
  
## <a name="changing-the-manifest-template"></a>Alterar o modelo de manifesto  
 Você pode alterar o código XML para o arquivo de manifesto do recurso no Editor de XML do Visual Studio ou no painel de manifesto do modelo. As alterações para o código XML é mesclado no arquivo de manifesto do pacote para o recurso. Por exemplo, você talvez queira alterar o modelo de manifesto para personalizar uma propriedade de recurso.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Para alterar o modelo de manifesto usando o Editor de XML  
  
1.  No **recurso Designer**, escolha o **manifesto** guia, expanda o **editar opções** nó e, em seguida, escolha o **aberto no Editor de XML** link.  
  
     As alterações ao XML são mescladas no arquivo de manifesto do pacote.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Para alterar o modelo de manifesto usando o painel de manifesto do modelo  
  
1.  No **recurso Designer**, escolha o **manifesto** guia, expanda o **editar opções** nó e altere o XML que aparece no painel de manifesto do modelo.  
  
     As alterações ao XML aparecem no **visualização de empacotado manifesto** painel.  
  
## <a name="overwriting-the-packaged-manifest-file"></a>Substituindo o arquivo de manifesto do pacote  
 Você pode desabilitar o Designer de recurso e criar manualmente o arquivo feature. Na primeira vez que você executar esse procedimento, as configurações atuais no Designer de recurso são salvas no arquivo de XML do modelo de recurso. Em seguida, você pode modificar ou substituir o código XML.  
  
> [!NOTE]  
>  Se você adicionar ou remove itens de projeto do SharePoint no arquivo XML, enquanto o Designer de recurso está desabilitado, esses itens de projeto não são compactados.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Para substituir o arquivo de manifesto do pacote, desativando o designer  
  
1.  No **recurso Designer**, escolha o **manifesto** guia.  
  
2.  Expanda o **editar opções** nó, escolha o **substituir XML e editar manifesto gerado no editor de XML** link e, em seguida, escolha o **Sim** botão.  
  
     O modelo é atualizado com o arquivo de manifesto de pacote atual.  
  
## <a name="enabling-the-feature-designer"></a>Habilitando o Designer de recursos  
 Você pode habilitar novamente o Designer de recursos para personalizar o arquivo feature.  
  
#### <a name="to-re-enable-the-designer"></a>Para habilitar novamente o designer  
  
1.  No **recurso Designer**, escolha o **edições de manifesto de descarte e habilite novamente o designer** link e, em seguida, escolha o **Sim** botão.  
  
2.  O modelo é atualizado com o texto original, e as alterações ao XML serão perdidas.  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  