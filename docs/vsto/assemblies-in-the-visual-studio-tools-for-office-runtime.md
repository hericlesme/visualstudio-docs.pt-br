---
title: Assemblies no Visual Studio Tools para Office runtime
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8ff32d472d0e2005b22acb8d751e03c6aa3f61ef
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Assemblies no Visual Studio Tools para Office runtime
  Quando você cria um projeto do Office, o Visual Studio adiciona automaticamente as referências para o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] assemblies que são usados para o tipo de projeto e o destino do .NET Framework do projeto. Há assemblies diferentes nas extensões do Office para o .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], e [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Para obter mais informações sobre as extensões do Office, consulte [Visual Studio Tools para visão geral de tempo de execução do Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Assemblies nas extensões do Office para o .NET Framework 4 e o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 A tabela a seguir lista os assemblies que são incluídos nas extensões do Office para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Para obter a documentação sobre os tipos nesses assemblies e namespaces, consulte [referência gerenciada &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Nome do assembly|Descrição|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Fornece os seguintes tipos:<br /><br /> -Tipos para a criação de marcas inteligentes e personalizações da faixa de opções. **Observação:** marcas inteligentes foram preteridas no [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Tipos para a criação de painéis de ações em personalizações no nível do documento e painéis de tarefas personalizados em suplementos do VSTO.|  
|Microsoft.Office.Tools.Excel.dll|Fornece interfaces que representam itens de host e controles de host para projetos do Excel e tipos de suporte. Para obter mais informações, consulte [automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Fornece tipos que você pode usar para criar regiões de formulário personalizadas nos suplementos do VSTO do Outlook.|  
|Microsoft.Office.Tools.Word.dll|Fornece interfaces que representam itens de host e controles de host para projetos do Word e tipos de suporte. Para obter mais informações, consulte [automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Fornece os seguintes tipos:<br /><br /> -Exceções que podem ser geradas pelo Visual Studio Tools para Office runtime.<br />-Regiões de formulário atributos que você pode usar ao criar o Outlook.|  
|Microsoft.Office.Tools.dll|Fornece tipos que fazem parte do Visual Studio Tools para a infraestrutura de tempo de execução do Office e não se destina a ser usado diretamente no seu código.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Fornece os seguintes tipos:<br /><br /> -A <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo e <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interface, que você pode usar para objetos de dados do cache em uma personalização no nível do documento. Para obter mais informações, consulte [dados armazenados em Cache](../vsto/caching-data.md).<br />-A <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interface, que você pode implementar para executar etapas adicionais de instalação como a etapa final do instalador do ClickOnce para uma solução do Office. Para obter mais informações, consulte [implantar uma solução do Office usando o ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-Exceções que podem ser geradas pelo Visual Studio Tools para Office runtime.<br />-Outros tipos que fazem parte do Visual Studio Tools para a infraestrutura de tempo de execução do Office e não se destina a ser usado diretamente no seu código.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Fornece os seguintes tipos:<br /><br /> -A <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe, que você pode usar para anexar os assemblies de personalização para documentos e acessar os dados armazenados em cache em documentos. Para obter mais informações, consulte [gerenciar documentos em um servidor usando a classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Várias classes que representam a hierarquia dos dados em uma personalização no nível do documento armazenados em cache. Para obter mais informações, consulte [acessar dados em documentos no servidor](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 Projetos que visam o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] também referenciar os seguintes assemblies. Esses assemblies não são parte do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] redistribuível. Em vez disso, eles são assemblies dependentes devem ser implantados com sua solução. Por padrão, eles são copiados para a pasta de saída de compilação para o seu projeto (o **Copy Local** propriedade para esses assemblies são definidos como **True**). Se você implantar seu projeto usando o ClickOnce, esses assemblies serão incluídos no pacote gerado.  
  
|Nome do assembly|Descrição|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Fornece as classes base para gerado `ThisAddIn` classe em projetos de suplemento do VSTO e a classe gerada da faixa de opções em todos os projetos.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Fornece os seguintes tipos:<br /><br /> -Base classes para gerado `ThisWorkbook` e `Sheet` classes no nível do documento projetos para o Excel.<br />-Controles de formulários do Windows que você pode usar em planilhas em projetos do Excel.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Fornece classes base para gerado `ThisAddIn` e classes de região de formulário em projetos do Outlook.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Fornece os seguintes tipos:<br /><br /> -Base classes para gerado `ThisDocument` classe em projetos de nível de documento para Word.<br />-Controles de formulários do Windows que você pode usar em documentos em projetos do Word.|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Assemblies nas extensões do Office para o .NET Framework 3.5  
 A tabela a seguir lista os assemblies que são incluídos nas extensões do Office para o .NET Framework 3.5. Para obter a documentação sobre os namespaces e classes nesses assemblies, consulte a seguinte seção de referência na documentação do Visual Studio 2008: [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Nome do assembly|Descrição|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Fornece os seguintes tipos:<br /><br /> -Microsoft.Office.Tools.AddIn classe base para suplementos do VSTO.<br />-Classes para a criação de marcas inteligentes e personalizações da faixa de opções. **Observação:** marcas inteligentes foram preteridas no [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Classes para a criação de painéis de ações em personalizações no nível do documento e painéis de tarefas personalizados em suplementos do VSTO.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Fornece os itens de host e controles de host para soluções do Excel. Para obter mais informações, consulte [automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Fornece classes que você pode usar para criar regiões de formulário personalizadas nos suplementos do VSTO do Outlook.|  
|Microsoft.Office.Tools.Word.v9.0.dll|Fornece os itens de host e controles de host para soluções do Word. Para obter mais informações, consulte [automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v9.0.dll|Fornece os seguintes tipos:<br /><br /> -A [RemoteBindableComponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) classe, que fornece os recursos de associação de dados para controles de host no nível do documento personalizações.<br />-Outros tipos que fazem parte do Visual Studio Tools para a infraestrutura de tempo de execução do Office e não se destina a ser usado diretamente no seu código.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Fornece os seguintes tipos:<br /><br /> -A <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo e <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interface, que você pode usar para objetos de dados do cache em uma personalização no nível do documento. Para obter mais informações, consulte [dados armazenados em Cache](../vsto/caching-data.md).<br />-Exceções que podem ser geradas pelo Visual Studio Tools para Office runtime.<br />-Outros tipos que fazem parte do Visual Studio Tools para a infraestrutura de tempo de execução do Office e não se destina a ser usado diretamente no seu código.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Fornece o <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interface, que você pode implementar para executar etapas adicionais de instalação como a etapa final do instalador do ClickOnce para uma solução do Office. Para obter mais informações, consulte [implantação de solução do Office avançado](http://msdn.microsoft.com/en-us/9147b6f6-849f-4cb1-b2c5-e22658d74b02).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Fornece os seguintes tipos:<br /><br /> -A <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe, que você pode usar para anexar programaticamente os assemblies de personalização a documentos e para acessar os dados armazenados em cache em documentos. Para obter mais informações, consulte [gerenciar documentos em um servidor usando a classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Várias classes que representam a hierarquia dos dados em uma personalização no nível do documento armazenados em cache. Para obter mais informações, consulte [acessar dados em documentos no servidor](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Fornece os seguintes tipos:<br /><br /> -As classes Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry e Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList, que você pode usar para criar entradas da lista para conceder confiança ao escritório de inclusão de usuário soluções que o .NET Framework 3.5 de destino.<br />-Outros tipos que fazem parte do Visual Studio Tools para a infraestrutura de tempo de execução do Office e não se destina a ser usado diretamente no seu código.|  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas do Visual Studio para visão geral de tempo de execução do Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Ferramentas do Visual Studio para cenários de instalação de tempo de execução do Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  