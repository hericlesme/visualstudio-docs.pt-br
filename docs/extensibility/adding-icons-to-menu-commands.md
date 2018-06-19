---
title: Adicionando ícones a comandos de Menu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8591c55a176493ace23df2de61ba26d58a3155e2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098386"
---
# <a name="adding-icons-to-menu-commands"></a>Adicionando ícones a comandos de Menu
Comandos podem aparecer em menus e barras de ferramentas. Na barra de ferramentas, é comum para um comando a ser exibido com apenas um ícone (para economizar espaço) ao mesmo tempo nos menus de que um comando normalmente aparece com um ícone e o texto.  
  
 Ícones são 16 pixels de largura por 16 pixels de altura e podem ser a profundidade de cor de 8 bits (256 cores) ou a profundidade de cor de 32 bits (cor true). ícones de cor de 32 bits são preferenciais. Ícones normalmente são organizados em uma única linha horizontal em um único bitmap, embora vários bitmaps são permitidos. Esse bitmap é declarado no arquivo. VSCT junto com os ícones individuais disponíveis no bitmap. Consulte a referência para o [Bitmaps elemento](../extensibility/bitmaps-element.md) para obter mais detalhes.  
  
## <a name="adding-an-icon-to-a-command"></a>Adicionar um ícone para um comando  
 O procedimento a seguir pressupõe que você tenha um projeto VSPackage existente com um comando de menu. Para saber como fazer isso, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Crie um bitmap com uma profundidade de cor de 32 bits. Um ícone é sempre um múltiplo de 16 pixels de largura e de 16 x 16 para que este bitmap deve ser 16 pixels de altura.  
  
     Cada ícone é colocado no bitmap próximos um do outro em uma única linha. Use o canal alfa para indicar os locais de transparência de cada ícone.  
  
     Se você usar uma profundidade de cor de 8 bits, use magenta, `RGB(255,0,255)`, como a transparência. No entanto, os ícones de cor de 32 bits são preferenciais.  
  
2.  Copie o arquivo de ícone para o diretório de recursos em seu projeto VSPackage. No Gerenciador de soluções, adicione o ícone para o projeto. (Selecionar recursos, no menu de contexto, clique em Adicionar e, em seguida, Item existente e selecione o arquivo de ícone.)  
  
3.  Abra o arquivo. VSCT no editor.  
  
4.  Adicionar um `GuidSymbol` elemento com um nome de **testIcon**. Criar um GUID (**ferramentas / criar GUID**, em seguida, selecione **formato do registro** e clique em Copiar) e cole-o no `value` atributo. O resultado deve ter esta aparência:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Adicionar um `<IDSymbol>` do ícone. O `name` atributo é a ID do ícone e o `value` indica sua posição na fita, se houver. Se houver apenas um ícone, adicione 1. O resultado deve ter esta aparência:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Criar um `<Bitmap>` no `<Bitmaps>` seção do arquivo. VSCT para representar o bitmap que contém os ícones.  
  
    -   Definir o `guid` valor para o nome do `<GuidSymbol>` elemento que você criou na etapa anterior.  
  
    -   Definir o `href` valor para o caminho relativo do arquivo de bitmap (neste caso **recursos\\< nome do arquivo de ícone\>**.  
  
    -   Definir o `usedList` valor para o IDSymbol que você criou anteriormente. Esse atributo especifica uma lista delimitada por vírgulas dos ícones a serem usados no VSPackage. Ícones não está na lista são excluídos de forma compilação.  
  
         O bloco de Bitmap deve ter esta aparência:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  Existentes no `<Button>` elemento, defina o `Icon` elemento com os valores de GUIDSymbol e IDSymbol que você criou anteriormente. Aqui está um exemplo de um elemento de botão com esses valores:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  O ícone de teste. Compile o projeto e comece a depuração. Na instância experimental, localize o comando. Ele deverá mostrar o ícone que é adicionado.  
  
## <a name="see-also"></a>Consulte também  
 [Comandos e Menus estendendo](../extensibility/extending-menus-and-commands.md)   
 [Referência do esquema XML do VSCT](../extensibility/vsct-xml-schema-reference.md)