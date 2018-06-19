---
title: Validação de quadros de gráficos | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9732cd3f3440448e5096e71f838d8ebcf20fb13
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473953"
---
# <a name="graphics-frame-validation"></a>Validação de quadro de gráficos
<!-- VERSIONLESS -->
2017 do Visual Studio e maior suporte a **validação de quadro** ferramenta.  A janela do quadro validação exibe erros e avisos associados com a lista de eventos.  Para exibir essa janela, selecione o **exibição > quadro validação** menu.

![Validação de quadro](media/gfx_diag_frame_validation.png)

Clique o **executar validação** botão no canto superior esquerdo para iniciar a análise.  Ele pode levar vários minutos dependendo da complexidade do quadro.  Os dados que aparece aqui é uma combinação de duas fontes: as mensagens que D3D próprio emite quando [camadas do SDK](https://msdn.microsoft.com/library/windows/desktop/ff476881(v=vs.85).aspx) estiver habilitado e os dados que são coletados de estado interno da ferramenta de rastreamento. Uma vez concluído, você verá várias colunas de dados:

**Coluna**|**Descrição**
---|---
ID do evento | ID que é mapeada para uma entrada de [lista de eventos](graphics-event-list.md) janela.
Severidade | Corrupção, erro, aviso, informações ou mensagem.
Categoria | Aplicativo definido, diverso, inicialização, limpeza, compilação, estado de criação, configuração de estado, obtendo estado, execução, manipulação de recursos, sombreador, redundante e não utilizado.
Mensagem | A mensagem associada ao evento.
evento | O evento associado com o erro ou aviso.

## <a name="see-also"></a>Consulte também  
[Diagnóstico de gráficos (depuração DirectX Graphics)](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->