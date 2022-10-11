# iamtuf.org

## Gettting Started with Webflow

Weblow has a great library of lessons in [Webflow University](https://university.webflow.com/). 

Please be sure to familiarize yourself with these Webflow concepts that are importantant to the foundational structure of `iamtuf.org` before diving in. 

1. **Using Classes & Combo Classes** - [https://university.webflow.com/lesson/web-styling-using-classes](https://university.webflow.com/lesson/web-styling-using-classes)
2. **Understanding Inheritance in Webflow** - [https://university.webflow.com/lesson/style-panel-overview](https://university.webflow.com/lesson/style-panel-overview)
3. **Symbols & Override Fields** - [https://university.webflow.com/lesson/symbols](https://university.webflow.com/lesson/symbols)

Also familarize yourself with our [Style Guide](https://iamtuf.webflow.io/style-guide) (`pw: iamtuf`) in editor mode to see the class structure. 

[Made in Webflow](https://webflow.com/made-in-webflow) is also a great resource for ideas and what is possible in Webflow. 


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
							* `[identifier]_[element-name]`
								* ...
		* [...Components]
	* Footer



#### Spacing 
We are using CF's standard spacing classes, which are applied to a `div` element that wraps the content you want to add spacing to. You can see them in our [Style Guide](https://iamtuf.webflow.io/style-guide#Spacing) (must be in Edit mode in the Desginer to see the classes in the Navigation panel). 

Examples:
* To add "medium" padding to the top and bottom: `padding-vertical` `padding-medium`
* To add a "small" margin to the right: `margin-right` `margin-small`
* To add "large" padding to all sides of an element: `padding-large`


#### Sizing
Per CF's guidelines, please use `rem` for sizing for _everything_. There may be a few exceptions where we use `em` and borders and border radiuses use `px`, but as a general rule use `rem` by default to keep sizing responsive.


#### Typography
All heading tags are styled, but please utilize the typography classes for all text elements. Heading tags should be applied for Semantic HTML/SEO purposes only, but do not need to dictate the styling. 

For example, a "Thank You" message might be styled with `heading-xlarge`, but should not have an `h1` or `h2` tag and should be a text block instead because it does not have semantic meaning within the context of the page.  

Additional text style classes can be found in the [Style Guide](https://iamtuf.webflow.io/style-guide). 

Remember to avoid "deep stacking" - if you need to apply 3 or more classes, consider creating a custom class. For example, if you need to add `heading-xlarge`, `text-align-center`, `text-color-yellow`, and `text-style-italic` to get the desired style for a text element, create a custom class with these styles instead, such as `page-header_heading`. 

##### Heading Classes
* `heading-xlarge`
* `heading-large`
* `heading-medium`
* `heading-small`
* `heading-xsmall`

##### Paragraph Classes
* `text-size-xlarge`
* `text-size-large`
* `text-size-medium`
* `text-size-regular`
* `text-size-small`
* `text-size-xsmall`



