---
title: 'Como: usar o Designer de esquema XML com literais XML | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cb0ba92afd8a3c8ab915d72237a5251643b32669
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464051"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Como: Use o designer de esquema XML com literais XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: usar o Designer de esquema XML com literais XML](https://docs.microsoft.com/visualstudio/xml-tools/how-to-use-the-xml-schema-designer-with-xml-literals).  
  
  
Este tópico descreve como exibir um esquema associado com um literal XML em um projeto Visual Basic.  
  
### <a name="to-create-a-new-visual-basic-console-application-project"></a>Para criar um novo projeto de aplicativo de console do Visual Basic  
  
1.  Inicie o Visual Studio 2010.  
  
2.  Dos **arquivo** menu, selecione **New**e, em seguida, selecione **projeto**. A caixa de diálogo **Novo Projeto** é exibida. Para **tipos de projeto**, selecione **outras linguagens,** e, em seguida, selecione **Visual Basic**. Para **modelos**, selecione o aplicativo de Console. Em seguida, digite `XMLLiterals` no **nome** campo e um local do projeto na **local** campo. Clique em **OK**.  
  
     O novo poject é criado. O projeto de XMLLiterals contém um arquivo de origem Visual Basic, Module1.vb.  
  
### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Para adicionar um arquivo XSD existente ao projeto  
  
1.  Abrir um novo arquivo de texto em Notepad.Copy o código de exemplo de esquema XML [esquema de ordem de compra](../xml-tools/sample-xsd-file-simple-schema.md) e cole-a para o arquivo.  
  
2.  Salve o arquivo em qualquer local com o nome PurchaseOrderSchema.xsd.  
  
3.  No Gerenciador de soluções, clique com botão direito o nome do projeto, selecione **Add**e, em seguida, selecione **Item existente...** . O **AddExisting Item** caixa de diálogo é exibida. Navegue até o arquivo de Purchaseorderschema, selecioná-lo e, em seguida, clique em **adicionar**.  
  
     O projeto de XMLLiterals agora contém dois arquivos: Module1.vb e PurchaseOrderSchema.xsd.  
  
### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Para adicionar código Visual Basic com uma literal XML, com base no arquivo XSD incluído no projeto  
  
1.  Substitua o código no arquivo Module1.vb com o seguinte código:  
  
    ```  
    Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">  
  
    Module Module1  
        Sub Main()  
  
            Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">  
                                 <ns:ShipTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:ShipTo>  
                                 <ns:BillTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:BillTo>  
                             </ns:PurchaseOrder>  
  
        End Sub  
    End Module  
    ```  
  
2.  Qualquer nó XML em um literal XML ou uma importação de namespace XML com o botão direito e selecione **Mostrar no Schema Explorer**.  
  
     XML Schema Explorer lado a lado é exibido com um arquivo Visual Basic que possui a literal XML assotiated com o esquema XML.



