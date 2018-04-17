---
title: Combinando VBA e personalizações no nível do documento | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 01870498522ce138925fdaaf4c6ada9b13961f76
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="combining-vba-and-document-level-customizations"></a>Combinando VBA e personalizações no nível do documento
  Você pode usar o Visual Basic para o código do VBA em um documento que faz parte de uma personalização no nível do documento para o Microsoft Office Word ou o Microsoft Office Excel. Você pode chamar o código do VBA no documento do assembly de personalização, ou você pode configurar seu projeto para habilitar o código do VBA no documento para chamar o código no assembly de personalização.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Comportamento do código VBA em um personalização no nível do documento  
 Quando você abre o projeto no Visual Studio, o documento é aberto no modo de design. Código do VBA não é executado quando o documento está no modo de design, para que possa trabalhar no documento e código sem executar o código do VBA.  
  
 Quando você executa a solução, manipuladores de eventos em VBA e o assembly de personalização acompanhar eventos que são gerados no documento e executar ambos os conjuntos de códigos. Não é possível determinar com antecedência qual código será executado antes da outra; Você deve determinar isso por meio de testes em cada caso individual. Você pode obter resultados inesperados se os dois conjuntos de código são não cuidadosamente coordenados e testados.  
  
## <a name="calling-vba-code-from-the-customization-assembly"></a>Chamando código VBA do Assembly de personalização  
 Você pode chamar macros em documentos do Word e você pode chamar funções e macros em pastas de trabalho do Excel. Para fazer isso, use um dos seguintes métodos:  
  
-   Para o Word, chame o <xref:Microsoft.Office.Interop.Word._Application.Run%2A>método o <xref:Microsoft.Office.Interop.Word.Application> classe.  
  
-   Para o Excel, chame o <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> método o <xref:Microsoft.Office.Interop.Excel.Application> classe.  
  
 Para cada método, o primeiro parâmetro identifica o nome da macro ou função que você deseja chamar e os parâmetros opcionais restantes especificam os parâmetros para passar para a macro ou função. O primeiro parâmetro pode ter diferentes formatos para o Word e Excel:  
  
-   Para o Word, o primeiro parâmetro é uma cadeia de caracteres que pode ser qualquer combinação de modelo, o módulo e o nome de macro. Se você especificar o nome do documento, seu código só poderá executar macros em documentos relacionados ao contexto atual, não qualquer macro em qualquer documento.  
  
-   Para o Excel, o primeiro parâmetro pode ser uma cadeia de caracteres que especifica o nome da macro, uma <xref:Microsoft.Office.Interop.Excel.Range> que indica onde está a função ou um identificador de registro para uma função de DLL (XLL) registrada. Se você passar uma cadeia de caracteres, a cadeia de caracteres será avaliada no contexto da planilha ativa.  
  
 O exemplo de código a seguir mostra como chamar uma macro denominada `MyMacro` de um projeto de nível de documento para Excel. Este exemplo supõe que `MyMacro` é definido em `Sheet1`.  
  
```vb  
Globals.Sheet1.Application.Run("MyMacro")  
```  
  
```csharp  
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,  
    missing, missing, missing, missing, missing, missing, missing,  
    missing, missing, missing, missing, missing, missing, missing,  
    missing, missing, missing, missing, missing, missing, missing,   
    missing, missing, missing, missing, missing, missing);  
```  
  
> [!NOTE]  
>  Para obter informações sobre como usar global `missing` variável no lugar de parâmetros opcionais no Visual c#, consulte [escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="calling-code-in-document-level-customizations-from-vba"></a>Chamando código em personalizações de nível de documento do VBA  
 Você pode configurar um projeto no nível do documento para Word ou Excel, para que esse código Visual Basic for Applications (VBA) no documento pode chamar código no assembly de personalização. Isso é útil nos seguintes cenários:  
  
-   Você deseja estender o código do VBA existente em um documento usando os recursos em uma personalização no nível do documento que está associada com o mesmo documento.  
  
-   Você deseja tornar os serviços que você desenvolve uma personalização de nível de documento disponíveis para os usuários finais que podem acessar os serviços, escrevendo código VBA no documento.  
  
 As ferramentas de desenvolvimento do Office no Visual Studio fornecem um recurso semelhante para suplementos do VSTO. Se você estiver desenvolvendo um suplemento do VSTO, você pode chamar o código no seu suplemento do VSTO de outras soluções do Microsoft Office. Para obter mais informações, consulte [chamando código em suplementos do VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
> [!NOTE]  
>  Esse recurso não pode ser usado em projetos de modelo do Word. Ele pode ser usado apenas no documento do Word, Excel ou projetos de modelo do Excel.  
  
## <a name="requirements"></a>Requisitos  
 Antes de habilitar o código do VBA chamar o assembly de personalização, seu projeto deve atender aos seguintes requisitos:  
  
-   O documento deve ter uma das seguintes extensões de nome de arquivo:  
  
    -   Para o Word: Docm ou. doc  
  
    -   Para Excel:. Xlsm,. xltm,. xls ou. xlt  
  
-   O documento já deve conter um projeto do VBA que contém um código do VBA.  
  
-   Código do VBA no documento deve ter permissão para executar sem avisar o usuário para habilitar as macros. Você pode confiar em código do VBA para executar, adicionando o local do Office project à lista de locais confiáveis nas configurações de Central de confiabilidade do Word ou Excel.  
  
-   O projeto do Office deve conter pelo menos uma classe pública que contém um ou mais membros públicos que você está expondo a VBA.  
  
     Você pode expor métodos, propriedades e eventos para VBA. A classe que você expõe pode ser uma classe de item de host (como `ThisDocument` para Word, ou `ThisWorkbook` e `Sheet1` para Excel) ou outra classe que você define no seu projeto. Para obter mais informações sobre itens de host, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="enabling-vba-code-to-call-into-the-customization-assembly"></a>Habilitando o código do VBA chamar o Assembly de personalização  
 Há duas maneiras diferentes que você pode expor os membros em um assembly de personalização para o código do VBA no documento:  
  
-   Você pode expor os membros de uma classe de item de host em um [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projeto VBA. Para fazer isso, defina o **EnableVbaCallers** propriedade do item de host para **True** no **propriedades** janela ao item de host (ou seja, o documento, planilha ou pasta de trabalho) Abrir no designer. O Visual Studio automaticamente executa todo o trabalho necessário para habilitar o código do VBA chamar membros da classe.  
  
-   Você pode expor os membros em qualquer classe pública em um projeto Visual c# ou classe de item de membros em um host não-um [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projeto para o VBA. Essa opção oferece mais liberdade para escolher quais classes expor para VBA, mas também requer mais etapas manuais.  
  
     Para fazer isso, você deve executar as seguintes etapas principais:  
  
    1.  Expor a classe COM.  
  
    2.  Substituir o **GetAutomationObject** método de uma classe de item de host em seu projeto para retornar uma instância da classe que você está expondo a VBA.  
  
    3.  Definir o **ReferenceAssemblyFromVbaProject** propriedade de qualquer classe de item de host do projeto a **True**. Isso incorpora a biblioteca de tipos do assembly de personalização para o assembly e adiciona uma referência à biblioteca de tipos para o projeto do VBA no documento.  
  
 Para obter instruções detalhadas, consulte [como: expor código para VBA em um projeto do Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) e [como: expor código para VBA em um Visual C&#35; projeto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 O **EnableVbaCallers** e **ReferenceAssemblyFromVbaProject** propriedades estão disponíveis apenas no **propriedades** janela no tempo de design; eles não podem ser usados em tempo de execução . Para exibir as propriedades, abra o designer de um item de host em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obter mais informações sobre as tarefas específicas que executa o Visual Studio quando você definir essas propriedades, consulte [tarefas executadas pelas propriedades do Item de Host](#PropertyTasks).  
  
> [!NOTE]  
>  Se a pasta de trabalho ou o documento ainda não contém código VBA ou se o código do VBA no documento não é confiável para ser executado, você receberá uma mensagem de erro ao definir o **EnableVbaCallers** ou **ReferenceAssemblyFromVbaProject**  propriedade **True**. Isso ocorre porque o Visual Studio não é possível modificar o projeto do VBA no documento nessa situação.  
  
## <a name="using-members-in-vba-code-to-call-into-the-customization-assembly"></a>Usando membros no código do VBA para chamar o Assembly de personalização  
 Depois de configurar seu projeto para habilitar o código do VBA chamar o assembly de personalização, o Visual Studio adiciona os seguintes membros para o projeto do VBA no documento:  
  
-   Para todos os projetos, o Visual Studio adiciona um método global chamado `GetManagedClass`.  
  
-   Para [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] classe do item de projetos em que você expõe membros de um host usando o **EnableVbaCallers** propriedade, o Visual Studio também adiciona uma propriedade chamada `CallVSTOAssembly` para o `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, ou `Sheet3` módulo no projeto VBA.  
  
 Você pode usar o `CallVSTOAssembly` propriedade ou `GetManagedClass` método para acessar os membros públicos da classe exposta ao código do VBA no projeto.  
  
> [!NOTE]  
>  Embora você desenvolver e implanta sua solução, há várias cópias diferentes do documento onde você pode adicionar o código do VBA. Para obter mais informações, consulte [diretrizes para adicionar o código do VBA para o documento](#Guidelines).  
  
### <a name="using-the-callvstoassembly-property-in-a-visual-basic-project"></a>Usando a propriedade CallVSTOAssembly em um projeto do Visual Basic  
 Use o `CallVSTOAssembly` propriedade para acessar os membros públicos que você adicionou à classe de item de host. Por exemplo, a macro VBA a seguir chama um método chamado `MyVSTOMethod` que é definido no `Sheet1` classe em um projeto de pasta de trabalho do Excel.  
  
```  
Sub MyMacro()  
    Sheet1.CallVSTOAssembly.MyVSTOMethod()  
End Sub  
```  
  
 Esta propriedade é uma maneira mais conveniente para chamar o assembly de personalização que usar o `GetManagedClass` método diretamente. `CallVSTOAssembly` Retorna um objeto que representa o host de classe de item que é exposta para VBA. Os membros e os parâmetros de método do objeto retornado exibidas no IntelliSense.  
  
 O `CallVSTOAssembly` propriedade tem uma declaração que é semelhante ao seguinte código. Esse código supõe que você tenha expostos a `Sheet1` classe de item em um projeto de pasta de trabalho do Excel chamado de host `ExcelWorkbook1` para VBA.  
  
```  
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1  
    Set CallVSTOAssembly = GetManagedClass(Me)  
End Property  
```  
  
### <a name="using-the-getmanagedclass-method"></a>Usando o método GetManagedClass  
 Para usar global `GetManagedClass` método, passe o objeto VBA que corresponde à classe de item de host que contém sua substituição do **GetAutomationObject** método. Em seguida, use o objeto retornado para acessar a classe que é exposto ao VBA.  
  
 Por exemplo, a macro VBA a seguir chama um método chamado `MyVSTOMethod` que é definido no `Sheet1` classe de item em um projeto de pasta de trabalho do Excel chamado de host `ExcelWorkbook1`.  
  
```  
Sub CallVSTOMethod  
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1  
    Set VSTOSheet1 = GetManagedClass(Sheet1)  
    VSTOSheet1.MyVSTOMethod  
End Sub  
```  
  
 O `GetManagedClass` método tem a seguinte declaração.  
  
```  
GetManagedClass(pdispInteropObject Object) As Object  
```  
  
 Esse método retorna um objeto que representa a classe que é exposto para VBA. Os membros e os parâmetros de método do objeto retornado exibidas no IntelliSense.  
  
##  <a name="Guidelines"></a> Diretrizes para adicionar o código do VBA no documento  
 Há várias cópias diferentes do documento em que você pode adicionar código VBA que chamam a personalização no nível do documento.  
  
 Ao desenvolver e testar sua solução, você pode escrever o código do VBA no documento que é aberta ao depurar ou executar o projeto no Visual Studio (ou seja, o documento na pasta de saída de compilação). No entanto, qualquer código do VBA que você adicionar a este documento será substituído na próxima vez que você compilar o projeto, como Visual Studio substitui o documento na pasta de saída de compilação com uma cópia do documento da pasta de projeto principal.  
  
 Se você deseja salvar o código do VBA que você adicionar ao documento durante a depuração ou executando a solução, copie o código do VBA para o documento na pasta do projeto. Para obter mais informações sobre o processo de compilação, consulte [criando soluções do Office](../vsto/building-office-solutions.md).  
  
 Quando você estiver pronto para implantar sua solução, há três locais de documento principal no qual você pode adicionar o código do VBA.  
  
### <a name="in-the-project-folder-on-the-development-computer"></a>Na pasta do projeto no computador de desenvolvimento  
 Esse local é conveniente se você tem controle total sobre o código do VBA no documento e o código de personalização. Porque o documento está no computador de desenvolvimento, você pode modificar facilmente o código do VBA, se você alterar o código de personalização. Código do VBA que você adicionar a esta cópia do documento permanecerá no documento, quando você criar, depura e publica sua solução.  
  
 Você não pode adicionar o código do VBA no documento enquanto ele está aberto no designer. Você deve fechar o documento no designer e, em seguida, abra o documento diretamente do Word ou Excel.  
  
> [!CAUTION]  
>  Se você adicionar o código do VBA que é executado quando o documento for aberto, em casos raros, esse código pode corromper o documento ou impedir que ele seja aberto no designer de.  
  
### <a name="in-the-publish-or-installation-folder"></a>Na pasta de instalação ou publicar  
 Em alguns casos, ele poderá ser adequado adicionar o código do VBA para o documento na pasta de instalação ou de publicação. Por exemplo, você pode escolher essa opção se o código do VBA é gravado e testado por um desenvolvedor diferente em um computador que não tenha instalado o Visual Studio.  
  
 Se os usuários instalarem a solução diretamente da pasta de publicação, você deve adicionar o código do VBA no documento toda vez que você publicar a solução. Quando você publicar a solução, o Visual Studio substitui o documento no local de publicação.  
  
 Se os usuários instalarem a solução de uma pasta de instalação diferente da pasta de publicação, você pode evitar adicionando o código do VBA no documento toda vez que você publicar a solução. Quando uma atualização de publicação está pronta para ser movido da pasta de publicação para a pasta de instalação, copie todos os arquivos para a pasta de instalação, exceto o documento.  
  
### <a name="on-the-end-user-computer"></a>No computador do usuário final  
 Se os usuários finais são os desenvolvedores VBA que chamem serviços que fornecem a personalização de nível de documento, você pode informar como chamar o seu código usando o `CallVSTOAssembly` propriedade ou o `GetManagedClass` método em suas cópias do documento. Quando você publicar atualizações para a solução, o código do VBA no documento no computador do usuário final não será substituído, porque o documento não é modificado pelo publicar atualizações.  
  
##  <a name="PropertyTasks"></a> Tarefas executadas pelas propriedades do Item de Host  
 Quando você usa o **EnableVbaCallers** e **ReferenceAssemblyFromVbaProject** propriedades, o Visual Studio executará conjuntos diferentes de tarefas.  
  
### <a name="enablevbacallers"></a>EnableVbaCallers  
 Quando você define o **EnableVbaCallers** propriedade de um item de host para **True** em um projeto do Visual Basic, Visual Studio executará as seguintes tarefas:  
  
1.  Ele adiciona o <xref:Microsoft.VisualBasic.ComClassAttribute> e <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributos para a classe de item de host.  
  
2.  Ela substitui o **GetAutomationObject** método da classe de item de host.  
  
3.  Ele define o **ReferenceAssemblyFromVbaProject** propriedade do item de host para **True**.  
  
 Quando você define o **EnableVbaCallers** propriedade **False**, Visual Studio executará as seguintes tarefas:  
  
1.  Remove o <xref:Microsoft.VisualBasic.ComClassAttribute> e <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributos do `ThisDocument` classe.  
  
2.  Remove o **GetAutomationObject** método da classe de item de host.  
  
    > [!NOTE]  
    >  O Visual Studio não define automaticamente o **ReferenceAssemblyFromVbaProject** propriedade **False**. Você pode definir essa propriedade **False** manualmente usando o **propriedades** janela.  
  
### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject  
 Quando o **ReferenceAssemblyFromVbaProject** propriedade de qualquer item de host em um projeto do Visual Basic ou Visual c# é definida como **True**, Visual Studio executará as seguintes tarefas:  
  
1.  Ele gera uma biblioteca de tipos para o assembly de personalização e incorpora a biblioteca de tipos no assembly.  
  
2.  Ele adiciona uma referência para as seguintes bibliotecas de tipo no projeto VBA do documento:  
  
    -   A biblioteca de tipos para o assembly de personalização.  
  
    -   O Microsoft Visual Studio Tools para Office biblioteca de tipos de 9.0 do mecanismo de execução. Essa biblioteca de tipo está incluída no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 Quando o **ReferenceAssemblyFromVbaProject** propriedade é definida como **False**, Visual Studio executará as seguintes tarefas:  
  
1.  Remove as referências da biblioteca de tipo do projeto VBA no documento.  
  
2.  Remove a biblioteca de tipos incorporada do assembly.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 A tabela a seguir lista alguns erros e sugestões para corrigir os erros comuns.  
  
|Erro|Sugestão|  
|-----------|----------------|  
|Depois de definir o **EnableVbaCallers** ou **ReferenceAssemblyFromVbaProject** propriedade, uma mensagem de erro indica que o documento não contém um projeto do VBA, ou você não tem permissão para acessar o Projeto do VBA no documento.|Certifique-se de que o documento no projeto contém pelo menos uma macro VBA, o projeto do VBA possui confiança suficiente para ser executado e o projeto do VBA não está protegido por uma senha.|  
|Depois de definir o **EnableVbaCallers** ou **ReferenceAssemblyFromVbaProject** propriedade, uma mensagem de erro indica que o <xref:System.Runtime.InteropServices.GuidAttribute> declaração está ausente ou corrompido.|Certifique-se de que o <xref:System.Runtime.InteropServices.GuidAttribute> declaração está localizada no arquivo AssemblyInfo.cs ou AssemblyInfo em seu projeto e que esse atributo é definido como um GUID válido.|  
|Depois de definir o **EnableVbaCallers** ou **ReferenceAssemblyFromVbaProject** propriedade, uma mensagem de erro informando que o número de versão especificado pelo <xref:System.Reflection.AssemblyVersionAttribute> não é válido.|Certifique-se de que o <xref:System.Reflection.AssemblyVersionAttribute> declaração no arquivo AssemblyInfo.cs ou AssemblyInfo em seu projeto está definida como um número de versão de assembly válido. Para obter informações sobre números de versão de assembly válido, consulte o <xref:System.Reflection.AssemblyVersionAttribute> classe.|  
|Depois de renomear o assembly de personalização, código do VBA que chamam o assembly de personalização para de funcionar.|Se você alterar o nome do assembly de personalização depois expô-lo ao código do VBA, o vínculo entre o projeto do VBA no documento e o assembly de personalização será interrompido. Para corrigir esse problema, altere o **ReferenceFromVbaAssembly** propriedade em seu projeto para **False** e, em seguida, de volta para **True**e, em seguida, substitua todas as referências a assembly anterior nome no código do VBA com o novo nome de assembly.|  
  
## <a name="see-also"></a>Consulte também  
 [Como: expor código para VBA em um projeto do Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Como: expor código para VBA em um Visual C&#35; projeto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Passo a passo: Chamando código do VBA em um projeto do Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Passo a passo: Chamando código do VBA em um Visual C&#35; projeto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)   
 [VBA e soluções do Office no Visual Studio comparadas](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)   
 [Programando personalizações no nível do documento](../vsto/programming-document-level-customizations.md)  
  
  