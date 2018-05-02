---
title: Typedefs do Visual C++ no Designer de Classe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: a0c854fabdc18337b806cd64733de1d0c88758c5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="visual-c-typedefs-in-class-designer"></a>Typedefs do Visual C++ no Designer de Classe

As instruções typedef criam uma ou mais camadas de indireção entre um nome e seu tipo subjacente. O **Designer de Classe** é compatível com tipos de typedef do C++ que são declarados com a palavra-chave `typedef`, por exemplo:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Então, você pode usar esse tipo para declarar uma instância:

`COORD OriginPoint;`

Embora seja possível declarar um typedef sem um nome, o **Designer de Classe** não usará o nome da marca que você especificar. Ele usará o nome que o Modo de Exibição de Classe gerar. Por exemplo, a declaração a seguir é válida, mas ela aparece no **Modo de Exibição de Classe** e no **Designer de Classe** como um objeto chamado **__unnamed**:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

Para obter mais informações sobre o uso do tipo `typedef`, confira [Typedefs](/cpp/aliases-and-typedefs-cpp#typedefs).

Uma forma de typedef do C++ tem a forma do tipo especificado no typedef. Por exemplo, se a fonte declara `typedef class`, a forma terá cantos arredondados e o rótulo **Classe**. Para `typedef struct`, a forma tem cantos quadrados e o rótulo **Struct**.

Classes e estruturas podem ter typedefs aninhados declarados dentro deles. Sendo assim, formas de classe e de estrutura podem mostrar declarações de typedef aninhado como formas aninhadas.

As formas typedef dão suporte aos comandos **Mostrar como Associação** e **Mostrar como Associação de Coleções** no menu de contexto.

A seguir estão alguns exemplos dos tipos typdef com os quais o **Designer de Classe** é compatível:

`typedef type name`

*nome* : *tipo*

typedef

Desenha uma linha de associação conectando-se ao tipo *nome*, se possível.

`typedef void (*func)(int)`

`func: void (*)(int)`

typedef

Typedef para ponteiros de função. Nenhuma linha de associação é desenhada.

O **Designer de Classe** não exibirá um typedef se seu tipo de origem for um ponteiro de função.

```cpp
typedef int MyInt;
class A {
   MyInt I;
};
```

`MyInt: int`

typedef

`A`

Classe

Desenha uma linha de associação apontando da forma do tipo de origem para a forma do tipo de destino.

`Class B {};`

`typedef B MyB;`

`B`

Classe

`MyB : B`

typedef

Ao clicar com o botão direito do mouse em uma forma de typedef e clicar em **Mostrar como Associação** exibe o typedef ou a classe e uma linha **Alias de** unindo as duas formas (semelhante a uma linha de associação).

`typedef B MyB;`

`typedef MyB A;`

`MyBar : Bar`

typedef

Mesmo que anterior.

```cpp
Class B {};
typedef B MyB;

class A {
   MyB B;
};
```

`B`

Classe

`MyB : B`

typedef

`A`

Classe

`MyB` é uma forma de typedef aninhado.

`#include <vector>`

`...`

`using namespace std;`

`...`

`typedef vector<int> MyIntVect;`

`vector<T>`Classe

`MyIntVect : vector<int>`

typedef

`class B {};`

`typedef B MyB;`

`class A : MyB {};`

`MyB : B`

typedef

-> B

`B`

`A`

Classe

-> MyB

O **Designer de Classe** não é compatível com a exibição deste tipo de relação usando um comando de menu de contexto.

`#include <vector>`

`Typedef MyIntVect std::vector<int>;`

`Class MyVect : MyIntVect {};`

`std::vector<T>`

Classe

`MyIntVect : std::vector<int>`

typedef

`MyVect`

Classe

-> MyIntVect

## <a name="see-also"></a>Consulte também

- [Trabalhando com código do Visual C++](working-with-visual-cpp-code.md)
