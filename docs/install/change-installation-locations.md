---
title: Alterar locais de instalação no Visual Studio 2017
description: Saiba como reduzir o volume de instalação na unidade do sistema mudando o local do cache de download, dos componentes compartilhados, dos SDKs e das ferramentas para unidades diferentes.
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- move installation files to different drives
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0460e61fea7e617e497a46c55f8af811ba2e24fe
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="change-the-installation-locations-in-visual-studio-2017"></a>Alterar os locais de instalação no Visual Studio 2017

**Novidade no 15.7**: é possível reduzir o volume de instalação na unidade do sistema movendo o cache de download, os componentes compartilhados, os SDKs e as ferramentas para unidades diferentes.

Veja como.

1. Ao instalar o Visual Studio, escolha a guia **Opções de instalação**.

  ![Visual Studio 2017 – Alterar o local de instalação](media/installation-options-by-location.png "Alterar o local de instalação")

  > [!IMPORTANT]
  > Se você interromper a instalação e retomá-la mais tarde, o Visual Studio continuará de onde parou. Ou seja, o progresso da instalação se aplicará ao que ainda precisa ser baixado e instalado e não iniciará da contagem anterior.

2. Na seção **Visual Studio**, aceite os valores padrão. Isso instala o produto principal e inclui arquivos específicos desta versão do Visual Studio.

 > [!IMPORTANT]
 > Se a unidade do sistema é uma SSD (unidade de estado sólido), este é o motivo para recomendarmos que você aceite o local padrão na unidade do sistema: ao desenvolver com o Visual Studio, você lê e grava em muitos arquivos, o que aumenta a atividade de E/S de disco.  É melhor escolher sua unidade mais rápida para lidar com a carga.

2. Na seção **Cache de download**, decida se você deseja manter o cache de download e, em seguida, marque ou desmarque **Manter cache de download** de acordo com sua opção. <br><br>Se você optar por não manter o cache de download, o local será usado somente temporariamente. Além disso, essa ação não afetará ou excluirá arquivos de instalações anteriores. (Para limpar todos os pacotes de instalação, você precisará modificar as instalações anteriores separadamente.)

3. Na seção **Cache de download**, especifique a unidade na qual deseja armazenar os manifestos e os arquivos de instalação. <br><br>Por exemplo, se você selecionar a carga de trabalho **Desenvolvimento para desktop com C++** o tamanho temporário necessário será de 1,58 GB na unidade do sistema, que será liberado assim que a instalação for concluída.

 > [!NOTE]
 > Primeiro, os arquivos são baixados em uma pasta temporária na unidade do sistema e, posteriormente, são excluídos após o Visual Studio verificar e, em seguida, movê-los para a pasta de cache de download. Se você optar por manter o cache de download em uma unidade diferente, o Visual Studio ainda precisará de espaço em disco equivalente ao tamanho do cache de download na unidade do sistema.
 > [!IMPORTANT]
 > O local é definido com sua primeira instalação e não pode ser alterado posteriormente usando a interface do usuário do instalador. Em vez disso, você precisará [usar parâmetros de linha de comando](use-command-line-parameters-to-install-visual-studio.md) para mover o cache de download

4. Na seção **Componentes compartilhados, SDKs e ferramentas**, especifique a unidade na qual você deseja armazenar os arquivos compartilhados pelas instalações do Visual Studio lado a lado. SDKs e ferramentas que permitem que o instalador do Visual Studio altere seu local de instalação também são armazenados nesse diretório.

 > [!NOTE]
 > Há algumas ferramentas e SDKs que têm regras diferentes sobre onde podem ser instalados. (Essas ferramentas e SDKs ainda serão instalados em sua unidade do sistema, mesmo que você escolha outro local.)

## <a name="get-support"></a>Obter suporte

Às vezes, as coisas podem dar errado. Se a instalação do Visual Studio falhar, confira a página [Solução de problemas de instalação e de atualização do Visual Studio 2017](troubleshooting-installation-issues.md) para obter ajuda. Você também pode contatar nosso [chat ao vivo](https://www.visualstudio.com/vs/support/#talktous) (somente em inglês) para obter ajuda na instalação. Para obter mais informações, confira a [página “Fale Conosco” do Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aqui estão algumas outras opções de suporte:

* Você pode nos relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), exibida no Instalador do Visual Studio e no IDE do Visual Studio.
* Você pode compartilhar uma sugestão de produto conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Você pode acompanhar os problemas do produto e encontrar respostas na [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) (Comunidade de desenvolvedores do Visual Studio).
* Também é possível interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio). (Esta opção requer uma conta do [GitHub](https://github.com/).)

## <a name="see-also"></a>Consulte também

* [Instalar o Visual Studio 2017](install-visual-studio.md)
* [Atualizar o Visual Studio 2017](update-visual-studio.md)
* [Modificar o Visual Studio 2027](update-visual-studio.md)
* [Desinstalar o Visual Studio 2017](uninstall-visual-studio.md)
