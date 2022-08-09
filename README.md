# iamtuf.org

## Class Structure & Naming Convention

We are using [classes and combo classes](https://university.webflow.com/lesson/web-styling-using-classes) to apply styles in Webflow with a modified version of the BEM methodology. 

### BEM
**BEM** (Block, Element, Modifier) is a component-based approach to web development. You can learn more about the BEM methodology [here](https://en.bem.info/methodology/quick-start/) and more about using it in Webflow [here](https://webflow.com/blog/class-naming-101-bem). The below summarizes how we are utilizing it specifically for iamtuf.org. 

* Classes are all lowercase
* Mutiple words for a Block, Element, or Modifier are separated by a single hyphen (`-`) (rather than a space)
* Elements are linked to a block with a single underscore (`_`)
* Modifiers are a separate class prefixed with double hyphens (`--`)
* Modifiers are represented by its _key_ (eg. `bg-color`) and its _value_ (eg. `yellow`), separated by an underscore `_`
* For the sake of the examples in this document, classes are prefixed with a period (`.`) to identify them as classes, but the period is not included in the actual class name. 

```css
.block-name{}
.block-name_element1-name{}
.block-name_element2-name{}
.block-name_element3-name{}
.block-name_element1-name .--modifier1-key_modifier1-value{}
```

#### Blocks
* **Block** - A functionally indepedent component that can be re-used
  *  Examples: Navbars, buttons, hero, etc.

#### Elements
* **Element** - A part of a block that can't be used separately. An element is always a part of a block, not another element. 
  * Examples: Menu items, button text, section heading, etc. 


#### Modifiers
* **Modifier** - A modification usually represented by a key-value pair
  * Examples: bg-color, color, size, etc. 


#### Mix
* **Mix** - Comprised of a block and an element of another block. Allows for creation of unique components based on existing global ones. 
  * Examples: hero-section, content-section, etc. 


### Component Structure
With the exception of the navbar and footer, all internal components are built with the following standard structure:
* **Section** - Section is a standard Webflow element. The section element should never be modified. The section is named with a class that represents the name of the component (eg. `.hero-section`), which is technically a mix (eg. `.section .hero-section`). Any modifications to the section are added as modifiers (eg. `.hero-section .--bg-color_blue`). 
  * **Container** - There is a container Webflow element, but we are using a custom `.container` class that has `5% padding` on all sides. This is added within the section to standardize page padding, but still allow for full-width backgrounds at the section-level. 
    * **Blocks & Elemeents** - The rest of the component is built within the container following the BEM convention


### Utility Classes


## Symbols


### Current Symbols


