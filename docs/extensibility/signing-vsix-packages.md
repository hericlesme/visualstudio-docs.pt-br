---
title: Assinando pacotes VSIX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84166ed96fb49567f4ede3e8e0c4b7e8ba3cc814
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="signing-vsix-packages"></a>Assinando pacotes VSIX
Assemblies de extensão não precisa ser assinado antes de que podem ser executados no Visual Studio, mas é uma boa prática fazer isso.  
  
 Se você deseja proteger a sua extensão e verifique se que ele não foi adulterado, você pode adicionar uma assinatura digital a um pacote do VSIX. Quando um VSIX está conectado, o instalador do VSIX exibirá uma mensagem indicando que está assinada, além de obter mais informações sobre a própria assinatura. Se o conteúdo do VSIX foram modificado, e o VSIX não foi assinado novamente, o instalador do VSIX mostrará que a assinatura não é válida. A instalação não for interrompida, mas o usuário é avisado.  
  
> [!IMPORTANT]
>  A partir de 2015, pacotes VSIX assinados usando algo diferente de criptografia SHA256 serão identificados como ter uma assinatura inválida. Instalação de VSIX não é bloqueada, mas o usuário será avisado.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Assinatura de um VSIX com VSIXSignTool  
 Há uma ferramenta disponível a partir de assinatura de criptografia de SHA256 [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) em nuget.org em [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Para usar o VSIXSignTool  
  
1.  Adicione o VSIX para um projeto.  
  
2.  Clique com o botão direito no nó do projeto no Gerenciador de soluções, selecionando **adicionar &#124; gerenciar pacotes NuGet**.  Para obter mais informações sobre o NuGet e adicionando consulte de pacotes do NuGet, consulte o [NuGet documentação](/NuGet) e [Package Manager UI](/NuGet/Tools/Package-Manager-UI) tópicos.  
  
3.  Procure VSIXSignTool de VisualStudioExtensibility e instale o pacote NuGet.  
  
4.  Agora você pode executar o VSIXSignTool de local de pacotes local do projeto. Consulte a Ajuda de linha de comando da ferramenta para seu cenário de autenticação (VSIXSignTool.exe /?).  
  
 Por exemplo, para entrar com um arquivo de certificado protegido por senha:  
  
 VSIXSignTool.exe entrada /f \<certfile >/p \<senha > \<VSIXfile >  
  
## <a name="see-also"></a>Consulte também  
 [Enviar extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)