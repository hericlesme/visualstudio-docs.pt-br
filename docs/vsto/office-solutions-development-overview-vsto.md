---
title: Visão geral do desenvolvimento de soluções Office (VSTO) | Microsoft Docs
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
ms.openlocfilehash: f36b75b8c8c3cde4441520819ab566696d1d9066
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="office-solutions-development-overview-vsto"></a>Visão geral do desenvolvimento de soluções do Office (VSTO)
  Ao usar o Microsoft Office como front-end para soluções, você pode tirar proveito das ferramentas, como os recursos de processamento de texto no Word, os recursos de análise de dados do Excel e os recursos de gerenciamento de email do Outlook e interfaces de usuário do Microsoft Office familiar . Você pode desenvolver soluções no Visual Studio para personalizar os aplicativos do Office e adicionar os recursos específicos que necessários para seus processos de negócios. Por exemplo, você pode transformar palavras em um gerador de contrato que monta contratos fora das partes pré-existentes que podem ser feitas editável ou não editável. Com o Excel, você pode criar uma planilha de orçamento automatizada personalizada para projetos diferentes. Os usuários também podem tirar soluções do office offline, que torna mais prático do que seria se você usar uma arquitetura baseada na web a soluções complexas.  
  
 Este tópico fornece uma visão geral dos tipos de soluções do Office que você pode criar usando o Visual Studio Tools para modelos do Office (VSTO) disponíveis nas ferramentas de desenvolvedor do Office no Visual Studio. Para obter informações gerais sobre como desenvolver com o Office, consulte o [Office Developer Center](https://dev.office.com/).  
  
## <a name="choosing-an-office-project-type"></a>Escolhendo um tipo de projeto do Office  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fornece os seguintes tipos de modelos de projeto para desenvolvimento do Office com base em VSTO:  
  
-   **Personalizações no nível do documento** estão associados um documento específico.  
  
-   **Suplementos do VSTO** estão associados com o aplicativo em si.  
  
 Para decidir qual desses tipos de projeto é melhor para sua solução, lembre-se você deseja que seu código seja executado somente quando um documento específico está aberto ou se você deseja que o código esteja disponível sempre que o aplicativo está em execução. Para obter mais informações sobre os modelos de projeto, consulte [visão geral de modelos de projeto do Office](../vsto/office-project-templates-overview.md).  
  
 Os tipos de projetos, que você pode criar dependem de quais aplicativos do Office que você instalou no computador de desenvolvimento. Para obter mais informações, consulte [recursos disponibilizados pelo aplicativo do Office e pelo tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md).  
  
### <a name="document-level-customizations"></a>Personalizações no nível de documento  
 Personalizações no nível do documento consistem em um assembly que está associado um único documento, a pasta de trabalho ou o modelo no Microsoft Office Word ou o Microsoft Office Excel. O assembly é carregado quando o documento associado é aberto. Recursos que você criar personalizações estão disponíveis somente quando o documento associado é aberto. As personalizações não podem fazer alterações em todo o aplicativo, como exibir uma nova guia de faixa de opções ou de item de menu quando qualquer documento está aberto.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inclui ferramentas para ajudá-lo a criar personalizações no nível do documento. O documento que você personalizar hospedado como uma superfície de design em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], que permite que o documento de design arrastando e soltando os controles nele. Muitos outros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] recursos estão disponíveis em projetos de nível de documento, como os controles de formulários do Windows, associação de dados de arrastar e soltar e um depurador integrado.  
  
 Para obter mais informações sobre personalizações, consulte os tópicos a seguir:  
  
-   [Introdução a personalizações no nível de documento da programação para Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)  
  
-   [Introdução a personalizações no nível de documento da programação para Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)  
  
-   [Arquitetura de personalizações no nível do documento](../vsto/architecture-of-document-level-customizations.md)  
  
### <a name="vsto-add-ins"></a>Suplementos do VSTO  
 Suplementos do VSTO consistem em um assembly que está associado um aplicativo do Microsoft Office. Normalmente, o suplemento do VSTO é executado quando o aplicativo associado é iniciado, embora os usuários também podem carregar suplementos do VSTO depois que o aplicativo já está em execução. Recursos em suplementos do VSTO que você cria estão disponíveis para o aplicativo em si, independentemente de qual documentos estiverem abertos.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inclui ferramentas para ajudá-lo a criar suplementos do VSTO. Projetos de suplemento inclui uma classe gerada automaticamente que representa o suplemento do VSTO. Essa classe fornece propriedades e eventos que você pode usar para acessar o modelo de objeto do aplicativo host e executar o código quando o suplemento do VSTO é carregado e desligar. Muitos outros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] recursos estão disponíveis em projetos do suplemento do VSTO, como formulários do Windows e um depurador integrado.  
  
 Para obter mais informações sobre os suplementos do VSTO, consulte os tópicos a seguir:  
  
-   [Introdução aos suplementos de programação VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
-   [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
## <a name="automating-office-applications-by-using-primary-interop-assemblies"></a>Automatizando aplicativos do Office usando Assemblies de interoperabilidade primários  
 Programaticamente, você pode incorporar os recursos de um aplicativo do Office em sua solução, escrevendo código que acessa o modelo de objeto do aplicativo. Modelos de objeto são uma organização de classes que expõem a funcionalidade por meio de várias propriedades e métodos. O modelo de objeto para cada aplicativo do Office é diferente.  
  
 Para usar o modelo de objeto de um aplicativo do Office em uma solução criada usando as ferramentas de desenvolvimento do Office em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], você deve usar o assembly de interoperabilidade primária (PIA) para o aplicativo. O PIA permite que o código gerenciado em sua solução para interagir com base em objeto modelo o aplicativo do Office.  
  
 Você deve ter os PIAs do Office instalado e registrado no cache de assembly global em seu computador de desenvolvimento para executar a maioria das tarefas de desenvolvimento. Para obter mais informações, consulte [Configurando um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md). PIAs do Office não são necessárias em computadores de usuários finais para executar soluções do Office do VSTO. Para obter mais informações, consulte [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md).  
  
 Para obter mais informações sobre como usar os PIAs em soluções do Office do VSTO, consulte os tópicos a seguir:  
  
-   [Escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md)  
  
-   [Assemblies de interoperabilidade primários do Office](../vsto/office-primary-interop-assemblies.md)  
  
## <a name="running-microsoft-vsto-office-solutions-on-end-user-computers"></a>Executando soluções do VSTO do Microsoft Office em computadores de usuário final  
 Quando você cria uma solução VSTO, considere como os requisitos de implantação podem afetar suas escolhas de desenvolvimento.  
  
### <a name="deployment-options"></a>Opções de implantação  
 Usar o ClickOnce ou o Windows Installer para implantar soluções que você cria usando as ferramentas de desenvolvimento do Office em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Implantação ClickOnce permite que você crie soluções de atualização automática que podem ser instaladas e executadas com mínima interação do usuário. Arquivos do Windows Installer (. msi) podem ser facilmente distribuídos aos computadores de usuário final ou distribuídos usando o Systems Management Server (SMS). Para obter mais informações sobre como implantar soluções do Office do VSTO, consulte [implantar uma solução Office](../vsto/deploying-an-office-solution.md).  
  
### <a name="installing-prerequisites"></a>Instalar os pré-requisitos  
 Antes dos usuários finais podem executar uma solução que você cria usando as ferramentas de desenvolvimento do Office no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], seus computadores devem ter certos pré-requisitos instalados. Se você implantar sua solução usando o ClickOnce ou criando um arquivo do Windows Installer, esses pré-requisitos podem ser instalados com sua solução. Para obter mais informações, consulte [pré-requisitos de solução do Office para implantação](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e) e [como: instalar pré-requisitos em computadores de usuário final para executar soluções do Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
### <a name="security"></a>Segurança  
 Para soluções do Office do VSTO é imposta por uma série de verificações de segurança que o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] faz quando ele é instalado e carrega a solução. Essas verificações incluem verificar se o local do manifesto de implantação é confiável ou se o certificado usado para assinar o manifesto de implantação é confiável. Para obter mais informações, consulte [Protegendo soluções do Office](../vsto/securing-office-solutions.md).  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Introdução &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Arquitetura de personalizações no nível do documento](../vsto/architecture-of-document-level-customizations.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Introdução a personalizações no nível do documento da programação para Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Introdução a personalizações no nível do documento da programação para Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [Introdução aos suplementos de programação VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  