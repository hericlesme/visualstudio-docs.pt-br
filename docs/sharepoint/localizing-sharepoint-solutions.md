---
title: "Localizando soluções do SharePoint | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 0d4cfa2b-8b48-45c7-bbee-ece9b0baffaf
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b8186110b04e3ff56b3c6b0cad03890f3233c03d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="localizing-sharepoint-solutions"></a>Localizando soluções do SharePoint
  O processo de preparar seus aplicativos para que eles podem ser usados em todo o mundo é conhecido como localização. Localização está convertendo recursos para uma cultura específica. Para obter mais informações, consulte [Globalizing e Localizando aplicativos](/visualstudio/ide/globalizing-and-localizing-applications). Este tópico fornece uma visão geral de como localizar uma solução do SharePoint.  
  
 Para localizar uma solução, você remove cadeias de caracteres codificadas do código e abstrai-los em arquivos de recurso. Um arquivo de recurso é um [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-com base em arquivo com uma extensão. resx. O arquivo de recurso contém as versões traduzidas das cadeias de caracteres usadas em sua solução. Para obter mais informações, consulte [recursos em aplicativos](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Adicione apenas os recursos de cadeia de caracteres para arquivos de recursos de solução do SharePoint. Embora o Editor de recursos permite que você adicione recursos de cadeia de caracteres não, os recursos de cadeia de caracteres não não é implantada no SharePoint.  
  
## <a name="resource-files"></a>Arquivos de recursos  
 Há três tipos de arquivos de recurso: padrão, com neutralidade de idioma e específicos de linguagem.  
  
|Tipo de arquivo de recurso|Descrição|  
|------------------------|-----------------|  
|Padrão|Também conhecido como um recurso de fallback, arquivos de recursos padrão contêm cadeias de caracteres localizadas para a cultura padrão, como o inglês. Eles são usados se nenhum arquivo de recurso localizado para o idioma especificado pode ser encontrado. Recursos padrão não tem arquivos separados, eles são armazenados no assembly principal do aplicativo.|  
|Com neutralidade de idioma|Um arquivo de recurso que contém cadeias de caracteres localizadas para um idioma, mas não uma cultura específica. Por exemplo, "fr" para francês.|  
|Específicos de linguagem|Um arquivo de recurso que contém cadeias de caracteres localizadas para um idioma e uma cultura. Por exemplo, "fr-CA" para francês (Canadá).|  
  
 Para obter mais informações, consulte [organização hierárquica de recursos para localização](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 Para especificar os arquivos de recursos padrão em projetos do SharePoint que você desenvolva em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], escolha **idioma invariável (país invariável)** na lista de cultura o **adicionar recurso** caixa de diálogo quando você Adicione um arquivo de recurso.  
  
## <a name="localizing-visual-studio-sharepoint-solutions"></a>Localizando soluções do SharePoint do Visual Studio  
 Quando você localiza uma solução, você deve considerar todas as informações textuais que exibe sua solução para os usuários. Mensagens informativas, mensagens de erro e [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] cadeias de caracteres devem ser convertidas e essas conversões colocado nos arquivos de recurso.  
  
 Cada cadeia de caracteres em um arquivo de recurso tem um identificador exclusivo. Use o mesmo identificador para a cadeia de caracteres traduzida em cada arquivo de recurso. Por exemplo, se "String1" é o identificador da primeira cadeia de caracteres no arquivo de recursos padrão, use o mesmo identificador para a primeira cadeia de caracteres em arquivos de recursos específicos do idioma.  
  
 Há três áreas, normalmente, você localiza no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplicativos do SharePoint: recursos, marcação de página ASPX e código. Para fins de ilustração, as seções a seguir, suponha que você tem uma solução do SharePoint que você deseja localizar em alemão e japonês. O idioma padrão é inglês.  
  
### <a name="localizing-features"></a>Localizando recursos  
 Para localizar um recurso, você precisa substituir o embutido título e descrição do recurso com uma expressão que faz referência ao título convertido e a cadeia de caracteres no arquivo de recursos localizados. Fazer essa alteração no **recurso Designer** em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obter mais informações, consulte [como: localizar um recurso](../sharepoint/how-to-localize-a-feature.md).  
  
 Para localizar o recurso em inglês em alemão e japonês, você deve adicionar três itens de projeto do arquivo de recurso ao seu projeto: um para inglês, um para o alemão e outra para japonês. Arquivos de recurso do recurso não podem ser usados para localizar marcação ASPX ou código; arquivos de recursos separado são necessários para eles.  
  
 Depois de criar o recurso de arquivos de recursos, adicione cadeias de caracteres traduzidas para eles. Acesse as cadeias de caracteres localizadas com uma expressão no seguinte formato:  
  
```  
$Resources:String ID  
```  
  
 Recurso recursos [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sempre são nomeados de recursos. Se você selecionar um idioma diferente do idioma invariável, em seguida, uma cultura [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] é adicionado ao nome do arquivo de recurso. Por exemplo, se você adicionar um arquivo de recurso do recurso de idioma invariável (padrão), ele é chamado resx. Se você adicionar um recurso de recurso específico do idioma, selecionando uma cultura japonês (Japão), o arquivo é chamado Resources.ja JP.resx. Nomes de arquivo de recurso do recurso são atribuídos automaticamente e não podem ser alterados.  
  
 O escopo de recursos do recurso é local para o recurso que são adicionados ao. Para criar recursos que podem ser usados por qualquer arquivo de recurso ou elemento na solução, adicione um **arquivo de recursos globais** item de projeto em vez de um arquivo de recurso do recurso. O **arquivo de recursos globais** item de projeto está localizado no **2010** pasta sob **SharePoint** no **Adicionar Novo Item** caixa de diálogo. Implantar arquivos de recursos globais para a pasta \Resources da pasta raiz do SharePoint.  
  
### <a name="localizing-aspx-page-markup"></a>Localizando a marcação da página ASPX  
 Para localizar [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] páginas, adicionar três itens de projeto do arquivo de recursos ao seu projeto: um para inglês, um para o alemão e outra para japonês. Se você não precisa localizar código além de marcação, você pode adicionar arquivos de recursos globais.  
  
 Forneça um nome para o arquivo de recurso de idioma padrão. Nomeie os arquivos de recurso localizado o mesmo concatenado com a cultura de idioma específico [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Por exemplo, MyAppResources.de. resx para alemão e MyAppResources.ja-JP.resx para japonês.  
  
 Definir o **tipo de implantação** propriedade de cada arquivo de recurso para **AppGlobalResource**. Isso faz com que os arquivos de recursos implantar na pasta App_GlobalResources, onde eles estão disponíveis para todas as páginas ASPX e controles na solução. Na pasta App_GlobalResources está localizada em C:\inetpub\wwwroot\wss\VirtualDirectories\\< número da porta\>\App_GlobalResources.  
  
> [!NOTE]  
>  Se você usar arquivos de recurso não globais, mova-os para a pasta de item de projeto para habilitar a propriedade de tipo de implantação e outras propriedades específicas do SharePoint.  
  
 Arquivos de recurso de marcação ASPX também podem ser usados para localizar o código. Se você estiver usando os recursos para localizar código além de marcação ASPX, deixe a configuração de propriedade do Build Action de cada arquivo de recurso incorporado para fazer com que o recurso para compilar em um assembly satélite. No entanto, se você estiver usando os arquivos de recurso apenas para localizar a marcação, você pode, opcionalmente, alterar ação de compilação ao conteúdo para impedir que o arquivo que está sendo compilado no assembly principal do aplicativo.  
  
 Substitua todas as cadeias de caracteres de propriedade embutida na sua marcação ASPX de páginas e controles com uma expressão no seguinte formato:  
  
```  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Por exemplo:  
  
```  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Para ASPX como texto, use uma expressão no seguinte formato:  
  
```  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Por exemplo:  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Para obter mais informações, consulte [como: localizar ASPX marcação](../sharepoint/how-to-localize-aspx-markup.md).  
  
### <a name="localizing-code"></a>Localizando o código  
 Além de localização de cadeias de caracteres de recurso e [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] marcação, você também precisa localizar as cadeias de caracteres de mensagem e cadeias de caracteres de erro que aparecem no código de sua solução. Localizados informativas e mensagens de erro estão contidas em assemblies de satélite. Assemblies satélites contêm cadeias de caracteres que são visíveis aos usuários, como [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] exceções, como mensagens de texto e de saída.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]usa o modelo padrão de hub e spoke do .NET Framework. O hub ou o assembly de programa principal contém os recursos de idioma padrão. Raios ou assemblies de satélite, contêm os recursos específicos do idioma. Para obter mais informações, consulte [Empacotamento e implantação de recursos](http://go.microsoft.com/fwlink/?LinkId=179280). Assemblies de satélite são compilados dos arquivos de recursos (. resx). Quando você adicionar arquivos de recursos específicos de idioma para o projeto e o pacote de solução, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compila os arquivos de recurso em assemblies de satélite chamados *nome do projeto*. Resources.  
  
 Como com marcação ASPX, localizar o código de aplicativo do SharePoint, adicionando itens de projeto de arquivos de recursos separados para seu projeto. um para o idioma padrão e uma para cada idioma de localizado. No entanto, conforme mencionado anteriormente, se você já tiver arquivos de recursos para localizar marcação ASPX, você pode reutilizá-los para localização de código. Se você precisar criar arquivos de recursos, nomeie o arquivo de recurso de idioma padrão de sua escolha concatenada com uma extensão. resx. Nomeie os arquivos de recurso localizado o mesmo nome anexado com a cultura de idioma específico [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Defina a propriedade de ação de compilação de cada arquivo de recurso para recurso inserido para habilitar a criação de conjuntos de recursos de satélite.  
  
 Para criar os assemblies de satélite, compilar o projeto e, em seguida, adicione os arquivos como assemblies adicionais por meio de **avançado** guia do **Package Designer**. Ao adicionar os assemblies, preceda uma cultura [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] pasta para o caminho de local, como de-DE\\*nome do Item de projeto*. Resources. Isso permite que o pacote contém arquivos que têm o mesmo nome.  
  
 No seu código, substitua as cadeias de caracteres codificadas com chamadas para o <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> método usando a seguinte sintaxe:  
  
```  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Para obter mais informações, consulte [como: Localizar código](../sharepoint/how-to-localize-code.md).  
  
#### <a name="web-part-code-localization"></a>Localização de código do Web Part  
 Web parts incluem um recurso de editor de propriedade personalizada que inclui os atributos de código que usam cadeias de caracteres codificadas, como WebDisplayName, categoria e WebDescription. Para substituir os valores de cadeia de caracteres para esses atributos, crie uma classe separada que deriva da classe do atributo. Nessas classes, defina a propriedade do atributo. A propriedade de atributo depende da classe base. Por exemplo, a propriedade do atributo WebDisplayName é DisplayNameValue e a propriedade do atributo WebDescription é DescriptionValue.  
  
 Na classe derivada, referencie a ID de cadeia de caracteres do arquivo de recurso e o objeto de ResourceManager para obter o valor localizado para a ID da cadeia de caracteres. Esse valor de retorno para o atributo do editor de propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [Como: localizar um recurso](../sharepoint/how-to-localize-a-feature.md)   
 [Como: localizar marcação ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Como: Localizar código](../sharepoint/how-to-localize-code.md)   
 [Como: adicionar um arquivo de recurso](../sharepoint/how-to-add-a-resource-file.md)   
 [Como usar um arquivo de recurso para especificar nomes localizados, propriedades e permissões](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
  