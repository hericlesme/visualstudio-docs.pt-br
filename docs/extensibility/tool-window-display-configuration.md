---
title: "Ferramenta de configuração de exibição da janela | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 585ea78e0591ad979d09a3e5b208635c3f75f903
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="tool-window-display-configuration"></a>Configuração de exibição da janela de ferramenta
Quando um VSPackage registra uma janela de ferramenta, a posição padrão, tamanho, estilo de encaixe e outras informações de visibilidade é especificado em valores opcionais. Para obter mais informações sobre o registro da janela da ferramenta, consulte [janelas de ferramenta no registro](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Informações de exibição da janela  
 Configuração de exibição básica de uma janela ferramenta é armazenada em até seis valores opcionais:  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|Nome|REG_SZ|"O nome curto aqui"|Um nome curto que descreve a janela da ferramenta. Usado somente para referência no registro.|  
|Float|REG_SZ|"X1, Y1, X2, Y2"|Quatro valores separados por vírgula. X1, Y1 é a coordenada do canto superior esquerdo da janela de ferramentas. X2, Y2 é a coordenada do canto inferior direito. Todos os valores estão em coordenadas da tela.|  
|Estilo|REG_SZ|"MDI"<br /><br /> "Flutuar"<br /><br /> "Vincular"<br /><br /> "Guias"<br /><br /> "AlwaysFloat"|Uma palavra-chave especificando inicial exibir o estado da janela de ferramentas.<br /><br /> "MDI" = encaixado com janela MDI.<br /><br /> "Flutuar" = flutuante.<br /><br /> "Vincular" = vinculado a outra janela (especificada na entrada de janela).<br /><br /> "Guias" = combinada com outra janela de ferramenta.<br /><br /> "AlwaysFloat" = não pode ser encaixada.<br /><br /> Para obter mais informações, consulte a seção de comentários abaixo.|  
|Janela|REG_SZ|*\<GUID >*|O GUID de uma janela para que a janela da ferramenta pode ser vinculada ou com guias. O GUID pode pertencer a uma das suas próprias janelas ou as janelas do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE.|  
|{1&gt;Orientação&lt;1}|REG_SZ|"Esquerda"<br /><br /> "Direita"<br /><br /> "Top"<br /><br /> "Inferior"|Consulte a seção de comentários abaixo.|  
|DontForceCreate|REG_DWORD|0 ou 1|Quando essa entrada estiver presente e seu valor não for zero, a janela é carregada, mas não imediatamente exibida.|  
  
### <a name="comments"></a>Comentários  
 A entrada de orientação define a posição em que a janela da ferramenta encaixa quando sua barra de título é clicado duas vezes. É a posição relativa à janela do especificado na entrada de janela. Se a entrada de estilo é definida como "Vinculados", a entrada de orientação pode ser "Esquerda", "Direita", "Top" ou "Inferior". Se a entrada de estilo é "Com guias", a orientação de entrada pode ser "esquerda" ou "Direita" e especifica onde a guia é adicionada. Se a entrada do estilo "Flutuar", a janela da ferramenta flutua pela primeira vez. Quando a barra de título é clicado duas vezes, as entradas de janela e de orientação se aplicam, e a janela usa o estilo "com guias". Se a entrada de estilo é "AlwaysFloat", a janela da ferramenta não pode ser encaixada. Se a entrada do estilo "MDI", a janela da ferramenta está vinculada à área de MDI e a entrada de janela é ignorada.  
  
### <a name="example"></a>Exemplo  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>Visibilidade da janela de ferramenta  
 Valores na subchave visibilidade opcional determinam as configurações de visibilidade de uma janela ferramenta. Os nomes dos valores são usados para armazenar os GUIDs dos comandos que exigem a visibilidade da janela. Se o comando é executado, o IDE garante que a janela de ferramentas é criada e ficam visível.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|(Padrão)|REG_SZ|Nenhum|Deixe em branco.|  
|*\<GUID >*|REG_DWORD ou REG_SZ|0 ou uma cadeia de caracteres descritiva.|Opcional. Nome da entrada deve ser o GUID de um comando que exigem a visibilidade. O valor contém apenas uma cadeia de caracteres informativa. Normalmente, o valor é um `reg_dword` definido como 0.|  
  
### <a name="example"></a>Exemplo  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)