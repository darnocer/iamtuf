# iamtuf.org

## Gettting Started with Webflow

Weblow has a great library of lessons in [Webflow University](https://university.webflow.com/). Please be sure to familiarize yourself with these Webflow concepts that are importantant to the foundational structure of `iamtuf.org` before diving in. 

* **Using Classes & Combo Classes** - [https://university.webflow.com/lesson/web-styling-using-classes](https://university.webflow.com/lesson/web-styling-using-classes)
* **Understanding Inheritance in Webflow** - [https://university.webflow.com/lesson/style-panel-overview](https://university.webflow.com/lesson/style-panel-overview)
* **Symbols & Override Fields** - [https://university.webflow.com/lesson/symbols](https://university.webflow.com/lesson/symbols)



## Architecture 


### "Client First"
We are using a slightly modified version of [Client First](https://www.finsweet.com/client-first/docs/intro) naming, an industry-standard scalable architecture convention specifically for Webflow websites. The docs go into depth about the methodology, but the key points are summarized below. 

There is a Client First Chrome extension with some great features here: https://www.finsweet.com/extension 

It may also be helpful, but not necessary, to understand the basic concept of BEM Methodology. **BEM** (Block, Element, Modifier) is a component-based approach to web development. You can learn more about the BEM methodology [here](https://en.bem.info/methodology/quick-start/) and more about using it in Webflow [here](https://webflow.com/blog/class-naming-101-bem). 

Please be sure to adhere to these guidelines as closely as possible when creating new elements or classes so our website will be scalable and maintainable into the future by anyone. 



### Key Concepts

Notes:
* Nearly every element will have a class applied
* Avoid applying margins and paddings directly to elements, and utilize spacing elements instead where possible.
* Do not "deep stack" classes. If it is necessary to use more than 2 or 3 utility classes, use a custom class instead. 



#### Class Types
**Utility Class** - Utility classes are global in nature and are used to apply a specific CSS property or combination of CSS properties to an element.

> Utility classes are _hyphenated_. 

Examples:

* `text-weight-bold`
* `text-style-muted`
* `text-align-center`
* `padding-large`




**Custom Class** - If an element doesn't have a global or utility class applied, it should have a custom class, even if you don't apply any styles. 

> Custom Classes include an _underscore_ with the convention `[identifier]_[element-name]`. 

Each section will have an _identifier_, and all non-global elements within that block should be prefixed with the same identifier. 

Examples:

* `home-hero_component`
* `key-stats_block`
* `nav_menu-list`





**Global Class** - Utility classes are global classes. Custom Classes can also be a Global Class if it's a structure that's repeated across different components. 

> Global Custom Classes are prefixed with a `c_` (where the 'c' stands for "component"). 

Examples:
* `c_content`
* `c_button`
* `c_cta-container`
* `c_arrow-link`


**Modifiers** - Modifiers are added as a combo class to an existing global or custom "base" class, and similar to utility classes, change 1 or 2 specific CSS properties as a variation of the base class. If you need to add 2 or more modifiers, consider creating a new custom class instead. 

> Modifiers are prefixed with a double hypen `--`, and will only work when combined with the base class. 

* `c_button` `--yellow`
* `c_button` `--secondary`



#### Page & Symbol Strucuture
Nearly all pages should have all content wrapped within a `page-wrapper` container, that has little to no styles applied, and all of the "main" page content (excluding Navigation and Footer) live within a `main-wrapper` container (applies `<main>` tag for accessibility). 

Body
* `page-wrapper`
	* Navigation
	* `main-wrapper`
		* `section_[identifier]`
			* `padding-global`
				* `container-[size]`
					* `padding-vertical` `padding-[size]`
						* `[identifer]_component`
							* [identifier]_[element-name]`
								* ...
		* [...Components]
	* Footer



#### Spacing 


#### Sizing


#### Typography



