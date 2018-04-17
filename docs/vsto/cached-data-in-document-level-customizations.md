---
title: Dados em personalizações no nível do documento em cache | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0919e046f9e50578df46853c6db9f60cea2f71e3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="cached-data-in-document-level-customizations"></a>Dados armazenados em cache em personalizações no nível do documento
  É o principal objetivo de personalizações no nível do documento separar dados de exibição em documentos do Office. Dados referem-se às informações armazenadas no documento, incluindo números e texto. Modo de exibição refere-se a interface do usuário e o modelo de objeto do Microsoft Office Word e Microsoft Office Excel.  
  
 O Visual Studio separa os dados da exibição em personalizações no nível do documento, permitindo que os dados a ser inserido como um *ilha de dados*, também chamado de *cache de dados*. Você pode ler ou modificar os dados diretamente sem iniciar o Word ou Excel. Isso é útil quando você precisa modificar dados em documentos em um servidor que não tenha o Microsoft Office instalado. Word e Excel são destinados para uso em ambientes de cliente; eles não são projetados para ser executado em um servidor.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Para obter mais informações sobre personalizações no nível do documento, consulte [visão geral de desenvolvimento de soluções do Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) e [arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understanding-the-cached-data-programming-model"></a>Compreendendo o modelo de programação de dados armazenados em cache  
 A ilha de dados pode conter qualquer objeto em sua solução que atenda a certos requisitos. Esses objetos incluem <xref:System.Data.DataSet> objetos, <xref:System.Data.DataTable> objetos e qualquer outro objeto que pode ser serializado pela <xref:System.Xml.Serialization.XmlSerializer> classe. Para obter mais informações, consulte consulte [Caching Data](../vsto/caching-data.md).  
  
 Para fornecer o modo de exibição para os dados em cache, você pode associar controles de formulários do Windows e *hospedar controles* no documento para objetos na ilha de dados. Associação de dados entre a ilha de dados e os controles de associação de dados mantém as duas sincronizadas. Você também pode adicionar código de validação para os dados que é independentes dos controles. Para obter mais informações, consulte [vinculação de dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Controles de host são estendidos versões de objetos nativos em modelos de objeto do Excel e Word. Ao contrário de objetos nativos, controles de host podem ser vinculados diretamente a objetos de dados gerenciados. Para obter mais informações, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md) e [controles dos Windows Forms na visão geral de documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="accessing-cached-data-on-the-server"></a>Acessar dados armazenados em cache no servidor  
 Para acessar dados armazenados em cache em um documento, você pode usar o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Essa classe é parte do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], e ele pode ser usado em um servidor sem execução Excel ou Word. Quando o usuário abre o documento após modificar os dados em cache, todos os controles que estão associados aos dados serão sincronizados automaticamente com as alterações e é exibida com os dados atualizados para o usuário. Para obter mais informações, consulte [acessar dados em documentos no servidor](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excel e Word não são necessários para gravar os dados no servidor, somente para exibi-lo no cliente. Excel e Word ainda precisa ser instalado no servidor. Isso fornece maior escalabilidade e a capacidade de executar o processamento rápido de lote de documentos que contêm ilhas de dados.  
  
## <a name="data-caching-for-offline-use"></a>Dados em cache para uso Offline  
 Armazenando dados em ilha de dados permite cenários offline. Quando um usuário abre um documento ou solicita o documento do servidor, a ilha de dados é preenchida com os dados mais recentes. A ilha de dados é armazenado em cache no documento e, em seguida, está disponível offline. O usuário (e seu código) podem manipular os dados, mesmo que nenhuma conexão ao vivo está disponível. Quando o usuário reconecta, as alterações aos dados podem ser propagadas de volta para uma fonte de dados do servidor.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Dados armazenados em cache e partes XML personalizadas em comparação comparadas  
 Partes XML personalizadas foram introduzidos no sistema Microsoft Office 2007 como uma maneira de armazenar partes arbitrárias de XML em um documento. Embora a partes XML personalizadas são úteis em muitos dos mesmos cenários como o cache de dados, há algumas diferenças entre a ilha de dados e partes XML personalizadas. Para obter mais informações sobre partes XML personalizadas, consulte [visão geral sobre o partes XML personalizadas](../vsto/custom-xml-parts-overview.md).  
  
 A tabela a seguir lista algumas das diferenças e semelhanças.  
  
||Cache de dados|Partes XML personalizadas|  
|-|----------------|----------------------|  
|Quais aplicativos do Office podem usá-los?|Personalizações de nível de documento para os seguintes aplicativos:<br /><br /> -Excel<br />-Word|Soluções de nível de documento e nível de aplicativo para os seguintes aplicativos:<br /><br /> -Excel<br />-PowerPoint<br />-Word|  
|Quais tipos de dados pode armazenar?|Qualquer objeto público em seu assembly de personalização que atenda a certos requisitos. Para obter mais informações, consulte [Caching Data](../vsto/caching-data.md).|Todos os dados XML.|  
|Você pode acessar os dados sem iniciar aplicativos do Microsoft Office?|Sim, usando o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe fornecida pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Sim, usando classes no <xref:System.IO.Packaging> namespace, ou usando o SDK de formato XML aberto.|  
  
## <a name="see-also"></a>Consulte também  
 [Dados em soluções do Office](../vsto/data-in-office-solutions.md)   
 [Arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  