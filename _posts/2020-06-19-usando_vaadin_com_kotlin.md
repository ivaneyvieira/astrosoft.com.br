---
layout: posts
title: Usando o Vaadin com o Kotlin
date: 2020-06-19 07:27
category: Linguagem
author: Ivaney Vieira de Sales
tags: [kotlin]
classes: wide
---

O Vaadin suporta a linguagem de programação Kotlin através da biblioteca Karibu-DSL , que contém várias extensões para usar o Vaadin com o Kotlin. Talvez o mais importante seja a biblioteca que permite criar a interface do usuário do Vaadin de maneira declarativa usando uma linguagem específica de domínio (DSL).

Para uma rápida introdução à DSL, para ter um formulário com dois campos de entrada de texto, defina-os hierarquicamente sob o initmétodo (um próprio bloco) da seguinte maneira:

```kotlin
@Route("")
class MyView : KComposite() { (1)
    private val root = ui { (2)
        verticalLayout {
            formLayout { (3)
                textField("Name:") { (4)
                    placeholder = "Last name, first name" (5)
                }
                textField("Age:") {
                    width = "5em"
                }
          }
    }
}
```

1. Uma visão normalmente deve estender o KCompositecomponente ou um componente de layout Vaadin (nesse caso, a classe é definida de uma maneira um pouco diferente).
1. A ui {}função cuida de aninhar o VerticalLayoutcomponente, produzido pela verticalLayout{}função DSL, corretamente no KComposite, tornando VerticalLayoutefetivamente o componente raiz da visualização.
1. Um FormLayoutcomponente Vaadin .
1. Um TextFieldcomponente Vaadin com legenda fornecida.
1. Defina os atributos do componente. Por exemplo, definir o valor das placeholderchamadas de propriedade setPlaceholder() no TextFieldcomponente, definir o texto do espaço reservado que é mostrado como uma dica quando não há texto digitado no campo.

Você pode misturar esses blocos declarativos com o código normal, conforme demonstrado mais adiante.

Para mais informações, visite os seguintes recursos:

* [DSL: explained](http://www.vaadinonkotlin.eu/dsl_explained-v10.html) - uma descrição mais detalhada da criação de UIs do Vaadin com o Karibu-DSL.
* O repositório da biblioteca Karibu DSL em github.com/mvysny/karibu-dsl .