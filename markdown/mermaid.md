# Mermaid

## flowchart

````mermaid
---
Title: Trình biên dịch C1 và C2
---
flowchart LR
    A("public String method() {...}")-->B(C1) --> C(Native level 1)
    B --> D(Native level 2)
    B --> E(Native level 3)
    A-->F(C2) --> G(Native level 4)
````

## stateDiagram-v2

````mermaid
stateDiagram-v2
    state1: 4*fractorial(3)
    state2: 3*fractorial(2)
    state3: 2*fractorial(1)
    state4: 1
    
    [*] --> state1
    state1 --> state2
    state2 --> state3
    state3 --> state4
    
    state4 --> state3 : =1
    state3 --> state2 : =2
    state2 --> state1 : =6
    state1 --> [*] : =24
````

## classDiagram

````mermaid
---
Title: UML diagram của Builder design pattern
---
classDiagram
    direction LR
    class Builder {
        <<interface>>
        + buildPiece1()
        + buildPiece2()
        + getCompleteProduct()
    }
    class ConcreteBuilder{
        + buildPiece1()
        + buildPiece2()
        + getCompleteProduct()
    }
    class Director{
        + createObject(Builder builder)
    }
    Builder <|-- ConcreteBuilder
    Director o-- Builder
    Product <.. ConcreteBuilder : creates 
````

## block-beta

````mermaid
---
Title: Region based collection
---
block-beta
    columns 1
    A["Heap Layout"]
    blockArrowId6<["&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"]>(down)
    block:Collectors
        B["Y"]
        C["Y"]
        D["O"]
        E["Y"]
        F["O"]
        G["O"]
        H[" "]
        I[" "]
        J["Y"]
        K["Y"]
        L["O"]
        M["Y"]
        N[" "]
        O["Y"]
        P["Y"]
    end
````

## flowchart

````mermaid
---
Title: Vòng đời của thực thể trong JPA
---
flowchart 
    A(TRANSIENT)-->|"persist(entity)"| B(MANAGED)
    B --> |"detach(entity), clear(), close()"| E(DETACHED)
    E --> |"merge(entity)"| B
    B --> |"remove(entity)"| D(REMOVED)
    D --> |"flush()"| C
    B --> |"flush()"| C[(CSDL)]
    C --> |"find, getReference, getResultList..."| B
    D --> |"persist(entity)"| B
````

## graph

````mermaid
---
Title: Bộ nhớ Java
---
graph LR
    subgraph Stack
        s1(someList)
        s2(someString)
        s3(myList)
    end

    subgraph Heap
        subgraph list1 [List]
            direction TB
            l1(0)
            l2(1)
            l3(2)
            l4(3)
        end

        subgraph string1 [String]
            direction TB
            one(One)
        end
        subgraph string2 [String]
            direction TB
            two(Two)
        end
        subgraph string3 [String]
            direction TB
            three(Three)
        end
        subgraph string4 [String]
            direction TB
            four(Four)
        end

        l1 --> one
        l2 --> two
        l3 --> three
        l4 --> four
    end

    s1 --> list1
    s3 --> list1
    s2 --> two
````

## sequenceDiagram

````mermaid
sequenceDiagram
  participant A as "Observer 1"
  participant B as "Observer 1"
  participant C as "Subject"
  actor D
  A ->> C: registerObserver(observer1)
  B ->> C: registerObserver(observer2)
  D ->> C: setState()
  activate C
  C ->> C: 
  C ->> A: update()
  activate A
  A ->> C: getStatus()
  deactivate A
  C ->> B: update()
  activate B
  B ->> C: getStatus()
  deactivate B
  deactivate C
````

