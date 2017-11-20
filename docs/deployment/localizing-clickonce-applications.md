---
title: Localizando aplicativos ClickOnce | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, ClickOnce applications
- ClickOnce deployment, globalization
- deploying applications [ClickOnce], localizing ClickOnce applications
- localization, ClickOnce deployment
- ClickOnce deployment, download on-demand
- ClickOnce deployment, localization
- Windows Forms, ClickOnce applications
- console applications, ClickOnce applications
ms.assetid: c92b193b-054d-4923-834b-d4226a4c7a1a
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 60643d872594e9e868243adda33ae21a82dc7198
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="localizing-clickonce-applications"></a>Localização de aplicativos ClickOnce
A localização é o processo de tornar o aplicativo apropriado para uma cultura específica. Esse processo envolve a conversão de texto de interface de usuário para um idioma específico de região, usando a data correta e a formatação de moeda, ajuste o tamanho dos controles em um formulário, e controles de espelhamento da direita para a esquerda, se necessário.  
  
 Localizando os resultados de aplicativo na criação de um ou mais assemblies de satélite. Cada assembly contém cadeias de caracteres, imagens e outros recursos específicos para uma determinada cultura de interface do usuário. (O arquivo executável principal do aplicativo contém as cadeias de caracteres para a cultura padrão para seu aplicativo.)  
  
 Este tópico descreve três maneiras de implantar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para outras culturas:  
  
-   Inclua todos os assemblies satélite em uma única implantação.  
  
-   Gere uma implantação para cada cultura, com um assembly satélite único incluído em cada um.  
  
-   Baixe os assemblies satélite por demanda.  
  
## <a name="including-all-satellite-assemblies-in-a-deployment"></a>Incluindo todos os Assemblies satélite em uma implantação  
 Em vez de publicação de várias [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantações, você pode publicar um único [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação que contém todos os assemblies de satélite.  
  
 Esse método é o padrão em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para usar este método em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você não precisa fazer qualquer trabalho adicional.  
  
 Para usar esse método com MageUI.exe, você deve definir a cultura do seu aplicativo para **neutro** em MageUI.exe. Em seguida, você deve incluir manualmente todos os assemblies satélite em sua implantação. Em MageUI.exe, você pode adicionar os assemblies satélite usando o **popular** botão o **arquivos** guia de manifesto do aplicativo.  
  
 A vantagem dessa abordagem é que ele cria uma única implantação e simplifica a sua história de implantação localizada. Em tempo de execução, o assembly satélite será usado, dependendo da cultura padrão do sistema de operacional do Windows do usuário. Uma desvantagem dessa abordagem é que ele baixa todos os assemblies de satélite, sempre que o aplicativo é instalado ou atualizado em um computador cliente. Se seu aplicativo tiver um grande número de cadeias de caracteres, ou os clientes tenham uma conexão de rede lenta, esse processo pode afetar o desempenho durante a atualização do aplicativo.  
  
> [!NOTE]
>  Essa abordagem supõe que o seu aplicativo ajusta a altura, largura e a posição dos controles automaticamente para acomodar tamanhos de cadeia de caracteres de texto diferente em diferentes culturas. Windows Forms contém uma variedade de controles e tecnologias que permitem que você cria um formulário para torná-lo facilmente localizáveis, incluindo o <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel> controles, bem como a <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade.  Consulte também [como: localização de suporte no Windows Forms usando AutoSize e o controle TableLayoutPanel](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\)).  
  
## <a name="generate-one-deployment-for-each-culture"></a>Gerar uma implantação para cada cultura  
 Essa estratégia de implantação, você deve gerar várias implantações. Em cada implantação incluir somente o assembly satélite necessário para uma cultura específica e marcar a implantação mais específico para aquela cultura.  
  
 Para usar este método em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], defina o **idioma publicar** propriedade o **publicar** guia para a região desejada. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]incluirá automaticamente o assembly satélite necessário para a região que você selecionar e excluirá todos os outros assemblies de satélite da implantação.  
  
 Você pode realizar a mesma coisa usando a ferramenta de MageUI.exe no Microsoft [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Use o **popular** botão o **arquivos** guia de manifesto do aplicativo para excluir todos os outros assemblies de satélite do diretório de aplicativo e, em seguida, defina o **cultura**campo o **nome** guia para o manifesto de implantação no MageUI.exe. Essas etapas incluem não só o assembly satélite correto, mas também definem o `language` atributo no `assemblyIdentity` elemento em seu manifesto de implantação para a cultura correspondente.  
  
 Depois de publicar o aplicativo, você deve repetir esta etapa para cada cultura adicional sua oferece suporte a aplicativos. Você deve assegurar-se de que você publica em um diretório diferente do servidor Web ou o diretório de compartilhamento de arquivo sempre, porque cada manifesto de aplicativo fará referência a um assembly satélite diferentes, e cada manifesto de implantação tem um valor diferente para o `language`atributo.  
  
## <a name="downloading-satellite-assemblies-on-demand"></a>Baixando Assemblies satélite por demanda  
 Se você optar por incluir todos os assemblies satélite em uma única implantação, você pode melhorar o desempenho por meio de download sob demanda, que permite que você marcar assemblies como opcional. Os assemblies marcados não serão baixados quando o aplicativo é instalado ou atualizado. Você pode instalar os assemblies quando você precisar deles, chamando o <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> método sobre o <xref:System.Deployment.Application.ApplicationDeployment> classe.  
  
 Baixando assemblies satélite por demanda difere ligeiramente baixar outros tipos de assemblies por demanda. Para mais informações e exemplos de código sobre como habilitar esse cenário usando a [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] ferramentas para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consulte [passo a passo: baixando Assemblies satélite por demanda com a API de implantação do ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md).  
  
 Você também pode habilitar esse cenário no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Consulte também [passo a passo: baixando Assemblies satélite por demanda com o ClickOnce implantação API usando o Designer](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) ou [passo a passo: baixando Assemblies satélite por demanda com a API de implantação do ClickOnce Usando o Designer](http://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
## <a name="testing-localized-clickonce-applications-before-deployment"></a>Teste localizado aplicativos ClickOnce antes da implantação  
 Um assembly satélite será usado para um se somente de aplicativo do Windows Forms a <xref:System.Threading.Thread.CurrentUICulture%2A> propriedade para o thread principal do aplicativo é definida como a cultura do assembly satélite. Os clientes em locais mercados provavelmente já executará uma versão localizada do Windows com a cultura definida como o padrão apropriado.  
  
 Você tem três opções para implantações localizadas de teste antes de fazer seu aplicativo disponível aos clientes:  
  
-   Você pode executar sua [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo sobre as versões localizadas do Windows.  
  
-   Você pode definir o <xref:System.Threading.Thread.CurrentUICulture%2A> propriedade programaticamente no seu aplicativo. (Essa propriedade deve ser definida antes de chamar o <xref:System.Windows.Forms.Application.Run%2A> método.)  
  
## <a name="see-also"></a>Consulte também  
 [\<assemblyIdentity > elemento](../deployment/assemblyidentity-element-clickonce-deployment.md)   
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Globalizando o Windows Forms](/dotnet/framework/winforms/advanced/globalizing-windows-forms)