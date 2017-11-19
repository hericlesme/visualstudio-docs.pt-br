---
title: "Como: personalizar um pacote de solução do SharePoint | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: fd365f8c-8a80-4ce8-8e28-c0eb609f12f3
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d07f03c1aed1c2e85e65bd10a89bd62138d571c7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Como personalizar um pacote de soluções do SharePoint
  Você pode usar o Designer de pacote para criar e personalizar um pacote (. wsp). Por exemplo, você pode adicionar itens de projeto do SharePoint e recursos, especifique se o servidor Web é redefinido quando a solução for implantada e defina o tipo de servidor de implantação.  
  
## <a name="opening-the-package-designer"></a>Abrir o Designer de pacote  
  
#### <a name="to-open-the-package-designer"></a>Para abrir o Designer de pacote  
  
-   Em **Solution Explorer**, clique duas vezes em **pacote**, ou escolha **View Designer** no menu de atalho para **pacote**.  
  
## <a name="viewing-the-packaged-manifest-file"></a>Exibindo o arquivo de manifesto de pacote  
 Você pode usar o Designer de pacote para modificar e gerar o arquivo de manifesto de pacote. Em seguida, você pode exibir o código XML para este arquivo no Visual Studio.  
  
#### <a name="to-view-the-xml-source-file"></a>Para exibir o arquivo de origem XML  
  
1.  No **Package Designer**, escolha **manifesto**.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Para exibir o arquivo de manifesto de pacote usando o Gerenciador de soluções  
  
1.  Em **Solution Explorer**, escolha **Mostrar todos os arquivos**.  
  
2.  Expanda o pacote, expanda o pacote e, em seguida, abra o arquivo Package.Template.xml.  
  
    > [!NOTE]  
    >  Quando você abre o arquivo de manifesto XML para o modelo de pacote, os arquivos são validados automaticamente e você pode ignorar os avisos que aparecem na janela lista de erros.  
  
## <a name="changing-the-manifest-template"></a>Alterar o modelo de manifesto  
 Você pode alterar o código XML para o arquivo de manifesto de pacote no Editor de XML do Visual Studio ou no painel de manifesto do modelo. As alterações para o código XML são mescladas no arquivo de manifesto de pacote para o pacote.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Para alterar o modelo de manifesto usando o Editor de XML  
  
1.  No **Package Designer**, escolha o **manifesto** guia, expanda o **editar opções** nó e, em seguida, escolha o **aberto no Editor de XML** link.  
  
     As alterações ao XML são mescladas no arquivo de manifesto do pacote.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Para alterar o modelo de manifesto usando o painel de manifesto do modelo  
  
1.  No **Package Designer**, escolha o **manifesto** guia, expanda o **editar opções** nó e altere o XML que aparece no painel de manifesto do modelo.  
  
     As alterações ao XML aparecem no **visualização de empacotado manifesto** painel.  
  
## <a name="overwriting-the-packaged-manifest-file"></a>Substituindo o arquivo de manifesto do pacote  
 Você pode desabilitar o Designer de pacote e criar manualmente o arquivo manifest. XML. Na primeira vez que você executar esse procedimento, as configurações atuais no Designer de pacote são salvas no arquivo de XML do modelo de pacote. Em seguida, você pode modificar ou substituir o código XML.  
  
> [!NOTE]  
>  Se você adicionar ou remove itens de projeto do SharePoint e recursos no arquivo XML, enquanto o Designer de pacote está desabilitado, esses itens de projeto e os recursos não são compactados.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Para substituir o arquivo de manifesto do pacote, desativando o designer  
  
1.  No **Package Designer**, escolha o **manifesto** guia.  
  
2.  .  
  
3.  Expanda o **editar opções** nó, escolha o **substituir XML e editar manifesto gerado no editor de XML** link e, em seguida, escolha o **Sim** botão.  
  
     O modelo é atualizado com o arquivo de manifesto de pacote atual.  
  
## <a name="enabling-the-package-designer"></a>Habilitando o Designer de pacote  
 Você pode habilitar novamente o Designer de pacote para personalizar o arquivo manifest. XML.  
  
#### <a name="to-re-enable-the-designer"></a>Para habilitar novamente o designer  
  
1.  No **Package Designer**, escolha o **edições de manifesto de descarte e habilite novamente o designer** link e, em seguida, escolha o **Sim** botão.  
  
     O modelo é atualizado com o texto original, e as alterações ao XML serão perdidas.  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  