---
title: 'Extensão de exemplo do Excel: classe ExtensionPackage'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 43234161979df9190daddeec168e7a40a14db498
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Extensão de exemplo do Excel: classe ExtensionPackage
Essa classe estende a classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> e fornece o ponto de entrada para a extensão de teste de IU codificado que está testando uma Planilha do [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].

## <a name="assembly-attribute"></a>Atributos do Assembly
 O arquivo começa com um atributo de assembly que identifica o assembly como uma extensão de teste de interface do usuário.

```
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
    "ExcelExtensionPackage",
    typeof(
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]
```

 Esse atributo declara o nome de classe base, o nome da classe de pacote e o nome de classe totalmente qualificado da classe de pacote de extensão personalizada.

## <a name="simple-properties"></a>Propriedades Simples
 Essa classe tem propriedades que fornecem valores que são usados pela estrutura de teste da interface do usuário codificada para identificar e descrever a extensão e o assembly. Consulte os comentários do código para obter mais informações.

## <a name="getservice-method"></a>Método GetService
 O método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> é o único ponto de entrada usado pela estrutura de teste de IU codificado para obter acesso ao gerente de tecnologia, ao provedor de propriedade e ao filtro de ação, conforme identificado pela classe base de cada objeto.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Estendendo testes de IU codificados e gravações da ação para dar suporte ao Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
