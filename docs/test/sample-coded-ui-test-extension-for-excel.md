---
title: Extensão de teste de IU codificado de amostra para Excel
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2c76ba569a6f9f34d28d6aaaa268a366c1be7b31
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Extensão de teste de IU codificado de amostra para Excel
O componente de extensão da amostra é executado no processo de teste de IU codificado do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e é ligeiramente hierárquico com a classe `ExtensionPackage` na base. As classes `TechnologyManager`, `ActionFilter` e `PropertyProvider` estão no próximo nível, com os elementos de controle no nível superior.

 ![Arquitetura de extensão de teste do Excel](../test/media/excel_extarch.png "Excel_ExtArch") Arquitetura de extensão do Excel

## <a name="extension-points"></a>Pontos de extensão
 Essas classes representam os pontos de extensão implementados na amostra para habilitar o teste para de IU codificado para [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].

### <a name="extensionpackage"></a>ExtensionPackage
 Herdado da classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>, este é o ponto de entrada para o extensão de teste de IU codificado. A implementação dessa classe abstrata fornece o acesso interno ao framework de teste de IU codificado para seu gerente de tecnologia de teste de IU personalizado, provedor de propriedade de teste de IU e o filtro de ação de teste de IU para testar a nova IU. Para obter mais informações, consulte [Classe ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md).

### <a name="technologymanager"></a>TechnologyManager
 Herdada da classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>, essa classe fornece um gerente de tecnologia para gravação e reprodução de teste. Para obter mais informações, consulte [Classe TechnologyManager](../test/sample-excel-extension-technologymanager-class.md).

### <a name="actionfilter"></a>ActionFilter
 Herdada da classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, essa classe fornece uma classe base para agregar resultados de ações de teste semelhantes em um único resultado do teste. Para obter mais informações, consulte [Classe ActionFilter](../test/sample-excel-extension-actionfilter-class.md).

### <a name="technology-elements"></a>Elementos de tecnologia
 Uma classe base herdada da classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> fornece a base para os elementos de tecnologia em seus testes de interface do usuário que podem ser registrados e reproduzidos. Para obter mais informações, consulte [Classes de Elemento](../test/sample-excel-extension-element-classes.md).

### <a name="propertyprovider"></a>PropertyProvider
 Herdada da classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>, essa classe fornece uma classe base para dar suporte às propriedades dos elementos de interface do usuário para gravação e reprodução de teste. Para obter mais informações, consulte [Classe PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md).

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Classe ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md)
- [Classe TechnologyManager](../test/sample-excel-extension-technologymanager-class.md)
- [Classe ActionFilter](../test/sample-excel-extension-actionfilter-class.md)
- [Classes Element](../test/sample-excel-extension-element-classes.md)
- [Classe PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md)
