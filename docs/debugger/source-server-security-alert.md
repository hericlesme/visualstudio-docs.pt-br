---
title: "Alerta de segurança do servidor de origem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7eb50bec1967b9c1f7a969eb802888864f5e72eb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="source-server-security-alert"></a>Alerta de segurança do servidor de origem
Ao usar o Servidor de Origem, use somente os arquivos de símbolo que forem de um local conhecido e confiável.  
  
 Este aviso aparece quando você ativa o suporte do servidor de origem. Comandos do servidor de origem são inseridos nos arquivos de símbolo de depuração (***. PDB** arquivos). Verifique se você sabe de onde vêm seus arquivos PDB.  
  
> [!IMPORTANT]
>  As seguintes riscos de segurança devem ser levadas em consideração ao usar o servidor de origem: os comandos arbitrários podem ser inseridos no arquivo de PDB do aplicativo, de forma que você coloque somente aqueles que você deseja executar no arquivo de srcsrv.ini. Qualquer tentativa de executar um comando que não esteja no arquivo srcsvr.ini fará com que uma caixa de diálogo de confirmação seja exibida. Para obter mais informações, consulte [aviso de segurança: depurador deve executar comando não confiável](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Nenhuma validação é feita em parâmetros de comando, tenha cuidado com comandos confiáveis. Por exemplo, se você confiar no cmd.exe, um usuário mal-intencionado pode especificar parâmetros que tornariam o comando perigoso.  
  
## <a name="see-also"></a>Consulte também  
 [Especifique o símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Servidor de origem](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)