---
title: Trechos XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f92b96f09353bf8e432d6a3931a534064ad7c446
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="xml-snippets"></a>Trechos XML

O Editor de XML oferece um recurso chamado *trechos XML*, que permite que você crie arquivos XML mais rapidamente. Você pode reutilizar XML inserindo trechos nos seus arquivos. Você também pode gerar os dados XML com base no esquema de linguagem de definição de esquema XML (XSD).

## <a name="reusable-xml-snippets"></a>Trechos reutilizáveis XML

O editor XML inclui muitos trechos que abrangem algumas tarefas comuns. Isso permite que você crie arquivos XML mais facilmente. Por exemplo, se você estivesse criando um esquema XML, usando o elemento de sequência tipo complexo” e “os trechos do elemento tipo simples” inserir o seguinte texto XML para o arquivo. Você alteraria o valor de `name` para atender às suas necessidades.

```xml
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

 Você pode inserir trechos de duas maneiras. O **Inserir trecho** comando insere o trecho XML na posição do cursor. O **Surround With** comando encapsula o trecho de código XML ao redor do texto selecionado. Os dois comandos estão disponíveis ou do **IntelliSense** submenu a **editar** menu, ou no menu de atalho do editor.

 Para obter mais informações, consulte [como: usar trechos de XML](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Trechos Esquema- gerados XML
 O editor XML também tem a capacidade de gerar um trecho de um esquema XML. Esse recurso permite que você popule um elemento com elementos XML gerados de informações de esquema para esse elemento.

 Para obter mais informações, consulte [como: gerar um XML de um esquema XML do trecho](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Crie novos trechos XML
 Além de trechos de código que estão incluídos com [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio, por padrão, você também pode criar e usar seus próprios trechos de código XML.

 Para obter mais informações, consulte [como: criar trechos de código XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Consulte também

- [Editor de XML](../xml-tools/xml-editor.md)