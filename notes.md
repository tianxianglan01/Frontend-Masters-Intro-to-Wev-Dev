## Notes of interest

Note: HTML is rendered in md files so if you want to see the original code, look at your local files!

### HTML
- always use classes 
- divs are simply containers to hold 'content'

### CSS

#### Cascade
- when applying a style to a class or a tag, the last styling option wins
- a class can have 2 classes of equal value. Ergo 
class = 'title-2 title1'
- both classes are of equal value. Which styling gets applied follows the rule above as in the last style 'wins'
- however if a class has two styles AND there are different rules applied, then both rules are applied. However if there's a color rule in both classes, then the 'last' class' colors get applied
- this is why it's called 'Cascade'. 
- Specificity is the example above with a class with 2 classes and 2 rules applied to the class
- however say you have 2 rules: *main-brand-3.title-3* and *title-3* and they apply to:
class = "title-3 main-brand-3"

Q: which rule wins? 
A: main-brand-3.title-3 wins because it is more specific

- classes are more specific than tags. ergo you have a class: title-4 and a tag: h1. the rule that applies to title-4 wins
- Brian's mnemoic rule is a class has a specificity value of 10 and a tag has a specificity value of 1. 3 classes (.foo1.foo2.foo3) has 30 specificity points than a 1 tag (h1) but this rule is imperfect

Q: what if you have 1 tag 1 class (h1.main-brand), 2 classes (.mainbrand.title-5), or 1 class (.mainbrand) and they are in the given order?
A: the rule with 2 classes wins (20 points)

- don't use tags and classes together. Use classes (most of the time)
- you can repeat yourself with a rule
.site-brand-2.site-brand-2 
This makes you rule more specific 

#### IDs and !important
- don't use these unless you have a good reason. Styling by ID is an even worse idea
- Brian's point value example is an id is worth 200 'points'. One id will overpower 200 classes 
- select id with pound
'#site-brand'

- comments are used with /* and */
- what has even heavier weight is !important which is worth 1000 points. 
- cascade still applies to ids and !important

#### Pseudoclasses 
- will end use quite a bit. sometimes you wanna do CSS based on some sort of state that the UI will find itself in
- hover pseudo, in his example if you hover over a box- it changes color. Hover can also be used to hover over a hyperlink and say under line or darken the color of a word. 
<!-->
<style>
    .hover-example{
        width: 100px;
        height: 100px
        background-color: limegreen;
        color white;
    }
    .hover-example:hover {
        background-color: crimson;
        width: 150px;
        height: 150px;
    }
<style>
<-->
- So in the above example, when :hover is == True, then that element (i've been using rule up to this point) is selected. 
- any time we use a colon (:) in your styling then this is known as a pseudo class. A pseudo class has the same weight as a normal class 
<!-->
<style>
 .hover-example:hover {
    background-color: crimson;
    width: 150px;
    height: 150px;
  }
  .hover-example.hover-example {
  	background-color: purple;
 
  }
<style>
<-->
Q: Who would win?

A: .hover-example: hover and .hover-example.hover-example are equal. However because .hover-example.hover-example is below .hover-example:hover, .hover-example x2 wins. As a result purple overrides crimson's 'hover' but hover's width and height rules are applied. 

- another example of a pseudo-class: *first-child*. As in the first child of a parent. Because of the 'first-child' pseudo-class, the first, child (with the text 'First') is rendered limegreen
- in english: '.first-child-example:first-child', if this is part of the .first-child-example class and it is the first child, apply this color
- can also use last-child and nth-child

.first-child-example {
    color: crimson;
}
.first-child-example:first-child{
    color: limegreen;
}

<ol>
    <li> class= "first-child-example">First</li>
    <li> class= "first-child-example">Second</li>
    <li> class= "first-child-example">Third</li>
<ol>

- These are known as structural classes

#### Pseudo-elements and Wildcard Selector
- there's an article on the learning guide
- * is select everything and has a specificity of 0

#### Layout CSS
- *float*: used rarely

float: left

Go as far as you can left and once you can't go any further, stop there. 
- *flex*
##### Box Mode
- every tag (ol, p, a, etc) has a display property associated with it where display properties are the default settings of a tag. Ergo 

divs are display:block
spans are display:inline

- inline is when you wnat a tag to behave like text. However if you use inline, the browser will not let you change the height, width, padding, margins, etc
- if you're trying to change the width and the height of a tag and it's not working, you probably have the wrong display type 
- blocks will allow you to adjust width, height, etc. Blocks take the whole line to themselves
- flex allows for 
- box setting border box and box size. Can use wildcard (*) for width 
- the first thing to put on every website is 

* {
    box-sizing: border-box;
}
- which allows us to measure everything on the website in border-box instead of content box 
- width > padding > border > margin is the order of a box 

#### Floats

<style>
    .floated .box {
        float: left;
    }
</style>
- the space above says it's a descendent of this so

.floated.box is a box inside of floated 

- there's a hiearchy in floats where the current box will never be lower than the previous box

#### Effective Patterns for Coding CSS
- you 'link' your .html file and the css file by using a 

<link rel = 'stylesheet' href = "./style.css" />

- ./style.css means where ever the index.html file is, the style.css is in the same folder
- so to not repeat yourself in code, lightly use the cascade. Brian's example has a default button, warn button, and a success button where you have the basic button set up for default, and then adjustments in the war and success. 
- try to keep your css related elements on the same page
- good idea to have comment 'element y inherits from element x'

- easiest way to open the devtool is to right click and click on 'inspect element'
- you can also play around in the console to edit the htmlcss code and see what would happen 
- when writing css, instead of going straight towards editor, go straight towards the browser and figure out what you want to do.
- then copy what worked and paste into editor
- in the dev tools, you can click on computed to see the details of an element. In computed, you can also modify values to see what the end result would look like 
- layout is useful for css grid
- box model properties are all in layout
- animations has tools for how animaitons are happening 
- Fonts: to see which fonts
- you can overwrite important but it's not 'something to be proud of'
- there's an option to see how the website will load in depending on platform (iphone, mac, safari, android, etc)
- color dropper (firefox feature) to see what shade of an element is (hex number)
- as a general rule you don't want ot target specific browsers
- ideal answer is everything should work in every browser
- practical answer: you should know your audience through google analytics (this website is browsed by 95% of users using windows edge)
- also think about who will use the website: ie if your website is used to hail private helicopter taxis, make sure your website works on a high end iphone
- you're going to base things on th ewidth of a page

#### HTML & CSS Project Exercise, Part 1

- have an index.html and styles.css
- a UI/UX designer hands you a sketch and you need to recreate this
- when you open an html doc from your browser, your file system is acting as a server: the browser is making a request to your computer