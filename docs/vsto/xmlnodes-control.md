---
title: Controle XMLNodes | Microsoft Docs
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
- XMLNodes control, events
- XMLNodes control
ms.assetid: 25ba7a21-aabb-4cce-b0d7-57b4add3b485
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: e59fb1ee6f3f8ea0be474f6fffabdc2c4ef7510e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="xmlnodes-control"></a>Controle XMLNodes
  **Importante** as informações definidas neste tópico sobre o Microsoft Word são apresentada exclusivamente para o benefício e o uso de pessoas e organizações que estão localizados fora dos Estados Unidos e seus territórios ou que estão usando o ou desenvolvendo programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft antes de janeiro de 2010, quando a Microsoft removido uma implementação de determinada funcionalidade relacionado ao XML personalizado do Microsoft Word. Essas informações sobre o Microsoft Word não podem ser lidas ou usadas por indivíduos ou organizações nos Estados Unidos ou seus territórios que estão usando ou desenvolver programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft após 10 de janeiro de 2010 ; Esses produtos não se comportar o mesmo que produtos licenciados antes dessa data ou adquirido e licenciado para uso fora dos Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 O <xref:Microsoft.Office.Tools.Word.XMLNodes> controle é uma coleção de objetos de nó XML mapeadas que expõe eventos. O <xref:Microsoft.Office.Tools.Word.XMLNodes> controle é criado somente quando um elemento de esquema de repetição é mapeado para um documento do Microsoft Office Word. Se o elemento de repetição contém elementos filho, cada um dos elementos filho também é criada como uma <xref:Microsoft.Office.Tools.Word.XMLNodes> controle.  
  
 Depois que o Visual Studio cria a coleção de nós XML, você pode programar o controle diretamente sem a necessidade de desviar o modelo de objeto do Word. O <xref:Microsoft.Office.Tools.Word.XMLNodes> controle pode ser excluído somente removendo o mapeamento de elemento do documento.  
  
> [!NOTE]  
>  Se você acessar um elemento filho do <xref:Microsoft.Office.Tools.Word.XMLNodes> controlar por meio de <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> propriedade, ele retorna um <xref:Microsoft.Office.Interop.Word.XMLNode> objeto em vez de uma <xref:Microsoft.Office.Tools.Word.XMLNode> controle. Para obter mais informações, consulte [limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="binding-data-to-the-control"></a>Associação de dados ao controle  
 Um <xref:Microsoft.Office.Tools.Word.XMLNodes> controle não dá suporte à associação de dados. Isso ocorre porque o <xref:Microsoft.Office.Tools.Word.XMLNodes> controle não tem recursos de associação de dados complexos e associação de dados simples não pode representar dados de repetição.  
  
## <a name="formatting"></a>Formatação  
 Qualquer formatação que podem ser aplicados ao texto dentro do documento pode ser aplicado a um <xref:Microsoft.Office.Tools.Word.XMLNodes> controle.  
  
## <a name="events"></a>Eventos  
 Os eventos disponíveis para o <xref:Microsoft.Office.Tools.Word.XMLNodes> controle são:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## <a name="comparing-events"></a>Comparação de eventos  
 Você pode capturar um evento quando o usuário move o cursor dentro do contexto de um determinado <xref:Microsoft.Office.Tools.Word.XMLNodes> controle. Por exemplo, você pode ter um <xref:Microsoft.Office.Tools.Word.XMLNodes> controle chamado `Customer` que tem um filho <xref:Microsoft.Office.Tools.Word.XMLNodes> controle chamado `Company`, e `Company` tem dois filhos <xref:Microsoft.Office.Tools.Word.XMLNodes> controles denominados `CompanyName` e `CompanyRegion` da seguinte maneira:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Se você desejar mostrar um controle no painel Ações sempre que o cursor é movido para o `Company` nó, ele deve não importa se o cursor é colocado na `CompanyName` ou `CompanyRegion` porque ambos estão dentro do contexto de `Company`. Nesse caso, você pode escrever seu código no <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> evento `Company`.  
  
 Na maioria dos casos, quando o cursor entra um <xref:Microsoft.Office.Tools.Word.XMLNodes> controlar, ambos o <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> e <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> os eventos são gerados. A tabela a seguir mostra as diferenças entre esses eventos.  
  
|Selecione um evento|Evento ContextEnter|  
|------------------|------------------------|  
|Ocorre quando o cursor é colocado dentro de um dos nós da coleção <xref:Microsoft.Office.Tools.Word.XMLNodes>.|Ocorre quando o cursor é movido para dentro de um dos nós, ou nós descendentes, da coleção <xref:Microsoft.Office.Tools.Word.XMLNodes> para uma área fora do contexto do nó. Em outras palavras, ele é gerado somente quando o contexto é alterado e pode ser gerado para várias aninhadas <xref:Microsoft.Office.Tools.Word.XMLNodes> controles.|  
  
 Por exemplo, quando você move o cursor de fora do `Customer` em `CompanyName`, o <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> eventos para `Customer`, `Company`, e `CompanyName` são gerados. Se você mover o cursor do `CompanyName` para `CompanyRegion`, o <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> evento somente para `CompanyRegion` é gerado, porque o contexto é o mesmo para ambos `Company` e `Customer`. Você pode ter várias `Company` nós no documento. Se você mover o cursor do `CompanyName` nó de um `Company` para o `CompanyName` nó de outro `Company`, o contexto é o mesmo, portanto, somente o <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> é gerado.  
  
 O mesmo diferenças entre o <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> evento e o <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> evento.  
  
## <a name="see-also"></a>Consulte também  
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizando o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Controle XMLNode](../vsto/xmlnode-control.md)   
 [Como: adicionar controles XMLNodes a documentos do Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Como: mapear esquemas para documentos do Word dentro do Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitações programáticas de itens de Host e Controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  