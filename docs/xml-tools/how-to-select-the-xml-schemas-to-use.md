---
title: 'Como: Selecione os esquemas XML para usar'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d835a8592108b549a109f7bb7e128a8ae5b01611
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Como: selecione os esquemas XML a ser usado

O Editor de XML fornece um cache de esquema localizado no *%InstallDir%\Xml\Schemas* directory. O cache de esquema inclui esquemas XML conhecidos que são usados para validação do IntelliSense e de documento XML.

O **esquemas** propriedade de documento é usada para selecionar um ou mais XML esquema definition language (XSD) esquema (s) a ser usado. Permite que você selecionar esquemas de cache do esquema, ou especifica um esquema que não está localizado no cache.

Os esquemas que você especificar serão salvas no arquivo de opções de usuário solução oculto (. *suo*), juntamente com todos os outros XML propriedades do documento. Como resultado, você não tem que digitar novamente esses valores na próxima vez que você abrir a solução.

> [!NOTE]
> O editor pode validar usando um esquema embutido, ou um esquema referenciado pelo atributo de `xsd:schemaLocation` . Para obter mais informações, consulte [validação de documento XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Para selecionar um esquema XML do cache de esquema

1.  Abrir um arquivo no editor XML.

2.  Na janela de propriedades do documento, clique no botão no **esquemas** campo.

     O **esquemas XML** caixa de diálogo é exibida. A caixa de diálogo lista todos os esquemas com um. *xsd* extensão no cache do esquema (incluindo esquemas referenciadas no *Catalog* arquivo) e também qualquer esquema que está na solução atual, aberta no Visual Studio, referenciada em um `xsd:schemaLocation` atributo ou referenciados no **esquemas** propriedade.

3.  Selecione os esquemas para usar a validação seguindo um destes procedimentos:

    -   Selecione um esquema listado no **esquemas XML** caixa de diálogo, clique o **Use** coluna e, em seguida, selecione **utilizam este esquema**.

     -ou-

    -   Selecione vários esquemas listadas no **esquemas XML** caixa de diálogo, clique com botão direito e selecione **utilizam este esquema**.

4.  Clique em **OK**.

     A lista de esquemas selecionados é copiada de volta para o **esquemas** propriedade do documento.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Para adicionar um esquema XML para o cache de esquema

1.  Na janela de propriedades do documento, clique no botão no **esquemas** campo.

2.  Clique em **Adicionar**.

     Isso abre o **esquema XSD aberto** caixa de diálogo.

3.  Procurar e selecione os esquemas para adicionar ao cache de esquema.

4.  Clique em **abrir**.

     O esquema (s) adicionados ao esquema de cache e é o **Use** o valor da coluna é definido como **utilizam este esquema**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Para excluir um esquema XML do cache de esquema

1.  Na janela de propriedades do documento, clique no botão no **esquemas** campo.

2.  Selecione o esquema a remover e, em seguida, clique em **remover**.

     O esquema é removido do cache de memória do esquema, mas não é removido do sistema de arquivos.

    > [!NOTE]
    > Se você ainda tem uma referência para o esquema por meio de um `schemaLocation` atributo ou uma correspondência `targetNamespace` , em seguida, **remover** não funciona nessa situação devido a associação automática. Nesse caso é recomendável que você marca o esquema como **não usa os esquemas selecionados** no **usar** coluna.

## <a name="see-also"></a>Consulte também

- [Cache de esquema](../xml-tools/schema-cache.md)
- [Caixa de diálogo de esquemas XML](../xml-tools/xml-schemas-dialog-box.md)
- [Editor de XML](../xml-tools/xml-editor.md)