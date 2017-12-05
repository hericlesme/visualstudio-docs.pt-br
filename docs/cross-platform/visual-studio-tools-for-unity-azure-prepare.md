---
title: "Passo a passo da preparação do Azure para as Ferramentas do Visual Studio para Unity | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: B921C2AC-B5D6-4B24-918E-511F83D57275
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 92f85e39d0f643e896457cae48ab10aa0446dfcd
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="prepare-the-development-environment"></a>Preparar o ambiente de desenvolvimento

Há alguns pré-requisitos para usar o SDK do Azure Mobile Client no Unity.

## <a name="download-and-install-unity-2017"></a>Baixar e instalar o Unity 2017

O Unity 2017.1 ou versões posteriores é necessário. Todos os planos do Unity funcionam com o passo a passo, incluindo o plano Pessoal gratuito. Baixe o Unity em https://store.unity.com/.

## <a name="download-and-install-visual-studio-2017"></a>Baixar e instalar o Visual Studio 2017

O passo a passo requer o Visual Studio 2017 15.3 e versões posteriores, com o desenvolvimento de jogos com carga de trabalho do Unity. Todas as edições do Visual Studio 2017 funcionam com o passo a passo, incluindo a edição Community gratuita.

1. Baixe o Visual Studio 2017 em https://www.visualstudio.com/.

2. Instale o Visual Studio 2017 e lembre-se de habilitar a carga de trabalho de **Desenvolvimento de jogos com Unity**.

 ![Selecionar a carga de trabalho do Unity](media/vstu_azure-prepare-dev-environment-image0.png)

 > [!NOTE]
 > Caso o Visual Studio 2017 já esteja instalado, é possível exibir e modificar cargas de trabalho executando o Instalador do Visual Studio.

## <a name="create-a-new-3d-unity-project"></a>Criar um novo projeto 3D do Unity

Inicie o Unity e crie um novo projeto 3D.

![Criar um novo projeto do Unity](media/vstu_azure-prepare-dev-environment-image1.png)

## <a name="set-the-script-editor-to-visual-studio-preview-2017"></a>Definir o editor de scripts para a versão prévia do Visual Studio 2017

É possível que você já tenha o Visual Studio 2017 definido como editor de scripts externo do Unity, mas é importante garantir que a versão prévia 15.3 seja selecionada.

1. No menu **Editar** do Unity, clique em **Preferências...**.

  ![Abrir o menu Preferências](media/vstu_azure-prepare-dev-environment-image1.2.png)

2. Quando a janela Preferências do Unity for exibida, selecione a guia **Ferramentas Externas** no lado esquerdo.

3. No menu suspenso **Editor de Scripts Externo**, selecione **Visual Studio 2017**.

  ![Definir o editor de scripts externo](media/vstu_azure-prepare-dev-environment-image3.png)

## <a name="change-the-unity-scripting-runtime-to-net-46"></a>Alterar o tempo de execução de script do Unity para .NET 4.6
O passo a passo requer o .NET 4.6 para usar o SDK do Azure Mobile Client e suas dependências.

1. No menu **Arquivo** do Unity, clique em **Configurações de Build...**.

  ![Abrir as configurações de build](media/vstu_azure-prepare-dev-environment-image4.png)

2. Clique no botão **Configurações do Player...**.

  ![Abrir as configurações do player](media/vstu_azure-prepare-dev-environment-image5.png)

3. As Configurações do Player são abertas na janela Inspetor do Unity. No cabeçalho **Configuração**, clique no menu suspenso **Versão do Tempo de Execução de Script** e selecione **Experimental (Equivalente ao .NET 4.6)**. Uma caixa de diálogo será exibida solicitando a reinicialização do Unity. Selecione **Reiniciar**.

  ![Selecionar o .NET 4.6](media/vstu_azure-prepare-dev-environment-image6.png)

## <a name="add-a-reference-to-systemnethttpdll"></a>Adicionar uma referência a System.Net.Http.dll

O tempo de execução de script equivalente ao .NET 4.6 do Unity permite o uso do pacote System.Net.Http, exigido pelo SDK do Azure Mobile Client. O arquivo DLL está incluído no Unity, no entanto, uma referência deve ser adicionada para usá-lo.

1. Na janela Projeto do editor do Unity, **clique com o botão direito do mouse** na pasta **Ativos** e selecione **Mostrar no Explorer**.

  ![Mostrar pasta Ativos no Explorer](media/vstu_azure-prepare-dev-environment-image7.png)

2. Na janela Explorer exibida, clique duas vezes no diretório **Ativos** para abri-lo.

3. No diretório Ativos, **clique com o botão direito do mouse** e selecione **Novo > Documento de Texto**.

4. Abra o novo documento de texto em um editor de texto e adicione a linha: `-r:System.Net.Http.dll`

5. Salve o documento e feche-o.

4. Renomeie o novo documento de texto como "**mcs.rsp**" e não se esqueça de excluir a extensão de arquivo .txt.

  * Caso suas extensões de arquivos estejam ocultas, será necessário alterar as opções de exibição de pasta para mostrá-las.
  * Abra o menu Iniciar e digite "opções de pasta" no campo de pesquisa. Selecione "**Opções do Explorador de Arquivos**".
  * Selecione a guia **Exibição** e, nas configurações avançadas, verifique se "**Ocultar as extensões dos tipos de arquivo conhecidos**" está desmarcada.

    ![Mostrar pasta Ativos no Explorer](media/vstu_azure-prepare-dev-environment-image8.png)

Após concluir essas etapas, você deve ter um arquivo chamado **mcs.rsp** com a linha `r:System.Net.Http.dll` no diretório **Ativos** raiz do projeto do Unity.

>[!NOTE]
> A funcionalidade de referência exige as Ferramentas do Visual Studio para Unity 3.3 e versões posteriores, que estão incluídas na carga de trabalho Visual Studio 15.3 + Unity. Se esta etapa não funcionar para você, verifique se a versão correta das VSTU está instalada.

## <a name="add-the-newtonsoftjson-nuget-package-to-your-project"></a>Adicionar o pacote NuGet Newtonsoft.Json ao projeto

O SDK do Azure Mobile Client exige o pacote Newtonsoft.Json. Infelizmente, o Unity não tem suporte para o NuGet. Se você abrir um projeto do Unity no Visual Studio e adicionar um pacote com NuGet, o Unity o apagará na próxima vez que o projeto for aberto no editor do Unity. No entanto, os pacotes do NuGet podem ser adicionados manualmente a um projeto do Unity.

1. Crie uma nova pasta no diretório Ativos do projeto do Unity chamada "**Pacotes NuGet**". Isso é somente para organização.

2. Acesse https://www.nuget.org/packages/Newtonsoft.Json/ e clique no botão **Download Manual**. Baixe o arquivo .nupkg.

  ![Mostrar pasta Ativos no Explorer](media/vstu_azure-prepare-dev-environment-image9.png)

3. Localize o arquivo baixado e altera sua extensão de .nupkg para **.zip**. Assim, será possível exibir e extrair os arquivos incluídos, como em qualquer arquivo zip.

4. Abra ou extraia o diretório zip e navegue até **\lib\net45**.

5. Copie o arquivo **Newtonsoft.Json.dll** para o diretório **Ativos\NuGet Packages** do projeto do Unity.

## <a name="add-the-azure-mobile-client-sdk-nuget-package-to-your-project"></a>Adicionar o pacote NuGet do SDK do Azure Mobile Client ao projeto

O SDK do Azure Mobile Client contém funções que facilitam a leitura e a gravação no Azure Easy Tables.

1. Acesse https://www.nuget.org/packages/Microsoft.Azure.Mobile.Client/ e clique no botão **Download Manual**. Baixe o arquivo .nupkg.

2. Localize o arquivo baixado e altera sua extensão de .nupkg para **.zip**. Assim, será possível exibir e extrair os arquivos incluídos, como em qualquer arquivo zip.

3. Abra ou extraia o diretório zip e navegue até **\lib\net45**.

4. Copie o arquivo **Microsoft.Azure.Mobile.Client.dll** para o diretório **Ativos\NuGet Packages** do projeto do Unity.

>[!WARNING]
> Após concluir essas etapas, não se esqueça de reiniciar o Unity e o Visual Studio, ou o InteliSense pode não reconhecer os pacotes recém-adicionados.

## <a name="conclusion"></a>Conclusão

Depois de concluir essas etapas, o projeto do Unity estará configurado para usar o SDK do Azure Mobile Client. É possível testar o ambiente de desenvolvimento criando um novo script em C# no projeto do Unity, abrindo-o no Visual Studio e digitando o seguinte com instruções na parte superior:
```
using System.Net.Http;
using Newtonsoft.Json;
using Microsoft.WindowsAzure.MobileServices;
```

Se o InteliSense detectar essas instruções de uso, a configuração foi concluída corretamente. Se houver erros ou se o InteliSense não reconhecer esses pacotes, tente reiniciar o Unity e o Visual Studio. Se ainda não funcionar, repita as etapas acima.

## <a name="next-step"></a>Próximas etapas

* [Criar classes de modelo de dados](visual-studio-tools-for-unity-azure-data.md)
