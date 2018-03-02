---
title: "Configurando um computador para desenvolver soluções do Office | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 9b63b3b495b9cb15ea3e9eeedcecedb3a384f8a0
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="configuring-a-computer-to-develop-office-solutions"></a>Configurando um computador para desenvolver soluções do Office

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

[Guia de Introdução &#40; desenvolvimento do Office no Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Como configurar um computador para desenvolver soluções do Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Como instalar o tempo de execução redistribuível das Ferramentas do Visual Studio para o Office](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Como instalar assemblies de interoperabilidade primários do Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Funcionalidades disponibilizadas pelo aplicativo do Office e pelo tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md)
