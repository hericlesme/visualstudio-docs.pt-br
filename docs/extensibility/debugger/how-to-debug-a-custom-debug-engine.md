---
title: 'Como: Depurar um mecanismo de depuração personalizado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 95a2db2bc5e8990f536abc851941c337a1dee277
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Como: Depurar um mecanismo de depuração personalizado
Um tipo de projeto inicia o mecanismo de depuração (DE) do <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> método. Isso significa que o DE é iniciado sob o controle da instância do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controlar o tipo de projeto. No entanto, essa instância do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] não é possível depurar o DE. A seguir está as etapas para permitir que você depure seu personalizado DE.  
  
> [!NOTE]
>  : No procedimento "Depuração um personalizado depurar mecanismo", você deve aguardar o DE iniciar antes que você pode anexar a ela. Se você colocar uma caixa de mensagem próximo ao início do seu DE que aparece quando o DE inicia, você pode anexar nesse momento e, em seguida, desmarque a caixa de mensagem para continuar. Dessa forma, você pode capturar todos os eventos DE.  
  
> [!WARNING]
>  Você deve ter a depuração remota instalada antes de tentar os procedimentos a seguir. Consulte [depuração remota](../../debugger/remote-debugging.md) para obter detalhes.  
  
### <a name="debugging-a-custom-debug-engine"></a>Depuração de um mecanismo de depuração personalizado  
  
1.  Iniciar msvsmon.exe, o Monitor de depuração remota.  
  
2.  Do **ferramentas** menu msvsmon.exe, selecione **opções** para abrir o **opções** caixa de diálogo.  
  
3.  Selecione a opção "sem autenticação" e clique em **Okey**.  
  
4.  Iniciar uma instância de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e abra o projeto DE personalizado.  
  
5.  Inicie uma segunda instância de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e abra seu projeto personalizado que inicia DE (para o desenvolvimento, isso normalmente é no hive do registro experimental que é configurado quando VSIP está instalado).  
  
6.  Na segunda instância de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], carregar um arquivo de origem do seu projeto personalizado e iniciar o programa a ser depurado. Aguarde alguns instantes para permitir que o DE carregar ou aguarde até que um ponto de interrupção é atingido.  
  
7.  Na primeira instância do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (com o seu projeto DE), selecione **anexar ao processo** do **depurar** menu.  
  
8.  No **anexar ao processo** caixa de diálogo, altere o **transporte** para **remoto (somente nativo sem autenticação)**.  
  
9. Alterar o **qualificador** para o nome do seu computador (Observação: há um histórico de entradas, para que seja necessário digitar este nome apenas uma vez).  
  
10. No **processos disponíveis** , selecione a instância do seu DE que está em execução e clique no **Attach** botão.  
  
11. Após carregaram os símbolos em seu DE, coloque pontos de interrupção no seu código DE.  
  
12. Sempre que você para e reiniciar o processo de depuração, repita as etapas 6 a 10.  
  
### <a name="debugging-a-custom-project-type"></a>Depuração de um tipo de projeto personalizados  
  
1.  Iniciar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no hive do registro normal e carga seu projeto de tipo de projeto (isto é, a origem para o tipo de projeto, não uma instanciação de seu tipo de projeto).  
  
2.  Abra as propriedades do projeto e acesse o **depurar** página. Para o **comando**, digite o caminho para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (por padrão, isso é *[unidade]*\Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).  
  
3.  Para o **argumentos de comando**, tipo `/rootsuffix exp` para o hive de registro experimental (criado quando VSIP foi instalado).  
  
4.  Clique em **OK** para aceitar as alterações.  
  
5.  Inicie o tipo de projeto, pressionando F5. Isso iniciará uma segunda instância do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
6.  Neste ponto, você pode colocar pontos de interrupção em seu código de origem do tipo de projeto.  
  
7.  Na segunda instância de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], carregar ou criar uma nova instância do seu tipo de projeto. Durante a criação ou carga, seus pontos de interrupção podem ser atingidos.  
  
8.  Depura o tipo de projeto.  
  
9. Se você optar por depurar o processo de inicialização DE, você pode executar as etapas no procedimento "Depuração um personalizado depurar mecanismo" anexar a sua DE após ele é iniciado. Isso lhe dará três instâncias do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] em execução: uma para sua fonte de tipo de projeto, um segundo para o tipo de projeto instanciado e um terceiro anexado ao seu DE.  
  
## <a name="see-also"></a>Consulte também  
 [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)