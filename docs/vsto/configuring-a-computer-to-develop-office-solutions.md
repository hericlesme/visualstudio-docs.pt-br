---
title: Configurar um computador para desenvolver soluções do Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58458b51115834b5b94e858676ee8039d5894c70
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Configurar um computador para desenvolver soluções do Office

Para criar suplementos do VSTO e personalizações para o Microsoft Office, instale uma versão com suporte do Visual Studio, o .NET Framework e o Microsoft Office.

|Software|Versões com suporte|
|--------------|------------------------|
|Visual Studio 2017| Qualquer edição com o **desenvolvimento do Office para o SharePoint** carga de trabalho.|
|.NET Framework|-O .NET Framework 4 ou posterior.|
|Microsoft Office|<ul><li>Qualquer edição do pacote do Office, incluindo o Office Professional Plus para o Office 365.</li><li>Qualquer uma das aplicações autônomas seguintes:<br /><br /> <ul><li>Excel</li><li>InfoPath (Office 2013 e Office 2010 apenas)</li><li>Outlook</li><li>PowerPoint</li><li>Projeto</li><li>Visio</li><li>Palavra</li></ul></li></ul><br /> O Visual Basic for Applications (VBA) deve ser instalado como parte do Office. **Importante:** clique para executar versões de aplicativos do Office 2010 não têm suporte.|

Para obter etapas detalhadas de instalação, consulte [como: configurar um computador para desenvolver soluções do Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Se os modelos de projeto não são exibidos ou não funcionam no Visual Studio

Se você instalar uma versão com suporte do Visual Studio, o .NET Framework e o Microsoft Office, mas os modelos de projeto do Office não aparecem no Visual Studio **novo projeto** caixa de diálogo, ou você recebe um erro ao tentar usar um, Verifique o seguinte:

- Certifique-se de que o Microsoft Office Developer Tools esteja instalado no computador.

     O Office Developer Tools é um componente opcional do Visual Studio, mas geralmente é instalado automaticamente junto com o Visual Studio. Se você personalizar a instalação do Visual Studio especificando quais recursos a serem instalados, certifique-se de que você escolha **Microsoft Office Developer Tools** durante a instalação para instalar as ferramentas.

     Para certificar-se de que essas ferramentas são instaladas, inicie o programa de instalação do Visual Studio e escolha o **modificar** botão. Selecione o **Microsoft Office Developer Tools** caixa de seleção e, em seguida, escolha o **atualização** botão.

- Certifique-se de que você não estiver executando uma versão do Office que foi entregue por clique para executar. Consulte [como: verificar se o Outlook é um aplicativo clique para executar em um computador](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).

- Certifique-se de que você está executando apenas uma versão do Microsoft Office.

Se você continuar tendo problemas, consulte [suporte adicional para erros em soluções do Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Consulte também

[Introdução &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Como: configurar um computador para desenvolver soluções do Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Como: instalar o Visual Studio Tools for Office runtime redistribuível](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Como: assemblies de interoperabilidade primários do Office de instalação](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Recursos disponíveis por tipo de projeto e de aplicativo do Office](../vsto/features-available-by-office-application-and-project-type.md)
