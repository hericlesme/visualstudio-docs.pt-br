---
title: "Preparação da depuração: Tipos de projeto do Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project templates, debugging
- Visual C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8cc51e55af477edfac65b79ca29e26b720510c55
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-preparation-visual-c-project-types"></a>Preparação de depuração: tipos de projeto Visual C++
Esta seção descreve como depurar os tipos de projeto básicos criados pelos modelos de projeto do [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].  
  
 Observe que os tipos de projeto que criam DLLs como sua saída foram agrupados em [depurar projetos de DLL](../debugger/debugging-dll-projects.md) devido os recursos comuns que eles compartilham.  
  
##  <a name="BKMK_In_this_topic"></a> Neste tópico  
 [Definições de propriedade recomendadas](#BKMK_Recommended_Property_Settings)  
  
 [Projetos do Win32](#BKMK_Win32_Projects)  
  
-   [Para depurar um aplicativo C ou C++ Win32](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
-   [Para definir manualmente uma configuração de depuração](#BKMK_To_manually_set_a_Debug_configuration)  
  
 [Aplicativos do Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a>Definições de propriedade recomendadas  
 Certas propriedades devem ser definidas da mesma maneira para todos os cenários não gerenciados de depuração. As tabelas a seguir exibem as configurações de propriedade recomendadas. As configurações não listadas aqui podem variar entre os tipos de projeto não gerenciados diferentes. Para obter mais informações, consulte [configurações de projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>Propriedades de configuração &#124; C/C++ &#124; Nó de otimização  
  
|Nome da Propriedade|Configuração|  
|-------------------|-------------|  
|**Optimization**|Definido como **desabilitado (/ 0D).** O código otimizado é mais difícil de depurar porque as instruções geradas não correspondem diretamente ao código-fonte. Se você achar que seu programa tem um erro que aparece somente no código otimizado, você pode ativar essa configuração, mas lembre-se de que o código mostrado no **desmontagem** janela é gerada de fonte otimizada que talvez não corresponda a que você vê na sua fonte Windows. Outros recursos, como depuração, podem não se comportar como esperado.|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>Propriedades de configuração &#124; Vinculador &#124; Nó de depuração  
  
|Nome da Propriedade|Configuração|  
|-------------------|-------------|  
|**Gerar informações de depuração**|Você deve sempre definir esta opção **Yes (/debug)** para criar os arquivos necessários para depuração e símbolos de depuração. Quando o aplicativo entra em produção, você pode defini-lo como desativado.|  
  
 [Neste tópico](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a>Projetos do Win32  
 Os aplicativos Win32 são programas do Windows tradicionais escritos em C ou C++. Depurar esse tipo de aplicativo no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é simples.  
  
 Os aplicativos Win32 incluem aplicativos do MFC e projetos do ATL. Eles usam APIs do Windows e podem usar MFC ou ATL, mas não usam Common Language Runtime (CLR). Podem, no entanto, chamar código gerenciado que usa o CLR.  
  
 O procedimento a seguir explica como depurar um projeto do Win32 de dentro do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Outro modo de depurar um aplicativo Win32 é iniciar o aplicativo fora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e anexar a ele. Para obter mais informações, consulte [anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a>Para depurar um aplicativo C ou C++ Win32  
  
1.  Abra o projeto no Visual Studio.  
  
2.  Sobre o **depurar** menu, escolha **iniciar**.  
  
3.  A depuração usando as técnicas discutidas na [Noções básicas do depurador](../debugger/debugger-basics.md).  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a>Para definir manualmente uma configuração de depuração  
  
1.  Sobre o **exibição** menu, clique em **páginas de propriedade**.  
  
2.  Clique o **propriedades de configuração** nó para abri-lo se ele não ainda estiver  
  
3.  Selecione **geral**e defina o valor da **saída** linha à **depurar**.  
  
4.  Abra o **C/C++** nó e selecione **geral**.  
  
     No **depurar** linha que você especificar o tipo de informações de depuração para ser gerado pelo compilador. Você pode escolher os valores incluem **banco de dados do programa (/Zi)** ou **banco de dados do programa para Editar & continuar (/ZI)**.  
  
5.  Selecione **otimização**e no **otimização** linha, selecione **desabilitado (/ 0D)** na lista suspensa.  
  
     O código otimizado é mais difícil de depurar porque as instruções geradas não correspondem diretamente ao código-fonte. Se você descobrir que seu programa tem um bug que aparece apenas em código otimizado, poderá ativar essa configuração, mas lembre-se de que o código mostrado na janela Desmontagem é gerado de origem otimizada que pode não corresponder ao que é visto em suas janelas de origem. Os recursos como o depuração provavelmente mostram incorretamente pontos de interrupção e ponto de execução.  
  
6.  Abra o **vinculador** nó e selecione **depuração**. Na primeira **gerar** linha, selecione **Yes (/debug)** na lista suspensa. Sempre defina isso quando você estiver depurando.  
  
 Para obter mais informações, consulte[configurações de projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 [Neste tópico](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a>Aplicativos do Windows Forms (.NET)  
 O **aplicativos de formulários do Windows (.NET)** modelo cria um [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplicativo do Windows Forms. Para obter mais informações, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Depurar esse tipo de aplicativo no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é semelhante a depurar em aplicativos gerenciados do Windows Forms.  
  
 Quando você cria um projeto do Windows Forms com o modelo de projeto, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria automaticamente as configurações necessárias para as configurações de depuração e versão. Se necessário, você pode alterar essas configurações no  **\<nome do projeto > páginas de propriedade** caixa de diálogo. Para obter mais informações, consulte [configurações Debug e Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Para obter mais informações, consulte [configurações de projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Outro modo de depurar um aplicativo do Windows Forms 2 é iniciar o aplicativo fora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e anexar a ele. Para obter mais informações, consulte [anexar a um programa em execução ou vários programas](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [Neste tópico](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Configurações de projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Anexar a um programa em execução ou vários programas](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Como: criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)