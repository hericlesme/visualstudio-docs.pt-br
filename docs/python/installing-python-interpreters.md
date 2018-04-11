---
title: Selecionar e instalar interpretadores do Python | Microsoft Docs
description: Uma lista completa de interpretadores do Python que têm suporte no Visual Studio com instruções breves sobre onde localizar os instaladores.
ms.custom: ''
ms.date: 02/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 3b8d1bf4f0ac6c66222f86e73b7c18cfdceb3354
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="installing-python-interpreters"></a>Instalar interpretadores do Python

Por padrão, a instalação da carga de trabalho de desenvolvimento do Python no Visual Studio 2017 também instala o Python 3 (64 bits). Como opção, você pode optar por instalar versões de 32 bits e 64 bits do Python 2, Python 3, Anaconda 2 e Anaconda 3, conforme descrito em [Instalação](installing-python-support-in-visual-studio.md).

Você também pode instalar manualmente qualquer um dos interpretadores listados na tabela abaixo fora do instalador do Visual Studio. Por exemplo, se você instalar o Anaconda 3 antes de instalar o Visual Studio, não será necessário instalar novamente usando o instalador do Visual Studio.

Para o **Visual Studio 2015 e versões anteriores**, é necessário instalar manualmente um dos interpretadores.

O Visual Studio (todas as versões) detecta automaticamente cada interpretador Python instalado e seu ambiente verificando o Registro (seguindo [PEP 514 - Registro do Python no Registro do Windows](https://www.python.org/dev/peps/pep-0514/)).

Se o Visual Studio não detectar um ambiente instalado, confira [Identificar manualmente um ambiente existente](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment).

O Visual Studio mostra todos os ambientes conhecidos na [janela Ambientes de Python](managing-python-environments-in-visual-studio.md) e detecta automaticamente as atualizações para interpretadores existentes.

| Interpretador | Descrição |
| --- | --- |
| [CPython](https://www.python.org/) | O interpretador “nativo” e mais usado, disponível em versões de 32 e 64 bits (o recomendado é 32 bits). Inclui os últimos recursos de linguagem, a compatibilidade máxima com pacotes do Python, suporte de depuração completo e interoperabilidade com o [IPython](http://ipython.org/). Consulte também: [Devo usar o Python 2 ou 3?](http://wiki.python.org/moin/Python2orPython3). Observe que o Visual Studio 2015 e anteriores não são compatíveis com o Python 3.6 e podem resultar no erro "Versão do python 3.6 sem suporte". Use o Python 3.5 ou anteriores. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Uma implementação do .NET do Python, disponível em versões de 32 e 64 bits, que fornece interoperabilidade do C#/F#/Visual Basic, acesso às APIs do .NET, depuração padrão do Python (mas não a depuração de modo misto do C++) e a depuração mista do IronPython/C#. No entanto, o IronPython não dá suporte a ambientes virtuais. |
| [Anaconda](https://www.continuum.io) | Uma plataforma aberta de ciência de dados do Python, além de incluir a última versão do CPython e a maioria dos pacotes difíceis de serem instalados. Recomendamos usá-la, caso você esteja indeciso sobre qual plataforma deverá usar. |
| [PyPy](http://www.pypy.org/) | Uma implementação JIT de rastreamento de alto desempenho do Python que é boa para programas de execução longa e situações em que é possível identificar problemas de desempenho, mas em que não é possível encontrar outras resoluções. Funciona com o Visual Studio, mas com suporte limitado para recursos de depuração avançados. |
| [Jython](http://www.jython.org/) | Uma implementação do Python na JVM (Máquina Virtual Java). Semelhante ao IronPython, o código em execução no Jython pode interagir com classes e bibliotecas Java, mas poderá não usar várias bibliotecas destinadas ao CPython. Funciona com o Visual Studio, mas com suporte limitado para recursos de depuração avançados. |

Para os desenvolvedores que desejam fornecer novas formas de detecção para ambientes do Python, consulte [Detecção para ambiente da PTVS](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (github.com).

## <a name="moving-an-interpreter"></a>Mover um interpretador

Se você mover um interpretador existente para um novo local usando o sistema de arquivos, o Visual Studio não detectará automaticamente a alteração.

- Se você tiver especificado originalmente o local do interpretador por meio da janela **Ambientes de Python**, edite ambiente usando a guia **Configurar** nessa janela para identificar o novo local. Confira [Identificar manualmente um ambiente existente](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment).

- Se você instalou o interpretador usando um programa de instalação, use as etapas a seguir para reinstalar o interpretador no novo local:

  1. Restaure o interpretador do Python para o local original.
  2. Desinstale-o usando o instalador, que limpa as entradas do Registro.
  3. Reinstale o interpretador no local desejado.
  4. Reinicie o Visual Studio, que deve detectar automaticamente o novo local em vez de o local antigo.

Esse processo garante que as entradas do Registro que identificam o local do interpretador, usado pelo Visual Studio, sejam atualizadas corretamente. O uso de um instalador também lida com outros efeitos colaterais que possam existir.

## <a name="see-also"></a>Consulte também

- [Gerenciar ambientes do Python](managing-python-environments-in-visual-studio.md)
- [Selecionar um interpretador para um projeto](selecting-a-python-environment-for-a-project.md)
- [Usando requirements.txt para dependências](managing-required-packages-with-requirements-txt.md)
- [Caminhos de pesquisa](search-paths.md)
- [Referência à janela Ambientes do Python](python-environments-window-tab-reference.md)