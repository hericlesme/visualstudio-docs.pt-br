---
title: "Como: expor código para VBA em um projeto do Visual c# | Microsoft Docs"
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
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
ms.assetid: 56d5894b-4823-42f4-8c7e-d8739b859c52
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a52060f1a1b2200109c5003321857915d95bd12a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Como expor código para VBA em um projeto do Visual C#
  Se você quiser que os dois tipos de código interagem entre si, você pode expor código em um projeto Visual c# para o Visual Basic para código Applications (VBA).  
  
 O processo do Visual c# é diferente do processo do Visual Basic. Para obter mais informações, consulte [como: expor código para VBA em um projeto do Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="exposing-code-in-a-visual-c-project"></a>Expondo código em um projeto do Visual c#  
 Para habilitar o código do VBA chamar o código em um projeto Visual c#, modifique o código para que fique visível para COM e, em seguida, defina o **ReferenceAssemblyFromVbaProject** propriedade **True** no designer.  
  
 Para uma explicação passo a passo que demonstra como chamar um método em um projeto do Visual c# do VBA, consulte [passo a passo: chamando código de VBA em um Visual C &#35; Projeto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
#### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Para expor o código em um projeto Visual c# para VBA  
  
1.  Abra ou crie um projeto de nível de documento com base em um documento do Word, a pasta de trabalho do Excel ou o modelo do Excel que oferece suporte a macros e que já contém o código do VBA.  
  
     Para obter mais informações sobre os formatos de arquivo de documento que oferecem suporte a macros, consulte [combinando VBA e personalizações no nível do documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Esse recurso não pode ser usado em projetos de modelo do Word.  
  
2.  Certifique-se de que o código do VBA no documento pode ser executado sem avisar o usuário para habilitar as macros. Você pode confiar em código do VBA para executar, adicionando o local do Office project à lista de locais confiáveis nas configurações de Central de confiabilidade do Word ou Excel.  
  
3.  Adicionar o membro que você deseja expor ao VBA para uma classe pública em seu projeto e declarar o novo membro como **público**.  
  
4.  Aplicar o seguinte <xref:System.Runtime.InteropServices.ComVisibleAttribute> e <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributos para a classe que você está expondo a VBA. Esses atributos tornar visível a classe COM, mas sem gerar uma interface de classe.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  Substituir o **GetAutomationObject** método de uma classe de item de host em seu projeto para retornar uma instância da classe que você está expondo a VBA:  
  
    -   Se você estiver expondo uma classe de item de host para VBA, substituir o **GetAutomationObject** método que pertence a essa classe e retorna a instância atual da classe.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   Se você estiver expondo uma classe que não é um item de host para VBA, substituir o **GetAutomationObject** item em seu projeto de método de qualquer host e retornar uma instância da classe de item de host não. Por exemplo, o código a seguir pressupõe que você está expondo uma classe denominada `DocumentUtilities` para VBA.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     Para obter mais informações sobre itens de host, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md).  
  
6.  Extrai uma interface de classe que você está expondo a VBA. No **extrair Interface** caixa de diálogo, selecione os membros públicos que você deseja incluir na declaração de interface. Para obter mais informações, consulte [extrair Interface refatoração &#40; C &#35; &#41; ](/visualstudio/csharp-ide/extract-interface-refactoring-csharp).  
  
7.  Adicionar o **pública** palavra-chave para a declaração de interface.  
  
8.  Tornar a interface visível para COM adicionando o seguinte <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo para a interface.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. Abra o documento (para o Word) ou a planilha (para Excel) no designer de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. No **propriedades** janela, selecione o **ReferenceAssemblyFromVbaProject** propriedade e altere o valor para **True**.  
  
    > [!NOTE]  
    >  Se a pasta de trabalho ou o documento ainda não contém código VBA ou se o código do VBA no documento não é confiável para ser executado, você receberá uma mensagem de erro ao definir o **ReferenceAssemblyFromVbaProject** propriedade **True**. Isso ocorre porque o Visual Studio não é possível modificar o projeto do VBA no documento nessa situação.  
  
11. Clique em **Okey** na mensagem que é exibida. Esta mensagem lembra você de que, se você adicionar o VBA código para a pasta de trabalho ou ao executar o projeto a partir de documentos [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], o código do VBA serão perdido na próxima vez que você compilar o projeto. Isso ocorre porque o documento na compilação de pasta é substituída sempre que você compilar o projeto de saída.  
  
     Neste ponto, o Visual Studio configura o projeto para que possa chamar o projeto do VBA no assembly. O Visual Studio também adiciona um método chamado `GetManagedClass` para o projeto do VBA. Você pode chamar esse método de qualquer lugar no projeto VBA para acessar a classe que é exposto ao VBA.  
  
12. Compile o projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combinando VBA e personalizações no nível do documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Passo a passo: Chamando código de VBA em um Visual C &#35; Projeto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Como expor o código para VBA em um projeto do Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  