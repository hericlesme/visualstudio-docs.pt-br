---
title: 'Etapa 9: Experimentar outros recursos'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc842af3723a8b056d1de684bd798f4fda37cff8
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="step-9-try-other-features"></a>Etapa 9: Experimentar outros recursos
Para aprender mais, tente alterar os ícones e as cores, adicionar um temporizador de jogo e adicionar sons. Para tornar o jogo mais desafiador, tente aumentar o tabuleiro e ajustar o temporizador.  
  
 Para baixar uma versão completa do exemplo, veja [Complete Matching Game tutorial sample (Exemplo de tutorial completo de jogo da memória)](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).  
  
## <a name="to-try-other-features"></a>Para testar outros recursos  

-   Substitua os ícones e as cores pelos de sua preferência.  

    > [!TIP]
    >  Tente observar a propriedade [Forecolor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor.aspx) do rótulo.  

-   Adicione um temporizador de jogo que controla em quanto tempo o jogador ganha uma partida.  

    > [!TIP]
    >  Para isso, você pode adicionar um rótulo para exibir o tempo decorrido no formulário acima de <xref:System.Windows.Forms.TableLayoutPanel> e adicionar outro temporizador ao formulário para controlar o tempo. Use código para iniciar o temporizador quando o jogador começar o jogo e para interromper o temporizador depois que os dois últimos ícones forem encontrados.  

-   Adicione um som para quando o jogador encontrar um par, outro som para quando o jogador selecionar dois ícones que são diferentes e um terceiro som para quando o programa ocultar os ícones novamente.  

    > [!TIP]
    >  Para reproduzir sons, você pode usar o namespace <xref:System.Media>. Veja [Reproduzir sons no aplicativo Windows Forms (C#)](http://youtu.be/qOh4ooHg1UU) ou [Como reproduzir áudio no Visual Basic](http://youtu.be/-4oPDeQrtMs) para obter mais informações.  
  
-   Torne o jogo mais difícil aumentando o tamanho do tabuleiro.  

    > [!TIP]
    >  Você precisará fazer mais do que apenas adicionar linhas e colunas ao TableLayoutPanel – você também precisará considerar o número de ícones criados.  

-   Torne o jogo mais desafiador ocultando o primeiro ícone se o jogador demorar demais para reagir e não escolher o segundo ícone antes do término de um determinado tempo.  

## <a name="to-continue-or-review"></a>Para continuar ou revisar  
  
-   Se você estiver com dificuldades ou tiver dúvidas quanto à programação, tente publicar sua dúvida em um dos fóruns do MSDN. Veja [Fórum do Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) e [Fórum do Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
-   Há recursos de aprendizagem por vídeo excelentes e gratuitos disponíveis para você. Para saber mais sobre programação no Visual Basic, veja [Visual Basic Fundamentals: Development for Absolute Beginners (Conceitos básicos do Visual Basic: desenvolvimento para iniciantes absolutos)](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Para saber mais sobre programação no Visual C#, veja [C# Fundamentals: Development for Absolute Beginners (Conceitos básicos do C#: desenvolvimento para iniciantes absolutos)](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).  
  
-   Para retornar à etapa anterior do tutorial, veja [Etapa 8: Adicionar um método para verificar se o jogador ganhou](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
