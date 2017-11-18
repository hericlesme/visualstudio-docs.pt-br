---
title: "Validação de quadros de gráficos | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9312ad8a96c5829aae21c87e78a0d5f2f0db1b35
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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
Evento | O evento associado com o erro ou aviso.

## <a name="see-also"></a>Consulte também  
[Diagnóstico de gráficos (depuração DirectX Graphics)](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->