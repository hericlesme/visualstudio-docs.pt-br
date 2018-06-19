---
title: Comandos que devem ser executados após a instalação | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84f1651f311fbad7aefe40a2744c61dc7d81725c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132324"
---
# <a name="commands-that-must-be-run-after-installation"></a>Comandos que devem ser executados após a instalação
Se você implantar sua extensão por meio de um arquivo. msi, você deve executar `devenv /setup` como parte da instalação para que o Visual Studio para descobrir suas extensões.  
  
> [!NOTE]
>  As informações neste tópico se aplica a Localizando DevEnv com o Visual Studio 2008 e versões anteriores. Para obter informações sobre como descobrir DevEnv com versões posteriores do Visual Studio, consulte [detecção de requisitos de sistema](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Localizando devenv.exe  
 Você pode localizar cada versão devenv.exe do registro valores [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instaladores de gravação, usando a tabela de RegLocator e AppSearch tabela para armazenar os valores do registro como propriedades. Para obter mais informações, consulte [detecção de requisitos de sistema](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Linhas da tabela RegLocator localizar devenv.exe de diferentes versões do Visual Studio  
  
|Signature_|Raiz|Chave|Nome|Tipo|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Linhas da tabela AppSearch para linhas correspondentes da tabela RegLocator  
  
|Propriedade|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Por exemplo, o instalador do Visual Studio grava o valor de registro de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** como **C:\VS2008\Common7\IDE\devenv.exe**, um caminho completo para o executável deve executar o instalador.  
  
 **Observação** porque a coluna de tipo RegLocator for 2, não é necessário especificar as informações de versão adicionais na tabela de assinatura.  
  
## <a name="running-devenvexe"></a>Executando devenv.exe  
 Após a ação padrão é executada no instalador de AppSearch, cada propriedade na tabela AppSearch tem um valor que apontam para o arquivo devenv.exe para a versão correspondente do Visual Studio. Se qualquer um dos valores do Registro especificada não estão presentes — porque essa versão do Visual Studio não está instalado, a propriedade especificada está definida como null.  
  
 Windows Installer dá suporte à execução de um executável para o qual uma propriedade aponta por meio de ação personalizada digite 50. A ação personalizada deve incluir as opções de execução de script, msidbCustomActionTypeInScript (1024) e msidbCustomActionTypeCommit (512), para garantir que o VSPackage foi instalado com êxito antes de integrá-lo em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte personalizada de tabela e opções de execução de no Script de ação personalizada.  
  
 Ações personalizadas do tipo 50 especificar a propriedade que contém o executável como o valor da coluna de origem e os argumentos de linha de comando na coluna de destino.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>Linhas da tabela de ação personalizada para executar devenv.exe  
  
|Ação|Tipo|Origem|Destino|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|  
  
 Ações personalizadas devem ser criadas para a tabela InstallExecuteSequence para agendá-los para execução durante a instalação. Use a propriedade correspondente em cada linha da coluna de condição para impedir que a ação personalizada sejam executados se essa versão do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] não está instalado no sistema.  
  
> [!NOTE]
>  `Null` propriedades avaliadas como `False` quando usado em condições.  
  
 O valor da coluna de sequência para cada ação personalizada depende de outros valores de sequência no pacote do Windows Installer. Valores de sequência devem ser, de modo que as ações personalizadas devenv.exe executar como perto possível imediatamente antes da ação padrão InstallFinalize.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Tabela InstallExecuteSequence para agendar o devenv.exe de ações personalizadas  
  
|Ação|Condição|Sequência|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Consulte também  
 [Instalar VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)