---
title: "Caixa de diálogo Pré-requisitos | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 2ea735e5e300d2b2cde301a4cf52424cabbba934
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="prerequisites-dialog-box"></a>Caixa de diálogo Pré-requisitos

Essa caixa de diálogo especifica quais componentes de pré-requisito são instalados, como eles são instalados e em qual ordem os pacotes são instalados.

Para acessar essa caixa de diálogo, selecione um nó do projeto no **Gerenciador de Soluções** e, no menu **Projeto**, clique em **Propriedades**. Quando o **Designer de Projeto** for exibido, clique na guia **Publicar**. Na página **Publicar**, clique em **Pré-requisitos**. Para projetos de Instalação, no menu **Projeto**, clique em **Propriedades**. Quando a caixa de diálogo **Páginas de Propriedades** for exibida, clique em **Pré-requisitos**.

## <a name="uielement-list"></a>Lista UIElement

|Elemento|Descrição|
|-------------|-----------------|
|**Criar programa de instalação para instalar os componentes de pré-requisitos**|Inclui os componentes de pré-requisito no programa de instalação do aplicativo (Setup.exe) para que eles sejam instalados antes do aplicativo, na ordem de dependência. Por padrão, essa opção é selecionada. Se ela não for selecionada, nenhum Setup.exe será criado.|
|**Escolher quais pré-requisitos serão instalados**|Especifica se os componentes são instalados, como [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)], Crystal Reports e assim por diante.<br /><br /> Por exemplo, ao selecionar a caixa de seleção ao lado de **SQL Server 2005 Express Edition SP2**, você especifica que o programa de instalação verifica se esse componente é instalado no computador de destino e o instala se ele ainda não estiver instalado.<br /><br /> Para obter informações detalhadas sobre cada pacote de pré-requisitos, consulte a tabela de Informações de pré-requisitos adiante neste tópico.|
|**Verificar mais componentes redistribuíveis no Microsoft Update**|Ao clicar nesse link, você será levado para o site [pacotes de bootstrapper para redistribuir componentes](http://go.microsoft.com/fwlink/?LinkId=208835) para verificar se há atualizações.|
|**Baixar os pré-requisitos no site do fornecedor do componente**|Especifica que os componentes de pré-requisitos são instalados por meio do site do fornecedor. Esta é a opção padrão.|
|**Baixar os pré-requisitos no mesmo local do meu aplicativo**|Especifica que os componentes de pré-requisitos são instalados por meio do mesmo local que o aplicativo. Isso copia todos os pacotes de pré-requisitos no local de publicação. Para que essa opção funcione, os pacotes do pré-requisito devem estar no computador de desenvolvimento.|
|**Baixar os pré-requisitos no seguinte local**|Especifica que os componentes de pré-requisitos são instalados por meio do local selecionado. É possível usar o botão **Procurar** para selecionar um local.|

## <a name="prerequisites-information"></a>Informações de pré-requisitos

Os componentes de pré-requisitos exibidos na caixa de diálogo **Pré-requisitos** podem ser diferentes daqueles da lista a seguir. Os pacotes de pré-requisitos listados na **Caixa de diálogo Pré-requisitos** são definidos automaticamente na primeira vez em que a caixa de diálogo é aberta. Se você alterar posteriormente a estrutura de destino do projeto, será necessário selecionar os pré-requisitos manualmente para corresponder à nova estrutura de destino.

|Elemento|Descrição|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Esse pacote instala o seguinte:<br /><br /> -   .NET Framework versões 2.0, 3.0 e 3.5.<br />-   Suporte para todas as versões do .NET Framework em sistemas operacionais de 32 bits (x86) e 64 bits (x64).<br />-   Pacotes de idiomas para cada versão do .NET Framework que é instalada com o pacote.<br />-   Service packs para o .NET Framework 2.0 e 3.0.<br /><br /> O .NET Framework 3.0 está incluído no Windows Vista e o .NET Framework 3.5 está incluído no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. O .NET Framework 3.5 é necessário para todos os projetos do Visual Basic e C# que são compilados para sistemas operacionais de 32 bits e para quais a estrutura de destino é definida como **.NET Framework 3.5**, bem como para projetos do Visual Basic e C# compilados para sistemas operacionais de 64 bits. (Não há suporte para o IA64.) Observe que os projetos do Visual Basic e do C# são compilados para qualquer arquitetura de CPU, por padrão. Para saber mais, consulte [Visão geral de multissegmentação do Visual Studio](../../ide/visual-studio-multi-targeting-overview.md) e [Pré-requisitos de implantação para aplicativos de 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Por padrão, esse item está selecionado.|
|**Microsoft .NET Framework 4.x**|Esse pacote instala o .NET Framework 4.x para as plataformas x86 e x64.|
|**Microsoft System CLR Types para SQL Server 2014 (x64 e x86)**|Este pacote instala o Microsoft System CLR Types para SQL Server 2014 para x64 ou x86.|
|**SQL Server 2008 R2 Express**|Esse pacote instala o Microsoft SQL Server 2008 R2 Express, uma edição gratuita do Microsoft SQL Server 2008 R2, um banco de dados ideal para aplicativos Web, de servidor ou de área de trabalho pequenos. Pode ser usado gratuitamente para desenvolvimento e produção.|
|**SQL Server 2012 Express**|Este pacote instala o Microsoft SQL Server 2012 Express.|
|**SQL Server 2012 Express LocalDB**|Este pacote instala o Microsoft SQL Server 2012 Express LocalDB.|
|**Bibliotecas de Tempo de Execução do Visual C++ "14" (ARM)**|Esse pacote instala as bibliotecas em tempo de execução Visual C++ para a arquitetura Itanium, que fornecem rotinas de programação para o sistema operacional Microsoft Windows. Essas rotinas automatizam várias tarefas comuns de programação que não são fornecidas pelas linguagens C e C++.<br /><br /> Para obter mais informações, consulte [Referência da biblioteca em tempo de execução C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Bibliotecas de Tempo de Execução do Visual C++ "14" (x64)**|Esse pacote instala as bibliotecas em tempo de execução Visual C++ para os sistemas operacionais x64, que fornecem rotinas de programação para o sistema operacional Microsoft Windows. Essas rotinas automatizam várias tarefas comuns de programação que não são fornecidas pelas linguagens C e C++.<br /><br /> Para obter mais informações, consulte [Referência da biblioteca em tempo de execução C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Bibliotecas de Tempo de Execução do Visual C++ "14" (x86)**|Esse pacote instala as bibliotecas em tempo de execução Visual C++ para os sistemas operacionais x86, que fornecem rotinas de programação para o sistema operacional Microsoft Windows. Essas rotinas automatizam várias tarefas comuns de programação que não são fornecidas pelas linguagens C e C++.<br /><br /> Para obter mais informações, consulte [Referência da biblioteca em tempo de execução C](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Consulte também

- [Página de Publicação, Designer de Projeto](../../ide/reference/publish-page-project-designer.md)
- [Pré-requisitos de implantação de aplicativos](../../deployment/application-deployment-prerequisites.md)
- [Implantando pré-requisitos para aplicativos de 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Visão Geral do Visual Studio Multiplataforma](../../ide/visual-studio-multi-targeting-overview.md)
