---
title: "Como: importar uma página mestre ou tema | Microsoft Docs"
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
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
ms.assetid: 8b446cca-2adb-457b-bbfd-891209290e80
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 447fa8749958a3fa2b65a6ef7eb878b906170e6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-import-a-master-page-or-theme"></a>Como importar uma página mestre ou tema
  Você pode dar páginas no site do SharePoint uma aparência consistente criando e usando páginas mestras e temas. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]não fornece modelos para esses elementos, mas você pode criá-los no SharePoint Designer e, em seguida, importá-los para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obter mais informações, consulte [blocos de construção: páginas e a Interface do usuário](http://go.microsoft.com/fwlink/?LinkID=182095) no site da Microsoft.  
  
### <a name="to-import-a-master-page-or-theme"></a>Para importar uma página mestre ou tema  
  
1.  Em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], crie ou abra um projeto do SharePoint.  
  
     Para obter informações sobre como criar um projeto do SharePoint, consulte [projeto do SharePoint e modelos de Item de projeto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
3.  No **Adicionar Novo Item** caixa de diálogo caixa, expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
4.  Na lista de modelos do SharePoint, escolha o **módulo** modelo e, em seguida, especifique um nome para o módulo.  
  
     Um módulo contém arquivos (por exemplo, a página mestra ou arquivos de tema) para implantação em um local que você especificar no SharePoint.  
  
5.  No módulo, exclua o arquivo padrão, que é chamado Sample.  
  
6.  Escolha o nó de módulo.  
  
7.  Na barra de menus, escolha **projeto**, **Add Existing Item**e, em seguida, escolha o arquivo de tema ou de página mestra.  
  
     Arquivos de página mestre têm uma extensão. master, e os arquivos de tema têm uma extensão de .thmx.  
  
8.  Se você adicionou uma página mestre, alterar seu **resolução de conflitos de implantação** definindo como **automáticas** nas propriedades do módulo.  
  
    > [!NOTE]  
    >  Erros podem ocorrer se o nome da página mestra for igual ao nome de uma página mestra existente que está marcado como padrão o mestre de página ou página mestre personalizada. Para obter informações sobre como resolver esse problema, consulte [passo a passo: importar uma página de mestre personalizada e página do Site com uma imagem](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. O módulo, abra Elements.  
  
     Você deve atualizar o arquivo de Elements para fazer referência a página mestre ou tema que você adicionou.  
  
10. Para uma página mestra, substitua a marcação de módulo existente com a seguinte marcação.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Para um tema, substitua a marcação de módulo existente com a seguinte marcação.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Certifique-se de substituir os valores de espaço reservado com os nomes reais do módulo e a página mestre ou tema.  
  
     O atributo `Type="GhostableInLibrary"` indica que o item é adicionado para o banco de dados de conteúdo e o `Url` atributo do módulo Especifica onde armazenar o arquivo de banco de dados de conteúdo do SharePoint.  
  
11. Para alterar o escopo de implantação para uma página mestre, em **Solution Explorer**, abra o arquivo de recurso no Designer de recursos e, em seguida, escolha um novo escopo de implantação do **escopo** lista.  
  
     Um valor de **Web** significa que a página mestra aplica-se somente para o site especificado no projeto. Um valor de **Site** significa que a página mestra se aplica à coleção de site atual, que inclui todos os subsites e web raiz. Os outros valores não se aplicam.  
  
    > [!NOTE]  
    >  Como os temas aplicam-se somente ao nível de coleção de sites, é recomendável que você não definir o escopo de um tema para algo diferente de **Site**. Podem ocorrer erros se um tema for usado em um subsite.  
  
12. Na barra de menus, escolha **criar**, **implantar solução**.  
  
13. Para verificar se os arquivos foram implantados corretamente, abra o site do SharePoint, escolha o **ações do Site** menu, escolha o **configurações de Site** de comando e, em seguida, escolha o **páginas mestras**  link ou o **temas** link.  
  
     A lista de páginas mestras ou temas aparece e contém a página mestra ou o tema que você importou.  
  
## <a name="see-also"></a>Consulte também  
 [Páginas mestras](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Importando itens de um Site do SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Criando páginas para SharePoint](../sharepoint/creating-pages-for-sharepoint.md)   
 [Usando módulos para incluir arquivos na solução](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  