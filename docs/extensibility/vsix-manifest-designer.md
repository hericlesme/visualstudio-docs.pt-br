---
title: Designer de manifesto do VSIX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b90f8acd95d913e563ff167e21b743cbffec2ac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="vsix-manifest-designer"></a>Designer de manifesto do VSIX
Modifica um VSIX arquivo de manifesto pacote, que define o comportamento da instalação para uma extensão do Visual Studio.  
  
 O **Designer de manifesto do VSIX** mapeia para o esquema subjacente do VSIX. Cada elemento no esquema pode ser definido usando um controle correspondente no designer. Para obter mais informações sobre o esquema, consulte [2.0 referência do esquema de extensão de VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Para abrir o **Designer de manifesto do VSIX**, localize um arquivo source.extension.vsixmanifest **Solution Explorer**e abra o arquivo. Se o arquivo não contém XML válido, o designer de manifesto não será aberto.  
  
> [!NOTE]
>  Source.Extension.vsixmanifest é enviado para extension.vsixmanifest quando o pacote é criado.  
  
## <a name="uielement-list"></a>Lista UIElement  
 O **Designer de manifesto do VSIX** contém quatro seções que correspondem a esses elementos de nível superior do esquema:  
  
-   Metadados  
  
-   Instalar destinos  
  
-   Ativos  
  
-   Dependências  
  
 A área de título contém os seguintes controles.  
  
 **Nome do produto**  
 Descreve a extensão de nome.  
  
 **ID do produto**  
 Especifica as informações de identificação exclusivo para este pacote.  
  
 **Autor**  
 Especifica o nome do autor da extensão.  
  
 **Versão**  
 Especifica o número de versão da extensão.  
  
 O **metadados** guia contém os seguintes controles.  
  
 **Descrição**  
 Fornece uma descrição de texto da extensão a ser exibida no **Gerenciador de extensões**.  
  
 **Linguagem**  
 Especifica o idioma padrão para o pacote, que corresponde aos dados textuais no manifesto. O `Language` atributo segue a convenção de código localidade common language runtime (CLR) para assemblies de recurso, por exemplo, en-us, en, fr-fr. Por padrão, o valor é neutro; Isso significa que o pacote será executado em qualquer versão de idioma do Visual Studio.  
  
 **Licença**  
 Especifica o arquivo de texto que contém a licença de usuário, se houver.  
  
 **Ícone**  
 Especifica o arquivo de gráfico (. png,. bmp,. JPEG,. ico) que contém o ícone a ser exibido em **Gerenciador de extensões**, se houver um ícone. A imagem de ícone deve ter 32 x 32 pixels ou será redimensionado para essas dimensões. Se nenhum ícone for especificado, **Gerenciador de extensões** usa um ícone padrão.  
  
 **Imagem de visualização**  
 Especifica o arquivo de gráfico (. png,. bmp,. JPEG,. ico) que contém a imagem de visualização a ser exibida no **Gerenciador de extensões**, se houver uma imagem de visualização. A imagem de visualização deve ser 200 x 200 pixels. Se nenhuma imagem de visualização for especificada, **Gerenciador de extensões** usa uma imagem padrão.  
  
 **Marcas**  
 Adiciona as marcas de texto a ser usado para dicas de pesquisa.  
  
 **Notas de Versão**  
 Especifica um arquivo (. txt,. rtf) que contém as notas de versão. Também usa a URL de um site que exibe as notas de versão.  
  
 **Guia de Introdução**  
 Especifica um arquivo (. txt,. rtf) que contém informações sobre como usar a extensão ou o conteúdo do pacote VSIX. Este guia é exibida quando a instalação da extensão estiver concluída. Também usa a URL de um site que exibe o guia.  
  
 **URL para mais informações**  
 Especifica a URL de um site que contém informações adicionais sobre o produto.  
  
 O **instalar destinos** guia contém os seguintes controles.  
  
 **Tipo de instalação**  
 Lista **extensão do Visual Studio** e **SDK de extensão** como tipos de instalação de destino. As opções diferem, dependendo do tipo que você escolher.  
  
 **Extensão do Visual Studio**  
 Lista o **InstallationTarget** elementos que descrevem como o pacote pode ser instalado e em quais produtos Visual Studio para esta extensão pode ser instalada. Cada produto é identificado separadamente por nome e uma versão ou intervalo.  Produtos podem ser adicionados à lista, modificados e excluídos. O nome e a versão de um produto que correspondem ao **Id** e **versão** atributos de associado **InstallationTarget** elemento.  
  
 **Intervalo de versão** é [12.0, 14.0] e usa a notação a seguir:  
  
-   [-inclusivo de versão mínima  
  
-   ]-versão máxima inclusivo  
  
-   (-exclusivo de versão mínima  
  
-   )-versão máxima exclusivo  
  
-   Única versão # - somente a versão especificada  
  
 **SDK de extensão**  
 Especifica uma instalação global que não está no escopo de um produto específico e uma versão. **Identificador de plataforma de destino** é a plataforma, como "Windows", que você deseja. **Versão da plataforma de destino** é a versão, como 8.0, a plataforma de destino. **Nome do SDK** e **SDK versão** é o nome e o número de versão do SDK, respectivamente.  
  
 **Este VSIX é instalado para todos os usuários (requer elevação na instalação)** caixa de seleção  
 Se essa caixa de seleção for selecionada, essa extensão está instalada para todos os usuários; Caso contrário, ele é instalado apenas para o usuário atual.  
  
 **Este VSIX é instalado pelo Windows Installer** caixa de seleção  
 Se essa caixa de seleção for selecionada, essa extensão é instalada pelo Windows Installer (arquivo. msi); Caso contrário, ele é instalado como um pacote do VSIX típico (arquivo .vsix).  
  
 O **ativos** guia contém os seguintes controles.  
  
 **Lista de ativos**  
 Lista os elementos de ativo que descrevem os elementos de extensão ou o conteúdo desse pacote superfícies. Cada extensão ou um elemento de conteúdo é listado separadamente por origem, o tipo e o caminho. Elementos de extensões e o conteúdo podem ser adicionados à lista de, modificados e excluídos. O tipo e o caminho de um elemento de conteúdo ou extensão corresponde do `Type` e `Path` atributos de associado `Asset` elemento. Os seguintes tipos são conhecidos:  
  
-   Microsoft.VisualStudio.Package  
  
-   Microsoft.VisualStudio.MefComponent  
  
-   Microsoft.VisualStudio.ToolboxControl  
  
-   Microsoft.VisualStudio.Samples  
  
-   Microsoft.VisualStudio.ProjectTemplate  
  
-   Microsoft.VisualStudio.ItemTemplate  
  
-   Microsoft.VisualStudio.Assembly  
  
-   Microsoft.ExtensionSDK  
  
 Para adicionar ou editar um ativo, você deve especificar o tipo de ativo, se o ativo é um projeto na solução atual ou um arquivo no sistema de arquivos e o nome do projeto. Você também pode especificar o nome da pasta na qual deve ser inserido.  
  
 Você também pode criar seus próprios tipos e dar-lhes nomes exclusivos.  
  
 O **dependências** guia contém os seguintes controles.  
  
 **Nome, a origem e o intervalo de versão**  
 Lista os elementos de dependência desse pacote, que este pacote depende de outros pacotes. Se um pacote de dependência é especificado, ele deve ser instalado antes de instalar este pacote; Caso contrário, este pacote deve instalá-lo.  
  
 Os pacotes de dependência são especificados pelo identificador, nome, intervalo de versão, fonte e como a dependência é ser resolvido. Cada pacote de dependência é listada separadamente por nome, versão e origem. Os pacotes de dependência podem ser adicionados à lista, modificados e excluídos.  
  
 O identificador deve corresponder a `ID` atributo dos metadados do pacote de dependência. A origem pode ser um projeto na solução atual, uma extensão atualmente instalada ou um arquivo. O **como dependência é resolvida** configuração pode ser o caminho relativo de um pacote aninhado ou a URL do local de download para a dependência. A ID, a versão e a resolução do pacote de dependência correspondem do `Id`, `Version`, e `Location` atributos de associado `Dependency` elemento.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema 2.0 de extensão do VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)