# iamtuf.org Development Guide

## Resources

### Getting Started with Webflow

Weblow has a great library of lessons in [Webflow University](https://university.webflow.com/). 

Please be sure to familiarize yourself with these Webflow concepts that are importantant to the foundational structure of `iamtuf.org` before diving in: 

1. **Using Classes & Combo Classes** - [https://university.webflow.com/lesson/web-styling-using-classes](https://university.webflow.com/lesson/web-styling-using-classes)
2. **Understanding Inheritance in Webflow** - [https://university.webflow.com/lesson/style-panel-overview](https://university.webflow.com/lesson/style-panel-overview)
3. **Symbols & Override Fields** - [https://university.webflow.com/lesson/symbols](https://university.webflow.com/lesson/symbols)


### iamtuf.org-specific Resources
`pw: iamtuf`

1. [Style Guide](https://iamtuf.webflow.io/style-guide) (must be in editor mode to see the class structure)
2. Available [Symbols](https://iamtuf.webflow.io/Symbols)
3. [Figma Designs](https://www.figma.com/file/WJSS5O9jc3zrRVsEs2jLmK/TUF---iamtuf.org-2022?node-id=125%3A515)


### Fun Stuff
* [Made in Webflow](https://webflow.com/made-in-webflow) is a great resource for ideas and what is possible in Webflow. 
* Finsweet has a [Client First Chrome extension](https://www.finsweet.com/extension) with some great features 


## Site Architecture & Class Naming Convention


### "Client First" Overview
We are using a slightly modified version of [Client First](https://www.finsweet.com/client-first/docs/intro) naming, an industry-standard scalable architecture convention specifically for Webflow websites. The docs go into depth about the methodology, but the key points for `iamtuf.org` are summarized in this ReadME. 

It may also be helpful, but not necessary, to understand the basic concept of BEM Methodology. **BEM** (Block, Element, Modifier) is a component-based approach to web development. You can learn more about the BEM methodology [here](https://en.bem.info/methodology/quick-start/) and more about using it in Webflow [here](https://webflow.com/blog/class-naming-101-bem). 

‼️ Please be sure to adhere to these guidelines as closely as possible when creating new elements or classes so our website will be scalable and maintainable into the future by anyone. 



### Class Types
Nearly every element will have at least one class, even if there are no styles applied. The majority of styling should be done on the classes and not on the tag element itself.

✦ **Utility Class** - Utility classes are global in nature and are used to apply a specific CSS property or combination of CSS properties to an element.

> ℹ️ Utility classes are always _hyphenated_. 

Examples:

* `text-weight-bold`
* `text-style-muted`
* `text-align-center`
* `padding-large`

‼️ **Avoid "deep stacking" classes. If you need to apply 3 or more utility classes to achieve the desired style, consider creating a custom class instead.**




✦ **Custom Class** - Custom classes specific to the component being styled. If an element doesn't have a global and/or utility class applied, it should have a custom class, even if you don't apply any styles. 

> ℹ️ Custom Classes include an _underscore_ with the convention: `[identifier]_[element-name]`. 

Each section will have an _identifier_, and all non-global elements within that block should be prefixed with the same identifier. The identifier is typically the name of the symbol for that component. 

Examples:

* `home-hero_component`
* `key-stats_block`
* `nav_menu-list`





✦ **Global Class** - Utility classes are global classes. A Custom Class can also be a Global Class if it's a block structure that's repeated across different components, and not unique to the component being styled. 

For example, many symbols repeat a similar structure for the text content that includes: subtitle, heading, body text, and CTA. For this, we use the global component `c_content` which contains the elements with consistent margins and padding. 

> ℹ️ Global Custom Classes are prefixed with a `c_` (where the 'c' stands for "component"). 

Examples:
* `c_content`
* `c_button`
* `c_cta-container`
* `c_arrow-link`

<details>
<summary>ℹ️ How to Create Global Classes</summary>

Because of Webflow's "Combo Class" behavior, global classes need to be created indendendently on an element. 
	
For example, say you already have a heading styled with `heading-large`, and you want to change the heading color to yellow, but you don't have an existing global class for `color: yellow;`. If you stack a new `text-color-yellow` class on the `heading-large` base class and change the color to yellow, you would create a _combo class_, meaning `text-color-yellow` is now dependent on the `heading-large` base class. Applying `text-color-yellow` to any other class would not have the deisred result of changing the text color. 
	
In order to create `text-color-yellow` as a _global class_, you would need to style an element independently first. This is where the Style Guide comes in functionally. You'd first add an element to the Style Guide, create the `text-color-yellow` class indepedently, and style the element. This would create `text-color-yellow` as a _global class_, allowing you to use it independently on other elements or stack on other base classes like `heading-medium`, `heading-small`, etc. for the desired style. 
	
</details>




✦ **Modifiers** - Modifiers are added as a combo class to an existing global or custom "base" class, and similar to utility classes, change 1 or 2 specific CSS properties as a variation of the base class. There are intended to be a variation that is specific to the component you are styling. If you need to add 2 or more modifiers, consider creating a new custom class instead. 

> ℹ️ Modifiers are prefixed with a double hypen `--`, and will only work when combined with the base class. 

* `c_button` `--yellow`
* `c_button` `--secondary`

- [ ] TO DO: Refactor classes and avoid using Modifiers. Convert modifiers into global utility classes or custom classes (modifiers are an artifact from the BEM structure the website was built with at the beginning). 



#### Page & Symbol Strucuture
Nearly all pages should have all content wrapped within a `page-wrapper` container, that has little to no styles applied, and all of the "main" page content (excluding Navigation and Footer) live within a `main-wrapper` container (applies `<main>` tag for accessibility). 

Then, each _section_ will follow a similar structure to keep layout spacing consistent. We create 🟩 _Symbols_ from the section-level. Within the section, there will typically be several elements with global classes until the actual "component" element (`[identifier]-[component-name]`), which houses the component-specific styles and content and typically consist mostly of custom classes. The "component" element is often, not always, a grid element. Within the component, there may be "global" components such as `c_content`, `c_button`, etc. 

**Body**
* `page-wrapper` - wraps all page content
	* `🟩 Navigation` - Navigation symbol
	* `main-wrapper` - wraps all of the "main" content sections
		* `section_[identifier]` - each "section" level is a symbol
			* `padding-global` - keeps the right/left padding of the page consistent
				* `container-[size]` - a container with a max-width
					* `padding-vertical` `padding-[size]` - vertical padding that creates space between each section
						* `[identifer]_component` - the "parent" item of the component-specific content
							* `[identifier]_[element-name]` 
								* ...
		* `section_[identifier]`
		* `section_[identifier]`
	* `🟩 Footer`



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



