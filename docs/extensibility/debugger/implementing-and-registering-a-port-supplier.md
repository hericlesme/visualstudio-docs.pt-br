---
title: Implementando e registrando um fornecedor de porta | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54d6a4ab90b5ad169c5c940f52322dfd9b4974a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103169"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementando e registrando um fornecedor de porta
A função de um fornecedor de porta é rastrear e fornecer portas, que por sua vez, gerenciar processos. No momento em que uma porta precisa ser criado, o fornecedor de porta é instanciado usando CoCreate com o GUID do fornecedor de porta (o Gerenciador de sessão de depuração [SDM] usará o usuário selecionado do fornecedor de porta ou o fornecedor de porta especificado pelo sistema de projeto). O SDM chamará [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) para ver se todas as portas podem ser adicionadas. Se uma porta pode ser adicionada, uma nova porta é solicitada ao chamar [adicionar porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) e passá-lo um [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) que descreve a porta. `AddPort` Retorna uma nova porta representada por um [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface.  
  
## <a name="discussion"></a>Discussão  
 Uma porta é criada por um fornecedor de porta, o que é associado a um servidor de máquina ou de depuração. Um servidor pode enumerar seus fornecedores de porta por meio de[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) método e um fornecedor de porta podem enumerar as portas por meio de [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) método.  
  
 O registro COM típico, além de um fornecedor de porta deve ser registrado com o Visual Studio, colocando o CLSID e o nome nos locais do registro específica. Chamada de uma função do SDK de depuração auxiliar `SetMetric` manipula esta tarefa: ele é chamado uma vez para cada item a ser registrado, assim:  
  
```cpp  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricCLSID,  
          <CLSID of your port supplier>,  
          false,  
          NULL)  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricName,  
          <name of your port supplier>,  
          false,  
          NULL);  
```  
  
 Um fornecedor de porta cancela o registro em si chamando `RemoveMetric` (outra função do SDK de depuração auxiliar) uma vez para cada item que foi registrado, assim:  
  
```cpp  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricCLSID,  
             NULL);  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricName,  
             NULL);  
```  
  
> [!NOTE]
>  O [auxiliares do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` e `RemoveMetric` são funções estáticas definidas no dbgmetric.h e compilado em ad2de.lib. O `metrictypePortSupplier`, `metricCLSID`, e `metricName` auxiliares também são definidos no dbgmetric.h.  
  
 Um fornecedor de porta pode fornecer seu nome e GUID por meio dos métodos [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) e [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivamente.  
  
## <a name="see-also"></a>Consulte também  
 [Implementando um fornecedor de porta](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Auxiliares do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Fornecedores de porta](../../extensibility/debugger/port-suppliers.md)