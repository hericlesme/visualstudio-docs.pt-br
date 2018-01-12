---
title: "Como: expor código para VBA em um projeto do Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8d3d007024cdca160c194285da8f0a741100253d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Como expor código para VBA em um projeto do Visual Basic
  Você pode expor o código em um [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] de projeto do Visual Basic para código Applications (VBA) se você quiser que os dois tipos de código interagem entre si.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 O processo do Visual Basic é diferente do processo do Visual c#. Para obter mais informações, consulte [como: expor código para VBA em um Visual C &#35; Projeto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 O processo é diferente para o código em uma classe de item de host para o código em outras classes:  
  
-   [Expondo código em uma classe de item de host](#HostItemCode)  
  
-   [Expondo código que não está em uma classe de item de host](#NonHostItem)  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer i: chamar VSTO código do VBA?](http://go.microsoft.com/fwlink/?LinkId=136757).  
  
##  <a name="HostItemCode"></a>Expondo código em uma classe de Item de Host  
 Para habilitar o código do VBA chamar o código do Visual Basic em uma classe de item de host, defina o **EnableVbaCallers** propriedade do item de host para **True**.  
  
 Para uma explicação passo a passo que demonstra como expor um método de uma classe de item de host e, em seguida, chama do VBA, consulte [passo a passo: chamando código de VBA em um projeto do Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Para obter mais informações sobre itens de host, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md).  
  
#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Para expor o código em um item de host para VBA  
  
1.  Abra ou crie um nível de documento [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projeto com base em um documento do Word, a pasta de trabalho do Excel ou o modelo do Excel que oferece suporte a macros e que já contém o código do VBA.  
  
     Para obter mais informações sobre os formatos de arquivo de documento que oferecem suporte a macros, consulte [combinando VBA e personalizações no nível do documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Esse recurso não pode ser usado em projetos de modelo do Word.  
  
2.  Certifique-se de que o código do VBA no documento pode ser executado sem avisar o usuário para habilitar as macros. Você pode confiar em código do VBA para executar, adicionando o local do Office project à lista de locais confiáveis nas configurações de Central de confiabilidade do Word ou Excel.  
  
3.  Adicionar a propriedade, método ou evento que você deseja expor ao VBA para uma das classes de item de host em seu projeto e declarar o novo membro como **público**. O nome da classe depende do aplicativo:  
  
    -   Em uma palavra projeto, a classe de item de host é nomeada `ThisDocument` por padrão.  
  
    -   Em um projeto do Excel, as classes de item de host são nomeadas `ThisWorkbook`, `Sheet1`, `Sheet2`, e `Sheet3` por padrão.  
  
4.  Definir o **EnableVbaCallers** propriedade do item de host para **True**. Essa propriedade está disponível na **propriedades** janela quando o item de host está aberto no designer.  
  
     Depois que você define essa propriedade, o Visual Studio define automaticamente o **ReferenceAssemblyFromVbaProject** propriedade **True**.  
  
    > [!NOTE]  
    >  Se a pasta de trabalho ou o documento ainda não contém código VBA, ou se o código do VBA no documento não é confiável para ser executado, você receberá uma mensagem de erro ao definir o **EnableVbaCallers** propriedade **True**. Isso ocorre porque o Visual Studio não é possível modificar o projeto do VBA no documento nessa situação.  
  
5.  Clique em **Okey** na mensagem que é exibida. Essa mensagem informa que se você adicionar o código do VBA para a pasta de trabalho ou um documento enquanto você estiver executando o projeto de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], o código do VBA serão perdido na próxima vez que você compilar o projeto. Isso ocorre porque o documento na pasta de saída de compilação é substituído sempre que você compilar o projeto.  
  
     Neste ponto, o Visual Studio configura o projeto para que possa chamar o projeto do VBA no assembly. O Visual Studio também adiciona uma propriedade chamada `CallVSTOAssembly` para o `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, ou `Sheet3` módulo no projeto VBA. Você pode usar essa propriedade para acessar os membros públicos da classe que é exposto ao VBA.  
  
6.  Compile o projeto.  
  
##  <a name="NonHostItem"></a>Expondo código que não está em uma classe de Item de Host  
 Para habilitar o código do VBA chamar o código do Visual Basic que não está em uma classe de item de host, modifique o código para que fique visível para VBA.  
  
#### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Para expor o código que não está em uma classe de item de host para VBA  
  
1.  Abra ou crie um nível de documento [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projeto com base em um documento do Word, a pasta de trabalho do Excel ou o modelo do Excel que oferece suporte a macros e que já contém o código do VBA.  
  
     Para obter mais informações sobre os formatos de arquivo de documento que oferecem suporte a macros, consulte [combinando VBA e personalizações no nível do documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Esse recurso não pode ser usado em projetos de modelo do Word.  
  
2.  Certifique-se de que o código do VBA no documento pode ser executado sem avisar o usuário para habilitar as macros. Você pode confiar em código do VBA para executar, adicionando o local do Office project à lista de locais confiáveis nas configurações de Central de confiabilidade do Word ou Excel.  
  
3.  Adicionar o membro que você deseja expor ao VBA para uma classe pública em seu projeto e declarar o novo membro como **público**.  
  
4.  Aplicar o seguinte <xref:System.Runtime.InteropServices.ComVisibleAttribute> e <xref:Microsoft.VisualBasic.ComClassAttribute> atributos para a classe que você está expondo a VBA. Esses atributos tornar a classe visível para VBA.  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  Substituir o **GetAutomationObject** método de uma classe de item de host em seu projeto para retornar uma instância da classe que você está expondo a VBA. O exemplo de código a seguir pressupõe que você está expondo uma classe denominada `DocumentUtilities` para VBA.  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  Abra o documento (para o Word) ou o designer de planilha (para Excel) em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
7.  No **propriedades** janela, selecione o **ReferenceAssemblyFromVbaProject** propriedade e altere o valor para **True**.  
  
    > [!NOTE]  
    >  Se a pasta de trabalho ou o documento ainda não contém código VBA, ou se o código do VBA no documento não é confiável para ser executado, você receberá uma mensagem de erro ao definir o **ReferenceAssemblyFromVbaProject** propriedade **True** . Isso ocorre porque o Visual Studio não é possível modificar o projeto do VBA no documento nessa situação.  
  
8.  Clique em **Okey** na mensagem que é exibida. Essa mensagem informa que se você adicionar o código do VBA para a pasta de trabalho ou um documento enquanto você estiver executando o projeto de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], o código do VBA serão perdido na próxima vez que você compilar o projeto. Isso ocorre porque o documento na pasta de saída de compilação é substituído sempre que você compilar o projeto.  
  
     Neste ponto, o Visual Studio configura o projeto para que possa chamar o projeto do VBA no assembly. O Visual Studio também adiciona um método chamado `GetManagedClass` para o projeto do VBA. Você pode chamar esse método de qualquer lugar no projeto VBA para acessar a classe que é exposto ao VBA.  
  
9. Compile o projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combinando VBA e personalizações no nível do documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Passo a passo: Chamando código do VBA em um projeto do Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Como: expor código para VBA em um Visual C &#35; Projeto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  