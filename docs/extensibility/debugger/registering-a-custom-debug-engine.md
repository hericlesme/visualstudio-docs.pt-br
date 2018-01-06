---
title: "Mecanismo de depuração de registrar um personalizado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 50903d9b45828725da03c0fcb0db0f08d7f884eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="registering-a-custom-debug-engine"></a>Registrando um mecanismo de depuração personalizado
O mecanismo de depuração deve se registrar como uma fábrica de classe segue as convenções de COM, bem como registrar com o Visual Studio por meio da subchave do registro do Visual Studio.  
  
> [!NOTE]
>  Um exemplo de como registrar um mecanismo de depuração pode ser encontrado no exemplo TextInterpreter, que é criado como parte do [Tutorial: Criando um depurar mecanismo usando COM ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Processo do servidor de DLL  
 Normalmente, um mecanismo de depuração é implementado em seu próprio DLL como um servidor COM. Isso significa que o mecanismo de depuração deve registrar o CLSID de sua fábrica de classe com para que Visual Studio pode acessá-lo. Em seguida, o mecanismo de depuração deve ser registrado com o próprio Visual Studio para estabelecer as propriedades (conhecido como métricas) de depuração mecanismo oferece suporte. A escolha de métricas que são gravadas para a subchave de registro do Visual Studio para o mecanismo de depuração depende dos recursos que suporta o mecanismo de depuração.  
  
 [Auxiliares do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) descreve não apenas os locais de registro necessários para registrar um mecanismo de depuração; ele também descreve a biblioteca de dbgmetric.lib, que contém um número de funções úteis e declarações para os desenvolvedores de C++ que fazem Manipulando o registro mais fácil.  
  
### <a name="example"></a>Exemplo  
 A seguir está um exemplo típico (da amostra TextInterpreter) mostrando como usar o `SetMetric` função (de dbgmetric.lib) para registrar um mecanismo de depuração com o Visual Studio. As métricas que está sendo passadas também são definidas no dbgmetric.lib.  
  
> [!NOTE]
>  TextInterpreter é um mecanismo de depuração básico; ele não implementa — e, portanto, não registrar — todos os outros recursos. Um mecanismo de depuração mais completo teria uma lista completa de `SetMetric` chamadas ou seus equivalentes, uma para cada recurso, o mecanismo de depuração oferece suporte.  
  
```  
// Define base registry subkey to Visual Studio.  
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";  
  
HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)  
{  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);  
  
    return base::RegisterServer(bRegTypeLib, pCLSID);  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Auxiliares do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: Criando um mecanismo de depuração usando COM ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)