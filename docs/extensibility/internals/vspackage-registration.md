---
title: Registro de VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 348010982b015eaf19ba4de559eca66bb24930a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148880"
---
# <a name="vspackage-registration"></a>Registro de VSPackage
VSPackages deverá avisar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que eles são instalados e devem ser carregado. Esse processo é realizado por gravar informações no registro. É um trabalho típicas de um instalador.  
  
> [!NOTE]
>  É uma prática aceita durante o desenvolvimento de VSPackage para usar o registro automático. No entanto, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] parceiros não podem fornecer seus produtos usando auto-registro como parte da instalação.  
  
 Entradas do registro em um pacote do Windows Installer geralmente são feitas na tabela de registro. Você também pode registrar as extensões de arquivo na tabela de registro. No entanto, o Windows Installer fornece suporte interno por meio do identificador programático (ProgId), classe, extensão e tabelas de verbo. Para obter mais informações, consulte [tabelas de banco de dados](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Certifique-se de que as entradas do registro estão associadas com o componente que é apropriado para sua estratégia de lado a lado escolhida. Por exemplo, entradas do registro para um arquivo compartilhado devem ser associadas ao componente do Windows Installer desse arquivo. Da mesma forma, entradas do registro para um arquivo específico da versão devem ser associadas a componente desse arquivo. Caso contrário, instalar ou desinstalar o VSPackage para uma versão do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pode interromper o VSPackage em outras versões. Para obter mais informações, consulte [dando suporte a várias versões do Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  A maneira mais fácil de gerenciar o registro é usar os mesmos dados nos mesmos arquivos de registro de desenvolvedor e o registro de tempo de instalação. Por exemplo, algumas ferramentas de desenvolvimento de instalador podem consumir o arquivo no formato. reg no momento da compilação. Se os desenvolvedores mantêm arquivos. reg para seu próprio desenvolvimento diário e depuração, esses mesmos arquivos podem ser incluídos no instalador automaticamente. Se você não pode compartilhar automaticamente dados de registro, certifique-se de que a cópia do instalador dos dados de registro é atual.  
  
## <a name="registering-unmanaged-vspackages"></a>Registrando VSPackages não gerenciados  
 VSPackages gerenciados (incluindo os gerados pelo modelo de pacote do Visual Studio) usar arquivos. rgs do estilo ATL para armazenar informações de registro. O formato de arquivo. rgs é específico para ATL e geralmente não pode ser utilizado como-é uma ferramenta de criação de instalação. Informações de registro para o instalador VSPackage devem ser mantidas separadamente. Por exemplo, os desenvolvedores podem manter arquivos no formato. reg em sincronia com. rgs alterações de arquivo. Os arquivos. reg podem ser mesclados com RegEdit para trabalhos de desenvolvimento ou consumidos por um instalador.  
  
## <a name="registering-managed-vspackages"></a>Registrando VSPackages gerenciados  
 A ferramenta de RegPkg lê os atributos de registro de um VSPackage gerenciado e a gravar as informações diretamente para o registro ou arquivos de formato. reg de gravação que podem ser consumidos por um instalador.  
  
> [!NOTE]
>  A ferramenta de RegPkg não é redistribuível e não pode ser usada para registrar um VSPackage no sistema do usuário.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Por que o VSPackages não deve registrar automaticamente no momento da instalação  
 Seus instaladores VSPackage não devem depender de auto-registro. A princípio, manter os valores de registro de um VSPackage apenas o VSPackage próprio parece ser uma boa ideia. Considerando que os desenvolvedores precisam os valores de registro disponíveis para o trabalho de rotina e de teste, faz sentido para evitar a manter uma cópia separada dos dados do registro do instalador. O instalador pode contar com o VSPackage para gravar valores do registro.  
  
 Ao bom em teoria, auto-registro tem várias falhas daquele inadequados para instalação VSPackage:  
  
-   Suporte corretamente a instalação, desinstalação, reversão da instalação e reversão de desinstalação requer a criação de quatro ações personalizadas para cada VSPackage gerenciado que registra automaticamente chamando RegPkg.  
  
-   A abordagem para suporte lado a lado pode exigir que você criar quatro ações personalizadas que invocam RegSvr32 ou RegPkg para todas as versões com suporte do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Uma instalação com módulos automaticamente registrados não pode ser revertida com segurança porque há uma maneira de dizer se as chaves automaticamente registradas são usadas por outro aplicativo ou recurso.  
  
-   DLLs automaticamente registrados às vezes, vincule a DLLs auxiliares que não estão presentes ou estão na versão errada. Por outro lado, o Windows Installer pode registrar DLLs usando as tabelas de registro sem dependência no estado atual do sistema.  
  
-   Código de auto-registro pode ser negado acesso a recursos de rede, como bibliotecas de tipo, se um componente é especificado como executado a partir da origem tanto está listado na tabela SelfReg. Isso pode causar a instalação do componente falha durante uma instalação administrativa.  
  
## <a name="see-also"></a>Consulte também  
 [O Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Registro do pacote gerenciado](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)