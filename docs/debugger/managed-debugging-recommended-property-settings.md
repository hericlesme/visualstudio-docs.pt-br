---
title: 'A depuração gerenciada: Configurações de propriedade recomendadas | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e1c4b725871012f1fbf2c80f3e978f133d4db5b0
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476436"
---
# <a name="managed-debugging-recommended-property-settings"></a>Depuração gerenciada: configurações de propriedade recomendadas
Certas propriedades devem ser definidas da mesma maneira para todos os cenários gerenciados de depuração.  
  
 As tabelas a seguir exibem as configurações de propriedade recomendadas.  
  
 As configurações não listadas aqui podem variar entre os diferentes tipos de projeto gerenciados. Por exemplo, **iniciar ação** será diferente definido em um projeto do Windows Forms que em um [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projeto.  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>As propriedades de configuração na compilação (C#) ou na guia Compilar (Visual Basic)  
  
|**Nome da propriedade**|**Configuração**|  
|-----------------------|-----------------|  
|**Definir a constante DEBUG**|C# e F#: defina a caixa de seleção como verificado. Isso permite que o aplicativo use uma classe de Depuração.|  
|**Definir a constante TRACE**|C# e F#: defina a caixa de seleção como verificado. Isso permite que o aplicativo use uma classe de rastreamento.|  
|**Otimizar código**|F#, C# e Visual Basic: definidos como falso. O código otimizado é mais difícil de depurar porque as instruções geradas não correspondem diretamente ao código-fonte. Se você achar que seu programa tem um erro que aparece somente no código otimizado, você pode ativar essa configuração, mas lembre-se de que o código mostrado no **desmontagem** janela é gerada de fonte otimizada que pode não corresponder o que você vê no código Editor. Para depurar um código otimizado, você deve desativar o Apenas Meu Código. (Consulte [restringir passo a passo para apenas meu código](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Para obter mais informações, consulte [configurações do projeto para configurações de depuração do c#](../debugger/project-settings-for-csharp-debug-configurations.md) ou [configurações de projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Caminho de saída**|Definido como bin\Debug\\.|  
|**Opções avançadas de compilação**|Somente Visual Basic. Clique em **avançado** para definir as propriedades avançadas que são descritas na tabela a seguir.|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>Caixa de diálogo de Configurações Avançadas do Compilador  
  
|**Nome da propriedade**|**Configuração**|  
|-----------------------|-----------------|  
|**Habilitar otimizações**|Definido como false para os motivos especificados no **otimizar código** opção na tabela anterior.|  
|**Gerar informações de depuração**|Marque esta caixa de seleção para que o sinalizador /DEBUG seja definido ao compilar, o que vai gerar as informações necessárias para facilitar a depuração.|  
|**Definir a constante DEBUG**|Marque esta caixa de seleção para definir a constante de `DEBUG`, que permite que seu aplicativo use a classe <xref:System.Diagnostics.Debug>.|  
|**Definir a constante TRACE**|Marque esta caixa de seleção para definir a constante de `TRACE`, que permite que seu aplicativo use a classe <xref:System.Diagnostics.Trace>.|  
  
## <a name="see-also"></a>Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Tipos de projeto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)