---
title: "Configurar o Firewall do Windows para depuração remota | Microsoft Docs"
ms.custom: 
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9432c65ec6a481b23655fb2a92915a4a4365ed5e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Configurar o Firewall do Windows para depuração remota
Este tópico descreve como configurar o firewall para permitir a depuração remota em computadores que executam os seguintes sistemas operacionais:  
  
-   Windows 10  
  
-   Windows 8/8.1  
  
-   Windows 7   
  
-   Windows Server 2012 R2  

-   Windows Server 2012
  
-   Windows Server 2008 R2 
  
 Se a rede na qual você está depurando não está protegida por um firewall, essa configuração é desnecessária. Caso contrário, o computador que hospeda o Visual Studio e o computador remoto que será depurado exigem alterações na configuração de firewall.  
  
 **IPSec** se sua rede requer que a comunicação seja executada usando o IPSec, você deve abrir portas adicionais no computador host do Visual Studio e o computador remoto.  
  
 **Servidor Web** se você estiver depurando um servidor remoto, você deve abrir uma porta adicional no computador remoto. (Para o IIS, a porta 80 deve estar aberta.)  
  
 Observe que os dois computadores não precisa executar o mesmo sistema operacional. Por exemplo, o computador do Visual Studio pode executar o Windows 10 e o computador remoto pode executar o Windows Server 2012 R2.      
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Portas que habilitar a depuração remota no computador remoto  
  
|||||  
|-|-|-|-|  
|**Portas**|**Entrada/saída**|**Protocolo**|**Descrição**|   
|4022|entrada|TCP|Para 2017 VS. O número da porta é incrementado em 2 para cada versão do Visual Studio. Para obter mais informações, consulte [Visual Studio Remote Debugger atribuições de porta](../debugger/remote-debugger-port-assignments.md).|  
|4023|entrada|TCP|Para 2017 VS. O número da porta é incrementado em 2 para cada versão do Visual Studio. (Somente usado para remoto depurar um processo de 32 bits da versão de 64 bits do depurador remoto.) Para obter mais informações, consulte [Visual Studio Remote Debugger atribuições de porta](../debugger/remote-debugger-port-assignments.md).| 
|3702|Saída|UDP|(Opcional) Necessário para a descoberta de depurador remoto.|    
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Como configurar portas no Firewall do Windows  

Quando você instala o Visual Studio ou o depurador remoto, o software tenta abrir as portas corretas. No entanto, em alguns cenários (como o uso de um firewall de terceiros), você precisará abrir uma porta manualmente. Se você precisar verificar se as portas estão abertas, consulte [solução de problemas](#troubleshooting). Algumas instruções para abrir uma porta podem ser diferentes em versões anteriores do Windows.

Para abrir uma porta:
  
1. Abra o **iniciar** menu, procure **Firewall do Windows com segurança avançada**.

2. Em seguida, escolha **regras de entrada > nova regra > porta**e, em seguida, clique em **próximo**. (Para regras de saída, escolha **as regras de saída** em vez disso.)

3. Escolha **TCP** ou **UDP**, dependendo do número de porta.

4. Em **portas locais específicas**, digite o número da porta, clique em **próximo**.

5. Clique em **permitir a Conexão** e, em seguida, clique em **próximo**.

6. Selecione um ou mais tipos de rede para habilitar a porta e clique em **próximo**.

    O tipo que você selecionar deve incluir a rede à qual o computador remoto está conectado.
7. Adicione o nome (por exemplo, **msvsmon**, **IIS**, ou **implantação da Web**) para a regra e clique em **concluir**.

    Você deve ver a nova regra na lista de regras de entrada ou saída.

## <a name="troubleshooting"></a>Solução de problemas

Se você estiver tendo problemas para conectar-se ao seu aplicativo com o depurador remoto, você precisará verificar se as portas corretas estão abertas.

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-visual-studio-computer"></a>Verificar se as portas estão abertas no Firewall do Windows no computador do Visual Studio  
 As instruções para configurar o firewall do Windows é um pouco diferem em diferentes sistemas operacionais. No Windows 8/8.1, Windows 10 e Windows Server 2012, a palavra **aplicativo** é usado; no Windows 7 ou Windows Server 2008, a palavra **programa** é usado;  Nas etapas a seguir, usaremos a palavra **aplicativo**.  
  
1.  Abra a página de Firewall do Windows. (No **iniciar** caixa de pesquisa do menu, digite **Firewall do Windows**).  
  
2.  Clique em **permitem que um aplicativo ou recurso pelo Firewall do Windows**.  
  
3.  No **aplicativos e recursos permitidos** lista, procure **descoberta do depurador Visual Studio remoto**. Se estiver listado, certifique-se de que ele está selecionado e que um ou mais tipos de rede também são selecionados.  
  
4.  Se **descoberta do depurador Visual Studio remoto** não é listados, clique em **permitir que outro aplicativo**. Se você ainda não estiver visível no **adicionar um aplicativo** janela, clique em **procurar** e navegue até  **\<diretório de instalação do Visual Studio > \Common7\IDE\Remotedodepurador**. Localize a pasta apropriada para o aplicativo (x86, x64, Appx) e, em seguida, selecione **msvsmon.exe**. Em seguida, clique em **adicionar**.  
  
5.  No **aplicativos e recursos permitidos** lista, selecione **depurador remoto do Visual Studio**. Verificar um ou mais tipos de rede (**domínio, casa/do trabalho (privado), público**) que você deseja que o monitor de depuração remota para se comunicar com. Os tipos devem incluir a rede à qual o computador do Visual Studio está conectado. 

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-remote-computer"></a>Verificar se as portas estão abertas no Firewall do Windows no computador remoto  
 Os componentes de depuração remota podem ser instalados no computador remoto ou executar a partir de um diretório compartilhado. O firewall do computador remoto deve ser configurado em ambos os casos. Os componentes de depuração remota estão localizados em:  
  
 **\<Diretório de instalação do Visual Studio > \Common7\IDE\Remote depurador**  
  
 As instruções para configurar o firewall do Windows é um pouco diferem em diferentes sistemas operacionais. No Windows 8/8.1, Windows 10 e Windows Server 2012, a palavra **aplicativo** é usado; no Windows 7 ou Windows Server 2008, a palavra **programa** é usado;  Nas etapas a seguir, usaremos a palavra **aplicativo**.  
  
1.  Abra a página de Firewall do Windows. (No **iniciar** caixa de pesquisa do menu, digite **Firewall do Windows**.)  
  
2.  Clique em **permitem que um aplicativo ou recurso pelo Firewall do Windows**.  
  
3.  No **aplicativos e recursos permitidos** lista, procure **depurador remoto do Visual Studio**. Se estiver listado, certifique-se de que ele está selecionado e que um ou mais tipos de rede também são selecionados.  
  
4.  Se **depurador remoto do Visual Studio** não é listados, clique em **permitir que outro aplicativo**. Se você ainda não estiver visível no **adicionar uma janela de aplicativo**, clique em **procurar** e navegue até  **\<diretório de instalação do Visual Studio > \Common7\IDE\Remotedodepurador**. Localize a pasta apropriada para o aplicativo (x86, x64, Appx) e, em seguida, selecione **msvsmon.exe**. Em seguida, clique em **adicionar**.  
  
5.  No **permitido aplicativos** lista, selecione **depurador remoto do Visual Studio**. Verificar um ou mais tipos de rede (**domínio, casa/do trabalho (privado), público**) que você deseja que o monitor de depuração remota para se comunicar com. Os tipos devem incluir a rede à qual o computador do Visual Studio está conectado. 

### <a name="managed-or-native-compatibility-mode-open-additional-ports-on-the-remote-computer"></a>(Modo de compatibilidade gerenciado ou nativo) Abrir portas adicionais no computador remoto

Se você estiver usando o modo de compatibilidade para o depurador (**Ferramentas > Opções > depuração**), serão necessário abrir portas adicionais. Modo de compatibilidade habilita uma versão herdada do depurador e portas diferentes são necessárias.

> [!NOTE]
> A versão herdada do depurador é o depurador do Visual Studio 2010.
  
|||||  
|-|-|-|-|  
|**Portas**|**Entrada/saída**|**Protocolo**|**Descrição**|  
|135, 139, 445|Saída|TCP|Necessário.|  
|137, 138|Saída|UDP|Necessário.|  
|500, 4500|Saída|UDP|Necessário se a diretiva de domínio requer comunicação de rede a ser executada por meio de IPSec.|  
|80|Saída|TCP|Necessário para a depuração de servidor Web.|
  
## <a name="see-also"></a>Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)