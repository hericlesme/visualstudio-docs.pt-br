---
title: Propriedades de documento XML, a janela Propriedades | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d6529d936515c23c193a38861f1f13b71002566
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
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