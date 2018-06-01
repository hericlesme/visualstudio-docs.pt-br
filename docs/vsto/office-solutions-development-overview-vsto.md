---
title: Visão geral do desenvolvimento de soluções Office (VSTO)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies, Office
- Office development in Visual Studio, about developing solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 41fe3ab24b3b70c4cef596caa35c0b4173aaa8fd
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34694024"
---
# <a name="office-solutions-development-overview-vsto"></a>Visão geral do desenvolvimento de soluções Office (VSTO)
  Ao usar o Microsoft Office como front-end para soluções, você pode tirar proveito das ferramentas, como os recursos de processamento de texto no Word, os recursos de análise de dados do Excel e os recursos de gerenciamento de email do Outlook e interfaces de usuário do Microsoft Office familiar . Você pode desenvolver soluções no Visual Studio para personalizar os aplicativos do Office e adicionar os recursos específicos que necessários para seus processos de negócios. Por exemplo, você pode transformar palavras em um gerador de contrato que monta contratos fora das partes pré-existentes que podem ser feitas editável ou não editável. Com o Excel, você pode criar uma planilha de orçamento automatizada personalizada para projetos diferentes. Os usuários também podem tirar soluções do office offline, que torna mais prático do que seria se você usar uma arquitetura baseada na web a soluções complexas.  
  
 Este tópico fornece uma visão geral dos tipos de soluções do Office que você pode criar usando o Visual Studio Tools para modelos do Office (VSTO) disponíveis nas ferramentas de desenvolvedor do Office no Visual Studio. Para obter informações gerais sobre como desenvolver com o Office, consulte o [Central de desenvolvedores do Office](https://dev.office.com/).  
  
## <a name="choose-an-office-project-type"></a>Escolha um tipo de projeto do Office  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fornece os seguintes tipos de modelos de projeto para desenvolvimento do Office com base em VSTO:  
  
-   **Personalizações no nível do documento** estão associados um documento específico.  
  
-   **Suplementos do VSTO** estão associados com o aplicativo em si.  
  
 Para decidir qual desses tipos de projeto é melhor para sua solução, lembre-se você deseja que seu código seja executado somente quando um documento específico está aberto ou se você deseja que o código esteja disponível sempre que o aplicativo está em execução. Para obter mais informações sobre os modelos de projeto, consulte [visão geral de modelos de projeto do Office](../vsto/office-project-templates-overview.md).  
  
 Os tipos de projetos, que você pode criar dependem de quais aplicativos do Office que você instalou no computador de desenvolvimento. Para obter mais informações, consulte [recursos disponíveis por tipo de projeto e de aplicativo do Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
### <a name="document-level-customizations"></a>Personalizações no nível de documento  
 Personalizações no nível do documento consistem em um assembly que está associado um único documento, a pasta de trabalho ou o modelo no Microsoft Office Word ou o Microsoft Office Excel. O assembly é carregado quando o documento associado é aberto. Recursos que você criar personalizações estão disponíveis somente quando o documento associado é aberto. As personalizações não podem fazer alterações em todo o aplicativo, como exibir uma nova guia de faixa de opções ou de item de menu quando qualquer documento está aberto.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inclui ferramentas para ajudá-lo a criar personalizações no nível do documento. O documento que você personalizar hospedado como uma superfície de design em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], que permite que o documento de design arrastando e soltando os controles nele. Muitos outros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] recursos estão disponíveis em projetos de nível de documento, como os controles de formulários do Windows, associação de dados de arrastar e soltar e um depurador integrado.  
  
 Para obter mais informações sobre personalizações, consulte os tópicos a seguir:  
  
-   [Começar a programar personalizações no nível de documento para Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)  
  
-   [Introdução a personalizações no nível de documento para Word de programação](../vsto/getting-started-programming-document-level-customizations-for-word.md)  
  
-   [Arquitetura de personalizações no nível do documento](../vsto/architecture-of-document-level-customizations.md)  
  
### <a name="vsto-add-ins"></a>Suplementos do VSTO  
 Suplementos do VSTO consistem em um assembly que está associado um aplicativo do Microsoft Office. Normalmente, o suplemento do VSTO é executado quando o aplicativo associado é iniciado, embora os usuários também podem carregar suplementos do VSTO depois que o aplicativo já está em execução. Recursos em suplementos do VSTO que você cria estão disponíveis para o aplicativo em si, independentemente de qual documentos estiverem abertos.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inclui ferramentas para ajudá-lo a criar suplementos do VSTO. Projetos de suplemento inclui uma classe gerada automaticamente que representa o suplemento do VSTO. Essa classe fornece propriedades e eventos que você pode usar para acessar o modelo de objeto do aplicativo host e executar o código quando o suplemento do VSTO é carregado e desligar. Muitos outros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] recursos estão disponíveis em projetos do suplemento do VSTO, como formulários do Windows e um depurador integrado.  
  
 Para obter mais informações sobre os suplementos do VSTO, consulte os tópicos a seguir:  
  
-   [Introdução à programação de suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
-   [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Automatizar aplicativos do Office usando assemblies de interoperabilidade primários  
 Programaticamente, você pode incorporar os recursos de um aplicativo do Office em sua solução, escrevendo código que acessa o modelo de objeto do aplicativo. Modelos de objeto são uma organização de classes que expõem a funcionalidade por meio de várias propriedades e métodos. O modelo de objeto para cada aplicativo do Office é diferente.  
  
 Para usar o modelo de objeto de um aplicativo do Office em uma solução criada usando as ferramentas de desenvolvimento do Office em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], você deve usar o assembly de interoperabilidade primária (PIA) para o aplicativo. O PIA permite que o código gerenciado em sua solução para interagir com base em objeto modelo o aplicativo do Office.  
  
 Você deve ter os PIAs do Office instalado e registrado no cache de assembly global em seu computador de desenvolvimento para executar a maioria das tarefas de desenvolvimento. Para obter mais informações, consulte [configurar um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md). PIAs do Office não são necessárias em computadores de usuários finais para executar soluções do Office do VSTO. Para obter mais informações, consulte [Design e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md).  
  
 Para obter mais informações sobre como usar os PIAs em soluções do Office do VSTO, consulte os tópicos a seguir:  
  
-   [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)  
  
-   [Assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md)  
  
## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Executar soluções do Microsoft Office do VSTO em computadores de usuários finais  
 Quando você cria uma solução VSTO, considere como os requisitos de implantação podem afetar suas escolhas de desenvolvimento.  
  
### <a name="deployment-options"></a>Opções de implantação  
 Usar o ClickOnce ou o Windows Installer para implantar soluções que você cria usando as ferramentas de desenvolvimento do Office em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Implantação ClickOnce permite que você crie soluções de atualização automática que podem ser instaladas e executadas com mínima interação do usuário. Windows Installer (*. msi*) arquivos podem ser facilmente distribuídos aos computadores de usuário final ou distribuídos usando o Systems Management Server (SMS). Para obter mais informações sobre como implantar soluções do Office do VSTO, consulte [implantar uma solução do Office](../vsto/deploying-an-office-solution.md).  
  
### <a name="install-prerequisites"></a>Instalar pré-requisitos  
 Antes dos usuários finais podem executar uma solução que você cria usando as ferramentas de desenvolvimento do Office no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], seus computadores devem ter certos pré-requisitos instalados. Se você implantar sua solução usando o ClickOnce ou criando um arquivo do Windows Installer, esses pré-requisitos podem ser instalados com sua solução. Para obter mais informações, consulte [pré-requisitos de solução do Office para implantação](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e) e [como: instalar pré-requisitos em computadores de usuário final para executar soluções do Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
### <a name="security"></a>Segurança  
 Para soluções do Office do VSTO é imposta por uma série de verificações de segurança que o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] faz quando ele é instalado e carrega a solução. Essas verificações incluem verificar se o local do manifesto de implantação é confiável ou se o certificado usado para assinar o manifesto de implantação é confiável. Para obter mais informações, consulte [soluções do Office Secure](../vsto/securing-office-solutions.md).  
  
## <a name="see-also"></a>Consulte também  
 [Introdução &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Arquitetura de personalizações no nível do documento](../vsto/architecture-of-document-level-customizations.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Começar a programar personalizações no nível de documento para Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Introdução a personalizações no nível de documento para Word de programação](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [Introdução à programação de suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  