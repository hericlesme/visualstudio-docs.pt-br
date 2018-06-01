---
title: Entradas do registro para suplementos do VSTO
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e2aaec6df10a39d9f07938502a30eaa0a5d4ee9d
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692890"
---
# <a name="registry-entries-for-vsto-add-ins"></a>Entradas do registro para suplementos do VSTO
  Quando você implanta suplementos do VSTO que são criados usando o Visual Studio, você deve criar um conjunto específico de entradas do registro. Essas entradas de registro fornecem informações que permite que o aplicativo do Microsoft Office descobrir e carregar o suplemento do VSTO.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Quando você compila seu projeto, o Visual Studio cria essas entradas do registro no computador de desenvolvimento para que você pode facilmente executar e depurar o suplemento do VSTO. Se você usar o ClickOnce para implantar o suplemento do VSTO, as entradas do registro são criadas automaticamente no computador do usuário final. Se você usar o Windows Installer para implantar o suplemento do VSTO, você deve configurar o projeto do InstallShield Limited Edition para criar as entradas do registro no computador do usuário final.  
  
 Para obter mais informações sobre como as entradas do registro são usadas durante o processo de carregamento de suplementos do VSTO, consulte [suplementos da arquitetura do VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Neste tópico, o texto *na ID de-* representa uma ID exclusiva para o suplemento do VSTO. Por padrão, a ID é o nome do seu assembly do suplemento do VSTO.  
  
## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Registrar o suplemento do VSTO para o usuário atual e todos os usuários  
 Quando um suplemento do VSTO é instalado, ele pode ser registrado duas maneiras:  
  
-   Somente o usuário atual (ou seja, ele é disponível somente para o usuário que estiver conectado ao computador quando o suplemento do VSTO está instalado). Nesse caso, as entradas do registro são criadas sob o **HKEY_CURRENT_USER**.  
  
-   Para todos os usuários (ou seja, qualquer usuário que fizer logon no computador pode usar o suplemento do VSTO). Nesse caso, as entradas do registro são criadas em **HKEY_LOCAL_MACHINE**.  
  
 Todos os suplementos do VSTO que você cria usando o Visual Studio podem ser registrados para o usuário atual. No entanto, os suplementos do VSTO podem ser registrados para todos os usuários somente em determinados cenários. Nesses cenários dependem da versão do Microsoft Office no computador e como o suplemento do VSTO foi implantado.  
  
### <a name="microsoft-office-version"></a>Versão do Microsoft Office  
 Aplicativos do Office podem carregar suplementos do VSTO que são registrados em **HKEY_LOCAL_MACHINE** ou **HKEY_CURRENT_USER**.  
  
 Para carregar os suplementos do VSTO que são registrados em **HKEY_LOCAL_MACHINE**, os computadores devem ter o pacote de atualização 976477 instalado. Para obter mais informações, consulte [http://go.microsoft.com/fwlink/?LinkId=184923](http://go.microsoft.com/fwlink/?LinkId=184923).  
  
### <a name="deployment-type"></a>Tipo de implantação  
 Se você usar o ClickOnce para implantar um suplemento do VSTO, o suplemento do VSTO pode ser registrado apenas para o usuário atual. Isso ocorre porque o ClickOnce oferece suporte apenas a criação de chaves em **HKEY_CURRENT_USER**. Se você quiser registrar um suplemento do VSTO para todos os usuários em um computador, você deve usar o Windows Installer para implantar o suplemento do VSTO. Para obter mais informações sobre esses tipos de implantação, consulte [implantar uma solução do Office usando o ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) e [implantar uma solução do Office usando o Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## <a name="registry-entries"></a>Entradas do registro  
 As entradas de registro do suplemento do VSTO necessárias estão localizadas na seguinte chave do registro para todos os aplicativos, exceto o Visio, onde *raiz* é **HKEY_CURRENT_USER** ou **HKEY_LOCAL_MACHINE** .  
  
 **Todos os aplicativos, exceto o Visio**  
  
|Versão do Office|Caminho de configuração|  
|--------------------|------------------------|  
|32 bits|*Raiz*\Software\Microsoft\Office\\*nome do aplicativo*\Addins\\*ID do suplemento*|  
|64 bits|*Raiz*\Software\Wow6432Node\Microsoft\Office\\*nome do aplicativo*\Addins\\*ID do suplemento*|  
  
 **Visio**  
  
|Versão do Office|Caminho de configuração|  
|--------------------|------------------------|  
|32 bits|*Raiz*\Software\Microsoft\Visio\Addins\\*ID do suplemento*|  
|64 bits|*Raiz*\Software\Wow6432Node\Visio\Addins\\*ID do suplemento*|  
  
 A tabela a seguir relaciona as entradas nessa chave do registro.  
  
|Entrada|Tipo|Valor|  
|-----------|----------|-----------|  
|**Descrição**|REG_SZ|Necessário. Uma breve descrição do suplemento do VSTO.<br /><br /> Essa descrição é exibida quando o usuário seleciona o suplemento do VSTO no **Add-Ins** painel do **opções** caixa de diálogo no aplicativo do Microsoft Office.|  
|**Nome amigável**|REG_SZ|Necessário. Um nome descritivo do Add-in do VSTO que é exibido no **suplementos COM** caixa de diálogo no aplicativo do Microsoft Office. O valor padrão é a ID do suplemento do VSTO|  
|**LoadBehavior**|REG_DWORD|Necessário. Um valor que especifica quando o aplicativo tenta carregar o suplemento do VSTO e o estado atual do VSTO Add-in (carregado ou não carregado).<br /><br /> Por padrão, essa entrada é definida como 3, que especifica que o suplemento do VSTO é carregado na inicialização. Para obter mais informações, consulte [LoadBehavior valores](#LoadBehavior). **Observação:** se um usuário desativa o suplemento do VSTO, essa ação modifica **LoadBehavior** valor o **HKEY_CURRENT_USER** hive do registro. Para cada usuário, o valor da **LoadBehavior** valor na seção HKEY_CURRENT_USER substitui o padrão **LoadBehavior** definido no **HKEY_LOCAL_MACHINE** hive.|  
|**Manifesto**|REG_SZ|Necessário. O caminho completo do manifesto de implantação para o suplemento do VSTO. O caminho pode ser um local no computador local, um servidor Web (HTTP) ou um compartilhamento de rede (UNC).<br /><br /> Se você usar o Windows Installer para implantar a solução, você deve adicionar o prefixo **file:///** para o **manifesto** caminho. Você também deve acrescentar a cadeia de caracteres  **&#124;vstolocal** (ou seja, o caractere de pipe **&#124;** seguido por **vstolocal**) ao final desse caminho. Isso garante que sua solução será carregada a partir da pasta de instalação, em vez de cache do ClickOnce. Para obter mais informações, consulte [implantar uma solução do Office usando o Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md). **Observação:** quando você criar um suplemento do VSTO no computador de desenvolvimento, o Visual Studio anexa automaticamente o  **&#124;vstolocal** cadeia de caracteres para esta entrada do registro.|  
  
###  <a name="OutlookEntries"></a> Entradas do registro para regiões de formulário do Outlook  
 Se você criar uma região de formulário personalizado em um suplemento do VSTO para Outlook, entradas de registro adicionais são usadas para registrar a região de formulário com o Outlook. Essas entradas são criadas em uma chave do registro diferente para cada classe de mensagem que dá suporte a região do formulário. Essas chaves do registro estão no local a seguir, onde *raiz* é **HKEY_CURRENT_USER** ou **HKEY_LOCAL_MACHINE**.  
  
 *Raiz*\Software\Microsoft\Office\Outlook\FormRegions\\*classe message*  
  
 Como as outras entradas do registro compartilhadas por todos os suplementos do VSTO, Visual Studio cria o formulário região entradas de registro no computador de desenvolvimento quando você compilar o projeto. Se você usar o ClickOnce para implantar o suplemento do VSTO, as entradas do registro são criadas automaticamente no computador do usuário final. Se você usar o Windows Installer para implantar o suplemento do VSTO, você deve configurar o projeto do InstallShield Limited Edition para criar as entradas do registro no computador do usuário final.  
  
 Para obter mais informações sobre as entradas de registro de região de formulário, consulte [especificar o local de uma região de formulário em um formulário personalizado](http://msdn.microsoft.com/library/office/ff868998.aspx). Para obter mais informações sobre regiões de formulário do Outlook, consulte [regiões de formulário do Outlook criar](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="LoadBehavior"></a> Valores de LoadBehavior  
 O **LoadBehavior** entrada sob o *raiz*\Software\Microsoft\Office\\*nome do aplicativo*\Addins\\*suplemento ID* chave contém uma combinação bit a bit de valores que especificam o comportamento de tempo de execução do suplemento do VSTO. O bit mais baixo (os valores 0 e 1) indica se o suplemento do VSTO está descarregado ou carregado. Outros bits indicam quando o aplicativo tenta carregar o suplemento do VSTO.  
  
 Normalmente, o **LoadBehavior** entrada se destina a ser definido como 0, 3 ou 16 (em decimal) quando o suplemento do VSTO é instalado em computadores de usuários finais. Por padrão, o Visual Studio define o **LoadBehavior** entrada de seu suplemento do VSTO para 3 quando você compila ou publicá-lo.  
  
 A tabela a seguir lista todos os valores possíveis do **LoadBehavior** entrada. Algumas descrições nesta tabela consultem carregando um suplemento do VSTO manualmente ou programaticamente. Para carregar um suplemento do VSTO manualmente, marque a caixa de seleção ao lado do suplemento do VSTO no **suplementos COM** caixa de diálogo do aplicativo. Para carregar um suplemento do VSTO por meio de programação, defina o <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> propriedade o <xref:Microsoft.Office.Core.COMAddIn> objeto que representa o suplemento do VSTO para **true**.  
  
|Valor (decimal)|Status de suplemento do VSTO|Comportamento do VSTO suplemento de carga|Descrição|  
|--------------------------|-------------------------|--------------------------------|-----------------|  
|0|Descarregado|Não carregar automaticamente|O aplicativo nunca tenta carregar automaticamente o suplemento do VSTO. O usuário pode tentar carregar manualmente o suplemento do VSTO ou o suplemento do VSTO pode ser carregado por meio de programação.<br /><br /> Se o suplemento do VSTO é carregado com êxito, o **LoadBehavior** valor permanece 0, mas o status do suplemento do VSTO no **suplementos COM** caixa de diálogo será atualizada para indicar que o suplemento do VSTO é carregado.|  
|1|Carregado|Não carregar automaticamente|O aplicativo nunca tenta carregar automaticamente o suplemento do VSTO. O usuário pode tentar carregar manualmente o suplemento do VSTO ou o suplemento do VSTO pode ser carregado por meio de programação.<br /><br /> Embora o **suplementos COM** caixa de diálogo indica que o suplemento do VSTO é carregado depois que o aplicativo for iniciado, o suplemento do VSTO não está carregado até que ele seja carregado manualmente ou programaticamente.<br /><br /> Se o aplicativo é carregado com êxito o VSTO suplemento, o **LoadBehavior** valor é alterado para 0 e permanece em 0 depois que o aplicativo for fechado.|  
|2|Descarregado|Carregar na inicialização|O aplicativo não tentará carregar automaticamente o suplemento do VSTO. O usuário pode tentar carregar manualmente o suplemento do VSTO ou o suplemento do VSTO pode ser carregado por meio de programação.<br /><br /> Se o aplicativo é carregado com êxito o VSTO suplemento, o **LoadBehavior** valor é alterado para 3 e permanece em 3 depois que o aplicativo for fechado.|  
|3|Carregado|Carregar na inicialização|O aplicativo tenta carregar o suplemento do VSTO quando o aplicativo for iniciado. Este é o valor padrão quando você compila ou publica um suplemento do VSTO no Visual Studio.<br /><br /> Se o aplicativo é carregado com êxito o VSTO suplemento, o **LoadBehavior** valor permanece 3. Se ocorrer um erro ao carregar o Add-in do VSTO, o **LoadBehavior** valor muda para 2 e permanece em 2 depois que o aplicativo for fechado.|  
|8|Descarregado|Carregar sob demanda|O aplicativo não tentará carregar automaticamente o suplemento do VSTO. O usuário pode tentar carregar manualmente o suplemento do VSTO ou o suplemento do VSTO pode ser carregado por meio de programação.<br /><br /> Se o aplicativo é carregado com êxito o VSTO suplemento, o **LoadBehavior** valor é alterado para 9.|  
|9|Carregado|Carregar sob demanda|O suplemento do VSTO será carregado somente quando o aplicativo requer, como quando um usuário clica em um elemento de interface do usuário que usa a funcionalidade de suplemento do VSTO (por exemplo, um botão personalizado na faixa de opções).<br /><br /> Se o aplicativo é carregado com êxito o VSTO suplemento, o **LoadBehavior** valor permanece 9, mas o status do suplemento do VSTO no **suplementos COM** caixa de diálogo é atualizada para indicar que o suplemento do VSTO atualmente carregado. Se ocorrer um erro ao carregar o Add-in do VSTO, o **LoadBehavior** valor é alterado para 8.|  
|16|Carregado|Carregar primeira vez, em seguida, carregar sob demanda|Defina esse valor se você deseja que seu suplemento do VSTO para ser carregado sob demanda. O aplicativo carrega o suplemento do VSTO quando o usuário executa o aplicativo pela primeira vez. Na próxima vez que o usuário executa o aplicativo, o aplicativo carrega todos os elementos da interface do usuário que são definidos pelo suplemento do VSTO, mas o suplemento do VSTO não será carregado até que o usuário clica em um elemento de interface do usuário que está associado com o suplemento do VSTO.<br /><br /> Quando o aplicativo carrega com êxito o suplemento do VSTO pela primeira vez, o **LoadBehavior** valor permanece 16 enquanto o suplemento do VSTO é carregado. Depois que o aplicativo for fechado, o **LoadBehavior** valor é alterado para 9.|  
  
## <a name="see-also"></a>Consulte também  
 [Arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Criar soluções do Office](../vsto/building-office-solutions.md)   
 [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)  
  
  