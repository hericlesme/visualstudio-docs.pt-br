---
redirect_url: shell/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files
title: "Usado em cadeias de substituição. Pkgdef e. Arquivos de Pkgundef | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 220e6d9bb9d360a51f9a83b5d0b4420cf64aef91
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Usado em cadeias de substituição. Pkgdef e. Arquivos de Pkgundef
Você pode usar as cadeias de caracteres de substituição listadas na .pkgdef e .pkgundef arquivos definidos para o Visual Studio isolados do aplicativo de shell.  
  
## <a name="substitution-strings"></a>Cadeias de caracteres de substituição  
  
|Cadeia de caracteres|Descrição|  
|------------|-----------------|  
|$=*RegistryEntry*$|O valor de *RegistryEntry* entrada. Se a cadeia de caracteres de entrada de registro termina em uma barra invertida (\\), o valor padrão da subchave do registro é usado. Por exemplo, a substituição de cadeia de caracteres $= HKEY_CURRENT_USER\Environment\TEMP$ é expandido para a pasta temporária do usuário atual.|  
|$AppName$|O nome qualificado do aplicativo que é passado para os pontos de entrada AppEnv.dll. O nome qualificado consiste em nome do aplicativo, um sublinhado e o identificador de classe (CLSID) do objeto de automação aplicativo, também é registrado como o valor da configuração do arquivo de projeto .pkgdef ThisVersionDTECLSID.|  
|$AppDataLocalFolder|A subpasta % LOCALAPPDATA % para este aplicativo.|  
|$BaseInstallDir$|O caminho completo do local em que o Visual Studio foi instalado.|  
|$CommonFiles$|O valor da variável de ambiente % CommonProgramFiles %.|  
|$MyDocuments$|O caminho completo da pasta Meus documentos do usuário atual.|  
|$PackageFolder$|O caminho completo do diretório que contém os arquivos de assembly do pacote para o aplicativo.|  
|$ProgramFiles$|O valor da variável de ambiente % ProgramFiles %.|  
|$RootFolder$|O caminho completo do diretório raiz do aplicativo.|  
|$RootKey$|A chave do registro raiz para o aplicativo. Por padrão, a raiz é em HKEY_CURRENT_USER\\Software\\*CompanyName*\\*ProjectName*\\*VersionNumber* (quando o aplicativo é executado, _Config é anexado a essa chave). Ele é definido pelo valor RegistryRoot no *SolutionName*.pkgdef arquivo.<br /><br /> A cadeia de caracteres de $ $RootKey pode ser usada para recuperar um valor do registro na subchave do aplicativo. Por exemplo, a cadeia de caracteres "$= $RootKey$ \AppIcon$" retornará o valor da entrada AppIcon sob a subchave de raiz do aplicativo.<br /><br /> O analisador processa o arquivo .pkgdef sequencialmente e pode acessar uma entrada de registro na subchave aplicativo apenas se a entrada tiver sido definida anteriormente|  
|$ShellFolder$|O caminho completo do local em que o Visual Studio foi instalado.|  
|$System$|A pasta Windows\system32.|  
|$WINDIR$|A pasta do Windows.|  
  
 Se o analisador não reconhece a cadeia de caracteres de substituição ou não é possível determinar o valor de uma entrada de registro ou uma variável de ambiente, em seguida, ele não executa a substituição essa parte da cadeia de caracteres.