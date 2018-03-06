---
title: Usar um arquivo requirements.txt para gerenciar os requisitos do pacote | Microsoft Docs
description: "Você pode usar um arquivo requirements.txt para gerenciar as dependências de um projeto. Se você receber um projeto que contém um arquivo requirements.txt, você pode instalar facilmente essas dependências em uma única etapa."
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 808e7a66d4e0130ee8080b124b33b22561bb2a58
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2018
---
# <a name="managing-required-packages-with-requirementstxt"></a>Gerenciar os pacotes necessários com requirements.txt

Se você estiver compartilhando um projeto com outras pessoas, usando um sistema de compilação ou pretender [publicá-lo no Microsoft Azure](python-azure-cloud-service-project-template.md), precisará especificar os pacotes externos exigidos pelo projeto. A abordagem recomendada é usar um [arquivo requirements.txt](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) que contém uma lista de comandos do PIP que instala as versões necessárias dos pacotes dependentes.

Tecnicamente, qualquer nome de arquivo pode ser usado para acompanhar os requisitos (usando `-r <full path to file>` durante a instalação de um pacote), mas o Visual Studio fornece suporte específico para `requirements.txt`:

- Se você carregou um projeto que contém `requirements.txt` e deseja instalar todos os pacotes listados nesse arquivo, expanda o nó **Ambientes de Python** no **Gerenciador de Soluções** e, em seguida, clique com o botão direito do mouse em um nó de ambiente e selecione **Instalar de requirements.txt**:

    ![Instalar de requirements.txt](media/environments-requirements-txt-install.png)

- Se já tiver todos os pacotes necessários instalados em um ambiente, será possível clicar com o botão direito do mouse nesse ambiente, no Gerenciador de Soluções e selecionar **Gerar requirements.txt** para criar o arquivo necessário. Se o arquivo já existir, será exibido um prompt para como atualizá-lo:

    ![Opções de atualização de requirements.txt](media/environments-requirements-txt-replace.png)

  - **Substituir todo o arquivo** remove todos os itens, comentários e opções existentes.
  - **Atualizar as entradas existentes** detecta os requisitos do pacote e atualiza os especificadores de versão para que eles correspondam à versão instalada.
  - **Atualizar e adicionar entradas** atualiza todos os requisitos encontrados e adiciona todos os outros pacotes ao final do arquivo.

Como os arquivos `requirements.txt` se destinam a congelar os requisitos do ambiente, todos os pacotes instalados são escritos com versões precisas. Usar versões precisas garante que você possa reproduzir facilmente seu ambiente em outra máquina. Os pacotes serão incluídos, mesmo se eles foram instalados com um intervalo de versão, como uma dependência de outro pacote ou com um instalador que não seja o PIP.

Se um pacote não puder ser instalado pelo PIP e for exibido em um arquivo `requirements.txt`, toda a instalação falhará. Nesse caso, edite manualmente o arquivo para excluir esse pacote ou use as [opções do PIP](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) para se referir a uma versão instalável do pacote. Por exemplo, você pode preferir usar [`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) para compilar uma dependência e adicionar o opção `--find-links <path>` ao `requirements.txt`:

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="see-also"></a>Consulte também

- [Gerenciando ambientes do Python no Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selecionar um intérprete para um projeto](selecting-a-python-environment-for-a-project.md)
- [Caminhos de pesquisa](search-paths.md)
- [Referência à janela Ambientes do Python](python-environments-window-tab-reference.md)