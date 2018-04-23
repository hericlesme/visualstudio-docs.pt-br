---
title: Escolha o diretório de instalação para um VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 564a184e8b3907f5a61bccc26cfbafa8d2cf8e67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Escolha o diretório de instalação para um VSPackage
Um VSPackage e seus arquivos de suporte devem ser no sistema de arquivos do usuário. O local depende se o VSPackage é gerenciado ou não, o esquema de controle de versão lado a lado e escolha do usuário.  
  
## <a name="unmanaged-vspackages"></a>VSPackages não gerenciados  
 Um VSPackage não gerenciado é um servidor COM que pode ser instalado em qualquer local. Suas informações de registro deve reflete com precisão o local. Sua interface de usuário do instalador (IU) deve fornecer um local padrão como uma subpasta da propriedade ProgramFilesFolder Windows Installer. Por exemplo:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\  
  
 O usuário deve ter permissão para alterar o diretório padrão para acomodar usuários que manter uma partição de inicialização pequeno e preferir instalar aplicativos e ferramentas em outro volume.  
  
 Se o esquema de lado a lado usa um VSPackage com controle de versão, você pode usar subdiretórios para armazenar versões diferentes. Por exemplo:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>VSPackages gerenciados  
 VSPackages gerenciados também podem ser instalados em qualquer local. No entanto, você deve considerar sempre instalá-los para o cache de assembly global (GAC) para reduzir os tempos de carregamento do assembly. Como sempre, VSPackages gerenciados são assemblies de nomes fortes, instalá-los no GAC significa que sua verificação de assinatura de nome forte leva apenas no momento da instalação. Assemblies de nomes fortes instalados em outro lugar no sistema de arquivos devem ter suas assinaturas verificadas toda vez que eles são carregados. Quando você instala VSPackages gerenciados no GAC, use a ferramenta de regpkg **/assembly** switch para gravar entradas de registro apontando para o nome forte do assembly.  
  
 Se você instalar VSPackages gerenciados em um local diferente no GAC, siga o conselho anterior fornecido para VSPackages gerenciados para escolher as hierarquias de diretório. Use a ferramenta de regpkg **/codebase** switch para gravar entradas de registro apontando para o caminho do assembly VSPackage.  
  
 Para obter mais informações, consulte [Registrando e Cancelando o registro VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>DLLs satélite  
 Por convenção, VSPackage DLLs satélites — que contêm recursos para uma determinada localidade — estão localizados em subdiretórios do diretório VSPackage. Os subdiretórios correspondem aos valores de ID (LCID) de localidade.  
  
 [Gerenciando VSPackages](../../extensibility/managing-vspackages.md) indica que as entradas do registro controlam onde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] realmente procura um VSPackage satélite DLL. No entanto, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tenta carregar uma DLL satélite em um subdiretório nomeado para um valor LCID, na seguinte ordem:  
  
1.  Padrão LCID (VS LCID por exemplo \1033 para inglês)  
  
2.  LCID padrão com a subidioma padrão.  
  
3.  LCID padrão do sistema.  
  
4.  Padrão do sistema LCID com subidioma o padrão.  
  
5.  DOS EUA Inglês (. \1033 ou. \0x409).  
  
 Se sua DLL VSPackage inclui recursos e os pontos de entrada de registro SatelliteDll\DllName, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tentar carregá-los na ordem acima.  
  
## <a name="see-also"></a>Consulte também  
 [Escolhendo entre VSPackages compartilhados e com controle de versão](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Gerenciando VSPackages](../../extensibility/managing-vspackages.md)   
 [Registro do pacote gerenciado](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)