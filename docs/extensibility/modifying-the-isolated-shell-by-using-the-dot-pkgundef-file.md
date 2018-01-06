---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file
title: Modificando o Shell isolado usando o. Arquivo Pkgundef | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dfe0e4b39e96d98718ff98025add521a678699ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modificando o Shell isolado usando o. Arquivo Pkgundef
Você pode modificar o arquivo .pkgundef para excluir as entradas do Registro especificada de um aplicativo de shell isolado. Normalmente, a primeira vez que um aplicativo é iniciado em um computador, o shell do Visual Studio copia as entradas de registro existentes do Visual Studio para a chave do registro raiz para o aplicativo. Isso inclui todas as referências a VSPackages atualmente instalados.  
  
 Para excluir uma entrada de registro específico de um aplicativo de shell isolado, adicione a chave do pacote seguida pela entrada do arquivo de .pkgundef do aplicativo. Chaves e as entradas são representadas assim como o arquivo .pkgdef; ou seja, como [$RootKey$] ou [$RootKey$\\*subchave*] e "*entrada*" =*valor*, onde *subchave* é a subchave para afetar, *entrada* é a entrada para remover, e *valor* é `""` ou `dword:00000000`.  
  
 Para excluir várias entradas de uma chave do registro, apenas liste a chave de uma vez, seguido por uma linha para cada entrada a ser excluído.  
  
 Para excluir uma chave do Registro inteira de um aplicativo de shell isolado, adicionar a chave para o arquivo de .pkgundef do aplicativo, mas não especificam as entradas do registro para essa chave.  
  
 Você pode adicionar comentários para o arquivo .pkgundef. Um comentário de linha deve ter duas barras como os dois primeiros caracteres.  
  
 Por exemplo, para remover o **conectar-se ao banco de dados** e **conectar-se a servir r** comandos no **ferramentas** menu, você pode remover o comentário da linha:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 e adicione a linha:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 para o arquivo do aplicativo .pkgundef.  
  
## <a name="see-also"></a>Consulte também  
 [GUIDs de pacote de recursos do Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Personalizar o Shell isolado](../extensibility/customizing-the-isolated-shell.md)