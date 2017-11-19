---
title: 'Passo a passo: Usando recursos do Editor de XML | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bf90df0e5311cb1487334ba3851c5083030e2191
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2017
---
# <a name="walkthrough-using-xml-editor-features"></a>Passo a passo: Usando funcionalidades do editor XML
As etapas nessa explicação passo a passo mostram como criar um novo documento XML. A explicação passo a passo também usa alguns dos recursos do editor XML que tornam valioso para criar XML.  
  
> [!NOTE]
>  Antes de iniciar a explicação passo a passo, salve o arquivo de hireDate.xsd (incluído abaixo neste tópico) para seu computador local.  
  
### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Para criar um novo arquivo XML e associá-la com um esquema XML  
  
1.  Sobre o **arquivo** , aponte para **novo**e clique em **arquivo**.  
  
2.  Selecione **arquivo XML** no **modelos** painel e clique em **abrir**.  
  
     Um novo arquivo é aberto no editor. O arquivo contém uma declaração XML padrão, `<?xml version="1.0" encoding="utf-8">`.  
  
3.  Na janela de propriedades do documento, clique no botão Procurar (**...** ) sobre o **esquemas** campo.  
  
     O **esquemas XSD** caixa de diálogo é exibida.  
  
4.  Clique em **Adicionar**.  
  
     O **esquema XSD aberto** caixa de diálogo é exibida.  
  
5.  Selecione o arquivo hireDate.xsd e clique em **abrir**.  
  
6.  Clique em **OK**.  
  
     O esquema XML agora está associado com o documento XML. O esquema XML é usado para validar o documento. Também é usado pelo IntelliSense para preencher a lista de membros de elementos válidos.  
  
### <a name="to-add-data"></a>Para adicionar dados  
  
1.  Tipo `<` no painel do editor.  
  
     A lista de membros exibe os itens possíveis:  
  
    -   **!-** para adicionar um comentário.  
  
    -   **! DOCTYPE** para adicionar um tipo de documento.  
  
    -   **?** Para adicionar uma instrução de processamento.  
  
    -   **funcionário** para adicionar o elemento raiz.  
  
2.  Selecione **<!-** para adicionar um nó de comentário e pressione ENTER.  
  
     O editor insere uma marca de fim do comentário e colocar o cursor entre o início e marcas de comentário final.  
  
3.  Digite **arquivo XML de teste**.  
  
4.  Em uma nova linha, digite `<`e selecione **funcionário** da lista de membros.  
  
     O editor adiciona o início de um elemento XML, `<employee`. Neste momento você pode adicionar atributos para o elemento ou você pode fechar a tag de início digitando `>`.  
  
5.  Tipo `>` para a marca de fechamento.  
  
6.  O editor adiciona a marca de fim. A marca de fim é adicionada com um a linha subescrita ondulada que indica um erro de validação. A dica de ferramenta exibe a mensagem: O elemento “empregado” tem conteúdo incompleto. 'ID' esperado.  
  
7.  Tipo `<` e selecione **ID** da lista de membros. Digite `>`.  
  
     O editor adicione o elemento XML, `<ID></ID>`, e posicionar o cursor após a marca de início de identificação.  
  
8.  Tipo **abc**.  
  
     O **abc** texto tiver um sublinhado ondulado. A dica de ferramenta exibe a mensagem: O elemento “identificação” tem um valor inválido de acordo com seu tipo de dados.  
  
9. Clique com o botão direito no elemento de ID e selecione **ir para definição**.  
  
     O editor abre o arquivo de hireDate.xsd em uma nova janela de documento e posicionar o cursor na definição de elemento do esquema de identificação.  
  
10. Retornar para o arquivo XML e substitua o **abc** texto com **123**.  
  
     O sublinhado e o ToolTip ondulados são desmarcados no valor do elemento ID. A dica de ferramenta para a marca de fim do funcionário agora exibe a mensagem: O elemento “empregado” tem conteúdo incompleto. “Data de admissão esperada”.  
  
11. Coloque o cursor após a marca de fim de identificação, digite `<`, data de admissão select da lista de membros, e digite dentro `>`.  
  
     O editor adicione o elemento XML, `<hire-date></hire-date>`, e posicionar o cursor após a marca de início da data de admissão.  
  
12. Digite **2003-01-10** para o valor de data de contratação.  
  
### <a name="to-format-the-xml-document"></a>Para formatar o documento XML  
  
- Selecione o **documento** botão da barra de ferramentas do Editor de XML.
  
    O documento XML é reformatado.  
  
### <a name="to-save-the-xml-document"></a>Para salvar o documento XML  
  
1.  Do **arquivo** menu, selecione **Salvar como**.  
  
     O **salvar arquivo como** caixa de diálogo é exibida. O nome de arquivo padrão é “XMLFile1”.  
  
2.  Insira o nome do arquivo e o local para o documento XML e clique em **salvar**.  
  
## <a name="hiredatexsd-file"></a>hireDate.xsd Arquivo  
 O seguinte arquivo de esquema é usado por passo a passo.  
  
```xml
<?xml version="1.0"?>  
<xs:schema attributeFormDefault="unqualified"  
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"  
     xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="employee">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="ID" type="xs:unsignedShort" />  
        <xs:element name="hire-date" type="xs:date" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Editor de XML](../xml-tools/xml-editor.md)