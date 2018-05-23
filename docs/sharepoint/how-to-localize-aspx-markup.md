---
title: 'Como: localizar marcação ASPX | Microsoft Docs'
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
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b43a8833ea84c4f6d191200bcf3af80815deb03a
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2018
---
# <a name="how-to-localize-aspx-markup"></a>Como localizar marcação ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] páginas (. aspx) normalmente usam valores de cadeia de caracteres codificada. Para localizar essas cadeias de caracteres, substitua-os com expressões que referenciam recursos localizados.  
  
## <a name="localizing-aspx-markup"></a>Localizando marcação ASPX  
  
#### <a name="to-localize-aspx-markup"></a>Para localizar marcação ASPX  
  
1.  Adicionar arquivos de recurso separados: um para o idioma padrão e uma para cada idioma localizado.  
  
     Se você estiver localizando somente marcação e não o código, adicione um item de projeto do arquivo de recursos globais. Se você estiver localizando o código e a marcação, adicione um item de projeto do arquivo de recursos.  
  
    1.  Para adicionar um arquivo de recursos globais, em **Solution Explorer**, abra o menu de atalho para um item de projeto do SharePoint e, em seguida, escolha **adicionar**, **Novo Item**. Sob o SharePoint **2010** nó, escolha o **arquivo de recursos globais** modelo.  
  
    2.  Para adicionar um arquivo de recursos, em **Solution Explorer**, abra o menu de atalho para um item de projeto do SharePoint e, em seguida, escolha **adicionar**, **Novo Item**. Em um a **Visual Basic** ou **Visual C#** nó, escolha o **arquivo de recursos** modelo.  
  
    > [!NOTE]  
    >  Certifique-se de adicionar os arquivos de recurso para um item de projeto do SharePoint para habilitar a propriedade de tipo de implantação. Essa propriedade é necessária neste procedimento. Se sua solução não tem um item de projeto do SharePoint, você pode adicionar um projeto vazio do SharePoint e remover seu arquivo de Elements padrão.  
  
2.  Nomeie o arquivo de recurso de idioma padrão de sua escolha concatenada com uma extensão. resx, como MyAppResources.resx. Usar o mesmo nome de base para cada arquivo de recurso localizado, mas adicionar a cultura [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Por exemplo, nome de um recurso localizado alemão MyAppResources.de-de. resx.  
  
3.  Alterar o valor da **tipo de implantação** propriedade de cada arquivo de recurso para **AppGlobalResource** para levá-los implantar a pasta do servidor App_GlobalResources.  
  
4.  Se você estiver usando os recursos para localizar código além de marcação ASPX, deixe o valor da **ação de compilação** propriedade de cada arquivo como **recurso inserido**. Se você estiver usando os arquivos de recurso apenas para localizar a marcação, opcionalmente, você pode alterar o valor da propriedade dos arquivos a serem **conteúdo**. Para obter mais informações, consulte [Localizando soluções do SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Abra cada arquivo de recurso e adicionar cadeias de caracteres localizadas, usando a mesma cadeia de caracteres IDs em cada arquivo.  
  
6.  No [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] marcação para a página ASPX página ou controle, substitua as cadeias de caracteres codificadas com valores que usam o seguinte formato:  
  
    ```aspx-csharp  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Por exemplo, para localizar o texto de um controle de rótulo em uma página de aplicativo, você alteraria:  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     para  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  Escolha a tecla F5 para compilar e executar o aplicativo.  
  
8.  No SharePoint, altere o idioma de exibição padrão.  
  
     As cadeias de caracteres localizadas aparecem no aplicativo. Para exibir os recursos localizados, o servidor do SharePoint deve ter um pacote de idiomas instalado que corresponda a cultura do arquivo de recurso.  
  
## <a name="see-also"></a>Consulte também  
 [Localizando soluções do SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Como: localizar um recurso](../sharepoint/how-to-localize-a-feature.md)   
 [Como: adicionar um arquivo de recurso](../sharepoint/how-to-add-a-resource-file.md)   
 [Como localizar código](../sharepoint/how-to-localize-code.md)  
  
  