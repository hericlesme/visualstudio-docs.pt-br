---
title: Obtendo uma porta | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c20b3e3bdc2644e7af7d9a35de06af7f96d7680
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102987"
---
# <a name="getting-a-port"></a>Obtendo uma porta
Uma porta representa uma conexão a uma máquina que processos estão em execução. Esse computador pode ser o computador local ou em um computador remoto (que possivelmente pode estar executando um sistema operacional não baseado em Windows, consulte [portas](../../extensibility/debugger/ports.md) para obter mais informações).  
  
 Uma porta é representada pelo [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface. Ele é usado para obter informações sobre processos em execução no computador em que a porta está conectada a.  
  
 Um mecanismo de depuração precisa de acesso a uma porta para registrar nós de programa com a porta e para atender a solicitações de informações do processo. Por exemplo, se o mecanismo de depuração implementa o [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) interface, a implementação para o [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) método pode pedir que a porta para o processo necessário informações a serem retornadas.  
  
 O Visual Studio fornece a porta necessária para o mecanismo de depuração e obtém essa porta de um fornecedor de porta. Se um programa está anexado a (ou de dentro do depurador devido a uma exceção foi lançada, que aciona a caixa de diálogo Just-in-Time [JIT]), o usuário terá a opção de transporte (outro nome para um fornecedor de porta) a ser usado. Caso contrário, se o usuário inicia o programa a partir do depurador, o sistema do projeto Especifica o fornecedor de porta a ser usado. Em ambos os casos, o Visual Studio cria uma instância do fornecedor de porta, representado por um [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) de interface e solicita uma nova porta chamando [adicionar porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) com um [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) interface. Essa porta é então transmitida para o mecanismo de depuração em um formulário ou outro.  
  
## <a name="example"></a>Exemplo  
 Este fragmento de código mostra como usar a porta fornecida ao [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) para registrar um nó de programa em [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Parâmetros não estão diretamente relacionados a esse conceito foram omitidos para fins de esclarecimento.  
  
> [!NOTE]
>  Este exemplo usa a porta para iniciar e continuar o processo e pressupõe que o [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) interface é implementada na porta. Isso não é a única maneira de realizar essas tarefas, e é possível que a porta não pode ainda ser envolvida diferente do que o programa [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) atribuído a ele.  
  
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
 [Registrando o programa](../../extensibility/debugger/registering-the-program.md)   
 [Habilitar um programa a ser depurado](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Fornecedores de porta](../../extensibility/debugger/port-suppliers.md)   
 [Portas](../../extensibility/debugger/ports.md)