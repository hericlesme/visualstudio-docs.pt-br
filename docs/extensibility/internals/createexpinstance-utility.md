---
title: Utilitário de CreateExpInstance | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdcb37374c63b96e2169de28c6fe21742024ca98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="createexpinstance-utility"></a>CreateExpInstance Utility
Use o utilitário CreateExpInstance para criar, restaurar, ou excluir uma instância experimental do Visual Studio. Você pode usar a instância experimental para depurar e testar as extensões do Visual Studio sem alterar o produto subjacente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parâmetros  
 / Criar  
 Cria a instância experimental.  
  
 / Reset  
 Exclui a instância experimental e, em seguida, cria um novo.  
  
 /Clean  
 Exclui a instância experimental.  
  
 /Vsinstance  
 O nome do diretório que contém a instância do Visual Studio base para copiar.  
  
 /Rootsuffix  
 O sufixo a ser acrescentado ao nome do diretório de instância experimental.  
  
## <a name="remarks"></a>Comentários  
 Quando você estiver trabalhando em uma extensão do Visual Studio, você pode pressionar F5 para abrir a instância experimental do padrão e instalar a extensão atual. Se nenhuma instância experimental estiver disponível, o Visual Studio cria um que tenha as configurações padrão.  
  
 O local padrão da instância experimental depende do número de versão do Visual Studio. Por exemplo, para o Visual Studio 2015, o local é %localappdata%\Microsoft\VisualStudio\14.0Exp\ todos os arquivos no local de diretório são considerados parte dessa instância. Qualquer instância experimental adicional não será carregada pelo Visual Studio, a menos que o nome do diretório é alterado para o local padrão.  
  
 O Visual Studio não acessar o registro do sistema quando ele abre a instância experimental. Isso é diferente de versões anteriores do Visual Studio, que usou uma versão experimental da seção do registro.  
  
 O utilitário CreateExpInstance substitui o utilitário VsRegEx.  
  
 O exemplo a seguir redefine a instância experimental do padrão do Visual Studio.  
  
 **CreateExpInstance.exe /Reset /VSInstance = 14.0 /RootSuffix = Exp**  
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../../extensibility/internals/vspackages.md)