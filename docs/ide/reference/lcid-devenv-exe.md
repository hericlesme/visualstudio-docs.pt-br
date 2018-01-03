---
title: -LCID (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bdc04655ccfc8ca5f6c1e45e4378f15221b99f4c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
Define o idioma padrão usado para texto, moeda e outros valores dentro do IDE (ambiente de desenvolvimento integrado).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## <a name="arguments"></a>Arguments  
 `LocaleID`  
 Necessário. O LCID (identificação de localidade) do idioma que você especificar.  
  
## <a name="remarks"></a>Comentários  
 Carrega o IDE e define o idioma natural padrão do ambiente. Essa alteração é mantida entre sessões e refletida no painel **Configurações Internacionais** das opções de **Ambiente** na caixa de diálogo **Opções** no IDE.  
  
 Se o idioma especificado não estiver disponível no sistema do usuário, a opção /LCID será ignorada.  
  
 A tabela a seguir lista os LCIDs dos idiomas com suporte do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
|Idioma|LCID|  
|--------------|----------|  
|Chinês (simplificado)|2052|  
|Chinês (tradicional)|1028|  
|Inglês|1033|  
|Francês|1036|  
|Alemão|1031|  
|Italiano|1040|  
|Japonês|1041|  
|Coreano|1042|  
|Espanhol|3082|  
  
## <a name="example"></a>Exemplo  
 Este exemplo carrega o IDE com cadeias de caracteres de recursos em inglês.  
  
```  
devenv /LCID 1033  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Caixa de diálogo Configurações Internacionais, Ambiente, Opções](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [Personalizando layouts de janela](../../ide/customizing-window-layouts-in-visual-studio.md)