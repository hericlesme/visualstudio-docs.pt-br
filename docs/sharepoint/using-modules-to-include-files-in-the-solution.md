---
title: Usando módulos para incluir arquivos na solução | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9c11dd4ebd17b1ebef91c3d7752df7c15dd50da4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="using-modules-to-include-files-in-the-solution"></a>Usando módulos para incluir arquivos na solução
  Pode haver momentos em que você pode deseja implantar arquivos para o servidor do SharePoint, independentemente de seu tipo de arquivo, como novas páginas mestras. Para fazer isso, você pode usar *módulos* (não deve ser confundido com [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] módulos de código). Módulos são contêineres de arquivos em uma solução do SharePoint. Quando a solução for implantada, os arquivos no módulo são copiados para as pastas especificadas no servidor do SharePoint.  
  
## <a name="module-items-and-elements"></a>Elementos e itens de módulo  
 Para criar um módulo, adicioná-lo a um projeto clicando no **Adicionar Novo Item** caixa de diálogo. Em seguida, modifique seu arquivo Elements para incluir os nomes dos arquivos que você deseja implantar, onde estão localizados no sistema, e onde eles devem ser copiados no servidor do SharePoint.  
  
 Aqui está um exemplo do arquivo Elements para um módulo:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
    <Module Name="Module1">  
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />  
    </Module>  
</Elements>  
  
```  
  
 Módulos recém-criado contêm os seguintes arquivos padrão:  
  
|Nome do Arquivo|Descrição|  
|---------------|-----------------|  
|Elements|O arquivo de definição para o módulo.|  
|Txt|Um arquivo de espaço reservado que serve como um exemplo de um arquivo do módulo.|  
  
 O arquivo Elements contém os seguintes elementos:  
  
|Nome de elementos|Descrição|  
|------------------|-----------------|  
|Elementos|Contém todos os elementos definidos no módulo.|  
|Módulo|O elemento de módulo tem um único atributo, *nome*, que especifica o nome do módulo no formato `<Module Name="Module1">`.<br /><br /> Observe que, se você alterar o nome do módulo (ou seus *nome da pasta* propriedade), você deve atualizar manualmente o nome no elemento do módulo.<br /><br /> Se você especificar um subdiretório para o arquivo (s) no elemento do módulo, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) criará automaticamente uma estrutura de diretório correspondente para eles.|  
|Arquivo|O elemento de arquivo tem dois parâmetros, *caminho* e *Url*.<br /><br /> -Path: O nome e o local do arquivo da solução do SharePoint. O formato é, `Path="Module1\Sample.txt"`.<br /><br /> -Url: O local onde o arquivo será implantado no servidor do SharePoint. O formato é, `Url="Module1/Sample.txt"`.<br /><br /> -Tipo: Um atributo opcional que tem duas configurações: *GhostableInLibrary* e *Ghostable*. O formato é, `Type="GhostableInLibrary"`. Especificando *GhostableInLibrary* significa que o arquivo será adicionado à biblioteca de documentos no SharePoint junto com um item de lista para acompanhar o arquivo quando ele é adicionado à biblioteca. Especificando *Ghostable* faz com que o arquivo a ser adicionado ao SharePoint fora da biblioteca de documentos.|  
  
 Cada arquivo que você deseja implantar requer uma `<File>` entrada elemento Elements.  
  
## <a name="see-also"></a>Consulte também  
 [Como: incluir arquivos usando um módulo](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [como: configurar um arquivo](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Criando Web Parts do SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  