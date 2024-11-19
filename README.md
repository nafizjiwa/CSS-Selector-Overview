# CSS-Selectors-101-Overview

CSS Selectors 101
Volusion
January 27, 2015
CSS Selectors 101
When creating a website there are two essential coding languages being used - HTML and CSS. Cascading Style Sheets, or CSS, give your HTML layout, design, and display variations for various devices. By utilizing CSS selectors we can create a rule to target HTML elements that include properties to accomplish the desired design. We will cover what CSS selectors are, how to utilize them, and the types of selectors.

What is a CSS selector?
CSS selectors are part of a CSS rule that allows you to select the contents you want to style. In this post, we are going to look at the following types of selectors and see how we can utilize them.
Basic Selectors
Advanced Selectors
Combinators
Basic Selector Types
Type selectors
Class selectors
ID selectors
Universal selector
Type Selectors
Type selectors will match every instance of the element type (heading elements, p, span, div, etc.) in the document tree.
The following rule will target all H1 elements in the document tree:

h1 {
    font-size: 26px;
}
Class Selectors
Class selectors are designated with a . (period) before the class name when being used in a selector. Suppose we have an HTML document that has the following snippet of code:
<p class="quote">The only thing we have to fear is fear itself</p>
<span class="author">Franklin D. Roosevelt</span>
We can utilize the CSS class selector to target the .quote and .author classes to give the elements the desired styles like so:
.quote {
    font-style: italics;
}
.author {

display: block;

font-weight: bold;

text-align: right;

}


ID Selectors
As opposed to class selectors, an ID selectors uses a hash (#) when being used in a selector.
<h1 id="main-title">Cascading Style Sheets</h1>
Universal Selectors
Universal selectors will select all elements within a tag. The following example will select every element that is within a div.
div * {
    color: gray;
    font-size: 14px;
}
Advanced Selector Types
Pseudo-elements
Pseudo-classes
Attribute selectors
Pseudo-elements
Pseudo-elements permits formatting based on information that lies outside of the document tree. As of CSS3, in order to designate the difference between pseudo-elements and pseudo-classes, pseudo-elements are designated with two colons. For Internet Explorer 8 and below support, use a single colon. There are currently five total pseudo-elements:
::after
::before
::first-letter
::first-line
::selection
An ::after can be utilized for many things, including adding quotes to all q elements. For example:
q::before {
    content: open-quote;
}
q::after {

content: close-quote;

}


Alternatively a ::before/::after can also be used to insert content like so:
p::after {
    content: "The End";
    display: block;
    text-align: center;
}
Pseudo-classes
Pseudo classes are added to selectors to specify a certain state of an element. The full list of pseudo-classes includes:

      :link
      :visited
      :active
      :hover
      :focus
      :empty
      :target
      :checked
      :enabled
      :disabled
      :first-of-type
      :last-of-type
      :first-child
      :last-child
      :nth-child
      :nth-last-child
      :nth-of-type
      
Suppose we want our links to be dark blue, purple on hover, and red for visited links. We can achieve this with the code below.
a:link {
    color: darkblue;
}
a:visited {

color: red;

}


a:hover {

color: purple;

}


Alternatively, if we wanted to override the link color for all links with a class of .external we can do:
.external:link {
    color: lightblue;
}
Attribute Selectors
Attribute selectors are used to target elements based on the presence of and/or the value of HTML attributes associated with the element. These selectors are denoted with square brackets.
Using an link as an example, let's cover the seven ways we can target the link based on attribute of an anchor element.

a[href]Represents an anchor with the presence of an href.
a[href="http://www.volusion.com/"]Represents an anchor with an attribute of href and a value of exactly http://www.volusion.com/. Note that this is case-sensitive.
a[title~="Volusion"]Represents an anchor with a title whose value is a white-space separated list of words, where one of which consists of the value Volusion.
a[title|="foo"]Much like the ~= operator, the |= represents an anchor with a title whose values are hyphen-separated lists that contain the value of foo.
a[href^="http"]Represents all anchors with an attribute of href that start with http.
a[href$=".com"]Represents all anchors with an attribute of href that end with .com.
a[href*="volusion"]Represents all anchors with an attribute of href that contains the word volusion.

Combinators
On particular occasions where we want to target elements based on their relationship with other elements, we will want to utilize combinators. Combinators are a lot like human relationships in that like human families, CSS has descendants, children, parents, and siblings. We will cover each of the four different combinator types in detail.
Descendant selector
Child selector
Adjacent sibling selector
General sibling selector
Descendant Selectors
A descendant selector can target all elements that are a descendant of a specified element. To select all <p> elements that are within a <div>, we can do the following:
      
      div p {
          font-size: 14px;
      }
Child Selectors
A child selector is similar to a descendant, except it selects only immediate children.
        
        <div>
            <a href="#">Link</a> <!-- Selected -->
            <p>
                <a href="#">Link</a> <!-- Not selected -->
            </p>
        </div>
        div > a {
        
        font-size: 14px;
        
        }


Adjacent Sibling Selectors
The adjacent sibling selector is denoted using the plus symbol (+). This selector is used in cases where we want to target elements only when the element is immediate proceeded by another targeted element.
In the example below, the p element immediately proceeding the H1 will have the color of gray, while the color of the other p elements will be black.
      
      p {
          color: black;
      }
      h1 + p {
      
      color: gray;
      
      }


      <h1>Title</h1>
      <p>This is a paragraph.</p> <!-- targeted by adjacent sibling selector -->
      <p>This is a paragraph.</p> <!-- not targeted -->
      <p>This is a paragraph.</p> <!-- not targeted -->
      <p>This is a paragraph.</p> <!-- not targeted -->
General Sibling Selectors
A general sibling selector is much like an adjacent sibling selector, with the only difference being that it selects all elements proceeding a targeted element rather than one. The general sibling selector is denoted using a tilde (~).
In the example below, all p sibling of the H1 element will have the applied styles. However, the paragraph within the div will not because it is not a sibling of the H1.

        p {
            color: black;
        }
        h1 ~ p {
        
        color: gray;
        
        }


        <h1>Title</h1>
        <p>This is a paragraph.</p> <!-- targeted by general sibling selector -->
        <p>This is a paragraph.</p> <!-- targeted by general sibling selector -->
        <p>This is a paragraph.</p> <!-- targeted by general sibling selector -->
        <div>
            <p>This is a paragraph.</p> <!-- not targeted -->
        </div>
