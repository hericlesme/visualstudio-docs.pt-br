---
title: Como atualizar modelos existentes | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0fffcc55953e394c5efd00b86949f04474a66111
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-update-existing-templates"></a>Como atualizar modelos existentes
Depois de criar um modelo e compactar os arquivos em um arquivo .zip, modifique o modelo. É possível fazer isso alterando manualmente os arquivos no modelo ou exportando um novo modelo de um projeto com base no modelo.  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Usando o Assistente para Exportar de Modelo para atualizar um modelo existente  
O Visual Studio fornece um assistente **Exportar Modelo** que pode ser usado para atualizar um modelo existente.  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>Para usar o Assistente Exportar Modelo para atualizar um modelo existente  
  
1.  Abra a caixa de diálogo **Novo Projeto**, escolhendo **Arquivo**, **Novo**, **Projeto**.  
  
2.  Selecione o modelo que deseja atualizar, insira um nome e um local para o projeto e escolha **OK**.  
  
3.  Modifique o projeto no Visual Studio.  
  
4.  No menu **Projeto**, escolha **Exportar Modelo**.  

    O **Assistente para Exportar Modelo** é aberto.  

5.  Siga os prompts no assistente para exportar o modelo como um arquivo .zip.  

6.  Exclua o arquivo .zip de modelo antigo.  
  
## <a name="manually-updating-an-existing-template"></a>Atualizar manualmente um modelo existente  
Você pode atualizar um modelo existente fora do Visual Studio modificando os arquivos no arquivo .zip compactado.  
  
#### <a name="to-manually-update-an-existing-template"></a>Para atualizar manualmente um modelo existente  
  
1.  Localize o arquivo .zip que contém o modelo. Por padrão, esse arquivo está localizado em %USERPROFILE%\Documentos\Visual Studio \<versão\>\Meus Modelos Exportados\.  
  
2.  Extraia o arquivo .zip.  
  
3.  Modifique ou exclua os arquivos de modelo atuais ou adicione novos arquivos ao modelo.  
  
4.  Abra, modifique e salve o arquivo XML .vstemplate para tratar o comportamento atualizado ou novos arquivos.  

    Para obter mais informações sobre o esquema .vstemplate, consulte [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md). Para obter mais informações sobre o que você pode parametrizar nos arquivos de origem, consulte [Parâmetros do Modelo](../ide/template-parameters.md).  
  
5.  Selecione os arquivos em seu modelo, clique com o botão direito do mouse, escolha **Enviar Para** e, em seguida, escolha **Pasta Compactada (zipada)**.  

    Os arquivos selecionados são compactados em um arquivo .zip.  
  
6.  Coloque o novo arquivo .zip no mesmo diretório do antigo arquivo .zip.  
  
7.  Exclua os arquivos de modelo extraídos e o arquivo .zip de modelo antigo.  
  
8.  Inicie uma instância elevada do prompt de comando do desenvolvedor:  

  1. No menu Iniciar, navegue até **Visual Studio \<versão\>**, **Prompt de comando do desenvolvedor**.  

  2. No menu de contexto (acessado com o clique do botão direito do mouse), escolha **Mais**, **Executar como administrador**.  
  
9. Execute o seguinte comando: `devenv /installvstemplates`.  
  
## <a name="see-also"></a>Consulte também  
[Personalizando modelos](../ide/customizing-project-and-item-templates.md)   
[Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)   
[Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
[Parâmetros de modelo](../ide/template-parameters.md)   
[Como criar kits de início](../ide/how-to-create-starter-kits.md)