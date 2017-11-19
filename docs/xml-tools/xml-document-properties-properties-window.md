---
title: Propriedades de documento XML, a janela Propriedades | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24f3760fb328331684e6894954d79675ff27494e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="xml-document-properties-properties-window"></a>Propriedades de documento XML, a janela de propriedades
O **propriedades** janela fornece informações básicas sobre o documento ativo no Editor de XML. As propriedades que estão disponíveis varia dependendo do tipo de documento XML que está atualmente ativa.  
  
> [!NOTE]
>  Todas as propriedades de documento XML são salvas na solução. Como resultado, você não tem que digitar novamente esses valores na próxima vez que você abrir a solução.  
  
 **Codificação**  
 A codificação de caractere para o arquivo. Alterar essa propriedade também altera o atributo de codificação na declaração XML, e vice-versa. A nova codificação será usada para codificar o arquivo quando você salvar o arquivo.  
  
 **Entrada**  
 O documento de entrada associado com a folha de estilos XSLT. Ele é usado pelo **ShowXSLT saída** comando. Um documento pode ser selecionado usando o botão Procurar (**...** ) botão.  
  
 Esta propriedade é visível somente quando um arquivo fonte é atualmente ativa na janela editor.  
  
 **Saída**  
 O arquivo que é gerado para transformar um documento XML.  
  
 Se um arquivo é não especificado, um nome de arquivo padrão é gerado com base no atributo de `method` no elemento de `xsl:output` que determina a extensão de arquivo. O arquivo padrão é localizado no diretório temporário do usuário atual.  
  
 **Esquemas**  
 Os esquemas a ser usado para validação. O botão abre a **esquemas XSD** caixa de diálogo que pode ser usada para selecionar os esquemas para usar.  
  
 Você também pode ir para o caminho para esquemas. Se vários esquemas são especificados, cada caminho de esquema deve ser colocado entre aspas duplas.  
  
 **Folha de estilos**  
 O arquivo XSLT que é usado para transformar o documento quando o **Mostrar saída de XSLT** comando é usado. Se esse campo estiver em branco quando o **Mostrar saída de XSLT** comando é usado, o editor usa o valor fornecido a `xml-stylesheet` instrução do documento, ou de processamento solicitará o nome do arquivo.  
  
 Ao editar um arquivo XSLT, essa propriedade pode ser usada para especificar que uma folha de estilo diferente deve ser usado quando o **Mostrar saída de XSLT** ou **depuração XSLT** comando é selecionado. Por exemplo, você pode querer fazer isso quando você estiver editando uma folha de estilos incluída em uma folha de estilos pai.  
  
## <a name="see-also"></a>Consulte também  
 [Editor de XML](../xml-tools/xml-editor.md)   
 [Componentes do editor de XML](../xml-tools/xml-editor-components.md)