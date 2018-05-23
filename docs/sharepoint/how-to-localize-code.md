---
title: 'Como: Localizar código | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3b559239b537be4a57ff0815f67d8c50acb8b1ed
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2018
---
# <a name="how-to-localize-code"></a>Como localizar código
  Código não localizado usa valores de cadeia de caracteres codificada. Para localizar cadeias de caracteres de código, substituí-las por chamadas para <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>, que é um método que faz referência a recursos localizados.  
  
## <a name="localizing-code"></a>Localizando o código  
  
#### <a name="to-localize-code"></a>Para localizar código  
  
1.  Em **Solution Explorer**, abra o menu de atalho para um item de projeto e, em seguida, escolha **adicionar**, **módulo**.  
  
     Escolha o **arquivo de recursos** modelo.  
  
    > [!NOTE]  
    >  Certifique-se de adicionar o arquivo de recurso para um item de projeto do SharePoint para que a propriedade de tipo de implantação está disponível. Essa propriedade é necessária neste procedimento.  
  
2.  Nomeie o arquivo de recurso de idioma padrão de sua escolha concatenada com uma extensão. resx, como MyAppResources.resx.  
  
3.  Repita as etapas 1 e 2 para adicionar arquivos de recursos separado para o item de projeto do SharePoint: um para cada idioma localizado.  
  
     Usar o mesmo nome de base para cada arquivo de recurso localizado, mas adicione a ID da cultura. Por exemplo, nome de um recurso localizado alemão MyAppResources.de-de. resx.  
  
4.  Abra cada arquivo de recurso e adicionar cadeias de caracteres localizadas. Use a mesma cadeia IDs em cada arquivo.  
  
5.  Alterar o valor da **tipo de implantação** propriedade de cada arquivo de recurso para **AppGlobalResource** para fazer com que cada arquivo a ser implantado para a pasta do servidor App_GlobalResources.  
  
6.  Deixe o valor da **ação de compilação** propriedade de cada arquivo como **recurso inserido**.  
  
     Recursos incorporados são compilados na DLL do projeto.  
  
7.  Crie o projeto para criar o recurso DLLs satélite.  
  
8.  No **Package Designer**, escolha o **avançado** guia e, em seguida, adicione o assembly satélite.  
  
9. No **local** caixa, adicione uma pasta de identificação de cultura para o caminho de local, como de-DE\\*nome do Item de projeto*. Resources.  
  
10. Se sua solução já não faz referência a assembly System. Web, adicione uma referência a ele e adicione uma diretiva em seu código para <xref:System.Web>.  
  
11. Localize todas as cadeias de caracteres codificadas em seu código que são visíveis aos usuários, como o texto de interface do usuário, erros e texto da mensagem. Substituí-las por uma chamada para o <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> método usando a seguinte sintaxe:  
  
    ```csharp  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. Escolha a tecla F5 para compilar e executar o aplicativo.  
  
13. No SharePoint, altere o idioma de exibição padrão.  
  
     As cadeias de caracteres localizadas aparecem no aplicativo. Para exibir os recursos localizados, o servidor do SharePoint deve ter um pacote de idiomas instalado que corresponda a cultura do arquivo de recurso.  
  
## <a name="see-also"></a>Consulte também  
 [Localizando soluções do SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Como: localizar um recurso](../sharepoint/how-to-localize-a-feature.md)   
 [Como: localizar marcação ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Como adicionar um arquivo de recurso](../sharepoint/how-to-add-a-resource-file.md)  
  
  