---
title: Interface de comunicador do Excel de amostra
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 88aa282a2e742ffff53582fd4855d06e3a06db69
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="sample-excel-communicator-interface"></a>Interface de comunicador do Excel de amostra
A interface `IExcelUICommunication` de amostra é usada no objeto `ExcelUICommunicator` no projeto `ExcelAddIn`.

## <a name="iexceluicommunication-interface"></a>Interface IExcelUICommunication
 Essa interface define os pontos de comunicação entre o `CodedUIExtension`, que é executado no processo de teste de IU codificado e o `ExcelCodedUIAddIn`, que é executado no processo [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].

 O assembly `ExcelCodedUIAddinHelper` tem uma classe `ExcelUICommunicator` que deriva dessa interface e usa o modelo de objeto do Excel para processar os métodos.

 Alguns métodos obtém as informações solicitadas do Excel e, em seguida, criam e retornam uma das informações de objetos, como o objeto `CellInformation`.

 Outros métodos usam um objeto de informações fornecidas, localizam o controle correspondente no Excel e realizam um processo no controle. Por exemplo, o método `ScrollIntoView` rola a Planilha para que a célula designada fique visível.

## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>Comunicação CodedUIExtensibilitySample e ExcelCodedUIAddinHelper
 O assembly `ExcelCodedUIAddinHelper` é executado no processo do Excel e tem a classe `UICommunicator` que implementa a interface `IExcelUITestCommunication` e obtém ou define as informações necessárias diretamente da interface do usuário do Excel.

 O assembly `CodedUIExtensibilitySample` é executado no processo de teste de IU codificado do Visual Studio. Esse assembly tem a classe `Communicator` que abre um canal de comunicação remota do .NET e fornece uma propriedade `Instance` que usa a interface `IExcelUICommunication` para usar o objeto `UICommunicator` no assembly `ExcelCodedUIAddinHelper` para passar solicitações e objetos de informações, como um objeto `CellInformation` entre os dois assemblies.

## <a name="see-also"></a>Consulte também

- [Estendendo testes de IU codificados e gravações da ação para dar suporte ao Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
- [Suplemento de exemplo do Excel para testes de IU codificados](../test/sample-excel-add-in-for-coded-ui-testing.md)
- [Extensão de teste de IU codificado de exemplo para Excel](../test/sample-coded-ui-test-extension-for-excel.md)
