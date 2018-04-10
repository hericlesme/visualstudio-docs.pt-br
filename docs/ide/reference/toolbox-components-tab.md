---
title: Caixa de ferramentas, Guia Componentes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: aa91db706d7e1236162ef69e6fd31e791ed44dbb
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/10/2018
---
# <a name="toolbox-components-tab"></a>Caixa de Ferramentas, Guia Componentes

Exibe os componentes que podem ser adicionados a designers do Visual Basic e C#. Além dos componentes do .NET Framework incluídos no Visual Studio, como os componentes <xref:System.Messaging.MessageQueue> e <xref:System.Diagnostics.EventLog>, é possível adicionar seus próprios componentes ou os componentes de terceiros a essa guia.
  
 Para exibir essa guia, no menu **Exibir**, selecione **Caixa de ferramentas**. Na **Caixa de ferramentas**, selecione a guia **Componentes**.  
  
 **BackgroundWorker**  
 Cria uma instância do componente `System.ComponentModel.BackgroundWorker` que pode executar uma operação em um thread separado e dedicado.  
  
 **DirectoryEntry**  
 Cria uma instância do componente <xref:System.DirectoryServices.DirectoryEntry>, que encapsula um nó ou um objeto na hierarquia do Active Directory e pode ser usada para interagir com provedores de serviços do Active Directory.  
  
 **DirectorySearcher**  
 Cria uma instância do componente <xref:System.DirectoryServices.DirectorySearcher>, que pode ser usada para executar consultas no Active Directory.  
  
 **ErrorProvider**  
 Cria uma instância do componente `System.Windows.Forms.ErrorProvider`, que indica para o usuário final que um controle em um formulário tem um erro associado a ele.  
  
 **EventLog**  
 Cria uma instância do componente <xref:System.Diagnostics.EventLog>, que pode ser usada para interagir com logs do sistema e de eventos personalizados, incluindo a gravação de eventos em um log e a leitura dos dados de log.
  
 **FileSystemWatcher**  
 Cria uma instância do componente <xref:System.IO.FileSystemWatcher>, que pode ser usada para monitorar alterações em um diretório ou arquivo ao qual você tem acesso.
  
 **HelpProvider**  
 Cria uma instância do componente `System.Windows.Forms.HelpProvider` que fornece Ajuda pop-up ou online para controles.  
  
 **ImageList**  
 Cria uma instância do componente `System.Windows.Forms.ImageList` que fornece métodos para gerenciar uma coleção de objetos `System.Drawing.Image`.  
  
 **MessageQueue**  
 Cria uma instância do componente <xref:System.Messaging.MessageQueue>, que pode ser usada para interagir com filas de mensagens, incluindo a leitura e gravação de mensagens em filas, o processamento de transações e a realização de tarefas de administração de fila.

 **PerformanceCounter**  
 Cria uma instância do componente <xref:System.Diagnostics.PerformanceCounter>, que pode ser usada para interagir com contadores de desempenho do Windows, incluindo a criação de novas categorias e instâncias, a leitura de valores de contadores e a execução de cálculos nos dados do contador.
  
 **Processo**  
 Cria uma instância do componente <xref:System.Diagnostics.Process>, que pode ser usada para interromper, iniciar e manipular os dados associados a processos no sistema.
  
 **SerialPort**  
 Cria uma instância do componente `System.IO.Ports.SerialPort` que fornece E/S síncrona e controlada por evento, acesso ao PIN e estados de fixação e interrupção e acesso às propriedades do driver serial.  
  
 **ServiceController**  
 Cria uma instância do componente <xref:System.ServiceProcess.ServiceController>, que pode ser usada para manipular serviços existentes, incluindo a inicialização e a interrupção de serviços e o envio de comandos para eles.
  
 **Timer**  
 Cria uma instância do componente <xref:System.Windows.Forms.Timer>, que pode ser usada para adicionar funcionalidade baseada em tempo aos aplicativos baseados no Windows. Para obter mais informações, consulte [Componente de temporizador](/dotnet/framework/winforms/controls/timer-component-windows-forms).  
  
> [!NOTE]
>  Também há um <xref:System.Timers.Timer> baseado em sistema que pode ser adicionado à **Caixa de ferramentas**. Esse <xref:System.Timers.Timer> é otimizado para aplicativos de servidor e o <xref:System.Windows.Forms.Timer> do Windows Forms é mais adequado para uso no Windows Forms.  
  
## <a name="see-also"></a>Consulte também

[Programação com componentes](http://msdn.microsoft.com/Library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
[Passo a passos da programação de componentes](http://msdn.microsoft.com/Library/373cacf7-479e-4b05-991c-5cb18824e913)  
[Caixa de Ferramentas](../../ide/reference/toolbox.md)