---
title: Dados de cache
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 77b92b721f2c8b47bcb878aaa9f4cbf411015ccc
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264363"
---
# <a name="cache-data"></a>Dados de cache
  Você pode armazenar em cache objetos de dados em uma personalização no nível do documento para que os dados podem ser acessados offline ou sem abrir o Microsoft Office Word ou o Microsoft Office Excel. Para armazenar em cache um objeto, o objeto deve ter um tipo de dados que atenda a certos requisitos. Muitos tipos de dados comum do .NET Framework atendem a esses requisitos, incluindo <xref:System.String>, <xref:System.Data.DataSet>, e <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Há duas maneiras de adicionar um objeto para o cache de dados:  
  
-   Para adicionar um objeto para o cache de dados quando a solução é criada, aplicar o <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> de atributo para a declaração do objeto. Para obter mais informações, consulte [como: dados armazenados em Cache para uso offline ou em um servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Para adicionar programaticamente um objeto para o cache de dados em tempo de execução, use o `StartCaching` método de um host de item, como o `ThisDocument` ou `ThisWorkbook` classes. Para obter mais informações, consulte [como: cache programaticamente uma fonte de dados em um documento do Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
 Depois de adicionar um objeto para o cache de dados, você pode acessar e modificar os dados em cache sem iniciar o Word ou Excel. Para obter mais informações, consulte [acessar dados em documentos no servidor](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>Requisitos para objetos de dados a ser armazenado em cache  
 Para armazenar em cache um objeto de dados em sua solução, o objeto deve atender a esses requisitos:  
  
-   Ser um campo de leitura/gravação público ou propriedade de um item de host, como o `ThisDocument` ou `ThisWorkbook` classes.  
  
-   Não se um indexador ou outra propriedade com parâmetros.  
  
 Além disso, o objeto de dados deve ser serializado pela <xref:System.Xml.Serialization.XmlSerializer> classe, o que significa que o tipo de objeto deve ter as seguintes características:  
  
-   Ser um tipo público.  
  
-   Ter um construtor público sem parâmetros.  
  
-   Não execute o código que requer privilégios de segurança adicional.  
  
-   Expor somente leitura/gravação propriedades públicas (outras propriedades serão ignoradas).  
  
-   Não expor matrizes multidimensionais (matrizes aninhadas são aceitos).  
  
-   Interfaces não retorno de propriedades e campos.  
  
-   Não implementa <xref:System.Collections.IDictionary> se uma coleção.  
  
 Quando você armazena em cache um objeto de dados, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializa o objeto em uma cadeia de caracteres XML que é armazenada em um *parte XML personalizada* no documento. Para obter mais informações, consulte [visão geral de partes XML personalizadas](../vsto/custom-xml-parts-overview.md).  
  
## <a name="cached-data-size-limits"></a>Limites de tamanho de dados armazenados em cache  
 Existem alguns limites para a quantidade total de dados que você pode adicionar o cache de dados em um documento e o tamanho de qualquer objeto individual no cache de dados. Se você exceder esses limites, o aplicativo pode fechar inesperadamente, quando os dados são salvos no cache de dados.  
  
 Para evitar esses limites, siga estas diretrizes:  
  
-   Não adicione qualquer objeto maior do que 10 MB para o cache de dados.  
  
-   Não adicione mais de 100 MB de dados total para o cache de dados em um único documento.  
  
 Estes são valores aproximados. Os limites exatos dependem de vários fatores, incluindo a RAM disponível e o número de processos em execução.  
  
## <a name="control-the-behavior-of-cached-objects"></a>Controlar o comportamento de objetos armazenados em cache  
 Para obter mais controle sobre o comportamento de um objeto armazenado em cache, você pode implementar o <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interface no tipo do objeto armazenado em cache. Por exemplo, você pode implementar essa interface, se você quiser controlar como o usuário é notificado quando o objeto foi alterado. Para obter exemplos de código que demonstram como implementar <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, consulte o `ControlCollection` classe no exemplo de controles dinâmicos do Excel e Word dinâmico controles de exemplo em [amostras de desenvolvimento do Office e explicações passo a passo](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Manter as alterações nos dados armazenados em cache em documentos protegidos por senha  
 Se você armazenar em cache objetos de dados em um documento protegido com uma senha, as alterações nos dados armazenados em cache não serão salvas. Você pode salvar as alterações aos dados armazenados em cache, substituindo os dois métodos. Substituir esses métodos para remover temporariamente a proteção quando o documento é salvo e, em seguida, aplique novamente a proteção depois que a operação for concluída.  
  
 Para obter mais informações, consulte [como: Cache de dados em um documento protegido por senha](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Evitar a perda de dados durante a adição de valores nulos para o cache de dados  
 Quando você adiciona objetos para o cache de dados, todos os objetos armazenados em cache devem ser inicializados para não**nulo** valor antes do documento é salvo e fechado. Se tiver qualquer objeto armazenado em cache um **nulo** valor quando o documento é salvo e fechado, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] removerá automaticamente todos os objetos em cache do cache de dados.  
  
 Se você adicionar um objeto com um **nulo** valor para o cache de dados usando o <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo em tempo de design, você pode usar o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe ao inicializar os dados em cache objetos antes de abrir o documento. Isso é útil se você quiser inicializar os dados em cache em um servidor sem o Word ou Excel instalados, para que o documento está aberto por um usuário final. Para obter mais informações, consulte [acessar dados em documentos no servidor](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: dados armazenados em Cache para uso offline ou em um servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Como: cache programaticamente uma fonte de dados em um documento do Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Como: armazenar em Cache dados em um documento protegido por senha](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Passo a passo: Criar uma relação de detalhes mestre usando um conjunto de dados armazenados em cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  