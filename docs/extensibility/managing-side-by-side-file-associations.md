---
title: Gerenciamento de associações de arquivo lado a lado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e9144125786e7aa5f2a70823a033d49ac3fa2990
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146800"
---
# <a name="managing-side-by-side-file-associations"></a>Gerenciamento de associações de arquivo lado a lado
Se seu VSPackage fornece associações de arquivo, você deve decidir como lidar com instalações lado a lado em que uma versão específica do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve ser chamado para abrir um arquivo. Formatos de arquivo incompatível composta o problema.  
  
 Os usuários esperam que uma nova versão de um produto para ser compatível com versões anteriores, para que os arquivos existentes podem ser carregados em uma nova versão, sem perda de dados. Idealmente, o VSPackage pode carregar e salvar os formatos de arquivo de versões anteriores. Se não for verdadeiro, você deve oferecer atualizar o formato de arquivo para a nova versão do seu VSPackage. A desvantagem dessa abordagem é que o arquivo atualizado não pode ser aberto na versão anterior.  
  
 Para evitar esse problema, você pode alterar extensões quando formatos de arquivo são incompatíveis. Por exemplo, a versão 1 do seu VSPackage poderia usar a extensão, .mypkg10 e versão 2 pode usar a extensão .mypkg20. Essa diferença identifica o VSPackage que abre um arquivo específico. Se você adicionar mais recentes VSPackages à lista de programas que estão associados com uma extensão antiga, os usuários podem o arquivo de atalho e escolha abri-lo em um VSPackage mais recente. Nesse ponto, o VSPackage pode oferecer para atualizar o arquivo para o novo formato ou abrir o arquivo e manter a compatibilidade com versões anteriores do VSPackage.  
  
> [!NOTE]
>  Você pode combinar essas abordagens. Por exemplo, você pode oferecer a compatibilidade com versões anteriores ao carregar um arquivo antigo e oferta atualizar o formato de arquivo quando o usuário salvá-lo.  
  
## <a name="facing-the-problem"></a>Enfrentando o problema  
 Se você quiser vários VSPackages lado a lado para usar a mesma extensão, você deve escolher a versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que está associado com a extensão. Aqui estão duas alternativas:  
  
-   Abra o arquivo na versão mais recente do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instalada no computador do usuário.  
  
     Nessa abordagem, o instalador é responsável por determinar a versão mais recente do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e inclusive na entrada do registro gravada para a associação de arquivo. Em um pacote do Windows Installer, você pode incluir ações personalizadas para definir uma propriedade que indica a versão mais recente do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    > [!NOTE]
    >  Nesse contexto, "mais recente" significa "versão compatível mais recente." Essas entradas de instalador não detectará automaticamente uma versão subsequente do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Entradas no [detecção de requisitos de sistema](../extensibility/internals/detecting-system-requirements.md) e em [comandos que deve ser executado após a instalação](../extensibility/internals/commands-that-must-be-run-after-installation.md) são semelhantes aos apresentados aqui e são necessários para dar suporte a versões adicionais de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     As seguintes linhas na tabela de ação personalizada definir a propriedade DEVENV_EXE_LATEST para ser uma propriedade definida pelo AppSearch e tabelas RegLocator discutidos [comandos que deve ser executado após a instalação](../extensibility/internals/commands-that-must-be-run-after-installation.md). Linhas na tabela InstallExecuteSequence agendar as ações personalizadas no início na sequência de execução. Valores no Verifique coluna condição a lógica de trabalho:  
  
    -   Visual Studio .NET 2002 é a versão mais recente, se é a versão presente somente.  
  
    -   Visual Studio .NET 2003 é a versão mais recente somente se ele estiver presente e [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não está presente.  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é a versão mais recente, se é a versão presente somente.  
  
     O resultado líquido é DEVENV_EXE_LATEST contém o caminho da versão mais recente do devenv.exe.  
  
    ### <a name="customaction-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Linhas da tabela de ação personalizada que determinam a versão mais recente do Visual Studio  
  
    |Ação|Tipo|Origem|Destino|  
    |------------|----------|------------|------------|  
    |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|  
    |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|  
    |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|  
  
    ### <a name="installexecutesequence-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Linhas da tabela InstallExecuteSequence que determinam a versão mais recente do Visual Studio  
  
    |Ação|Condição|Sequência|  
    |------------|---------------|--------------|  
    |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 E NÃO (DEVENV_EXE_2003 OU DEVENV_EXE_2005)|410|  
    |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 E NÃO DEVENV_EXE_2005|420|  
    |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|  
  
     Você pode usar a propriedade DEVENV_EXE_LATEST na tabela de registro do pacote do Windows Installer para gravar o HKEY_CLASSES_ROOT*ProgId*valor da chave ShellOpenCommand padrão [DEVENV_EXE_LATEST] "%1"  
  
-   Execute um programa de iniciador compartilhado que pode fazer a melhor escolha de versões disponíveis de VSPackage.  
  
     Os desenvolvedores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] escolheu essa abordagem para lidar com os requisitos complexos de vários formatos de soluções e projetos que são provenientes de várias versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Nessa abordagem, você pode registrar um programa do iniciador como o manipulador de extensão. O iniciador examina o arquivo e decide qual versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e seu VSPackage pode lidar com esse arquivo específico. Por exemplo, se um usuário abrir um arquivo que foi salvo pela última vez por uma versão específica do seu VSPackage, o iniciador pode iniciar esse VSPackage na versão correspondente do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Além disso, um usuário pode configurar o iniciador para iniciar sempre a versão mais recente. Um iniciador também pode solicitar que um usuário para atualizar o formato do arquivo. Se o formato do arquivo inclui um número de versão, o iniciador pode informar um usuário se o formato de arquivo é de uma versão posterior a uma ou mais os VSPackages instalados.  
  
     O iniciador deve estar em um componente do Windows Installer que é compartilhado com todas as versões do seu VSPackage. Esse processo garante que a versão mais recente sempre é instalada e não é removida até que todas as versões do seu VSPackage são desinstaladas. Dessa forma, as associações de arquivo e outras entradas do registro do componente de iniciador serão preservadas mesmo se uma versão do VSPackage for desinstalada.  
  
## <a name="uninstall-and-file-associations"></a>Desinstale e associações de arquivos  
 Desinstalar um VSPackage que grava entradas do registro para associações de arquivo remove as associações de arquivo. Portanto, a extensão não tem nenhum programa associado. Windows Installer não "recover" as entradas do registro que foram adicionadas quando o VSPackage foi instalado. Aqui estão algumas maneiras de corrigir as associações de arquivo do usuário:  
  
-   Use um componente compartilhado do iniciador conforme descrito anteriormente.  
  
-   Instrua o usuário a executar um reparo da versão do VSPackage que o usuário quer ter a associação de arquivo.  
  
-   Forneça um programa executável separado que reescreve as entradas do registro apropriada.  
  
-   Forneça uma configuração Opções página ou caixa de diálogo que permite aos usuários escolher as associações de arquivo e recuperar associações perdidas. Instrua os usuários para executá-lo após a desinstalação.  
  
## <a name="see-also"></a>Consulte também  
 [Registrando extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Registrar verbos para extensões de nome de arquivo](../extensibility/registering-verbs-for-file-name-extensions.md)