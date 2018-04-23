---
title: Registrando o programa | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: febc798888cc046e514db4013edb077e25f5aaca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="registering-the-program"></a>Registrando o programa
Depois que o mecanismo de depuração adquiriu uma porta, representado por um [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface, a próxima etapa para habilitar o programa a ser depurado é registrá-lo com a porta. Depois de registrado, o programa está disponível para depuração por uma das seguintes maneiras:  
  
-   O processo de anexação, que permite que o depurador obter controle total de depuração de um aplicativo em execução.  
  
-   Just-in-time (JIT) depuração, que permite a depuração após o fato de um programa que é executado independentemente de um depurador. Quando a arquitetura de tempo de execução detecta uma falha, o depurador é notificado antes do sistema operacional ou o ambiente de tempo de execução libera a memória e os recursos do programa com falha.  
  
## <a name="registering-procedure"></a>Procedimento de registro  
  
#### <a name="to-register-your-program"></a>Para registrar seu programa  
  
1.  Chamar o [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) método implementado pela porta.  
  
     `IDebugPortNotify2::AddProgramNode` requer um ponteiro para um [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface.  
  
     Normalmente, quando o sistema operacional ou o ambiente de tempo de execução carrega um programa, ele cria o nó do programa. Se o mecanismo de depuração (DE) é solicitado a carregar o programa a DE cria e registra o nó do programa.  
  
     O exemplo a seguir mostra o mecanismo de depuração, inicie o programa e registrá-lo com uma porta.  
  
    > [!NOTE]
    >  Isso não é a única maneira de iniciar e reiniciar um processo; Isso é principalmente um exemplo de registro de um programa com uma porta.  
  
    ```cpp  
    // This is an IDebugEngineLaunch2 method.  
    HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,  
                                          IDebugPort2 *pPort,  
                                          /* omitted parameters */,  
                                          IDebugProcess2**ppDebugProcess)  
    {  
        // do stuff here to set up for a launch (such as handling the other parameters)  
        ...  
  
        // Now get the IPortNotify2 interface so we can register a program node  
        // in CDebugEngine::ResumeProcess.  
        CComPtr<IDebugDefaultPort2> spDefaultPort;  
        HRESULT hr = pPort->QueryInterface(&spDefaultPort);  
        if (SUCCEEDED(hr))  
        {  
            CComPtr<IDebugPortNotify2> spPortNotify;  
            hr = spDefaultPort->GetPortNotify(&spPortNotify);  
            if (SUCCEEDED(hr))  
            {  
                // Remember the port notify so we can use it in ResumeProcess.  
                m_spPortNotify = spPortNotify;  
  
                // Now launch the process in a suspended state and return the  
                // IDebugProcess2 interface  
                CComPtr<IDebugPortEx2> spPortEx;  
                hr = pPort->QueryInterface(&spPortEx);  
                if (SUCCEEDED(hr))  
                {  
                    // pass on the parameters we were given (omitted here)  
                    hr = spPortEx->LaunchSuspended(/* omitted paramters */,ppDebugProcess)  
                }  
            }  
        }  
        return(hr);  
    }  
  
    HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)  
    {  
        // Make a program node for this process  
        HRESULT hr;  
        CComPtr<IDebugProgramNode2> spProgramNode;  
        hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);  
        if (SUCCEEDED(hr))  
        {  
            hr = m_spPortNotify->AddProgramNode(spProgramNode);  
            if (SUCCEEDED(hr))  
            {  
                // resume execution of the process using the port given to us earlier.  
               // (Querying for the IDebugPortEx2 interface is valid here since  
               // that's how we got the IDebugPortNotify2 interface in the first place.)  
                CComPtr<IDebugPortEx2> spPortEx;  
                hr = m_spPortNotify->QueryInterface(&spPortEx);  
                if (SUCCEEDED(hr))  
                {  
                    hr  = spPortEx->ResumeProcess(pDebugProcess);  
                }  
            }  
        }  
        return(hr);  
    }  
  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Obtendo uma porta](../../extensibility/debugger/getting-a-port.md)   
 [Habilitar um programa para depuração](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)