---
title: Trechos de código do Visual C++
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: 0eca50a938312f6c463ff661c83fd90c9218b5ec
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="visual-c-code-snippets"></a>Trechos de código do Visual C++

No Visual Studio, você pode usar trechos de código para adicionar código comumente usado nos seus arquivos de código do C++. Em geral, você pode usar os trechos de código de forma bem parecida com o C#, mas o conjunto de trechos de código padrão é diferente.

Você pode adicionar um trecho de código em um local específico no seu código (inserção) ou envolver algum código selecionado com um trecho de código.

## <a name="inserting-a-code-snippet"></a>Inserindo um trecho de código

Para inserir um trecho de código, abra um arquivo de código do C++ (.cpp ou .h), clique em algum lugar dentro do arquivo e siga um destes procedimentos:

- Clique com o botão direito do mouse para obter o menu de contexto e selecione **Inserir Trecho**

- No menu **Editar / IntelliSense**, selecione **Inserir Trecho**

- Use as teclas de atalho: **Ctrl**+**K**+**X**

Você deve ver uma lista de opções que começam com **#if**. Ao selecionar **#if**, você verá o seguinte código adicionado ao arquivo:

```cpp
#if 0

#endif // 0
```

Em seguida, você pode substituir o 0 pela condição correta.

## <a name="using-a-code-snippet-to-surround-selected-code"></a>Usar um trecho de código para envolver o código selecionado

Para usar um trecho de código para envolver o código selecionado, selecione uma linha (ou várias linhas) e siga um destes procedimentos:

- Clique com o botão direito do mouse para obter o menu de contexto e selecione **Envolver Com**

- No menu **Editar** > **IntelliSense**, selecione **Envolver Com**

- Usando o teclado, pressione: **CTRL**+**K**+**S**

Selecione **#if**. Você deve ver algo parecido com isso:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

Em seguida, você pode substituir o 0 pela condição correta.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>Onde posso encontrar uma lista completa dos trechos de código do C++?

Você pode encontrar a lista completa de trechos de código do C++ indo até o **Gerenciador de Trechos de Código** (no menu **Ferramentas**) e configurando a **Linguagem** para **Visual C++**. Na janela abaixo, expanda **Visual C++**. Você verá os nomes de todos os trechos de código do C++ em ordem alfabética.

Os nomes da maioria dos trechos de código são auto-explicativos, mas alguns nomes podem ser confusos.

## <a name="class-vs-classi"></a>Class versus classi

O trecho **class** fornece a definição de uma classe chamada MyClass, com o construtor e o destruidor padrão apropriado, em que as definições do construtor e do destruidor estão localizadas fora da classe:

```cpp
class MyClass
{
public:
    MyClass();
    ~MyClass();

private:

};

MyClass::MyClass()
{
}

MyClass::~MyClass()
{
}
```

O trecho de código **classi** também fornece a definição de uma classe chamada MyClass, mas o construtor e o destruidor padrão estão definidos dentro da definição de classe:

```cpp
class MyClass
{
public:
    MyClass()
    {
    }

    ~MyClass()
    {
    }

private:

};
```

## <a name="for-vs-forr-vs-rfor"></a>para vs. forr vs rfor

Há três trechos de código **for** diferentes que fornecem diferentes tipos de loops `for`.

O trecho **rfor** fornece um loop for [baseado em intervalo](/cpp/cpp/range-based-for-statement-cpp) (link). Este constructo é preferível em relação aos loops `for` baseados em índice.

```cpp
for (auto& i : v)
{

}
```

O trecho **for** fornece um loop `for` no qual a condição é baseada no comprimento (em `size_t`) de um objeto.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

O trecho **forr** fornece um loop `for` reverso em que a condição é baseada no comprimento (em inteiros) de um objeto.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>O trecho de destruidor (~)

O trecho de destruidor (**~**) apresenta comportamento diferente em diferentes contextos. Se você inserir este trecho dentro de uma classe, ele fornecerá um destruidor para essa classe. Por exemplo, considerando o seguinte código:

```cpp
class SomeClass {

};
```

Se você inserir o trecho de destruidor, ele fornecerá um destruidor para a SomeClass:

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

Se você tentar inserir o trecho de destruidor fora de uma classe, ele fornecerá um destruidor com um nome de espaço reservado:

```cpp
~TypeNamePlaceholder()
{

```

## <a name="see-also"></a>Consulte também

- [Trechos de código](../ide/code-snippets.md)