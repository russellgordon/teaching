---
{"dg-publish":true,"permalink":"/cemc/sccst-2023/slides/","dgHomeLink":false}
---


[[CEMC/SCCST2023/A Rapid Workflow for Publishing CS Teaching Materials\|🏡 Home]]

---


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



### A Rapid Workflow for Publishing CS Teaching Materials

Russell Gordon
<small>Lakefield College School</small>

---

###  Motivation

Avoid fiddling with GUI-based page layout, slides, and diagramming software.

---

###  Motivation

Satisfy 80/20 rule.

---

###  Motivation

Meet the needs of English language learners.

![Screenshot 2023-08-15 at 2.31.25 PM.png|700](/img/user/Attachments/Screenshot%202023-08-15%20at%202.31.25%20PM.png)

---

### Benefits

Syntax-highlighted code blocks for most languages.

```python
# Greet the world using a function in Python
def hello_world():
  return "Hello, world!"
```

---

### Benefits

Math notation using LaTeX: single-line.

$x=\frac{-b \pm\sqrt{b^2-4ac}}{2a}$

---

### Benefits

Math notation using LaTeX: multi-line.

$
\begin{aligned}
a &= -0.25 \\
b &= 2 \\
c &= 1.5
\end{aligned}
$

---

### Benefits

Mermaid: left-right [flowchart](https://mermaid.js.org/syntax/flowchart.html).

```mermaid
flowchart LR

id1["App Entry Point\n(NavigationView)"] --> id2["List\n(NavigationLink)"]
id2 --> id3[Blue Jays]
id2 --> id4[Cheesecake]
id2 --> id5[Claire]
id2 --> id6[Jen]
id2 --> id7[Lasagna]
id2 --> id8[Piper]
```

---

### Benefits

Mermaid: top-down [flowchart](https://mermaid.js.org/syntax/flowchart.html).

```mermaid
flowchart TD

id1["App Entry Point\n(NavigationView)"] --> id2["List\n(NavigationLink)"]
id2 --> id3[Blue Jays]
id2 --> id4[Cheesecake]
id2 --> id5[Claire]
id2 --> id6[Jen]
id2 --> id7[Lasagna]
id2 --> id8[Piper]
```

---

### Benefits

Mermaid: [sequence](https://mermaid.js.org/syntax/sequenceDiagram.html) diagram.

```mermaid
sequenceDiagram
    Alice->>John: Hello John, how are you?
    John-->>Alice: Great!
    Alice-)John: See you later!
```

---

### Benefits

Mermaid: [class](https://mermaid.js.org/syntax/classDiagram.html) diagram.

```mermaid
classDiagram
    Animal <|-- Duck
    Animal <|-- Fish
    Animal <|-- Zebra
    Animal : +int age
    Animal : +String gender
    Animal: +isMammal()
    Animal: +mate()
    class Duck{
        +String beakColor
        +swim()
        +quack()
    }
    class Fish{
        -int sizeInFeet
        -canEat()
    }
    class Zebra{
        +bool is_wild
        +run()
    }
```

---

### Benefits

Mermaid: [state](https://mermaid.js.org/syntax/stateDiagram.html) diagram.

```mermaid
stateDiagram-v2
    [*] --> Still
    Still --> [*]

    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]
```

---

### Benefits

Mermaid: [entity-relationship](https://mermaid.js.org/syntax/entityRelationshipDiagram.html) diagram.

```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE-ITEM : contains
    CUSTOMER }|..|{ DELIVERY-ADDRESS : uses
```

---

### Benefits

Mermaid: [user journey](https://mermaid.js.org/syntax/userJourney.html) diagrams.

```mermaid
journey
    title My working day
    section Go to work
      Make tea: 5: Me
      Go upstairs: 3: Me
      Do work: 1: Me, Cat
    section Go home
      Go downstairs: 5: Me
      Sit down: 5: Me
```

---

### Benefits

Mermaid: [Gantt](https://mermaid.js.org/syntax/gantt.html) charts.

```mermaid
gantt
    title A Gantt Diagram
    dateFormat YYYY-MM-DD
    section Section
        A task          :a1, 2014-01-01, 30d
        Another task    :after a1, 20d
    section Another
        Task in Another :2014-01-12, 12d
        another task    :24d
```
---

### Benefits

Mermaid: [pie](https://mermaid.js.org/syntax/pie.html) charts.

```mermaid
pie title Pets adopted by volunteers
    "Dogs" : 386
    "Cats" : 85
    "Rats" : 30
```
---

### Benefits

Mermaid: [git graph](https://mermaid.js.org/syntax/gitgraph.html) diagrams.

```mermaid
gitGraph
   commit
   commit
   branch develop
   checkout develop
   commit
   commit
   checkout main
   merge develop
   commit
   commit
```

---

### Benefits

Add images quickly by drag and drop.

![Screenshot 2023-08-14 at 1.01.16 PM.png|450](/img/user/Attachments/Screenshot%202023-08-14%20at%201.01.16%20PM.png)

---

### Benefits

Use animations to convey key concepts without distraction.

![Linear Search Example.gif|600](/img/user/Attachments/Linear%20Search%20Example.gif)

---

### Benefits

Focus on content, not presentation, by writing [in Markdown](https://help.obsidian.md/Editing+and+formatting/Basic+formatting+syntax).

---

### Benefits

Your data is stored in plain text files – less potential for lock-in.

---

### Benefits

Link quickly to existing content.

![Screenshot 2023-08-14 at 1.06.26 PM.png|400](/img/user/Attachments/Screenshot%202023-08-14%20at%201.06.26%20PM.png)

---

### Benefits

Publish a searchable site.

![Screenshot 2023-08-16 at 1.04.00 PM 1.png](/img/user/Attachments/Screenshot%202023-08-16%20at%201.04.00%20PM%201.png)

---

### Benefits

Free hosting (at [Netlify](https://www.netlify.com/) or [Vercel](https://vercel.com/)).

---

### Drawbacks

Dependencies on:

- [Obsidian](https://obsidian.md)
- [Digital Garden](https://dg-docs.ole.dev) plugin.
- [GitHub](https://github.com)
- [Netlify](https://www.netlify.com) or [Vercel](https://vercel.com)

---

### Personal Conclusion

Benefits outweigh potential for software failure.

Better than manually writing HTML, using a word processor, or a proprietary content management system.


</div></div>
