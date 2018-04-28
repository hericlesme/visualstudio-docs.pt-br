---
title: Arquitetura de personalizações no nível do documento | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- formats [Office development in Visual Studio]
- file formats [Office development in Visual Studio]
- vstoee.dll
- managed code extensions [Office development in Visual Studio], definition
- document-level customizations [Office development in Visual Studio]
- AddInLoader.dll
- architecture [Office development in Visual Studio], document-level customizations
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fb5ac7217ef1b217ef9909d833392ffa22093387
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="architecture-of-document-level-customizations"></a>Arquitetura de personalizações no nível do documento
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] inclui projetos para criar personalizações no nível de documento para o Microsoft Office Word e Microsoft Office Excel. Este tópico descreve os seguintes aspectos de personalizações no nível do documento:  
  
-   [Personalizações de Noções básicas sobre](#UnderstandingCustomizations)  
  
-   [Componentes de personalizações](#Components)  
  
-   [Como as personalizações trabalham com aplicativos do Microsoft Office](#HowCustomizationsWork)  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Para obter informações gerais sobre como criar personalizações no nível do documento, consulte [visão geral de desenvolvimento de soluções do Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md), [obtendo iniciado de programação em nível de documento personalizações para o Word ](../vsto/getting-started-programming-document-level-customizations-for-word.md), e [Introdução a personalizações no nível do documento da programação para Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md).  
  
##  <a name="UnderstandingCustomizations"></a> Noções básicas sobre personalizações  
 Quando você usa as ferramentas de desenvolvedor do Office no Visual Studio para criar uma personalização no nível do documento, você pode criar um assembly de código gerenciado que está associado um documento específico. Um documento ou a pasta de trabalho com um assembly vinculado deve ter extensões de código gerenciado. Para obter mais informações, consulte [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md).  
  
 Quando um usuário abre o documento, o assembly é carregado pelo aplicativo do Microsoft Office. Depois que o assembly é carregado, a personalização pode responder a eventos enquanto o documento está aberto. A personalização também pode chamar o modelo de objeto para automatizar e estender o aplicativo enquanto o documento está aberto, e ele pode usar qualquer uma das classes no [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
 O assembly se comunica com componentes COM, do aplicativo por meio do assembly de interoperabilidade primária do aplicativo. Para obter mais informações, consulte [Assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md) e [visão geral de desenvolvimento de soluções do Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 Se um usuário abre várias personalizações em nível de documento ao mesmo tempo, cada assembly é carregado em um domínio de aplicativo diferente. Isso significa que uma solução que se comporta incorretamente não pode fazer com que outras soluções de falha. Personalizações no nível do documento são projetadas para trabalhar com um único documento em um único domínio de aplicativo. Eles não são projetados para comunicação entre documentos. Para obter mais informações sobre domínios de aplicativo, consulte [domínios de aplicativo](/dotnet/framework/app-domains/application-domains).  
  
> [!NOTE]  
>  Personalizações no nível do documento que você cria usando as ferramentas de desenvolvedor do Office no Visual Studio são projetadas para ser utilizada somente quando o aplicativo é iniciado por um usuário final. Se o aplicativo for iniciado por meio de programação, por exemplo, usando a automação, a personalização pode não funcionar conforme o esperado.  
  
### <a name="design-time-and-run-time-experiences"></a>Experiências de tempo de design e tempo de execução  
 Para entender a arquitetura de personalizações no nível do documento, é importante para entender as experiências de criação de uma solução e da execução de uma solução.  
  
#### <a name="design-time"></a>Tempo de design  
 A experiência de tempo de design inclui as seguintes etapas:  
  
1.  O desenvolvedor cria um projeto no nível do documento em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. O projeto inclui o documento e o assembly que é executado por trás do documento. O documento talvez já exista (talvez criada por um designer) ou um novo documento pode ser criado juntamente com o projeto.  
  
2.  O designer — ou o desenvolvedor que cria o projeto ou outra pessoa — cria a aparência final do documento para o usuário final.  
  
#### <a name="run-time"></a>Tempo de execução  
 A experiência de tempo de execução inclui as seguintes etapas:  
  
1.  O usuário final abrir um documento ou a pasta de trabalho que tem extensões de código gerenciado.  
  
2.  O documento ou a pasta de trabalho carrega o assembly compilado.  
  
3.  O assembly responde a eventos como o usuário trabalha no documento ou pasta de trabalho.  
  
#### <a name="developer-and-end-user-perspective-compared"></a>Desenvolvedor e a perspectiva do usuário final em comparação comparada  
 Como funciona o desenvolvedor principalmente em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]e o usuário final funciona no Word ou Excel, há duas maneiras de compreender as personalizações no nível do documento.  
  
|Ponto de vista do desenvolvedor|Perspectiva do usuário final|  
|-----------------------------|----------------------------|  
|Usando [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], o desenvolvedor escreve o código que é acessível para o Word e Excel.<br /><br /> Embora possa parecer que o desenvolvedor está criando um arquivo executável que executa o Word ou Excel, o processo funciona na verdade o oposto. O documento está associado um assembly e contém um ponteiro para esse assembly. Quando o documento for aberto, Word ou Excel localiza o assembly e executa o código em resposta a todos os eventos processados.|Aqueles que usam a solução simplesmente abrir o documento ou a pasta de trabalho (ou criar um novo documento de um modelo) apenas como eles abriria qualquer outro arquivo do Microsoft Office.<br /><br /> O assembly fornece personalizações no documento ou pasta de trabalho como automaticamente populá-lo com dados atuais, ou mostrar uma caixa de diálogo para solicitar informações.|  
  
### <a name="supported-document-formats-for-document-level-customizations"></a>Formatos de documento suportados para personalizações no nível do documento  
 Quando você cria um projeto de personalização, você pode escolher o formato do documento que você deseja usar no projeto. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 A tabela a seguir lista os formatos de documentos, que você pode usar em personalizações no nível de documento para Excel e Word.  
  
|Excel|Palavra|  
|-----------|----------|  
|Pasta de trabalho do Excel (. xlsx)<br /><br /> Pasta habilitada para macro do Excel (. xlsm)<br /><br /> Pasta de trabalho binária do Excel (. xlsm)<br /><br /> Pasta de trabalho do Excel 97-2003 (. xls)<br /><br /> Modelo do Excel (. xltx)<br /><br /> Modelo habilitado para macro do Excel (. xltm)<br /><br /> Modelo do Excel 97-2003 (. xlt)|Documento do Word (. docx)<br /><br /> Documento habilitado para macro do Word (. docm)<br /><br /> Documento do Word 97-2003 (. doc)<br /><br /> Modelo do Word (. dotx)<br /><br /> Modelo habilitado para macro do Word (. dotm)<br /><br /> Modelo de Word 97-2003 (. dot)|  
  
 Você deve projetar extensões de código gerenciado apenas para documentos nos formatos com suporte. Caso contrário, determinados eventos não podem ser gerados quando o documento é aberto no aplicativo. Por exemplo, o <xref:Microsoft.Office.Tools.Excel.Workbook.Open> evento não será gerado quando você usa extensões de código gerenciado com pastas de trabalho salvadas no formato de planilha XML do Excel ou o formato de página da web (. htm,. HTML).  
  
### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>Suporte para documentos do Word que têm extensões de nome de arquivo. XML  
 Os modelos de projeto de nível de documento não permitem a criação de projetos com base nos seguintes formatos de arquivo:  
  
-   Documento XML do Word (* xml).  
  
-   Documento XML do Word 2003 (* xml).  
  
 Se desejar que os usuários finais para usar as personalizações nos seguintes formatos de arquivo, crie e implante uma personalização que usa um dos formatos de arquivo com suporte especificados na tabela acima. Depois de instalar a personalização, os usuários finais podem salvar o documento no documento XML do Word (* xml) formato ou o documento XML do Word 2003 (\*xml) formato e a personalização continuarão a funcionar como esperado.  
  
##  <a name="Components"></a> Componentes de personalizações  
 Os principais componentes de uma personalização são o documento e o assembly. Além desses componentes, há várias outras partes que desempenham um papel importante em como os aplicativos do Microsoft Office descobrirem e carregue as personalizações.  
  
### <a name="deployment-manifest-and-application-manifest"></a>O manifesto de implantação e o manifesto do aplicativo  
 Personalizações usam manifestos de aplicativo e manifestos de implantação para identificar e carregar a versão mais atual do assembly de personalização. A implantação do manifesto aponta para o manifesto do aplicativo atual. O aplicativo aponta para o assembly de personalização de manifesto e especifica a entrada ponto de classe (ou classes) para executar no assembly. Para obter mais informações, consulte [manifestos de aplicativo e implantação em soluções do Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
### <a name="visual-studio-tools-for-office-runtime"></a>O Visual Studio Tools for Office Runtime  
 Para executar as personalizações no nível do documento que são criadas usando as ferramentas de desenvolvedor do Office no Visual Studio, os computadores do usuário final devem ter o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instalado. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] inclui componentes não gerenciados que carregam o assembly de personalização e também um conjunto de assemblies gerenciados. Esses assemblies gerenciados fornecem o modelo de objeto que usa o código de personalização para automatizar e estender o aplicativo host.  
  
 Para obter mais informações, consulte [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
##  <a name="HowCustomizationsWork"></a> Como as personalizações trabalham com aplicativos do Microsoft Office  
 Quando um usuário abre um documento que faz parte de uma personalização do Microsoft Office, o aplicativo usa o manifesto de implantação que está vinculado ao documento para localizar e carregar a versão mais atual do assembly de personalização. O local do manifesto de implantação é armazenado em uma propriedade de documento personalizadas denominada assemblylocation. A cadeia de caracteres que identifica este local é inserida na propriedade quando você compila a solução.  
  
 Os pontos de manifesto da implantação para o manifesto de aplicativo, que aponta para o assembly mais recente. Para obter mais informações, consulte [manifestos de aplicativo e implantação em soluções do Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 A ilustração a seguir mostra a arquitetura básica de uma personalização no nível do documento.  
  
 ![Arquitetura de personalização do office 2007](../vsto/media/office07-custom.png "arquitetura de personalização do Office 2007")  
  
> [!NOTE]  
>  Em soluções do Office que se destinam a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], soluções chamarão o modelo de objeto do aplicativo host por usando as informações de tipo de assembly de interoperabilidade primária (PIA) que são inseridas no assembly solução, em vez de chamar o PIA diretamente. Para obter mais informações, consulte [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="loading-process"></a>Processo de carregamento  
 As seguintes etapas ocorrem quando um usuário abre um documento que é parte de uma solução do Microsoft Office.  
  
1.  O aplicativo do Microsoft Office verifica as propriedades de documento personalizadas para verificar se existem extensões de código gerenciado associadas com o documento. Para obter mais informações, consulte [visão geral de propriedades de documento personalizadas](../vsto/custom-document-properties-overview.md).  
  
2.  Se houver extensões de código gerenciado, o aplicativo carrega VSTOEE.dll, que carrega VSTOLoader.dll. Eles são gerenciados DLLs que são os componentes de carregador para o Visual Studio 2010 Tools for Office Runtime. Para obter mais informações, consulte [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
3.  VSTOLoader.dll carrega o [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] e inicia a parte gerenciada do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
4.  Se o documento for aberto de um local diferente do computador local, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verifica se o local do documento é o **locais confiáveis** lista no **definições** para Esse aplicativo específico do Office. Se o local do documento não estiver em um local confiável, a personalização não é confiável e o processo de carregamento será interrompido aqui.  
  
5.  O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instala a solução se ele ainda não foi instalado, baixa os manifestos de aplicativo e implantação mais recentes e executa uma série de verificações de segurança. Para obter mais informações, consulte [Protegendo soluções do Office](../vsto/securing-office-solutions.md).  
  
6.  Se a personalização é confiável para ser executado, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usa o manifesto de implantação e o manifesto do aplicativo para verificar se há atualizações do assembly. Se uma nova versão do assembly está disponível, o tempo de execução baixa a nova versão do assembly para o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] cache no computador cliente. Para obter mais informações, consulte [implantar uma solução Office](../vsto/deploying-an-office-solution.md).  
  
7.  O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] cria um novo domínio de aplicativo no qual carregar o assembly de personalização.  
  
8.  O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] carrega o assembly de personalização para o domínio de aplicativo.  
  
9. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chama o **inicialização** manipulador de eventos em seu assembly de personalização. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md)  
  
## <a name="see-also"></a>Consulte também  
 [Arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Ferramentas do Visual Studio para visão geral de tempo de execução do Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Protegendo soluções do Office](../vsto/securing-office-solutions.md)   
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)   
 [Visão geral de propriedades de documento personalizadas](../vsto/custom-document-properties-overview.md)   
 [Dados armazenados em cache em personalizações no nível do documento](../vsto/cached-data-in-document-level-customizations.md)  
  
  