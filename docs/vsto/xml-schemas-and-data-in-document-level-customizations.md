---
title: "Esquemas XML e dados em personalizações no nível do documento | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
ms.assetid: 74bd5773-6cb0-44fb-9738-75e2f2c6e48d
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d53a17484a350e361459f5c975ed3090779332bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Esquemas e dados XML em personalizações no nível do documento
  **Importante** as informações definidas neste tópico sobre o Microsoft Word são apresentada exclusivamente para o benefício e o uso de pessoas e organizações que estão localizados fora dos Estados Unidos e seus territórios ou que estão usando o ou desenvolvendo programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft antes de janeiro de 2010, quando a Microsoft removido uma implementação de determinada funcionalidade relacionado ao XML personalizado do Microsoft Word. Essas informações sobre o Microsoft Word não podem ser lidas ou usadas por indivíduos ou organizações nos Estados Unidos ou seus territórios que estão usando ou desenvolver programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft após 10 de janeiro de 2010 ; Esses produtos não se comportar o mesmo que produtos licenciados antes dessa data ou adquirido e licenciado para uso fora dos Estados Unidos.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 O Microsoft Office Excel e o Microsoft Office Word fornecem a capacidade de mapear esquemas para seus documentos. Esse recurso pode simplificar a importar e exportar dados XML para dentro e fora do documento.  
  
 Expõe do Visual Studio mapeado elementos de esquema em personalizações no nível do documento como controles no modelo de programação. Para Excel, o Visual Studio adiciona suporte para os controles de associação a dados em bancos de dados, serviços da Web e objetos. Para o Word e Excel, o Visual Studio adiciona suporte para painéis de ações, que pode ser usado com um documento de esquema mapeado para criar uma experiência de usuário final avançado para suas soluções. Para obter mais informações, consulte [visão geral do painel de ações](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  Você não pode usar os esquemas XML com diversas partes em soluções do Excel.  
  
## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Criação de objetos quando esquemas são anexados a pastas de trabalho do Excel  
 Quando você anexa um esquema para uma pasta de trabalho, o Visual Studio automaticamente cria vários objetos e os adiciona ao seu projeto. Esses objetos não devem ser excluídos usando ferramentas do Visual Studio, porque eles são gerenciados pelo Excel. Para excluí-los, remova os elementos mapeados da planilha ou desanexar o esquema, usando ferramentas do Excel.  
  
 Há dois objetos principais:  
  
-   Esquema XML (arquivo XSD). Para cada esquema na pasta de trabalho, o Visual Studio adiciona um esquema para o projeto. Isso é exibido como um item de projeto com uma extensão XSD em **Gerenciador de soluções**.  
  
-   Um tipo <xref:System.Data.DataSet> classe. Essa classe é criada com base no esquema. Essa classe de conjunto de dados é visível no **exibição de classe**.  
  
## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Objetos criado quando os elementos do esquema são mapeados para planilhas do Excel  
 Quando você mapeia um elemento de esquema do **origem XML** painel de tarefas para uma planilha, o Visual Studio automaticamente cria vários objetos e os adiciona ao seu projeto:  
  
-   Controles. Para cada objeto mapeado na pasta de trabalho, um <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control (para elementos do esquema não repetitivo) ou um <xref:Microsoft.Office.Tools.Excel.ListObject> control (para elementos do esquema de repetição) é criada no modelo de programação. O <xref:Microsoft.Office.Tools.Excel.ListObject> controle pode ser excluído apenas com a exclusão de objetos mapeados e os mapeamentos da pasta de trabalho. Para obter mais informações sobre os controles, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md).  
  
-   BindingSource. Quando você cria um <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> mapeando um elemento de esquema não repetição para a planilha, um <xref:System.Windows.Forms.BindingSource> é criado e o <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controle está vinculado a <xref:System.Windows.Forms.BindingSource>. Você deve associar o <xref:System.Windows.Forms.BindingSource> a uma instância da fonte de dados que corresponde ao esquema mapeado para o documento, como uma instância do tipado <xref:System.Data.DataSet> classe que foi criado. Criar uma associação, definindo o <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriedades, que são expostas no **propriedades** janela.  
  
    > [!NOTE]  
    >  O <xref:System.Windows.Forms.BindingSource> não é criado para <xref:Microsoft.Office.Tools.Excel.ListObject> objetos. Você deve vincular manualmente o <xref:Microsoft.Office.Tools.Excel.ListObject> à fonte de dados, definindo o <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriedades no **propriedades** janela.  
  
### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office mapeado esquemas e a janela de fontes de dados do Visual Studio  
 A funcionalidade de esquema mapeado do Office e o Visual Studio **fontes de dados** janela pode ajudá-lo a apresentar dados em uma planilha do Excel para relatórios ou edição. Em ambos os casos, você pode arrastar os elementos de dados para a planilha do Excel. Ambos os métodos criam controles de dados vinculados por meio de um <xref:System.Windows.Forms.BindingSource> para uma fonte de dados, como um <xref:System.Data.DataSet> ou um serviço Web.  
  
> [!NOTE]  
>  Quando você mapeia um elemento de esquema repetido em uma planilha, o Visual Studio cria um <xref:Microsoft.Office.Tools.Excel.ListObject>. O <xref:Microsoft.Office.Tools.Excel.ListObject> automaticamente não está associado a dados por meio de <xref:System.Windows.Forms.BindingSource>. Você deve vincular manualmente o <xref:Microsoft.Office.Tools.Excel.ListObject> à fonte de dados, definindo o <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriedades no **propriedades** janela.  
  
 A tabela a seguir mostra algumas das diferenças entre os dois métodos.  
  
|Esquema XML|janela Fontes de Dados|  
|----------------|-------------------------|  
|Usa a interface do Office.|Usa **fontes de dados** janela no Visual Studio.|  
|Permite que os recursos internos do Office para importar e exportar dados de arquivos XML.|Você deve fornecer importar e exportar funcionalidade programaticamente.|  
|Você deve escrever código para preencher os controles gerados com dados.|Controles adicionados a partir de **fontes de dados** janela tem código gerado automaticamente para preenchê-los, juntamente com as cadeias de caracteres de conexão necessárias ao usar servidores de banco de dados.|  
  
## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Comportamento quando esquemas são anexados a documentos do Word  
 Objetos de dados não são criados quando você anexa um esquema a um documento do Word que é usado em um projeto de nível de documento do Office. No entanto, quando você mapear um elemento de esquema para o documento, os controles são criados. O tipo de controle depende de qual tipo de elemento que você mapear; geram elementos de repetição <xref:Microsoft.Office.Tools.Word.XMLNodes> controles e elementos de não repetição gerar <xref:Microsoft.Office.Tools.Word.XMLNode> controles. Para obter mais informações, consulte [controle XMLNodes](../vsto/xmlnodes-control.md) e [controle XMLNode](../vsto/xmlnode-control.md).  
  
## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Implantação de soluções que incluem esquemas XML  
 Você deve criar um instalador para implantar uma solução que usa um esquema XML que é mapeado para um documento. O instalador deve registrar o esquema na biblioteca do esquema no computador do usuário. Se você não registrar o esquema, a solução ainda funcionará como o Word gera um esquema temporário com os elementos que estão no documento, quando o usuário o abrir. No entanto, o usuário não poderá executar a validação em relação a ou salve o esquema que foi usado para criar o projeto. Para obter mais informações sobre instaladores, consulte [implantação de aplicativos, serviços e componentes](/visualstudio/deployment/deploying-applications-services-and-components).  
  
 Você também pode adicionar código ao seu projeto para verificar se o esquema está na biblioteca e registrado. Se não estiver, você pode avisar o usuário.  
  
 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: mapear esquemas para documentos do Word dentro do Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Como mapear esquemas para planilhas dentro do Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  