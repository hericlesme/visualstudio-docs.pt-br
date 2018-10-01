---
title: Utilitário CreateExpInstance | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9b08ba5ac68a09f6c44937634375add3065e5e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464383"
---
# <a name="createexpinstance-utility"></a>Utilitário CreateExpInstance
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [utilitário CreateExpInstance](https://docs.microsoft.com/visualstudio/extensibility/internals/createexpinstance-utility).  
  
Use o utilitário CreateExpInstance para criar, redefinir, ou excluir uma instância experimental do Visual Studio. Você pode usar a instância experimental para depurar e testar as extensões do Visual Studio sem alterar o produto subjacente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parâmetros  
 / Criar  
 Cria a instância experimental.  
  
 / Redefinição  
 Exclui a instância experimental e, em seguida, cria um novo.  
  
 /Clean  
 Exclui a instância experimental.  
  
 / VSInstance  
 O nome do diretório que contém a instância do Visual Studio base para copiar.  
  
 / RootSuffix  
 O sufixo a ser acrescentado ao nome do diretório de instância experimental.  
  
## <a name="remarks"></a>Comentários  
 Quando você estiver trabalhando em uma extensão do Visual Studio, você pode pressionar F5 para abrir a instância experimental do padrão e instalar a extensão atual. Se nenhuma instância experimental estiver disponível, o Visual Studio cria um que tenha as configurações padrão.  
  
 O local padrão da instância experimental depende do número de versão do Visual Studio. Por exemplo, para o Visual Studio 2015, o local é %localappdata%\Microsoft\VisualStudio\14.0Exp\ todos os arquivos no local de diretório são considerados parte dessa instância. Qualquer instância experimental adicional não será carregada pelo Visual Studio, a menos que o nome do diretório é alterado para o local padrão.  
  
 Visual Studio não acessar o registro do sistema quando ele é aberto na instância experimental. Isso é diferente de versões anteriores do Visual Studio, que usavam uma versão experimental da seção do registro.  
  
 O utilitário CreateExpInstance substitui o utilitário VsRegEx.  
  
 O exemplo a seguir redefine a instância experimental do padrão do Visual Studio.  
  
 **CreateExpInstance.exe /Reset /VSInstance = 14.0 /RootSuffix = Exp**  
  
## <a name="see-also"></a>Consulte também  
 [Liberando um produto](../../misc/releasing-a-visual-studio-integration-product.md)

