---
title: "Adicionar itens para o adicionar novo Item caixas de diálogo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f7058d097ab3eb6faeb8acf96b98ae6346887361
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Adicionar itens para o adicionar novo Item caixas de diálogo
O processo para adicionar itens para o **Adicionar Novo Item** caixa de diálogo começa com as chaves do registro. Conforme mostrado nas seguintes entradas do registro, a seção de AddItemTemplates contém o caminho do e o nome do diretório em que os itens disponibilizada no **Adicionar Novo Item** caixa de diálogo são colocados.  
  
> [!NOTE]
>  A tabela imediatamente após o segmento de código contém informações adicionais sobre a entrada do registro.  
  
 Esta seção está localizada em [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects].  
  
 O primeiro GUID é o CLSID para projetos desse tipo; o GUID segundo indica o tipo de projeto registrado para os modelos de adicionar itens.  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \1  
  
 @="#6"  
  
 "TemplatesDir"="\<caminho de instalação do SDK do Visual Studio\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems"  
  
 "SortPriority" = dword:00000064  
  
|Nome|Tipo|Dados (a partir do arquivo. rgs)|Descrição|  
|----------|----------|-----------------------------|-----------------|  
|@ (Padrão)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY %|ID de recurso para **Adicionar Item** modelos.|  
|Val TemplatesDir|REG_SZ|%TEMPLATE_PATH%\ SomeProjectItems|O caminho dos itens de projeto exibido na caixa de diálogo para o **Adicionar Novo Item** assistente.|  
|Val SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)])|Determina a ordem de classificação no nó de árvore de arquivos exibidos no **Adicionar Novo Item** caixa de diálogo.|  
  
> [!NOTE]
>  Os GUIDS para os tipos de projeto do Visual c# e Visual Basic são da seguinte maneira:[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 O diretório listado para TemplateDirs, que é % TEMPLATE_PATH%\SomeProjectItems, é o nó no lado esquerdo do **Adicionar Novo Item** árvore da caixa de diálogo. Elementos adicionais na árvore de baseiam-se o subdiretório no diretório raiz. Os arquivos disponíveis para serem adicionados ao projeto são os itens no painel à direita do **Adicionar Novo Item** caixa de diálogo.  
  
 Normalmente, essa pasta conterá os arquivos de modelo para o projeto como um modelo de HTML ou arquivo. cpp e todos os arquivos. vsz para iniciar assistentes. Para controlar como os itens são exibidos, você também pode incluir arquivos de .vsdir para localização de ícones e nomes de diretório. A cadeia de caracteres localizada é a legenda que aparece na caixa de diálogo que representa este nó na árvore de caixa de diálogo Adicionar Novo Item.  
  
 No entanto, você não precisa ter tudo em um arquivo de .vsdir. Você pode ter um arquivo de .vsdir para cada item no diretório. Para obter mais informações, consulte [Assistente (. Arquivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) e [descrição do modelo do diretório (. Arquivos Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  Os arquivos .vsdir nos diretórios de modelo são opcionais. Se você quiser apenas para colocar um elemento de projeto no diretório e exibi-lo no **Adicionar Novo Item** caixa de diálogo, você pode colocar esse arquivo no diretório de modelos especificado na instrução TemplatesDir. O arquivo, em seguida, será exibido no painel à direita do **Adicionar Novo Item** caixa de diálogo para o projeto. No entanto, se você quiser exibir uma legenda localizada para o arquivo ou um ícone, você deve incluir pelo menos um arquivo de .vsdir no diretório de modelos.  
  
## <a name="grouping-project-items"></a>Itens de projeto de agrupamento  
 Se deseja incluir grupos de modelos em pastas de **Adicionar Novo Item** árvore da caixa de diálogo, você deve ter subpastas sob o diretório raiz do modelo com os itens nelas. Quando o **Adicionar Novo Item** caixa de diálogo é exibida aos usuários, eles também Consulte subpastas e ser capaz de selecionar os elementos do projeto deles.  
  
 A prioridade de classificação no segmento de código determina onde esse diretório modelo será criado na árvore em relação a outros elementos do nó de árvore. Para o **Adicionar Novo Item** caixa de diálogo, a prioridade de classificação é tudo o que você deve incluir para que os itens serão exibidos no local correto na caixa de diálogo.  
  
 Você também pode implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interface para filtrar o que é exibido o **Adicionar Novo Item** caixa de diálogo. Ao implementar esta interface, você pode definir o diretório de um modelo em disco que contém, por exemplo, 50 arquivos de modelo e o assistente. Dessa forma, você pode ter diferentes tipos de projeto com 20 arquivos que pertencem a um tipo de projeto, os 30 arquivos que pertencem a outro tipo de projeto e todos os arquivos disponíveis em um tipo geral de projeto. Dessa maneira, dependendo de qual projeto modelo for criado, você pode exibir um conjunto diferente de arquivos de modelo.  
  
 Por exemplo, em um projeto do Visual Basic, você pode ter projetos da Web e projetos de cliente. Formulários da Web não são itens úteis para adicionar a um projeto de cliente e formulários do windows não são itens úteis para adicionar a um projeto do servidor Web. Portanto, você pode criar um diretório de modelo que contém todos os arquivos para os dois tipos de projeto. Em seguida, implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, você pode ocultar itens que não devem ser exibidos com base no tipo de projeto ou configurações de projeto no projeto.  
  
## <a name="filtering-project-items"></a>Filtrar itens de projeto  
 `IVsFilterAddProjectItemDlg2`fornece filtragem dos elementos na árvore (painel esquerdo) e arquivos de projeto (painel direito) das seguintes maneiras:  
  
-   Os nomes localizados (legendas exibidas na caixa de diálogo que está contida no arquivo .vsdir) fornecidas pelo `IVsFilterAddProjectItemDlg`.  
  
-   Os nomes reais dos arquivos e pastas no disco (não localizado — nenhum arquivo .vsdir) fornecidas pelo `IVsFilterAddProjectItemDlg`.  
  
-   Por categoria, fornecida pelo `IVsFilterAddProjectItemDlg2`.  
  
 Para filtrar por categoria, forneça uma cadeia de caracteres da categoria a um item no arquivo .vsdir, como "Formulário da Web" ou "Item do cliente" no Visual Basic. O código da caixa de diálogo, em seguida, recupera a classificação de categoria do arquivo .vsdir e passá-lo para você. Você pode passar essas informações para sua implementação de `IVsFilterAddProjectItemDlg2` para filtrar o **Adicionar Novo Item** caixa de diálogo categorias. Você também pode filtrar itens para páginas da Web ou como casos de cliente do aplicativo Win32. Além disso, você pode identificar [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] marcados itens como Microsoft Foundation Classes (MFC) ou itens de biblioteca (ATL) do modelo ativo. Ao identificar esses itens, o sistema de projeto pode definir suas próprias classificações para que o sistema pode ser filtrado com base nas categorias e classificações.  
  
 Se você implementar essa funcionalidade de filtro, você não precisa mapear uma tabela de cada item que deve ser oculto. Você pode simplesmente classificar itens em tipos e inserir as classificações .vsdir arquivo ou arquivos. Em seguida, você pode ocultar qualquer um dos itens que têm uma classificação específica ao implementar a interface. Dessa forma, você pode fazer os itens a **Adicionar Novo Item** dinâmico da caixa de diálogo com base no estado dentro do projeto.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Registro de modelos de projeto e Item](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATIDs para objetos que normalmente são usados para estender a projetos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Adicionando o projeto e modelos de Item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Descrição do modelo do diretório (. Arquivos de Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Arquivo do assistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)