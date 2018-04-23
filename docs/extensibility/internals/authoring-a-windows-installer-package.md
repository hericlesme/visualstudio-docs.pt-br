---
title: Criação de um pacote do Windows Installer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 215e1496d35059448cf11457658b7d1270b5677d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="authoring-a-windows-installer-package"></a>Criação de um pacote do Windows Installer
Unidades de dados do modelo do Windows Installer. Em vez de escrever um script de procedimento para copiar arquivos e gravar as entradas do registro, por exemplo, você cria linhas e colunas em tabelas de banco de dados que contêm dados de arquivo e registro.  
  
## <a name="database-entries"></a>Entradas do banco de dados  
 Para instalar um VSPackage, um pacote do Windows Installer deve conter entradas do banco de dados para executar as seguintes tarefas:  
  
-   Pesquisar para localizar as versões do sistema [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (usando tabelas do Windows Installer que incluem AppSearch, CompLocator, RegLocator, DrLocator e assinatura) dá suporte a seu VSPackage.  
  
-   Cancelar a instalação se nenhuma versão com suporte do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está instalado ou se outro requisito de sistema do VSPackage não for atendido (usando a tabela de LaunchCondition).  
  
-   Instale o VSPackage e arquivos dependentes (usando o diretório, componente e tabelas de arquivo).  
  
-   Adicione as informações adequadas para o VSPackage no registro (usando a tabela de registro).  
  
-   Integrar o VSPackage em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chamando **devenv.exe /setup** (usando a tabela de ação personalizada).  
  
 Para obter mais informações, consulte [do Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Ferramentas de configuração  
 Uma variedade de ferramentas de configuração de terceiros fornecem um ambiente de desenvolvimento de pacotes do Windows Installer. Duas ferramentas gratuitas são os seguintes:  
  
-   InstallShield Limited Edition  
  
     Você pode obter uma versão limitada do InstallShield por meio do Visual Studio **novo projeto** caixa de diálogo. Expanda **outros tipos de projetos** e, em seguida, selecione **instalação e implantação**. Selecione o modelo do InstallShield.  
  
-   Conjunto de Ferramentas XML do Windows Installer  
  
     O conjunto de ferramentas cria pacotes do Windows Installer XML dos arquivos de origem. O conjunto de ferramentas é um projeto de código-fonte aberto da Microsoft. Você pode baixar o código-fonte e os executáveis de [ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix).  
  
 Para os produtos comerciais integram [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usando o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], consulte [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Consulte também  
 [Instalar VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)