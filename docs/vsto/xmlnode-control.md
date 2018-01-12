---
title: Controle XMLNode | Microsoft Docs
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
helpviewer_keywords: XMLNode control
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f89c80850c5f91cdc6d147d733d2626f8641dab6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="xmlnode-control"></a>Controle XMLNode
  **Importante** as informações definidas neste tópico sobre o Microsoft Word são apresentada exclusivamente para o benefício e o uso de pessoas e organizações que estão localizados fora dos Estados Unidos e seus territórios ou que estão usando o ou desenvolvendo programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft antes de janeiro de 2010, quando a Microsoft removido uma implementação de determinada funcionalidade relacionado ao XML personalizado do Microsoft Word. Essas informações sobre o Microsoft Word não podem ser lidas ou usadas por indivíduos ou organizações nos Estados Unidos ou seus territórios que estão usando ou desenvolver programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft após 10 de janeiro de 2010 ; Esses produtos não se comportar o mesmo que produtos licenciados antes dessa data ou adquirido e licenciado para uso fora dos Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 O <xref:Microsoft.Office.Tools.Word.XMLNode> controle é um objeto de nó XML mapeado que expõe eventos e pode ser associado a dados. O <xref:Microsoft.Office.Tools.Word.XMLNode> controle é criado somente quando um elemento de esquema não repetitivo é mapeado para um documento do Microsoft Office Word. Depois que o Visual Studio cria o nó XML, você pode programar em relação a ela diretamente sem a necessidade de desviar o modelo de objeto do Word.  
  
 O <xref:Microsoft.Office.Tools.Word.XMLNode> controle pode ser excluído somente removendo o mapeamento de elemento no Word.  
  
## <a name="binding-data-to-the-control"></a>Associação de dados ao controle  
 Um <xref:Microsoft.Office.Tools.Word.XMLNode> controle oferece suporte à associação de dados simples. O nó XML deve ser vinculado a uma fonte de dados usando o <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> propriedade. Se os dados no conjunto de dados associado são atualizados, o <xref:Microsoft.Office.Tools.Word.XMLNode> controle reflete as alterações.  
  
## <a name="formatting"></a>Formatação  
 Formatação que pode ser aplicado a um <xref:Microsoft.Office.Interop.Word.XMLNode> objeto pode ser aplicado a um <xref:Microsoft.Office.Tools.Word.XMLNode> controle. Isso inclui fontes, estilos de sublinhado e estilos de caractere.  
  
## <a name="events"></a>Eventos  
 Os seguintes eventos estão disponíveis para o <xref:Microsoft.Office.Tools.Word.XMLNode> controle:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## <a name="comparing-events"></a>Comparação de eventos  
 Você pode capturar um evento quando o usuário move o cursor dentro do contexto de um determinado <xref:Microsoft.Office.Tools.Word.XMLNode> controle. Por exemplo, você pode ter um <xref:Microsoft.Office.Tools.Word.XMLNode> controle chamado `Customer` que tem um filho <xref:Microsoft.Office.Tools.Word.XMLNode> controle chamado `Company`, e `Company` tem dois filhos <xref:Microsoft.Office.Tools.Word.XMLNode> controles denominados `CompanyName` e `CompanyRegion` da seguinte maneira:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Se você desejar mostrar um controle no painel Ações sempre que o cursor é movido para o `Company` nó, ele deve não importa se o cursor é colocado na `CompanyName` ou `CompanyRegion` porque ambos estão dentro do contexto de `Company`. Nesse caso, você pode escrever seu código no <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> evento `Company`.  
  
 Na maioria dos casos, quando o cursor entra um <xref:Microsoft.Office.Tools.Word.XMLNode> controlar, ambos o <xref:Microsoft.Office.Tools.Word.XMLNode.Select> e <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> os eventos são gerados. A tabela a seguir mostra as diferenças entre esses eventos.  
  
|Selecione um evento|Evento ContextEnter|  
|------------------|------------------------|  
|Ocorre quando o cursor é colocado dentro de um <xref:Microsoft.Office.Tools.Word.XMLNode>.|Ocorre quando o cursor é colocado dentro de um <xref:Microsoft.Office.Tools.Word.XMLNode> ou um de seus nós descendentes, de uma área fora do contexto do nó. Em outras palavras, ele é gerado somente quando o contexto é alterado.|  
  
 Por exemplo, quando você move o cursor de fora do `Customer` em `CompanyName`, o <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> evento `Customer`, `Company`, e `CompanyName` é gerado. Se você mover o cursor do `CompanyName` para `CompanyRegion`, somente o <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> evento `CompanyRegion` foi gerado porque ainda está dentro do contexto de ambos `Company` e `Customer`.  
  
 O mesmo diferenças entre o <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> eventos e <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizando o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Controle XMLNodes](../vsto/xmlnodes-control.md)   
 [Como: adicionar controles XMLNode a documentos do Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Como: mapear esquemas para documentos do Word dentro do Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Limitações programáticas de itens de Host e Controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  