---
redirect_url: shell/shell-isolated-or-integrated
title: Shell (isolado ou integrado) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f06af0b884d404b3fd2e8e36cac235c10d254bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="shell-isolated-or-integrated"></a>Shell (isolado ou integrado)
Você pode criar seu próprio aplicativo com base no Visual Studio em modo integrado ou isolado. No modo integrado, muitos recursos do Visual Studio estão disponíveis além de seu aplicativo. No modo isolado, você deve escolher um subconjunto de recursos do Visual Studio que você deseja distribuir junto com sua própria extensão.  
  
## <a name="integrated-mode"></a>Modo integrado  
 Modo integrado permite que os usuários usar os recursos padrão do Visual Studio juntamente com suas ferramentas personalizadas. O shell integrado destina-se principalmente para hospedagem de linguagens de programação e ferramentas de desenvolvimento de software.  
  
 Ferramentas personalizadas que são criadas automaticamente no shell integrado de mesclagem com qualquer outra edição do Visual Studio está instalado no mesmo computador. Se o Visual Studio não estiver instalado, você pode fornecer uma versão redistribuível do shell do Visual Studio integrado.  
  
 A versão redistribuível do shell do Visual Studio integrado não inclui os recursos que oferecem suporte a seus respectivos sistemas de projeto e idiomas de programação.  
  
> [!NOTE]
>  O modo integrado do Visual Studio shell pode ser instalado junto com todas as edições do Visual Studio, exceto as edições Express.  
  
 Para obter mais informações, consulte [Visual Studio Shell (integrado)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Modo isolado  
 Modo isolado permite que você crie ferramentas personalizadas que são executadas lado a lado com outras versões do Visual Studio. Ele destina-se principalmente para as ferramentas que podem acessar os serviços do Visual Studio sem dependendo de todos os recursos padrão do Visual Studio. Você pode personalizar a aparência de aplicativos baseados no shell do Visual Studio isolado. Você pode facilmente desativar os recursos e grupos de comando de menu que você não deseja aparecem junto com o aplicativo.  
  
 Para obter mais informações, consulte [Visual Studio Shell isolado](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Distribuir seu aplicativo de Shell integrado ou isolado  
 Para distribuir seu aplicativo de shell isolado ou integrada, você precisa incluir o seu aplicativo, um especial shell integrado ou isolado redistribuível e um programa de instalação. Para obter mais informações sobre a distribuição e a instalação, consulte [distribuir aplicativos isolados do Shell](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  O [contrato de licença de usuário final (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552) para o Visual Studio integrado e isolada shells inclui uma seção sobre a coleta de dados (**seção 3. Dados**).  Ele descreve os dados de uso do cliente que podem ser coletados pela Microsoft de usuários do que o software de shell isolado ou integrada que você cria no seu aplicativo. Para obter mais informações, consulte [Microsoft Visual Studio família de declaração de privacidade do](https://www.visualstudio.com/en-us/dn948229).  
>   
>  Se você coletar dados de uso separado de seus clientes por meio de seu aplicativo, você deve fornecer aviso apropriado para os usuários de seu aplicativo com o que você coletar.  Quando você distribui o software de shell isolado ou integrado como parte do seu aplicativo, de acordo com a licença do Visual Studio SDK, você deve incluir um dos seguintes:  
>   
>  -   o contrato de licença de usuário final como parte da sua licença de aplicativo  
> -   seu próprio EULA que exige que os clientes concordar com os termos que protejam o Visual Studio integrated ou isolado do shell de pelo menos a quantidade como os termos de licença de usuário final da Microsoft para o software de shell  
  
## <a name="additional-resources"></a>Recursos adicionais  
 Para obter mais informações sobre os pacotes redistribuíveis, consulte o [Downloads do Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) site da Web.  
  
## <a name="see-also"></a>Consulte também  
 [Enviar extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)