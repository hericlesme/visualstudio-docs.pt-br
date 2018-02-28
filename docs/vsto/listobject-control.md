---
title: Controle ListObject | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.Toolbox.List
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- lists, events
- ListObject control
- ListObject control, events
- ListObject control, data binding
- ListObject control, improving performance when bound to data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 2100a1c30fda5981d3d7e58f2f5077e0cdf87a2d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="listobject-control"></a>Controle ListObject
  O <xref:Microsoft.Office.Tools.Excel.ListObject> controle é uma lista que expõe eventos e pode ser associada a dados. Quando você adiciona uma lista em uma planilha, o Visual Studio cria um <xref:Microsoft.Office.Tools.Excel.ListObject> controle que você pode programar diretamente sem a necessidade de desviar o modelo de objeto do Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="creating-the-control"></a>Criando o controle  
 Em projetos de nível de documento, você pode adicionar <xref:Microsoft.Office.Tools.Excel.ListObject> controles em uma planilha em tempo de design ou em tempo de execução. Em projetos de suplemento do VSTO, você pode adicionar <xref:Microsoft.Office.Tools.Excel.ListObject> controles para planilhas somente em tempo de execução. Para obter mais informações, consulte [como: adicionar controles ListObject a planilhas](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Por padrão, os objetos de lista criados dinamicamente não são persistentes na planilha como hospedar controles quando a planilha está fechada. Para obter mais informações, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="binding-data-to-the-control"></a>Associação de dados ao controle  
 Um <xref:Microsoft.Office.Tools.Excel.ListObject> controle oferece suporte à associação de dados simples e complexas. O <xref:Microsoft.Office.Tools.Excel.ListObject> controle pode ser vinculado a uma fonte de dados usando o <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> e <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> propriedades em tempo de design ou o <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> método em tempo de execução.  
  
> [!NOTE]  
>  O <xref:Microsoft.Office.Tools.Excel.ListObject> é atualizada automaticamente quando ele está vinculado a uma fonte de dados, como um <xref:System.Data.DataTable>, que gera eventos quando os dados são alterados. Se você associar o <xref:Microsoft.Office.Tools.Excel.ListObject> para uma fonte de dados que não gera eventos quando os dados forem alterados, você deve chamar o <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> ou <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> para atualizar o <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
 Quando você adiciona um <xref:Microsoft.Office.Tools.Excel.ListObject> para uma célula de planilha, mapeando um elemento de esquema de repetição para que a célula, o Visual Studio mapeia automaticamente o <xref:Microsoft.Office.Tools.Excel.ListObject> ao conjunto de dados gerado. No entanto, o <xref:Microsoft.Office.Tools.Excel.ListObject> automaticamente não está associado aos dados. Você pode adotar medidas para associar o <xref:Microsoft.Office.Tools.Excel.ListObject> ao conjunto de dados em tempo de design ou em tempo de execução em um projeto no nível do documento. Você pode vincular programaticamente o <xref:Microsoft.Office.Tools.Excel.ListObject> ao conjunto de dados em tempo de execução em um suplemento do VSTO.  
  
 Como os dados são separados do <xref:Microsoft.Office.Tools.Excel.ListObject>, você deve adicionar e remover dados por meio do conjunto de dados associado e não diretamente o <xref:Microsoft.Office.Tools.Excel.ListObject>. Se os dados no conjunto de dados associado são atualizados por meio de qualquer mecanismo de <xref:Microsoft.Office.Tools.Excel.ListObject> controle automaticamente reflete as alterações. Para obter mais informações, consulte [vinculação de dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Você pode preencher rapidamente um <xref:Microsoft.Office.Tools.Excel.ListObject> controle associando o <xref:Microsoft.Office.Tools.Excel.ListObject> para uma fonte de dados. Se você editar os dados em uma associação de dados <xref:Microsoft.Office.Tools.Excel.ListObject>, as alterações são feitas automaticamente na fonte de dados. Se você deseja preencher uma <xref:Microsoft.Office.Tools.Excel.ListObject> e, em seguida, permitir que o usuário alterar os dados no <xref:Microsoft.Office.Tools.Excel.ListObject> sem modificar a fonte de dados, você pode usar o <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> método para desanexar o <xref:Microsoft.Office.Tools.Excel.ListObject> da fonte de dados. Para obter mais informações, consulte [como: Preencher controles ListObject com dados](../vsto/how-to-fill-listobject-controls-with-data.md).  
  
> [!NOTE]  
>  Não há suporte para associação de dados na sobreposição <xref:Microsoft.Office.Tools.Excel.ListObject> controles.  
  
### <a name="improving-performance-in-listobject-controls"></a>Melhorando o desempenho em controles ListObject  
 Ler um arquivo XML em uma associação de dados <xref:Microsoft.Office.Tools.Excel.ListObject> controle tende a ser mais lento se você associar o controle primeiro e, em seguida, chame <xref:System.Data.DataSet.ReadXml%2A> para preencher o conjunto de dados. Para melhorar o desempenho, chame <xref:System.Data.DataSet.ReadXml%2A> antes de associar o controle.  
  
### <a name="disconnecting-listobject-controls-from-the-data-source"></a>Desconectando controles ListObject da fonte de dados  
 Depois que você preenche uma <xref:Microsoft.Office.Tools.Excel.ListObject> controle com dados associando-a uma fonte de dados, você pode desconectá-lo para que as modificações feitas nos dados no objeto de lista não afetam a fonte de dados. Para obter mais informações, consulte [como: Preencher controles ListObject com dados](../vsto/how-to-fill-listobject-controls-with-data.md).  
  
### <a name="restoring-column-and-row-order"></a>Restauração de coluna e ordem de linha  
 Quando você associa dados para um <xref:Microsoft.Office.Tools.Excel.ListObject> controle foi adicionado a um documento em tempo de design, o Visual Studio mantém controle sobre a ordem de coluna e linha sempre que a pasta de trabalho é salvo. Se um usuário move o <xref:Microsoft.Office.Tools.Excel.ListObject> colunas ou linhas durante o tempo de execução, a nova ordem é preservada na próxima vez em que a pasta de trabalho é aberta e o <xref:Microsoft.Office.Tools.Excel.ListObject> controle associado à fonte de dados novamente.  
  
 Se você deseja restaurar o <xref:Microsoft.Office.Tools.Excel.ListObject> para sua coluna original e a ordem das linhas, você pode chamar o <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> método. Este método remove as propriedades de documento personalizadas relacionadas à coluna e ordem de linha de especificado <xref:Microsoft.Office.Tools.Excel.ListObject>. Chame este método do <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> evento da pasta de trabalho se você não deseja preservar a ordem de coluna e linha do <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
## <a name="formatting"></a>Formatação  
 Formatação que pode ser aplicado a um <xref:Microsoft.Office.Interop.Excel.ListObject> pode ser aplicado a um <xref:Microsoft.Office.Tools.Excel.ListObject> controle. Isso inclui as bordas, fontes, formato de número e estilos. Os usuários finais podem reorganizar as colunas em uma associação de dados <xref:Microsoft.Office.Tools.Excel.ListObject>, e essas alterações serão mantidas com o documento, fornecido o <xref:Microsoft.Office.Tools.Excel.ListObject> foi adicionada ao documento em tempo de design. Na próxima vez em que o documento for aberto, o objeto da lista será associado à mesma fonte de dados, mas a ordem da coluna refletirão as alterações de usuários.  
  
## <a name="adding-and-removing-columns-at-run-time"></a>Adicionar e remover colunas em tempo de execução  
 Não é possível adicionar ou remover colunas em uma associação de dados manualmente <xref:Microsoft.Office.Tools.Excel.ListObject> controle em tempo de execução. Se um usuário final tenta excluir uma coluna, ele será restaurado imediatamente e quaisquer colunas adicionadas serão removidas. Portanto, é importante ao escrever código para explicar aos usuários por que eles não podem executar essas ações em um <xref:Microsoft.Office.Tools.Excel.ListObject> que está associada aos dados. O Visual Studio fornece vários eventos em um <xref:Microsoft.Office.Tools.Excel.ListObject> relacionadas à associação de dados. Por exemplo, você pode usar o <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> evento avisar os usuários que os dados que eles tentaram excluir não podem ser excluídos e foi restaurados.  
  
## <a name="adding-and-removing-rows-at-run-time"></a>Adicionando e removendo linhas em tempo de execução  
 Você pode adicionar e remover linhas em uma associação de dados manualmente <xref:Microsoft.Office.Tools.Excel.ListObject> controlar, desde que a fonte de dados permite a adição de novas linhas e não é somente leitura. Você pode escrever código para eventos, como o <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> para validar os dados. Para obter mais informações, consulte [como: validar dados quando uma nova linha é adicionada a um controle ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md).  
  
 Às vezes, a relação do objeto de lista para a fonte de dados causa erros de rotina. Por exemplo, você pode mapear as colunas que você deseja que apareça no <xref:Microsoft.Office.Tools.Excel.ListObject>, portanto, se você omitir colunas que têm restrições, como um campo que não pode aceitar valores nulos, os erros são gerados sempre que uma linha é criada. Você pode escrever código para adicionar os valores ausentes em um manipulador de eventos para o <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> evento.  
  
## <a name="renaming-listobject-controls-in-excel"></a>Renomeando controles ListObject no Excel  
 Excel permite aos usuários alterar o nome das tabelas do Excel em tempo de execução usando o **Design** guia. No entanto, o <xref:Microsoft.Office.Tools.Excel.ListObject> controle não dá suporte a esse recurso. Se um usuário tentar renomear uma tabela do Excel que corresponde a um <xref:Microsoft.Office.Tools.Excel.ListObject>, o nome da tabela do Excel será revertida automaticamente para o nome original quando a pasta de trabalho é salvo.  
  
## <a name="events"></a>Eventos  
 Os seguintes eventos estão disponíveis para o <xref:Microsoft.Office.Tools.Excel.ListObject> controle:  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>  
  
## <a name="see-also"></a>Consulte também  
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Como: adicionar controles ListObject a planilhas](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Como: redimensionar controles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Como: validar dados quando uma nova linha é adicionada a um controle ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [Como: mapear colunas ListObject para dados](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Como: Preencher controles ListObject com dados](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Explicações passo a passo e exemplos de desenvolvimento do office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Como: preencher planilhas com dados de um banco de dados](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Limitações programáticas de itens de Host e Controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  