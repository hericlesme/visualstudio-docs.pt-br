---
title: Visão geral das opções de configuração | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85ee328b278ef9eb1d81acfc5a8299920a221e59
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132463"
---
# <a name="configuration-options-overview"></a>Visão geral das opções de configuração
Projetos em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pode dar suporte a várias configurações que podem ser criadas, depurado, execução, e/ou implantado. Uma configuração é um tipo de compilação descrito com um conjunto nomeado de propriedades, normalmente switches de compilador e locais de arquivos. Por padrão, novas soluções contêm duas configurações Debug e Release. Essas configurações podem ser aplicadas usando as configurações padrão ou modificadas para atender às suas necessidades específicas de solução e/ou projeto. Alguns pacotes podem ser criados de duas maneiras: como um editor de ActiveX ou como um componente no local. Projetos não é necessário dar suporte a várias configurações, no entanto. Se houver apenas uma configuração, essa configuração é mapeada para todas as configurações de solução.  
  
 Configurações normalmente consistem em duas partes — o nome da configuração (como depurar ou versão) e as configurações da plataforma. Nome da configuração da plataforma identifica o ambiente em que os destinos de configuração, como uma API definidos ou plataforma de sistema operacional. Os usuários do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] não é possível criar uma plataforma; eles devem escolher das seleções um projeto permite o VSPackage. Quando um usuário instala um VSPackage, a plataforma de distribuição criada durante o desenvolvimento do pacote pode aparecer em qualquer nome desejado da plataforma com base em quaisquer critérios definidos pelo criador do pacote. O usuário pode selecionar na lista de plataformas disponibilizados por meio de VSPackage quando as páginas de propriedade são instanciadas.  
  
 Nomes de plataforma são opcionais, pois nem todos os projetos oferece suporte ao conceito de plataformas. Quando uma configuração não tem um nome de plataforma, a cadeia de caracteres "n / a" é exibido na interface do usuário.  
  
 Cada solução tem seu próprio conjunto de configurações, apenas um deles pode estar ativo por vez. Uma configuração de solução é um conjunto de não mais de uma configuração de cada projeto. É o requisito de "não mais do que" devido a opção para excluir um projeto de uma configuração de solução. Os usuários podem criar suas próprias configurações de solução personalizada.  
  
 A tabela a seguir ilustra a configuração de configurações típicas de um projeto. As linhas são rotuladas com nomes de configuração e as colunas com nomes de plataforma.  
  
|Nome da configuração|Plataforma — Win32|Plataforma — Win64|  
|------------------------|----------------------|----------------------|  
|Depurar|\<Depurar configurações de Win32 >|\<Depurar configurações Win64 >|  
|Versão|\<Versão Win32 Configurações >|\<Versão Win64 Configurações >|  
|MyConfig|N/D|\<Configurações de MyConfig Win64 >|  
  
> [!NOTE]
>  Não é possível criar uma configuração de solução "MyConfig" que exclui uma plataforma "Win32", a menos que o projeto de que destino não suporta Win32.  
  
 Alterando a configuração ativa para uma solução seleciona o conjunto de configurações de projeto que são criadas, executar, depurado ou implantado na solução. Por exemplo, se você alterar a configuração de solução ativa de versão para depuração, todos os projetos na solução serão criados automaticamente com a configuração dos projetos indicada na configuração de depuração da solução. As configurações os projetos normalmente também são nomeados de depuração, a menos que o usuário tenha feito alterações manuais no Gerenciador de configuração do ambiente.  
  
 As propriedades de configuração de solução armazenadas para cada projeto incluem o nome do projeto, o nome de configuração do projeto, sinalizadores para indicar se deseja ou não para compilar ou implantar e o nome da plataforma. Para obter mais informações, consulte [configuração de solução](../../extensibility/internals/solution-configuration.md).  
  
 O usuário pode exibir e definir parâmetros de configuração de solução, selecionando a solução na hierarquia (Gerenciador de soluções) e abrir as páginas de propriedades. Da mesma forma, você pode exibir e definir parâmetros de configuração do projeto selecionando um projeto no Gerenciador de soluções e abrir as páginas de propriedades para o projeto.  
  
 O usuário também pode criar um projeto usando configurações de versão e os demais com definições de configuração de depuração, se necessário. Para obter mais informações, consulte [configuração do projeto para criar](../../extensibility/internals/project-configuration-for-building.md).  
  
 O diagrama a seguir mostra como as interfaces que dão suporte a configurações de solução e projeto são implementadas:  
  
 ![Gráfico de Interfaces de configuração](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Interfaces de configuração  
  
 Algumas observações relacionadas ao diagrama anterior:  
  
-   `IDispatch` é marcado como opcional no objeto de configuração. Especificamente, é opcional para ter interfaces de configuração no objeto de procura.  
  
-   `IVsDebuggableProjectCfg` é marcado como opcional no objeto de configuração, mas é necessário para suporte à depuração.  
  
-   `IVsProjectCfg2` é marcado como opcional no objeto de configuração, mas é necessário para suporte de agrupamento de saída.  
  
-   O `Config Provider` objeto está marcado como um objeto opcional, mas a opção é onde implementá-lo. Você pode implementar o objeto no objeto de projeto ou em um objeto separado.  
  
-   `IVsCfgProvider2` é necessário para suporte de plataforma e a edição de configuração. `IVsCfgProvider` é suficiente se você não implementar essa funcionalidade.  
  
-   Alguns desses objetos mostrados no diagrama como objetos separados podem ser combinados na mesma classe quando for prático com base em suas necessidades de design específico. Em outros tópicos desta seção, no entanto, os objetos e interfaces associadas a esses objetos serão discutidos acordo com o cenário apresentado no diagrama.  
  
-   Determinados objetos são implementados separadamente. Por exemplo, o projeto e criação de solução ocorrerem em threads separados e o objeto para gerenciar a vida de compilação separadamente do objeto que descreve a configuração para a compilação.  
  
 Para obter mais informações sobre as interfaces de objeto de configuração e as interfaces de objeto de provedor de configuração no diagrama anterior, consulte [o objeto de configuração do projeto](../../extensibility/internals/project-configuration-object.md). Além disso, [configuração do projeto para criar](../../extensibility/internals/project-configuration-for-building.md) fornece mais informações sobre as interfaces de construtor de configuração e criar o objeto de dependência, e [configuração do projeto para gerenciar implantação](../../extensibility/internals/project-configuration-for-managing-deployment.md) mais descreve as interfaces anexadas ao implantador configuração e objetos de dependência da implantação. Por fim, [configuração do projeto para a saída](../../extensibility/internals/project-configuration-for-output.md) descreve as interfaces de objeto de saída e de grupo de saída e o uso das páginas de propriedades para exibir e definir propriedades dependentes de configuração.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Configuração de projeto para criação](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuração da solução](../../extensibility/internals/solution-configuration.md)