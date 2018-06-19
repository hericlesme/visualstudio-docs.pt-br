---
title: Instalando VSPackages com o Windows Installer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6fafebe0dc2bb8e13c99be8b340e7f5663a9930f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130994"
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalando VSPackages com o Windows Installer
Integrando o VSPackage em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] requer mais do que apenas copiar arquivos para o computador do usuário. Instalador do VSPackage deve instalar o VSPackage e seus arquivos dependentes e registrar e integrá-las em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. O VSPackage pode tirar proveito dos recursos de integração, como exibir um ícone no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sobre caixa de diálogo e de tela de abertura.  
  
 Arquivos do Microsoft Windows Installer são a maneira recomendada para distribuir os VSPackages. Fácil de usar o Windows Installer pacotes podem ser executados em qualquer sistema operacional do Windows com suporte pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte [do Windows Installer](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Noções básicas do Windows Installer](../../extensibility/internals/windows-installer-basics.md)  
 Fornece uma visão geral do Windows Installer.  
  
 [Cenários de configuração do VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Descreve maneiras diferentes, você pode dar suporte a instalações lado a lado de ambos os seus VSPackages e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Criar um pacote do Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Fornece uma visão geral das etapas comuns instaladores seguem para instalar corretamente e integrar VSPackages em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Detectar os requisitos do sistema](../../extensibility/internals/detecting-system-requirements.md)  
 Descreve como detectar um instalador [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e seus componentes e cancelar a instalação se VSPackage requisitos não forem atendidos.  
  
 [Gerenciamento de componente](../../extensibility/internals/component-management.md)  
 Descreve como desenvolver um instalador que mantém a integridade de versões anteriores do produto.  
  
 [Escolher o diretório de instalação para um VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Resume as opções para localizar a VSPackages.  
  
 [Registrar o VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Discute como VSPackages são registrados no momento da instalação e por que o registro automático não é recomendável.  
  
 [Implantar tipos de projeto](../../extensibility/internals/deploying-project-types.md)  
 Discute como usar o novo agregador de tipo de projeto para tipos de projeto de código gerenciado.  
  
 [Como gerar informações de registro para um instalador](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Explica como usar RegPkg.exe para gerar um manifesto de registro para um VSPackage gerenciado.  
  
 [Comandos que devem ser executados após a instalação](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Explica como executar comandos de pós-instalação para integrar VSPackages em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Desinstalar um VSPackage com o Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Descreve as etapas que o instalador deve executar quando os usuários desinstalarem o VSPackage.  