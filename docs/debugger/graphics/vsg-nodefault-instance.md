---
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d064f4a5b983058d9f1ad4428e2b37cf2e82dcf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473154"
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
Define sua presença se uma instância padrão do [classe VsgDbg](vsgdbg-class.md) classe — que fornece a interface de captura programática — é fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Valor  
 Pré-processador de um símbolo que por sua presença ou ausência determina se uma instância padrão do `VsgDbg` classe é fornecida. Se este símbolo for definido, em seguida, nenhuma instância padrão do `VsgDbg` classe é fornecida; caso contrário, uma instância padrão é fornecida e inicializada antes que o programa for executado.  
  
 A interface de programação de captura é fornecida através de um ponteiro que tem escopo global, `g_pVsgDbg`.  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Comentários  
 A instância padrão é geralmente suficiente, mas para usar a interface de programação de captura dentro de uma DLL quando o dispositivo D3D foi criado fora dessa DLL, você deve criar e gerenciar sua própria instância do `VsgDbg` classe. Se você estiver gerenciando sua própria interface para a API de captura programática dessa maneira, desabilitar a instância padrão definindo `VSG_NODEFAULT_INSTANCE` para evitar a sobrecarga.  
  
 Se a instância padrão não for desabilitada, ele é inicializado automaticamente antes da execução do seu programa e é destruído automaticamente quando o programa for finalizado. Não é necessário que inicializar ou não a essa instância explicitamente.  
  
 Para desabilitar a instância padrão, você deve definir `VSG_NODEFAULT_INSTANCE` antes de você incluir `vsgcapture.h` em seu programa.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como desabilitar a instância padrão:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```