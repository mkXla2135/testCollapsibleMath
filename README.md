# Inline math in details tag prevents from using code blocks

As per [documentation](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/organizing-information-with-collapsed-sections), one can
>  temporarily obscure sections of your Markdown by creating a collapsed section that the reader can choose to expand. For example, when you want to include technical details in an issue comment that may not be relevant or interesting to every reader, you can put those details in a collapsed section.



## Correct behaviour
E.g., the example from the documentation page shows that you can hide code via `details`:

<details>

<summary>Tips for collapsed sections</summary>

### You can add a header

You can add text within a collapsed section. 

You can add an image or a code block, too.

```ruby
   puts "Hello World"
```

</details>

The same way, one can hide LaTeX math:


<details>

<summary>Collapsed section containing a math block and a code block</summary>

```math
x^2 + y^2 + z^2 = 1
```

```cpp
#include <iostream>

int main() {
    std::cout << "Hello World!";
    return 0;
}
```

</details>


And you can also hide some random text with an inline math:

<details>

<summary>Collapsed section inline math</summary>

 Lorem ipsum dolor $x=y$ sit amet, consectetur adipiscing elit. Nulla consequat non dolor non ultricies. Vestibulum aliquet viverra dolor. Ut tempus, odio ac semper venenatis, nulla mi lacinia justo, nec venenatis est mi ac diam. Sed lacus ligula, efficitur sit amet pulvinar in, fringilla sed justo. Nullam tincidunt lacinia massa, nec fermentum leo venenatis sit amet. Vestibulum ac ipsum in sapien fermentum varius eget sit amet nulla. Ut fringilla vulputate sapien et cursus. Maecenas ac risus elementum, dapibus libero ac, molestie quam. Morbi mollis arcu quis scelerisque lobortis. Sed tempus dictum volutpat. In venenatis mauris in nisl sodales, sit amet dapibus lacus pretium. $e^{i\pi}$

</details>

## Incorrect behaviour
But currently you **cannot** combine inline math with code blocks: while the inline math is rendered correctly, the code block loses syntax coloring.

**Neither this works:**

<details>
  
<summary>Collapsed section containing inline math and a code block</summary>

I think that $x+y=0$.

```cpp
#include <iostream>

int main() {
    std::cout << "Hello World!";
    return 0;
}
```

</details>

**nor this** (which makes sense since the code blocks are not correctly rendered):

<details>
  
<summary>Collapsed section containing inline math and a math block</summary>

I think that $x+y=0$.

```math
x^2 + y^2 + z^2 = 1
```


</details>


One can also put the inline math in the `summary`  and **stil observe the issue**:
<details>
  
<summary>
   I think that $x+y=0$
</summary>


```cpp
#include <iostream>

int main() {
    std::cout << "Hello World!";
    return 0;
}
```

</details>


At last, when viewing the repository on the GH mobile app, in all cases the syntax is highlighted normally, but math (either inline or in the fenced block) isn't rendered at all (probably GH Mobile does not render LaTeX, therefore also the issue with syntax highlighting does not appear)
