---
title: "Extensão de amostra do Excel: Classe PropertyProvider | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: "9"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 7617b7aafac6c7345a94d0e792bc312c7e212e56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Extensão de exemplo do Excel: classe PropertyProvider
Essa classe interna estende a classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> e fornece serviços de propriedade a elementos [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] para registrar e reproduzir testes de interface do usuário.  
  
## <a name="getcontrolsupportlevel-method"></a>Método GetControlSupportLevel  
 O método <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> retorna um número que indica o nível do suporte que o provedor da propriedade pode oferecer para o controle fornecido. Quanto maior o valor retornado, mais o provedor de propriedade pode dar suporte ao controle. Nesse caso, o método verifica o valor da propriedade <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> do controle fornecido. Se o valor for "Excel" e se o <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> indicar que é um `CellElement`, o método retornará o valor mais alto; caso contrário, retornará zero, o que indica que não há suporte.  
  
## <a name="getpropertynames-method"></a>Método GetPropertyNames  
 Retorna um dicionário de nomes e descritores de propriedades para as propriedades de um controle de célula do Excel com suporte.  
  
## <a name="getpropertydescriptor-method"></a>Método GetPropertyDescriptor  
 Este método é chamado pelo framework de teste para obter o descritor de propriedade predefinidos para o nome da propriedade fornecido.  
  
## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>Métodos GetPropertyValue e SetPropertyValue  
 O método `GetPropertyValue` utiliza a classe `Communicator` dessa extensão para retornar o valor da propriedade do Excel. O método `SetPropertyValue` usa a classe <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> e o componente `Communicator` para definir o valor da propriedade. Esses métodos são chamados pela estrutura de teste.  
  
## <a name="code-generation-customization-methods"></a>Métodos de personalização de geração de código  
 Esses métodos não são implementados para essa extensão. Portanto, elas retornam `null` ou geram a <xref:System.NotImplementedException>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [Estendendo testes de IU codificados e gravações da ação para dar suporte ao Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
