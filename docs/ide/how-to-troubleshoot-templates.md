---
title: Solucionar problemas de carregamento de modelo de projeto e de item do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d9242d053044fa66e6eb3d506382cf7cfb5d0295
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-troubleshoot-templates"></a>Como solucionar problemas de modelos

Se houver falha no carregamento de um modelo no ambiente de desenvolvimento, haverá várias maneiras de localizar o problema.

## <a name="validate-the-vstemplate-file"></a>Valide o arquivo .vstemplate

Se o arquivo .vstemplate em um modelo não estiver de acordo com o esquema de modelo do Visual Studio, o modelo poderá não aparecer na caixa de diálogo **Novo Projeto**.

### <a name="to-validate-the-vstemplate-file"></a>Para validar o arquivo .vstemplate

1. Localize o arquivo .zip que contém o modelo.

1. Extraia o arquivo .zip.

1. No menu **Arquivo** do Visual Studio, escolha **Abrir** > **Arquivo**.

1. Selecione o arquivo .vstemplate para o modelo e escolha **Abrir**.

1. Verifique se o XML do arquivo .vstemplate adota o esquema de modelo. Para obter mais informações sobre o esquema do .vstemplate, consulte [Referência de esquema de modelo](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Para obter suporte do IntelliSense enquanto cria o arquivo .vstemplate, adicione um atributo `xmlns` ao elemento `VSTemplate` e atribua um valor igual a http://schemas.microsoft.com/developer/vstemplate/2005.

1. Salve e feche o arquivo .vstemplate.

1. Selecione os arquivos incluídos no modelo, clique com o botão direito do mouse e escolha **Enviar para** > **Pasta compactada (zipada)**. Os arquivos selecionados são compactados em um arquivo .zip.

1. Insira o novo arquivo .zip no mesmo diretório do antigo arquivo .zip.

1. Exclua os arquivos de modelo extraídos e o arquivo .zip de modelo antigo.

## <a name="enable-diagnostic-logging"></a>Habilitar o registro em log de diagnóstico

Você pode habilitar o registro em log de diagnóstico para a descoberta de modelo, seguindo as etapas em [Solucionando problemas de descoberta do modelo (extensibilidade)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Consulte também

[Solucionando problemas de descoberta do modelo (extensibilidade)](../extensibility/troubleshooting-template-discovery.md)  
[Personalizando modelos](../ide/customizing-project-and-item-templates.md)  
[Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)  
[Referência de esquema de modelo](../extensibility/visual-studio-template-schema-reference.md)