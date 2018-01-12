---
title: Criando Web Parts do SharePoint | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d0c5acfac06702894f67a8bfc1547462a0069e15
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="creating-web-parts-for-sharepoint"></a>Criando Web Parts para SharePoint
  Usando web parts, você pode modificar o conteúdo, a aparência e o comportamento das páginas de um site do SharePoint usando um navegador. Web parts são controles do servidor que é executado dentro de uma página de web part: eles são os blocos de construção de páginas que aparecem em um site do SharePoint. Consulte [blocos de construção: Web Parts](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 Você pode criar e depurar web parts em um site do SharePoint usando modelos do Visual Studio.  
  
## <a name="creating-a-web-part-in-visual-studio"></a>Criando uma Web Part no Visual Studio  
 Criar uma web part, adicionando um **Web Part** item a qualquer projeto do SharePoint. Você pode usar um **Web Part** item em uma solução em modo seguro ou uma solução de farm.  
  
 Se você quiser criar uma web part visualmente usando um designer, crie um **Web Part Visual** ou adicione **Web Part Visual** item a qualquer projeto do SharePoint. Você pode usar um **Web Part Visual** item em uma solução de farm.  
  
### <a name="web-part-item"></a>Item da Web Part  
 Um **Web Part** item fornece os arquivos que você pode usar para criar uma web part para um site do SharePoint. Quando você adiciona um **Web Part** item, o Visual Studio cria uma pasta em seu projeto e, em seguida, adiciona vários arquivos na pasta. A tabela a seguir descreve cada arquivo.  
  
|Arquivo|Descrição|  
|----------|-----------------|  
|Elements|Contém informações que o arquivo de definição de recurso em seu projeto usa para implantar a web part.|  
|arquivo. WebPart|Fornece informações que precisa para exibir a web part em uma galeria de web parts de SharePoint.|  
|Arquivo de código|Contém métodos que adicionar controles para a web part e que geram conteúdo personalizado dentro da web part.|  
  
 Para obter mais informações, consulte [como: criar uma Web Part do SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### <a name="visual-web-part-item"></a>Item da Web Part Visual  
 Uma web part visual é uma web part que você cria usando o designer Visual Web Developer no Visual Studio. Uma web part visual funciona como qualquer outra web part. Para adicionar controles, como botões e caixas de texto, a uma web part, você pode adicionar código para um arquivo XML. No entanto, você adicionar controles a uma web part visual arrastando ou copiá-los para a web part do Visual Studio **caixa de ferramentas**. O designer, em seguida, gera o código necessário no arquivo XML. Consulte [como: criar uma Web Part do SharePoint usando um Designer](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## <a name="sharepoint-controls"></a>Controles do SharePoint  
 Visual Studio fornece alguns controles para a criação de páginas do SharePoint, como as páginas de aplicativo. Esses controles aparecem no **caixa de ferramentas** em **controles do SharePoint**. A funcionalidade desses controles deriva o [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) namespace, que contém os controles de servidor ASP.NET que são usados em páginas de site e de lista do SharePoint.  
  
|Nome do controle|Descrição|  
|------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Insere um menu do ASP. Para obter mais informações, consulte [visão geral do controle de Menu](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Insere um **LINK** elemento na página. aspx e aplica um ou mais folhas de estilos externas definidas pelo **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Insere um controle de DateTime na página. aspx.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Insere uma validação de segurança na página. aspx|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Retorna uma propriedade de uma lista especificada.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Retorna uma propriedade global do site atual.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Insere um link para um RSS feed na página. aspx.|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Fornece propriedades e métodos para o registro de recursos, como scripts, em uma página para que eles podem ser solicitados quando a página é renderizada.|  
|[Tema](http://go.microsoft.com/fwlink/?LinkId=235314)|Aplica um tema para a página. aspx.|  
  
## <a name="debugging-a-web-part"></a>Depurando uma Web Part  
 Você pode depurar um projeto do SharePoint que contém uma web part exatamente como você faria para depurar outros projetos do Visual Studio. Quando você inicia o depurador do Visual Studio, o Visual Studio abrirá o site do SharePoint.  
  
 Para começar a depurar seu código, adicione a web part a uma página de web part no SharePoint.  
  
 Para obter mais informações sobre como depurar projetos do SharePoint, consulte [Solucionando problemas de soluções do SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="visual-web-part-limitations"></a>Limitações da Web Part Visual  
 A partir do Visual Studio, você pode adicionar partes da web do visual para soluções em modo seguro do SharePoint e soluções de farm. No entanto, o visual web parts têm as seguintes limitações:  
  
-   Partes do Visual web não dão suporte a parâmetros substituíveis. Para obter mais informações, consulte [parâmetros substituíveis](../sharepoint/replaceable-parameters.md).  
  
-   Controles de usuário ou visual de web parts não podem ser arrastados e descartadas ou copiados em partes da web do visual. Essa ação faz com que um erro de compilação.  
  
-   Partes do Visual web diretamente não oferecem suporte a tokens de servidor do SharePoint como $SPUrl. Para obter mais informações, consulte "Token restrições em área restrita Visual Web Parts" no tópico [Solucionando problemas de soluções do SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
-   Visual web parts na solução de área restrita ocasionalmente receber o erro, "a solicitação de execução de código em modo seguro foi recusada porque o serviço de Host do código em modo seguro estava muito ocupado para processar a solicitação". Para obter mais informações sobre esse erro, consulte esta postagem no [Blog da equipe do SharePoint Developer](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
-   Depuração de JavaScript do lado do servidor não tem suporte no Visual Studio, mas há suporte para depuração de JavaScript do lado do cliente.  
  
     Embora você possa adicionar embutido JavaScript em um arquivo de marcação do lado do servidor, depuração não tem suporte para pontos de interrupção adicionados a marcação. Para depurar o JavaScript, fazer referência a um arquivo JavaScript externo no arquivo de marcação e, em seguida, defina os pontos de interrupção no arquivo de JavaScript.  
  
-   Depuração de embutido [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] código deve ser feito no arquivo de código gerado em vez de no arquivo de marcação.  
  
-   Partes do web Visual não suportam o uso da `<@ Assembly Src=` diretiva.  
  
-   SharePoint controles da web e alguns [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] controles não são suportados no ambiente de área restrita do SharePoint. Se não há suporte para os controles são usados em uma web part visual em uma solução em modo seguro, o erro "O nome do namespace ou tipo 'Theme' não existe no namespace 'Microsoft.SharePoint.WebControls'" será exibida.  
  
 Para obter mais informações sobre soluções em modo seguro, consulte [diferenças entre em modo seguro e soluções de Farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="creating-older-style-sharepoint-based-web-parts"></a>Criando Web Parts com Base no SharePoint em Estilo Mais Antigo  
 Você pode usar os modelos no Visual Studio para criar personalizado [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] web parts do SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)]partes da Web são criados sobre o [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] infra-estrutura de web part e são o tipo recomendado para novos projetos.  
  
 Em alguns raros casos, você terá que criar uma web part usando o mais antigo baseado no SharePoint web Parts. Você pode usar o Visual Studio para criar esses tipos de web parts, mas o Visual Studio não fornece qualquer modelos que são projetados especificamente para ajudá-lo a criá-los.  
  
 Para obter mais informações sobre quando você talvez queira criar um estilo antigo baseado no SharePoint web parts, consulte [infra-estrutura de parte da Web no Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290). Para obter mais informações sobre como criar uma web part usando o mais antigo baseado no SharePoint web parts, consulte [passo a passo, criar uma Web Part do SharePoint básico](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Como criar um Web Part para o SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Mostra como criar web parts para as páginas do SharePoint.|  
|[Como criar um Web Part do SharePoint usando um designer](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Mostra como criar web parts para SharePoint usando uma superfície de design visual.|  
|[Como criar um controle de usuário para uma página de aplicativo do SharePoint ou Web Part](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Mostra como criar controles reutilizáveis e personalizados que podem ser consumidos por páginas de aplicativos e web parts que são executados no SharePoint.|  
|[Instruções passo a passo: criando um Web Part para o SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Descreve como criar uma web part do SharePoint.|  
|[Instruções passo a passo: criando um Web Part para o SharePoint usando um designer](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Descreve como criar uma web part para SharePoint arrastando controles a uma superfície de design visual.|  
|[Instruções passo a passo: criando um Web Part do Silverlight que exiba OData para o SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Descreve como criar uma web part do SharePoint que hospeda um aplicativo do Silverlight e exibe dados de listas do SharePoint.|  
  
  