---
title: Classes específicas de cultura para Windows Forms e Web Forms globais
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8289b44359508d788b43fa155c6f91b58d304138
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916993"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Classes específicas de cultura para Windows Forms e Web Forms globais

Cada cultura tem diferentes convenções para exibir datas, hora, números, moeda e outras informações. O namespace <xref:System.Globalization> contém classes que podem ser usadas para modificar o modo como os valores específicos de cultura são exibidos, como:
- <xref:System.Globalization.DateTimeFormatInfo>
- **Calendar**
- <xref:System.Globalization.NumberFormatInfo>

## <a name="using-the-culture-setting"></a>Usando a configuração de cultura

Use a configuração de cultura armazenada no aplicativo ou no painel de controle **Opções Regionais** para determinar as convenções de cultura no tempo de execução e formatar as informações adequadamente. Para saber mais sobre como configurar a cultura, consulte [Como definir a cultura e a cultura da interface do usuário para globalização de página da Web do ASP.NET](http://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0). As classes que formatam informações automaticamente de acordo com a configuração de cultura são chamadas classes *específicas de cultura*. Alguns métodos específicos de cultura são
- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>

Algumas funções específicas de cultura (na linguagem do Visual Basic) são `MonthName` e `WeekDayName`.

Por exemplo, o código a seguir mostra como você pode usar o método <xref:System.IFormattable.ToString%2A> para formatar a moeda para a cultura atual:

```vb
' Put the Imports statements at the beginning of the code module
Imports System.Threading
Imports System.Globalization
' Display a number with the culture-specific currency formatting
Dim MyInt As Integer = 100
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))
```

```csharp
// Put the using statements at the beginning of the code module
using System.Threading;
using System.Globalization;
// Display a number with the culture-specific currency formatting
int myInt = 100;
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));
```

Se a cultura for definida como "fr-FR", você verá o seguinte na janela de saída:

`100,00`

Se a cultura for definida como "en-US", você verá o seguinte na janela de saída:

`$100.00`

## <a name="see-also"></a>Consulte também

- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Globalization.DateTimeFormatInfo>
- <xref:System.Globalization.NumberFormatInfo>
- <xref:System.Globalization.Calendar>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>
- [Globalizando e localizando aplicativos](../ide/globalizing-and-localizing-applications.md)