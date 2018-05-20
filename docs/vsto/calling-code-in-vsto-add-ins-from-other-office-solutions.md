---
title: Chamar o código em suplementos do VSTO de outras soluções do Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 982fa23fa933bbade63222b78d677b88680601fc
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>Chamar o código em suplementos do VSTO de outras soluções do Office
  Você pode expor um objeto no seu suplemento do VSTO para outras soluções, incluindo outras soluções do Microsoft Office. Isso é útil se o suplemento do VSTO fornece um serviço que você deseja habilitar outras soluções para usar. Por exemplo, se você tiver um suplemento do VSTO para o Microsoft Office Excel que executa cálculos nos dados financeiros de um serviço Web, outras soluções podem executar esses cálculos chamando o suplemento do Excel VSTO em tempo de execução.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Há duas etapas principais neste processo:  
  
-   O VSTO Add-in, expor um objeto para outras soluções.  
  
-   Em outra solução, acesse o objeto exposto pelo suplemento do VSTO e os membros do objeto de chamada.  
  
## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Tipos de soluções que podem chamar o código em um suplemento  
 Você pode expor um objeto em um suplemento do VSTO para os seguintes tipos de soluções:  
  
-   Código Visual Basic for Applications (VBA) em um documento que é carregado no processo do aplicativo como o suplemento do VSTO.  
  
-   Personalizações no nível do documento que são carregadas no mesmo processo de aplicativo como o suplemento do VSTO.  
  
-   Outros suplementos do VSTO criados usando os modelos de projeto do Office no Visual Studio.  
  
-   Suplementos do VSTO COM (ou seja, suplementos do VSTO que implementam o <xref:Extensibility.IDTExtensibility2> diretamente da interface).  
  
-   Qualquer solução que está em execução em um processo diferente que seu suplemento do VSTO (esses tipos de soluções também são chamados de *clientes fora do processo*). Isso inclui aplicativos que automatizam um aplicativo do Office, como um aplicativo Windows Forms ou console e suplementos do VSTO que são carregados em um processo diferente.  
  
## <a name="expose-objects-to-other-solutions"></a>Expõe objetos de outras soluções  
 Para expor um objeto no seu suplemento do VSTO para outras soluções, execute as etapas a seguir no seu suplemento do VSTO:  
  
1.  Defina uma classe que você deseja expor para outras soluções.  
  
2.  Substituir o <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> método o `ThisAddIn` classe. Retorne uma instância da classe que você deseja expor para outras soluções.  
  
### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Definir a classe que você deseja expor para outras soluções  
 No mínimo, a classe que você deseja expor deve ser pública, ele deve ter o <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo definido como **true**, e ele deve expor o [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) interface.  
  
 A maneira recomendada para expor o [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) interface é executar as seguintes etapas:  
  
1.  Defina uma interface que declara os membros que você deseja expor para outras soluções. Você pode definir essa interface em seu projeto de suplemento do VSTO. No entanto, você talvez queira definir essa interface em um projeto de biblioteca de classe separada, se você quiser expor a classe para soluções VBA não, para que as soluções que chamam o suplemento do VSTO podem fazer referência a interface sem fazer referência a seu projeto de suplemento do VSTO.  
  
2.  Aplicar o <xref:System.Runtime.InteropServices.ComVisibleAttribute> de atributo a esta interface e defina este atributo como **true**.  
  
3.  Modificar sua classe para implementar esta interface.  
  
4.  Aplicar o <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> a sua classe de atributo e definir esse atributo para o **nenhum** valor o <xref:System.Runtime.InteropServices.ClassInterfaceType> enumeração.  
  
5.  Se você quiser expor essa classe para clientes fora do processo, também convém fazer o seguinte:  
  
    -   Derive a classe de <xref:System.Runtime.InteropServices.StandardOleMarshalObject>. Para obter mais informações, consulte [expor classes para clientes fora do processo](#outofproc).  
  
    -   Definir o **registrar para interoperabilidade COM** propriedade no projeto em que você define a interface. Esta propriedade é necessária somente se você quiser permitir que os clientes usam associação inicial para chamar o suplemento do VSTO.  
  
 O exemplo de código a seguir demonstra um `AddInUtilities` classe com um `ImportData` método que pode ser chamado por outras soluções. Para ver esse código no contexto de um maior passo a passo, consulte [passo a passo: chamar o código em um suplemento do VSTO por meio do VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
 [!code-csharp[Trin_AddInInteropWalkthrough #3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
 [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
### <a name="expose-classes-to-vba"></a>Expor classes para VBA  
 Quando você executar as etapas acima, código do VBA pode chamar apenas os métodos que você declarar na interface. Código do VBA não é possível chamar outros métodos na sua classe, incluindo métodos que sua classe obtém de classes base, como <xref:System.Object>.  
  
 Como alternativa, você pode expor o [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) interface definindo o <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> de atributo para o valor de AutoDispatch ou AutoDual o <xref:System.Runtime.InteropServices.ClassInterfaceType> enumeração. Se você expuser a interface, você não precisa declarar os métodos em uma interface separada. No entanto, o código VBA pode chamar métodos públicos e não-estático em sua classe, incluindo métodos obtidos de classes base, como <xref:System.Object>. Além disso, os clientes fora do processo que usam associação inicial não é possível chamar sua classe.  
  
###  <a name="outofproc"></a> Expor classes para clientes fora do processo  
 Se você quiser expor uma classe no seu suplemento do VSTO para clientes fora do processo, você deve derivar a classe de <xref:System.Runtime.InteropServices.StandardOleMarshalObject> para garantir que os clientes fora do processo podem chamar seu objeto exposto do suplemento do VSTO. Caso contrário, as tentativas para obter uma instância do objeto exposto em um cliente fora de processo podem falhar inesperadamente.  
  
 Essa falha ocorre porque todas as chamadas ao modelo de objeto de um aplicativo do Office devem ser feitas no thread da interface do usuário principal, mas chegarão chamadas de um cliente fora de processo para o objeto em um thread de (chamada de procedimento remoto) de RPC arbitrário. O mecanismo de empacotamento COM o .NET Framework não mudará threads e, em vez disso, ele tentará realizar marshaling da chamada para o objeto no thread RPC de entrada em vez do thread de interface do usuário principal. Se o objeto é uma instância de uma classe que deriva de <xref:System.Runtime.InteropServices.StandardOleMarshalObject>, chamadas de entrada para seu objeto são empacotadas automaticamente para o thread em que foi criado o objeto exposto, que será o thread de interface do usuário principal do aplicativo host.  
  
 Para obter mais informações sobre o uso de threads em soluções do Office, consulte [suporte a Threading no Office](../vsto/threading-support-in-office.md).  
  
### <a name="override-the-requestcomaddinautomationservice-method"></a>Substitua o método RequestComAddInAutomationService  
 O exemplo de código a seguir demonstra como substituir <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> no `ThisAddIn` classe no seu suplemento do VSTO. O exemplo supõe que você define uma classe denominada `AddInUtilities` que você deseja expor para outras soluções. Para ver esse código no contexto de um maior passo a passo, consulte [passo a passo: chamar o código em um suplemento do VSTO por meio do VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
 Quando o suplemento do VSTO é carregado, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chama o <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> método. O tempo de execução atribui o objeto retornado para o <xref:Microsoft.Office.Core.COMAddIn.Object%2A> propriedade de um <xref:Microsoft.Office.Core.COMAddIn> objeto que representa o suplemento do VSTO. Isso <xref:Microsoft.Office.Core.COMAddIn> o objeto está disponível para outras soluções do Office e as soluções que automatizam o Office.  
  
## <a name="access-objects-from-other-solutions"></a>Objetos de acesso de outras soluções  
 Para chamar o objeto exposto no seu suplemento do VSTO, execute as seguintes etapas da solução de cliente:  
  
1.  Obter o <xref:Microsoft.Office.Core.COMAddIn> objeto que representa o Add-in do VSTO exposto. Os clientes podem acessar todos os VSTO Add-ins disponíveis usando o `Application.COMAddIns` propriedade no modelo de objeto do host do aplicativo do Office.  
  
2.  Acesso a <xref:Microsoft.Office.Core.COMAddIn.Object%2A> propriedade o <xref:Microsoft.Office.Core.COMAddIn> objeto. Essa propriedade retorna o objeto exposto do suplemento do VSTO.  
  
3.  Chame os membros do objeto exposto.  
  
 A maneira como você usa o valor de retorno de <xref:Microsoft.Office.Core.COMAddIn.Object%2A> propriedade é diferente para os clientes do VBA e não VBA. Para clientes fora do processo, o código adicional é necessário para evitar uma condição de corrida possíveis.  
  
### <a name="access-objects-from-vba-solutions"></a>Objetos de acesso de soluções do VBA  
 O exemplo de código a seguir demonstra como usar o VBA para chamar um método que é exposto por um suplemento do VSTO. Esta macro VBA chama um método chamado `ImportData` que é definido em um Add-in do VSTO chamado **ExcelImportData**. Para ver esse código no contexto de um maior passo a passo, consulte [passo a passo: chamar o código em um suplemento do VSTO por meio do VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
```vb
Sub CallVSTOMethod()  
    Dim addIn As COMAddIn  
    Dim automationObject As Object  
    Set addIn = Application.COMAddIns("ExcelImportData")  
    Set automationObject = addIn.Object  
    automationObject.ImportData  
End Sub  
```  
  
### <a name="access-objects-from-non-vba-solutions"></a>Objetos de acesso de soluções não VBA  
 Em uma solução não VBA, você deve converter o <xref:Microsoft.Office.Core.COMAddIn.Object%2A> valor de propriedade para a interface ele implementa e, em seguida, você pode chamar os métodos expostos no objeto de interface. O exemplo de código a seguir demonstra como chamar o `ImportData` método de um diferente do VSTO suplemento que foi criado usando as ferramentas de desenvolvedor do Office no Visual Studio.  
  
```vb  
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")  
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _  
    addIn.Object, ExcelImportData.IAddInUtilities)  
utilities.ImportData()  
```  
  
```csharp  
object addInName = "ExcelImportData";  
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);  
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;  
utilities.ImportData();  
```  
  
 Neste exemplo, se você tentar converter o valor da <xref:Microsoft.Office.Core.COMAddIn.Object%2A> propriedade para o `AddInUtilities` classe em vez de `IAddInUtilities` interface, o código gerará uma <xref:System.InvalidCastException>.  
  
## <a name="see-also"></a>Consulte também  
 [Programa de suplementos do VSTO](../vsto/programming-vsto-add-ins.md)   
 [Passo a passo: Chamar o código em um suplemento do VSTO por meio do VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Desenvolver soluções do Office](../vsto/developing-office-solutions.md)   
 [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Personalizar os recursos de interface do usuário usando interfaces de extensibilidade](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  