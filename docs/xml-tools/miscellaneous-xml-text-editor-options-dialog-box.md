---
title: "Diversos, XML, Editor de texto, opções de caixa de diálogo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4773bf87e89bd504b477d9a1a31dfe961a3f29ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Caixa de diálogo Diversos, XML, Editor de Texto, Opções
Esta caixa de diálogo permite que você altere a automático e as configurações de esquema para o editor XML. Você pode acessar o **opções** na caixa de diálogo de **ferramentas** menu.  
  
> [!NOTE]
>  Essas configurações estão disponíveis quando você seleciona o **Editor de texto** pasta, o **XML** pasta e, em seguida, o **diversos** opção o **opções** caixa de diálogo.  
  
## <a name="auto-insert"></a>AutoInserção  
 **Fechar marcas**  
 Se a configuração de autocompletar é verificada, o editor adiciona automaticamente uma marca de fim quando você digita um sinal de maior (>) para fechar uma tag de início, se a marca não é fechada. Este é o comportamento padrão.  
  
 A conclusão de um elemento vazio não depende da configuração de autocompletar. Você sempre pode autocomplete um elemento vazio digitando uma barra invertida (/).  
  
 **Aspas de atributo**  
 Ao criar atributos XML, o editor insere o caracteres de `=" "` e posiciona o acento circunflexo (^) dentro de aspas duplas.  
  
 Selecionado por padrão.  
  
 **Declarações de namespace**  
 O editor inserir automaticamente declarações namespace onde quer que são necessárias.  
  
 Selecionado por padrão.  
  
 **Outra remarcação (comentários, CDATA)**  
 Comentários, CDATA, DOCTYPE, as instruções de processamento, e a outra marcação automática são concluídos.  
  
 Selecionado por padrão.  
  
## <a name="network"></a>Rede  
 **Baixar automaticamente DTDs e esquemas**  
 Os esquemas e as definições de tipo (DTDs) de documentos são baixados automaticamente locais HTTP. Este recurso usa System.Net com a detecção automática do servidor de proxy ativada.  
  
 Selecionado por padrão.  
  
## <a name="outlining"></a>Estrutura de tópicos  
 **Entrar no modo de estrutura de tópicos na abertura dos arquivos**  
 Ativa o recurso de estruturação quando um arquivo é aberto.  
  
 Selecionado por padrão.  
  
## <a name="caching"></a>Cache  
 **Esquemas**  
 Especifica o local do cache de esquema. O botão Procurar (**...** ) abre o **Directory procurar** caixa de diálogo no local de cache de esquema atual. Você pode selecionar um diretório diferente, ou você pode selecionar uma pasta na caixa de diálogo, clique com botão direito e escolha **abrir** para ver o que está no diretório.  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades de documento XML, janela de propriedades](../xml-tools/xml-document-properties-properties-window.md)   
 [Componentes do editor de XML](../xml-tools/xml-editor-components.md)