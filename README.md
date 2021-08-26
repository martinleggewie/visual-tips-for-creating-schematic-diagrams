
<!--
    Some meta information about this document:

    * I use the GitHub flavor of markdown.
    See [https://guides.github.com/features/mastering-markdown](https://guides.github.com/features/mastering-markdown) for how to use it.

    * I follow the one sentence per line approach which I came across several years ago when learning AsciiDoc(tor).
    See [https://asciidoctor.org/docs/asciidoc-recommended-practices/#one-sentence-per-line](https://asciidoctor.org/docs/asciidoc-recommended-practices/#one-sentence-per-line) for the reasoning behind this approach.

    * Most parts of this whole article I have written with Visual Studio Code, benefitting from its in-built Markdown support.
    To get the table of content created automically, I have added the extension "huntertran.auto-markdown-toc" and use it with its default configuration.
    So, in case you would like to change something in the structure of this article, please consider using this extension as well to keep the toc consistent with the content.
 -->


# Visual tips for system diagrams


_Martin Leggewie, 2021-08-26_

In this article I describe a collection of visual tips for creating so-called system diagrams.
The purpose of such diagrams is to convey information about a system landscape to the audience, and be the basis for discussions.
Therefore, it is a good advice to keep these diagrams as simple as possible.
If you want/need to create such diagrams yourself, then these tips can support you in reaching this "as simple as possible" goal.

----

<!-- TOC ignore:true -->
## Table of Contents

<!-- TOC -->

- [Introduction](#introduction)
    - [Definition and goal: System diagram](#definition-and-goal-system-diagram)
    - [Why should you care about how system diagrams look like?](#why-should-you-care-about-how-system-diagrams-look-like)
    - [What is in for you?](#what-is-in-for-you)
    - [Mind-map of the things to come TODO](#mind-map-of-the-things-to-come-todo)
- [General guidelines](#general-guidelines)
    - [General guideline 1: Use simple visual attributes, avoid the "bling-bling"](#general-guideline-1-use-simple-visual-attributes-avoid-the-bling-bling)
        - [Do not use color gradients](#do-not-use-color-gradients)
        - [Do not use 3D elements](#do-not-use-3d-elements)
        - [Do not use drop shadows](#do-not-use-drop-shadows)
        - [Do not use the "sketch" visual style](#do-not-use-the-sketch-visual-style)
    - [General guideline 2: Define the meaning of all visual elements in a legend](#general-guideline-2-define-the-meaning-of-all-visual-elements-in-a-legend)
    - [General guideline 3: Apply high-contrast coloring style](#general-guideline-3-apply-high-contrast-coloring-style)
    - [General guideline 4: Use stroke width to support high-contrast](#general-guideline-4-use-stroke-width-to-support-high-contrast)
- [Canvas](#canvas)
    - [Canvas guideline 1: Use infinite space](#canvas-guideline-1-use-infinite-space)
    - [Canvas guideline 2: Set-up a square-shaped grid with reasonable absolute dimensions](#canvas-guideline-2-set-up-a-square-shaped-grid-with-reasonable-absolute-dimensions)
    - [Canvas guideline 3: Enable snap to grid](#canvas-guideline-3-enable-snap-to-grid)
- [Text](#text)
    - [Text guideline 1: Use sans-serif font face](#text-guideline-1-use-sans-serif-font-face)
    - [Text guideline 2: Select font size in relation to box size](#text-guideline-2-select-font-size-in-relation-to-box-size)
    - [Text guideline 3: Use font style to guide to important parts first](#text-guideline-3-use-font-style-to-guide-to-important-parts-first)
        - [Use bold style for all important names](#use-bold-style-for-all-important-names)
        - [Use normal font style for all companion text](#use-normal-font-style-for-all-companion-text)
        - [Use italics style for meta information only](#use-italics-style-for-meta-information-only)
- [Boxes](#boxes)
    - [Box guideline 1: Use same size for boxes which represent the same type of entity](#box-guideline-1-use-same-size-for-boxes-which-represent-the-same-type-of-entity)
    - [Box guideline 2: Choose width and height for inner-most boxes to be even multiples of canvas grid size](#box-guideline-2-choose-width-and-height-for-inner-most-boxes-to-be-even-multiples-of-canvas-grid-size)
    - [Box guideline 3: Choose suitable size for inner-most boxes to allow making good use of the snap-to-grid feature](#box-guideline-3-choose-suitable-size-for-inner-most-boxes-to-allow-making-good-use-of-the-snap-to-grid-feature)
    - [Box guideline 4: Choose consistent corner curvature for rounded boxes](#box-guideline-4-choose-consistent-corner-curvature-for-rounded-boxes)
    - [Box guideline 5: Choose different stroke widths when boxes are located inside other boxes](#box-guideline-5-choose-different-stroke-widths-when-boxes-are-located-inside-other-boxes)
- [Connection arrows](#connection-arrows)
    - [Connection arrow guideline 1: Define what different types of connection arrows actually mean](#connection-arrow-guideline-1-define-what-different-types-of-connection-arrows-actually-mean)
    - [Connection arrow guideline 2: Make different types of connection arrows appear differently enough](#connection-arrow-guideline-2-make-different-types-of-connection-arrows-appear-differently-enough)
    - [Connection arrow guideline 3: For call dependencies provide exactly one arrow head](#connection-arrow-guideline-3-for-call-dependencies-provide-exactly-one-arrow-head)
    - [Choose arrow heads to be big enough compared to diagram size TODO](#choose-arrow-heads-to-be-big-enough-compared-to-diagram-size-todo)
    - [Avoid arrow heads in both directions for call dependencies TODO](#avoid-arrow-heads-in-both-directions-for-call-dependencies-todo)
    - [Attach a bigger dot at the arrow start TODO](#attach-a-bigger-dot-at-the-arrow-start-todo)
- [Color TODO](#color-todo)
    - [Choose color so that audience's attention will be guided to the most important diagram elements first TODO](#choose-color-so-that-audiences-attention-will-be-guided-to-the-most-important-diagram-elements-first-todo)
    - [Color styles TODO](#color-styles-todo)
        - [Black border, normal fill TODO](#black-border-normal-fill-todo)
        - [Black border, inverted fill TODO](#black-border-inverted-fill-todo)
        - [No border, inverted fill TODO](#no-border-inverted-fill-todo)
- [Layout of boxes and their connection arrows TODO](#layout-of-boxes-and-their-connection-arrows-todo)
    - [Apply a "hidden grid" when positioning boxes TODO](#apply-a-hidden-grid-when-positioning-boxes-todo)
    - [Flow either top-to-down or left-to-right TODO](#flow-either-top-to-down-or-left-to-right-todo)
    - [Place boxes in such a way to minimize the amount of corners in the connection arrows TODO](#place-boxes-in-such-a-way-to-minimize-the-amount-of-corners-in-the-connection-arrows-todo)
    - [Try to avoid crossing connection arrows TODO](#try-to-avoid-crossing-connection-arrows-todo)
    - [Never ever allow overlapping connection arrows TODO](#never-ever-allow-overlapping-connection-arrows-todo)
    - [Don't start or end different connection arrows at the same point TODO](#dont-start-or-end-different-connection-arrows-at-the-same-point-todo)
    - [Connection routing path styles TODO](#connection-routing-path-styles-todo)
    - [Choose gap between boxes TODO](#choose-gap-between-boxes-todo)
- [Closing words TODO](#closing-words-todo)

<!-- /TOC -->

----


## Introduction

Before I start with the actual tips, let me first define what a system diagram is and what it is good for.


### Definition and goal: System diagram

A **system diagram** is a visual representation of a given real-world system landscape, typically located in the IT world.
In such a landscape a collection of systems and contained system components are connected to each other in order to make a specific functionality available to its users.

The **goal of a system diagram** is to explain how the structure of a system landscape looks like, and how the users interact with it.
Once the audience has understood this structure, the system diagram can be the  basis for discussions.

A system diagram could look like this:

![example system diagram - horizontal layout](diagrams/example-systemdiagram_horizontal-layout.png)


Typically, the **visual language of system diagrams** consists of the following elements:

| Element | used to represent |
|---|---|
| stick figure | users |
| box | system, system component, environment |
| cylinder | data storage system |
| cloud | environment which is huge and/or unknown |
| arrow | call dependency, data flow |
| text | name of a visual element |

In addition, certain types of shapes (typically the boxes) can be placed inside other shapes to represent that one element contains or consists of other elements.


### Why should you care about how system diagrams look like?

Maybe you think that it is more important to create system diagrams correctly, compared to how they look like.
To follow this "A over B" catchphrase style used in the <https://agilemanifesto.org> and <https://www.halfarsedagilemanifesto.org>:

"Correct and useful content over simple and easy-to-understand visuals"

I absolutely agree.

Of course, we first need to make sure that our diagrams contain the correct information, specifically created for the intended type of audience.
But then, once we have the correct structure defined, we should also make sure that the audience does not need to suffer too much when trying to understand the information.

I would like to demonstrate what I mean with a concrete example.
Below you see an example system diagram:

![example system diagram - reduced to the max](diagrams/example-systemdiagram_reduced-to-the-max.png)

I don't know about you, but I think that this diagram is already quite readable, and the audience should be able to understand

- with which system the user interacts,

- which systems store something in the database,

- which systems are somehow connected to which other systems, and

- what are the boundaries of the different elements.

Admittedly, this diagram is not very complicated because it contains only one user, three systems, one database, and in total six connection arrows.
With such a simple example, it should not be so important to put much emphasis on the visual style.

Well, let's see.

Let's have a look on another diagram which contains the exact same information.
But this time the creator applied a different visual style to the diagram elements.

![example system diagram - distracting and even hurting the eye](diagrams/example-systemdiagram_distracting.png)

In my point-of-view this diagram is much more difficult to read.
It is difficult to understand what all the elements are, and how they are related to each other.
The reason for this is a suboptimal usage of colors, fonts, shapes, and sizes and arrangement of elements in relation to each other.

Maybe you think that it was me who has created this second diagram in this difficult-to-read way on purpose, just to make a point, and that I exaggerated quite a bit.
The answer is: Yes, and no.

- Yes, I created the diagram intentionally like this, to make my point.

- No, I did not exaggerate.

If you don't believe me, please do an Internet search for the term "system diagram", and check the images your preferred search engine returns.
Some of them will be in a clean style, maybe similar to the first example diagram shown above.
But there also will be quite some images which are visually closer to the second example diagram.

I do think that if we put effort in the creation process to come to simple diagrams which strip unneeded clutter, the audience will thank us because it will be easier for them to get the information.
After all, these diagrams are not meant to be pieces of art.
Instead, their sole purpose is to convey information and to trigger people to talk about the diagram's topic.


### What is in for you?

If you agree with me that the second diagram is somehow suboptimal, and if you also agree that the creator should and could have done better, then we are on the same page.

Over the past years I have experimented a lot with visual tools which can be used to create system diagrams.
From those experiment results I distilled general tips and tricks I now apply when I need to create such diagrams.
These tips help me to create diagrams with a clean and consistent structure.

Now, if you invest your precious time in reading this text, you will find the list of all these tips.
Maybe you can take-away some ideas which support you the next time you have to create such diagrams yourself.


### Mind-map of the things to come (TODO)

_TODO: Create a proper and readable version of the following mind-map_
![slice 14](images/slice14.png)


## General guidelines

The foundation of all the tips to come are some general rules.
These rules are the **mission statement** for the style of visual representation for system landscapes.
Each of the following subsections explain one such rule.


### General guideline 1: Use simple visual attributes, avoid the "bling-bling"

Only use simple visual attributes like solid fill colors and 2D elements.
Avoid any other visual expression ways like drop shadows, pseudo 3D elements, and color gradients just "because you can".
Any type of visual aspect you use in your diagram should be connected to one type of information.
If you use a visual aspect just because your graphics software offers it, then resist the temptation:
Don't use it if it does not add any information to your diagram.

In the following I would like to show you some visual aspects I recommend not to use.


#### Do not use color gradients

Using a color gradient just because it "looks cool" is not very helpful.
It irritates the audience because they think that this gradient has some special meaning which in fact it does not.
And the gradient effect typically breaks down when you apply it to visual elements of different sizes.

----

**Example:**
The diagram below compares two system diagrams using solid and gradient fill colors for the boxes, respectively.
The gradient from top to bottom starts with yellow and ends with blue.
The fill algorithm of the graphical application I have used to create this diagram calculates all the colors in between in a linear transition.

![solid vs gradient color fill](diagrams/general-guideline_no-color-gradients.png)

The visuals of the diagram on the right side introduce some problems:

- The gradient fill makes it harder to read the text.
Of course, you could apply a brighter color as blue, but then there would not much be left from the gradient.
A gradient from a bright color to another bright color does not create much color transition.

- The gradient fill color looks different when comparing the taller box ("Huge Other System") with the other two.
As the taller box offers more vertical space to be filled, the audience can see more of all the intermediate colors.
In the example, a (quite muddy) green-ish color appears in the vertical middle.
The other two smaller boxes do not show this green-ish color because there is just not enough room available.
All in all this creates a different color appearance for the taller box although all three boxes should get the same color.

- Maybe just a minor thing:
At least in my perception the intermediate colors look somewhat polluted, as if there was some dust cover which has not been removed by the cleaning personnel.


#### Do not use 3D elements

As long as you do not plan to create a three-dimensional world in which the third dimension really has some specific meaning, stay away from any 3D perspective.
In my opinion, you will only stumble upon this additional dimension of complexity for no good.

----

**Example:**
In the example below, the two diagrams on the right side both apply an isometric 3D perspective.

![2D vs 3D](diagrams/general-guideline_no-3d-elements.png)

This shows the problems which arise because of not using 2D.

- In the upper right diagram the drawing tool's connection feature is used.
As the tool does not support real 3D, it applies the connectors in a wrong inconsistent way.

- In the lower right diagram I have manually corrected the inconsistencies, but now some arrow heads (visually correctly!) vanish.

Either way, you will only have some extra work to do with no real benefit as the third dimension does not convey any additional information.


#### Do not use drop shadows

Using drop shadows is a bit like using 3D for the diagrams:
It might look "more pleasing" or maybe even "more professional" (some say this is very important if you work in an enterprise environment).
But drop shadows do not provide any additional information; instead, they just add visual clutter to the scenery, and hence I recommend not using them at all.

----

**Example:** 
The following example diagram shows directly what the problems with the drop shadows are:

![without and with drop shadows](diagrams/general-guideline_no-drop-shadows.png)

Especially for the connection arrows it can look like as if there is another arrow directly below or next to the main ones.
This can be confusing, and even if not, the audience need some extra effort to realize that there are no additional arrows, and that these drop shadows do not have any meaning whatsoever.


#### Do not use the "sketch" visual style

Some graphical tools seem to "know" that they are typically used in concept phases, and that the created diagrams represent something which is not yet implemented, but still is in draft.
To represent this draft status, these tools provide some "sketch" or "concept" or "draft" or "scribble" mode.
In such a mode, the diagram should look like as if a human being has manually drawn everything by hand.
The problem with such sketchy-looking diagrams is that it is just more difficult for the audience to understand what the diagrams want to say.
Therefore, just don't use these sketch modes.

----

**Example:**
The example below shows the difference when comparing the normal style with the sketch style.

![normal vs. sketch mode](diagrams/general-guideline_no-sketch-mode.png)

While I have to admit that the sketch style looks appealing, it adds visual clutter which is not necessary, and therefore I strongly vote for using the normal style.


### General guideline 2: Define the meaning of all visual elements in a legend

Always add a legend to your diagram.
A legend explains the meaning of all visual elements and attributes used in the diagram.
Without this legend, the audience has no other choice than to interpret the meaning of the elements of your visual language.
And if the audience needs to interpret, then this will cause misunderstandings.

Even if you use a well-defined visual language like UML for your diagrams, add a legend to your diagram.
Maybe you know all the elements of - for example - UML deployment diagram style (see <https://en.wikipedia.org/wiki/Deployment_diagram>), but you cannot assume that the audience knows this as well.
Adding a legend becomes even more important if you use your own visual language (like I do all the time).
If you don't define this language, the audience cannot know what a box with rounded corners means and how it is different from the boxes with sharp corners, or what is the difference between yellow and green fill style.

It does not stop with the boxes.
Maybe even more important than the boxes are the connection lines, with or without arrow heads.
Such a connection line expresses that there is some kind of association between the entities it connects to each other.
And if you find arrow heads at the end of a line, then obviously the association has a direction of some kind.

But: What does the connection line and its direction stand for?
What kind of information is transferred via the connection?
Is this connection relevant during design, deploy, or runtime?
Do the arrow heads show the direction in which data flows, or do they show which systems call which other systems?
We cannot know until there is a legend which clearly defines this.

----

**Example:**
The following system diagram I have already shown in the introduction section, but now it finally also contains a legend (which I should have added to the example in the first place anyway).

![example system diagram - reduced to the max, now with legend](diagrams/example-systemdiagram_reduced-to-the-max_with-legend.png)

You might notice another small change in the diagram compared to the first version shown in the introduction section:
The connection arrow from "User" to "System A" has a "uses" annotation.
I could have put this type of relation "User uses system" also as an additional entry in the legend, next to the "System calls system" annotation.
But as this "User uses system" relation type only exists once in the diagram, I find it easier for the reader if the type of relation (i.e., "uses") appears directly next to the connection arrow.


### General guideline 3: Apply high-contrast coloring style

If you apply "enough" contrast to your diagrams, it becomes easier for the audience to tell all the contained elements apart.

In the visual domain, the term "contrast" defines the difference in either luminosity and/or color when comparing visual elements.
For a given visual element (say, a rectangle) luminosity defines how much light the element emits/reflects whereas color defines the wavelength of the light the element emits or reflects.

To achieve the highest possible **contrast with luminosity**, you need to put a black (= the complete absence of light) element next to a white (= all the light there is, of all wavelengths) element.

To achieve the highest possible **contrast with color**, you need to put elements with their corresponding complementary colors next to each other.

This means in principle:
You should always use white as the fill color when you choose black as the border color (or the other way around).
In whatever way, putting black and white next to each other results in the highest possible contrast at all, and so we should only use this, right?

Well.
The world is not only black and white:

- You might need different fill colors in the same diagram because fill color is one major visual aspect you can use to express different values for the same type of system attribute.

- You typically have white also as the background color.
Now, if all the boxes are white, as well as the background, then again it might become a bit difficult to separate everything, even when there is black as a border color.

----

**Example:**
The diagram below, left side, shows one way of achieving high contrast:
Use black as the color for borders and arrows, as well as for text in these boxes, and use bright colors to fill the boxes.

![high vs. low contrast](diagrams/general-guideline_high-contrast.png)

On the right side you see the very same system landscape, but this time the brightness of all four different fill colors is significantly decreased while at the same time the color for borders and arrows is increased.

This results in a lower contrast and thus bad readability because

- the black text is now closer to the luminosity value of the fill colors, and

- the grey color of the borders and arrows is now closer to the white background color.


### General guideline 4: Use stroke width to support high-contrast

In addition to using color to increase the contrast, you can (and should) also include the appearance of lines to your visual toolbox as well.
Lines are the main ingredient of the connection arrows, but they also come into play if you add borders to your boxes.

To support high-contrast to the diagram, make the lines "thick enough" so that they stand out and thus clearly separate both the inner areas of boxes and the connection arrows from their surroundings, respectively.

Diagram applications typically call this "thickness of a line" the **stroke width**.
As both boxes and connection arrows consist of lines, you can typically change the stroke width for both.

Unfortunately, it is hard to define concrete values for stroke widths to make lines "thick enough" because these values are completely relative to the complete size and shape of the whole diagram.
As a rule of thumb, choose the stroke width in such a way that it has a similar impact on the reader's attention as the boxes themselves and the text inside and outside these boxes.

----

**Example:**
Have a look at the following example diagram which shows different stroke width's values in action.
In this concrete example I would strongly vote for the "medium stroke width".

![stroke width](diagrams/general-guideline_stroke-width.png)


## Canvas

The canvas is the virtual piece of paper or whiteboard on which you draw your system diagram.

Typically, when you create a new file in your drawing application, there is a blank page with a white background color visible which awaits your creativity output.
This blank page is the canvas.

Even if the canvas naturally stays in the background all the time, there are some tips here as well which support you later when creating the actual diagram.


### Canvas guideline 1: Use infinite space

If possible, configure the canvas to have no boundaries which otherwise would restrict the available drawing estate.
The canvas should provide endless space to you so that you can place new visual elements anywhere you want during your design process.

If you have to define a canvas size upfront like 210x297 mm (DIN-A4) or 1920x1080 pixels (FullHD), this might tempt you to violate any layout principles which you normally would follow just "because the available space is out".
At the beginning of your creative process the drawing tool you use should not enforce any boundaries to you.
Such boundaries have no good reason because the only thing they do by restricting the available space is that they also might restrict your creativity process.

----

**Example:**
Let's say your company wants to increase marketshare and therefore would like to offer a new set of features to their service portfolio.
The idea is that these new features would attract many more customers.

You are in the position of a solution architect, and it is therefore your task to make a first draft of which new systems your company would need and how they would integrate into the existing system landscape.
Before you spend hours with describing all of this in a text document which nobody would read, you instead decide to create a system diagram which shows the upcoming changes visually.

*Step 1: You create a new file to get started*

So, you start you favorite drawing application and create a new file.
The drawing application asks you which page size you need.
Well, as you are at the beginning, you don't really know how many visual elements you need to add to your system diagram.
If you would know this already now, then most likely your job as a solution architect has already been finished.
In lack of any second-sight-abilities you just pick the default value which is FullHD (1920x1080 pixels).

The drawing application presents a canvas and a grid like this:

![infinite space 1](diagrams/canvas-guideline_infinite-space_1.png)

As you have no idea how the new systems can be integrated, you start warming up your diagramming skills by first drawing the current situation.

*Step 2: You add visual elements to represent the existing system landscape*

You add the typical frontend, backend, and database elements.
You start more or less at the upper left corner, and then add all other elements from left to right.

The diagram now looks like this:

![infinite space 2](diagrams/canvas-guideline_infinite-space_2.png)

Hm, looks good!
You have made use of the grid to align all elements in a evenly distributed way.
The horizontal distance between the elements is three blocks.
And the two boxes have a width of four boxes.
You like the airy design, leaving enough negative space to make it easy to the reader to understand the structure of the current system landscape.

But then you realize that you have forgotten an important part of any such diagram.

*Step 3: You add a forgotten element (the user)*

How could that happen? you ask yourself.
You have forgotten to add the user to the diagram.
The original goal of this whole exercise was and still is to offer new services to the customers.
Then maybe the system diagram should also contain a visual representation for them.

You want to add the stick-figure to the diagram.
You realize that you need to place it left of the "Frontend" box because you like the idea of arranging all visual elements from left to right, following the direction of the dependencies.
Unfortunately, there is not enough room because left of that box is already the boundary of the canvas.

But ok, not a big deal, you think.
You just grab all elements and move them to the right to free the space left of the "Frontend" box.
And then you add the stick-figure to represent the user.

After that change, the diagram looks like this:

![infinite space 3](diagrams/canvas-guideline_infinite-space_3.png)

The result still looks pleasing.
But you already get a first hint that maybe you were lucky so far that there has been enough horizontal canvas space available.

*Step 4: You add more visual elements to represent possible changes to the system landcape*

For the new features your company has been in discussion with a third-party vendor.
This vendor states to have a solution which would cover most of the features your company has in mind.
After careful consideration of the vendor's advertising material, and after a first meeting with them, you think you have understood enough about how a possible integration could look like.

You add more visual elements to the diagram.
To be able to better separate existing from possible new elements, you choose a different fill color for the new elements.
And yes, you already make a mental note that you definitely need to add a legend later.

After a short break and a coffee, you look at the result again:

![infinite space 4](diagrams/canvas-guideline_infinite-space_4.png)

The diagram still looks nice, but actually you had to violate the guideline that the placement of visual elements should follow a left-to-right order, according to the order of the dependencies.

And also you realize that the "Backend Integration Adapter" box needs more vertical space because currently its text looks a little bit crammed.

You decide that it is time for a bigger refactoring of the diagram.

*Step 5: You refactor the diagram*

Because you are quite picky when it comes to diagrams, you plan to refactor the diagram to meet the following rules:

- Any connection arrow needs to go from left to right because only then the connections follow the dependency order.

- All boxes need to have the same size.

- All distances between elements need to have the same size.

After some reshuffling of visual elements you realize that the canvas in its current size does not provide enough horizontal space, at least not if you also want to have a distance of three boxes between any two boxes.
You decide that a distance of two boxes would also be ok.
You do the change.

Dayum, the available horizontal space still is not enough:

![infinite space 5a](diagrams/canvas-guideline_infinite-space_5a.png)


You have to make a decision: either you increase the canvas size, or you decrease gap sizes even more.
As it is the whole point of this section to show that these canvas boundaries are not doing any good in the first place, you can't help but to decrease distances again, at least at some places.

After the refactoring, the diagram looks like this:

![infinite space 5b](diagrams/canvas-guideline_infinite-space_5b.png)

Now the distances between elements don't have the same size anymore.
Some are one, some are two boxes wide.
But ok, some say that perfectionism can be sub-optimal at times.
Admittedly, the diagram still looks nice, and the reader can still understand how the different systems are connected to each other.

Therefore, you call it a diagram day.
For many creative processes it is a good advice to regularly step away from the current state of your creation, let some time pass, and come back later to re-evaluate your work with a refreshed mind.

*Step 6: You add some more forgotten elements (the DWH and a database)*

When you come back several hours later, you realize that it has been a good idea to step away.
You have to face the fact that you have forgotten a major aspect of the integration.
The vendor people told you that in order to get proper reporting, you need to have an event bus mechanism in place which consumes event data during runtime and sends it to the datawarehouse (DWH) systems.

Of course your company already has a DWH up and running - you only forgot to add it to the diagram.
The DWH currently gets its data from the database via an asynchronous process.
Each time the backend changes data, the database sends a message including the data to an event bus, and the DWH consumes these events and data from there.

And while you think about the database, you realize that you also have forgotten that the vendor backend also needs to store its own data in a separate database.

Sigh.
It can't be helped, you have to extend the diagram even further.

Like this:

![infinite space 6a](diagrams/canvas-guideline_infinite-space_6a.png)

Again there is not enough horizontal space available, and this holds true even if you would not increase the database symbol width from two to three boxes (you just noticed this inconsistency at this point in time).
Whatever, you don't see how you can solve the lack of space without further bending of the rules you wanted to follow for designing the diagram.

After careful bending of the rules, you come up with the following result:

![infinite space 6b](diagrams/canvas-guideline_infinite-space_6b.png)

This diagram might still look pleasing to the eye, but you cannot deny that you had to violate the layout rules even further.
And you only had to do it because the canvas size is too limited, and for no good reason.

*Final step: You create the diagram you actually wanted to create*

Just to get an idea of how the diagram could/should look like if you would be able to follow the layout rules, you disable the canvas size at all and just draw with no boundaries in mind.

The result looks like this:

![infinite space final](diagrams/canvas-guideline_infinite-space_9.png)

This diagram follows several layout rules:

- Any system box (incl. database) has a size of 3x2 units.

- There is an invisible grid which defines four horizontal and seven vertical lanes on which symbols are located.

- The connection arrows follow the flow of dependencies.
Any incoming dependency enters a box from the left, and any outgoing dependeny leaves a box from the right.

You can find more details about layout rules in a later section of this document.


### Canvas guideline 2: Set-up a square-shaped grid with reasonable absolute dimensions

Select a square-shaped background grid with absolute dimensions as a layout guide, for example something like 10 mm x 10 mm, or 50 pixels x 50 pixels.

Any decent graphics application allows to specify such a grid which is only shown in the background, but is not part of the actual graphics you design.
The grid supports you with aligning visual elements horizontally and vertically by just looking at your graphics, with no need to use alignment tools the graphics applications typically offer.
It is of course nice that the applications have such alignment tools, but if you need to always use them to align any two boxes or connection arrows, it will cost you quite some time (and nerves).

There is no general rule for which exact grid values you should choose because this heavily depends on the type of graphics application and screen size you use.
The chosen grid size should be reasonable in such a way that it

- already allows you to horizontally and vertically align visual elements just by looking at them, but

- also leaves enough granularity to place the visual elements in the way you need.

As a rule of thumb I suggest the following process to come to reasonable values for the grid dimensions:

1. Bring your graphics application into fullscreen mode.

2. Select a view factor of 100%.

3. Have all the typically needed panels (e.g. "Shapes", "Properties", "Layers") visible which the graphics application offers.

4. Now, select the grid dimensions in such a way that about 40 squares fit horizontally.

----

**Example:**
The screenshot below shows how I chose a 20 pt x 20 pt grid in the graphics application "draw.io", and that about 39 square boxes fit in the available horizontal space.

![square grid](images/screenshot_drawio_canvas-guideline_grid.png)

----

Whatever grid size you use, make sure that these values are defined as absolute values like 10 mm, and not as relative values like "small" or "10% of view window".
Some graphics applications offer a relative or adaptive grid mode in which the grid size change depending on the current zoom level you chose.
While this relative or adaptive grid makes sense when you - for example - need to fine-tune an organic-looking illustration, it can be irritating when creating system diagrams.


### Canvas guideline 3: Enable snap to grid

Enable the snap-to-grid feature in your graphics application to make sure that the grid you have selected (see [canvas guideline 2](#canvas-guideline-2-set-up-a-square-shaped-grid-with-reasonable-absolute-dimensions)) really supports you with getting all visual elements aligned.

If possible, configure the snap feature to be "merciless".
That means:
Your graphics application should not allow you to place visual elements to locations which do not fit the grid settings.
Only then you can be sure that you get the intended horizontal and vertical alignment out of the box.

----

**Example:**
The diagram below shows what can happen if you just set a grid, but do not enable the snap-to-grid feature.

![square grid](diagrams/canvas-guideline_snap-to-grid.png)

On the left side all the six visual elements (three boxes, three connection arrows) are perfectly aligned to the grid.

The right side, however, shows what can happen if you have admittedly defined the grid, but for whatever reason not enabled the snap feature.
At first glance, the six visual elements are aligned more or less ok, but if you look closer, you see that the elements are placed a little bit "off".
This results in that the connection arrows are jagged, giving the whole diagram a somewhat noisy look.

For such a small diagram it might not be a big issue, but imagine a larger diagram which contains several dozens elements.
In such complicated diagrams it disturbs the reader if straight lines are in fact not straight lines, and if boxes which belong in one invisible row or column are slightly off-balanced.


## Text

Although a system diagram mainly focuses on combining graphical elements like boxes and connecting arrows, it cannot live without text.
The reason for this is that the boxes and arrows alone are too abstract.
They do not provide enough variety to express all the details of the system landscape which the diagram strives to explain.
In the end, they are just boxes and connecting arrows.

Even a quite extensive visual modeling language like [BPMN 2.0](https://en.wikipedia.org/wiki/Business_Process_Model_and_Notation) with its plethora of different shapes which all have concrete meaning cannot work without text.
The modeler needs to label a given shape to define what she exactly means with that shape in the given situation.

Likewise, in a system diagram the main usage for text is to label the boxes which represent different components of the system landscape.
Each label stands for the corresponding component's name, giving it a unique identity.
Otherwise, without the labels, there would be only boxes which would all look the same.
The reader would have a hard time with understanding what all the components in the system landscape were.

As with the other graphical elements, there are also some guidelines for using text in such a diagram, and as you have already expected, you can find the in following sections.


### Text guideline 1: Use sans-serif font face

Choose a sans-serif font face with a homogenic stroke width for all kinds of text in your system diagram.
Typical examples for such sans-serif font faces which are installed out-of-the box on many operating systems are Arial, Helvetica, Tahoma, and Verdana.

----

**Example: various sans-serif font faces**
Following table shows three sans-serif font faces in four different sizes to give you a first impression about how these look.

![example sans-serif font faces](diagrams/text-guideline_sans-serif-font-face_1.png)

----

Do not use serif, fancy display, or - worst of all - handwritten font faces because they can significantly reduce the readability.
All the addendums to the font faces like serifs and all the other fiddly odds-and-ends "pollute" the image, making it harder for the reader to read what is written.

This is especially important when you need to put a lot of visual elements and hence a lot of name labels to your diagram.
When you have that many elements in your diagram, the reader obviously needs to zoom out quite a bit if she wants to see the whole diagram, and then all the text will become relatively small.
In general it is true that the smaller the text, the more difficult it becomes to read.
But when not using a clean font face, the negative effect becomes unnecessarily amplified.

By the way:
This is the very same reason why traffic signs also use simple sans-serif fonts instead of more complicated ones.
The written text needs to be readable already from far away as good as possible, and this is perspective-wise the same as zooming out a given diagram.

----

**Example: sans-serif vs. serif font faces**
Below you can see the same text first in the sans-serif font face "Helvetica" compared to two common serif font faces "Garamond" and "Times New Roman".

![compare sans-serif font face with serif font faces](diagrams/text-guideline_sans-serif-font-face_2.png)

Depending on the zoom size you are currently using when viewing this text, you might see the difference when comparing text set in sans-serif with serif font faces.
Especially in small sizes the text set in sans-serif font is better readable than the one in serif font faces.

----

**Example: sans-serif vs. fixed font faces**
If you don't like to use a sans-serif font face, but agree that standard serif font faces are also no good alternative, then a possible compromise could be using a serif fixed font face.

So far, the font faces shown in the examples above were all proportional fonts.
"Proportional" means that separate characters get a different width when put next to each other to form complete words.
The character "i" needs less horizontal space than the character "w".
When using a proportional font face, the character "i" really gets less horizontal space than the character "w".

In contrast, when showing the same characters "i" and "w" in a fixed font face, all characters get the very same width.
This can lead to unbalanced (and therefore ugly) use of whitespace in written text, and this unbalance is the reason why you should not use a fixed font when displaying a longer text. 

But in system diagrams we typically don't display longer text, but instead we just have to show names of components and the like.
Using a fixed serif font face can be an alternative.

Below you see the comparison between the sans-serif proportional font face "Helvetica" and the serif fixed font face "Courier New".

![compare sans-serif font face with fixed font faces](diagrams/text-guideline_sans-serif-font-face_3.png)

Personally, I could accept using "Courier New", but only in the bold style (right column) because in the normal style (middle column) the stroke is too small, resulting in quite thin letters, and therefore make the text more difficult to read.
One drawback of such a fixed font face might be that you typically need more horizontal space for the same text compared to proportional font face.


### Text guideline 2: Select font size in relation to box size

When placing text inside boxes, choose a font size which sets the text in a good-readable relation to the box sizes.
The font size should be chosen in such a way that the reader can still read the text when looking at the diagram as a whole.
Stated differently: Neither should the text get lost in the vast emtpy area inside the boxes, and nor should the text constantly touch or even leap over the border of the boxes.

Like with other settings, it it not really possible to define absolut size values here because such sizes depend on the size of the boxes.
Therefore, following example shows good and bad choices of font sizes to make it understandable what I mean.

----

**Example:**
Below you see the same system diagram in three different variants.

![font size and box size](diagrams/text-guideline_font-size.png)

The one on the left shows a quite balanced relationship between the sizes of font and boxes.
The two on the right, however, show what happens when the font size is either too small or too large compared to the box sizes.


### Text guideline 3: Use font style to guide to important parts first

In addition to font attributes like face and size, you can also use the font's style to your benefit.
If you choose styles "**bold**", "normal", and "*italics*" in a meaningful way, then this will guide the reader to the important parts first, and only when she has understood these she will head over to the remaining parts of the diagram.

When solely looking on the difference between these three different styles, it seems that this does not make a big difference, and yes, this might be true.
But when combined with all the other guidelines, small differences like font style add up to something which makes a huge difference when applied to a complete and complicated system diagram.


#### Use bold style for all important names

This might not come as a surprise to you:
Text set in the bold style catches the reader's attention, especially when set in contrast to text in normal style.
You can make use of this feature to guide the reader to the important parts of your system diagram first.

----

**Example - all names are set in bold style:**
Below you see the standard way of how to use bold style in a system diagram.

![font style bold for all names](diagrams/text-guideline_font-style_1.png)

The left variant uses bold style for all the system names, whereas the right variant just uses the normal style.
When using the bold style, the system names pop out more and therefore better catch the reader's attention.
Especially when zoomed out, text in bold style is better readable because the font's stroke is larger.

----

**Example - names set in bold style emphasize a certain property:**
Sometimes you don't want to lead the reader's attention to all the systems, but only to those with a certain property.
The example diagram below shows how you can use bold style to put focus on the new systems first, and only then to the old systems.

![font style bold for names of new systems](diagrams/text-guideline_font-style_2.png)

The left variant shows how only the new systems' names are set in bold style, while the remaining old systems' names are set in normal style.
Because the bold style names pop out more, they catch the reader's attention first.

Just as comparison the two system diagrams on the right side show how to maybe not use the option between bold and normal style.


#### Use normal font style for all companion text

The previous section already contains an example in which we mix both bold and normal style text for the same type of diagram elements.
To generalize this: Use normal style for text which you would like the reader to notice and focus on after she has seen the most important text of the diagram.

Typical examples for such companion text are notes attached to certain boxes, or the description shown in the legend.

----

**Example:**
The image shown below compares how a slightly more complicated system diagram looks if bold and normal style used together to set the focus on the more important parts first.

![font style normal for companion text](diagrams/text-guideline_font-style_3.png)

The diagram on the left shows how the system names make use of the bold style, while the additional notes and the text in the legend is written in normal style.

Compare this to the "all bold style" approach on the right side.
Yes, the text in general is well readable, but as all text is in bold style, the reader does not really see where to look first.


#### Use italics style for meta information only

In general, text in italics style is less readable than normal style.
Therefore, do not use it for the main content of your system diagram because it only makes it even harder for the reader to get a grip on the information.

Instead, use italics style for information which has meaning on a meta level.
Typical example would be if you have some todos or questions about the diagram which you plan to discuss with your colleagues.

----

**Example:**
The system diagram below shows how italics style text can be used.

![font style italicy for meta information](diagrams/text-guideline_font-style_4.png)

There is a bullet point list titled "TODO" to the left free area to show the reader that certain aspects are not yet completely decided or clear.
Once these open points have been clarified, I would completely remove this text section from the diagram.


## Boxes

Besides the connection arrows (see next chapter), boxes are THE basic types of visual elements in our system diagrams.
I consider boxes and connection arrows as the backbone tools when creating abstractions.

Using a box in a diagram to represent something from the real world serves two purposes:

1. **Each box represents an entity.**
If we want to give that entity a name, we add the name as text inside the box.
With this high abstraction, we do not tell the reader more than a) there is something which can be told apart from the rest, and b) this something has a name.
This "reduced to the max" approach helps the reader to focus when we want to discuss a certain system landscape on a high level.
Typically, such entities are systems and/or system components of some sort.
![call dependency](diagrams/box_representing-systems.png)

2. **Boxes inside other boxes represent a hierarchical structure.**
Extending the simple abstraction from the previous paragraph:
We can draw boxes inside other boxes, forming a hierarchical structure (aka a tree).
With such a tree we tell the reader that some entity belongs to or is contained in another entity.
A typical example in a system diagram would be a complete application which consists of several components.
To represent this structure in a diagram, you would create a big box (the application), and in that big box you would add some smaller boxes, one box for each component.
![call dependency](diagrams/box_representing-systems-containing-components.png)

If you need to represent more types of information besides "There is something", "This something has a name", and "This something belongs to something else", you can use additional visual attributes like size, border stroke width, or background color as abstractions for these information.

The remaining sections of this chapter define certain guidelines for how to use these visual attributes to help the reader to get a good grip on the information.


### Box guideline 1: Use same size for boxes which represent the same type of entity

If you want to represent different entities as boxes in your system diagram, and if these entities are of the same type, then make all these boxes the same size.

The size of such a box is a visual attribute like color or stroke width.
Bigger boxes attract the reader's eye more than the smaller ones.
If you choose different sizes for the same type of entity you signal to the reader that the size has some special meaning.
She might think that entities represented by bigger boxes are more important, more complicated, or more expensive than the smaller ones.

If you choose different box sizes intentionally because you are aware of this effect, then kudos to you.
But: If you do this by intention, then you need to specify the meaning of these different sizes in the legend because otherwise the reader cannot know what that meaning might be.
Ha, gotcha, I bet you didn't think of this. :-)

And while we are at betting:
I would also bet that in 99.9% of the diagrams the real reason for having different sizes for boxes which represent the same type of entities is because the various names of the entities need significantly different space.
Diagram tools dynamically adjust the size (typically, the width) of boxes when you extend the number of characters needed for the names above a certain threshold.

That the tools have this auto-adjust feature is nice when you are just right in the middle of creating something when speed is very important.
But once you finished getting the information represented correctly in your diagram, you should invest some additional time to synchronize all the box sizes.
If you notice that you would need to extend the size for all boxes because there is just one box with a significantly longer name, then consider to abbreviate the long name until it fits to the current box size for the entity type.

----

**Example:**
A typical example of such types of entities are the "system" or the "application", or the contained "components" or "modules".

The two system diagrams shown below both represent the very same system landscape, but use the box sizes differently.

![same box size for same entity type](diagrams/box-guideline_same-size-for-same-entity-type.png)

The diagram to the left shows the in total seven boxes in the exact same size because each box represent one system.

Compare this to its pendant to the right which shows the same seven boxes as well, but this time uses different sizes for each of the boxes.
As the seven systems are just that, namely systems, with no further meaning or property, chosing different box sizes can be (and in my opinion is) confusing.


### Box guideline 2: Choose width and height for inner-most boxes to be even multiples of canvas grid size

Choose values for the inner-most boxes' width and height to be even multiples of the canvas grid size.
Let's invent a specific name for this: the "even multiple rule".

If you follow this rule, it will be very easy for you to align the connection arrows directly at the center of any of the box's edge.
The grid (with [snap-to-grid enabled](#canvas-guideline-3-enable-snap-to-grid)) will guide you to place the connection arrow at exactly the correct points.
This can come quite in handy especially if your diagram tool does not support boxes with "magnetic connectors" which glue connection arrows to the center of either the box itself or the edge of the box.

But even if your diagram tool has such a magnetic connector feature, it still has advantages to choose the width and height according to this "even multiples rule":
Sooner or later, when you need to connect more and more boxes with connection arrows, you will need to manually layout the path of the connection arrows.
And if the boxes' width and height are even multiples of the grid size, it will be straightforward to layout the paths because the snap-to-grid feature can support you here as well.

----

**Example:**
The following image shows how the "even multiple rule" allows you to benefit from the snap-to-grid feature (and how it does not if you apply an "odd multiple" rule).

![even multiple rule 1](diagrams/box-guideline_even-multiple-rule_1.png)

The diagram on the left follows the "even multiple rule", and therefore the start points and end points of the connection arrows are exactly aligned to the grid.
The snap-to-grid feature of your diagram tool can support you to align the connection arrows directly by hand.

The diagram on the right, on the other hand, shows how the start points and end points are just in between the grid when you want to have them connected to the middle of the box edges.
If your diagram tool does not have a "magnetic connector" feature, if will become more difficult to align everything correctly.

----

**Example:**
To continue from the first example shown above:
The system diagrams in the following images contain more boxes and more connection arrows which forces you to bend the arrows and do some manual layout of their paths.

![even multiple rule 2](diagrams/box-guideline_even-multiple-rule_2.png)

Here the advantage of following the "even multiple rule" becomes even more apparent.
In the left system diagram the corners in the connection arrow paths still fit exactly to the grid.
Because of this and combined with the snap-to-grid feature, setting up the paths like this would be a breeze.

On the contrary, the diagram on the right clearly shows that also the corners of the connection arrows do not fit to the canvas grid.
It would be tedious to get the path layout setup like this because the snap-to-grid feature is of no use at all.
Even worse:
you need to disable snap-to-grid in this situation because otherwise it will actively prevent you from layouting the paths like this.


### Box guideline 3: Choose suitable size for inner-most boxes to allow making good use of the snap-to-grid feature

Choose values for height and width for the inner-most boxes in such a way that these boxes get just the right size compared to the canvas grid so that the snap-to-grid feature of your diagram tool can help you aligning boxes easily.
The boxes should be large enough that the snap-to-grid feature of your diagram tool still leaves you some flexibility while aligning the boxes to each other and adding connection arrows.
But the boxes should also be not so large that the canvas grid gets too fine-grained and therefore the snap-to-grid feature cannot help you anymore with the manual aligning.

Well, this is a pretty vague and also complicated-sounding guideline so far, I know.

Let's make it concrete:
A good starting point for the box size would be to just multiply the intended box's width-to-height ratio with the absolute size of the squares of the canvas grid.
If we assume that you would like to have boxes with a width-to-height ratio of 4:2, and if we also assume that the canvas grid squares have a size of 10x10 pt, then the resulting size for the boxes would be 40x20 pt.

If you need to assign many connection arrows between the boxes or put boxes inside other boxes, it might be a good idea to double the box sizes.
So, the boxes would get a size of 80x40 pt.
That would mean that the snap-to-grid feature's resolution would be twice as high, but most likely this would still be course-grained enough that the feature helps you.

But if you would increase the box sizes even more, you would soon reach the point where the snap-to-grid feature would have so many snapping positions in such a high resolution that the feature would not really help you any longer.

In the end you have to find the "sweet spot" compromise for your diagram tool and your needs by yourself.
Maybe you have a really good eye and can easily detect that boxes are not exactly aligned to each other - in that case you can choose bigger box sizes.
But in case you want to make the most out of the snap-to-grid feature, then you might want to select rather small box sizes.

----

**Example:**
The diagrams below show two different box-to-canvas-grid-size ratios.

![width and height and canvas size](diagrams/box-guideline_width-height-and-canvas-size.png)

The left diagram shows a useful box-to-grid size ratio:
The boxes cover 4x2 canvas grid squares.
This still gives some flexibility when aligning the boxes to each other.
For example, we could manually increase the gap between boxes from 2 up to 3 canvas grid squares just by dragging the boxes around.
The snap-to-grid feature would support you directly because you can easily tell the difference between a gap of 2 and 3 squares.

Compare this to the diagram on the right.
The canvas grid squares are four times smaller, thus the boxes cover 16x8 canvas squares.
At this ratio, the snap-to-grid feature becames less useful because it can easier happen that you accidentally align boxes and connection just a little bit off.


### Box guideline 4: Choose consistent corner curvature for rounded boxes

If you use boxes with rounded (instead of sharp) corners, then watch out what happens to the curvature of these rounded corners when you change the boxes' sizes.
Depending on the diagram tool you use it can happen that when you change the size of the box by dragging one of its corners, the diagram tool not only changes the box's size (which you wanted), but also changes the curvature of the box's corners accordingly (which you most likely not wanted).

A typical name for the attribute which lets you define the curvature is "radius" or "arc size".
For the remainder of this chapter I will stick to the term "radius".

The radius feature typically comes into two modes: **relative** and **absolute**.

In my experience, diagram tools have the relative mode selected by default, and it is this mode which can cause problems when you need to change the box's size later.
When the relative radius mode is selected, then the diagram tool will allow you to specify the radius value as a percentage.
Now, when you - for example - would double the box's size in both width and height, then the diagram tool has to make the corners twice as round as before because it needs to follow the configured percentage value.

Maybe this result is what you want.
But if you mix up boxes with softer and harder curvatures, then this can confuse the reader because she might start to think about if these different curvatures would have a special meaning.
Also, when you need to place boxes inside other boxes, the outer boxes would have softer curvatures, thus leaving less space inside the box.
This can lead to situations in which you place text or inner boxes already in the curvature area of the outer box which at least to my eye looks not very pleasant.

So, the best practice to prevent this kind of situation is to always choose the absolute radius mode.

If you change this mode from relative to absolute, the diagram tool will also change the corresponding value from a percentage to an absolute value.
Instead of something like "25%" the diagram tool would select a value of "20 pt" or just "10".
How such an absolute value concretely influences how soft or hard the diagram tool draws the rounded corners is specific to the tool.
You need to experiment how changing these absolute values affect how the tool draws the boxes.

But with the absolute value, you can be sure that when you change the size of a box this has no effect on how soft or hard the corners will appear.
Instead, the curvature does not change at all, and this is what you typically want.

----

**Example:**
For starters, the diagrams below show how same-sized boxes with different curvatures might confuse the reader.

![consistent corner curvature 1](diagrams/box-guideline_consistent-corner-curvature_1.png)

To the left you see how both systems A and B are represented by boxes of same size and curvature. Nice!

Compare this to the diagram on the right in which both boxes have the same size, but different curvatures.
The box corners for "System B" have a softer curvature than the ones for "System A".
The difference in the curvatures is so significant that the reader might think that this difference has a specific meaning.

If you go for the harder or softer curvature is up to you, but you need to choose the same curvature for the same type of boxes.

----

**Example:**
After the previous warm-up example let's now check how relative and absolute radius values affect how the diagram tool paints boxes and their corners in different sizes.

![consistent corner curvature 2](diagrams/box-guideline_consistent-corner-curvature_2.png)

As you can see in the left diagram, the actual size of any box does not affect how soft or hard their corners appear.
All corners have the same absolute radius value, and therefore the diagram tool draws all the boxes with the same curvature.
This not only appears pleasant to the eye (at least to my eyes), it also allows a consistent use of the available area inside the box.
You can keep the corner areas empty and still stick to the intended horizontal and vertical gaps between the boxes.

The diagram to right, however, shows that the corner curvature of the big surrounding "Network Zone" box is significantly softer than the ones of the inside "System" boxes.
And this happened although the selected radius value for all boxes are same.
But here the relative mode has been selected, and therefore the diagram tool needed to apply a larger radius to corners compared to the ones of the inner boxes.


### Box guideline 5: Choose different stroke widths when boxes are located inside other boxes

When you need to place boxes inside other boxes, then choose a different width for the strokes of the outer boxes than for the inner boxes.
By choosing different stroke widths you guide the reader's attention to the more important parts of your diagram first.

A typical scenario for using boxes inside other boxes would be when you want to represent that there are several systems located in different network zones.
In such a scenario I would reckon that the systems and how they are connected to each other are more important than how they are distributed over these different network zones.
Therefore, the strokes of the system boxes (and the connection arrows) should be thicker compared to the ones of the network boundery boxes.

----

**Example:**
The diagrams below compare the effect of having different stroke widths for different types of boxes.

![different stroke widths](diagrams/box-guideline_different-stroke-widths-for-boxes-within-boxes.png) 

The two diagrams on the left show how you can either put focus on the systems or on the network zones because of the differently sized stroke widths.

In the diagram on the right all the stroke widths are all of the same size.
The reader might interpret this as that the systems and how they are connected is equally important as to which systems are located within which network zone.
This does not necessarily need to be a bad thing, but normally you can decide which aspect is more important than another, and in such situation it would be a missed opportunity if you would not use the stroke width to lead the reader's focus accordingly.


## Connection arrows

In case you have already read the chapter about [boxes](#boxes), then the following sentences might sound familiar to you:

Besides the boxes, connection arrows are THE basic types of visual elements in a system diagrams.
I consider boxes and connection arrows as the backbone tools when creating abstractions.

While the box represents some kind of entity like a system or a system component, and - in case such a box contains another box - a "consists of" relationship, an arrow which connects two boxes represents any other kind of relationship between entities.
In a system diagram, there are typically two types of such relationships:

- **Call dependency:** The connection arrow shows that one system calls another system.
![call dependency](diagrams/connectionarrow_call-dependency.png)

- **Data flow:** The connection arrow shows that data flows from one system to another system.
![call dependency](diagrams/connectionarrow_data-flow.png)

Note the difference in the style of the arrow heads in the two diagrams above.
Which arrow head style you use is mainly up to you, but of course if you would have both call dependency and data flow living together in your diagram, you need to choose a different arrow head style for each of the two relationship types.

You will find more details about all of this in the following sections.


### Connection arrow guideline 1: Define what different types of connection arrows actually mean

If you use connection arrows (and you most like will use them), then define the meaning(s) of each type of connection arrow in the legend.

Yes, this is a repetition of the overall rule of [general guideline 2](#general-guideline-2-define-the-meaning-of-all-visual-elements-in-a-legend).
But it can't be helped, I need to repeat and detail it here.
I have seen it all too often that diagrams contained all types of connection arrows (or connection lines, when there were no arrow heads), but unfortunately they did not contain any explanation about their kind of meaning.

If you don't define the meaning, then readers need to start guessing about it.
They will ask themselves "Does this connection between these boxes mean a call dependency, or is just data flowing around, or both? Or is this even a different kind of animal?".
And you don't want that.
You want that the reader directly knows what kind of information you wanted to express with these connection arrows.


### Connection arrow guideline 2: Make different types of connection arrows appear differently enough

If you want to express more than one type of relation in your diagram, make sure that each type of corresponding connection arrow looks different enough.
Otherwise it will be more difficult than necessary for the reader to tell the difference.

While this guideline of "make different types of things look different enough" is relevant for all kind of visual elements, it is most important for the connection arrows.
And that is because even with thicker stroke widths the connection arrows are small when compared to the other elements of the system diagrams.

----

**Example:**
The two system diagrams shown below visualize the very same system landscape, but they vary the visual representation style for the two types of relations.
Check for yourself in which diagram you can better tell the difference between call dependency and data flow.

![different types look different enough](diagrams/connectionarrow-guideline_different-types-look-different-enough.png)

In the left diagram the visual styles for the call dependency on the one hand and data flow on the other hand differ quite a bit:

| Style                       | Call dependency | Data flow |
|-----------------------------|-----------------|-----------|
| Stroke width                | medium          | thick     |
| Stroke color                | black           | blue      |
| Style of end arrow head     | filled triangle | two lines |
| Style of start arrow head   | filled dot      | none      |
| Lines connected with boxes? | yes             | no        |

Compare this to the diagram on the right:
There the only difference between the two visual styles is the shape of the arrow head end.
The connection arrow end heads for call dependencies have the shape of a filled triangle, while the ones for the data flow have a "curvy" filled triangle.


### Connection arrow guideline 3: For call dependencies provide exactly one arrow head

If your connection arrow visualizes that a system calls another system, then provide exactly one arrow head at the end of the arrow.
By using one arrow head (and not zero or two), you give your arrow its direction, and this clearly defines which system calls which other system:
**The arrow always points from the caller to the callee**.

If you have difficulty in memorizing this meaning of the direction (I surely had in the beginning!), try the following mnemonic in which the arrow represents that someone is looking at someone else.

---
**Example:** Given is this situation in which A is looking at B:

```
A --> B
```
B might notice that someone (or something?) is looking at it, but as the direction arrow points towards B, B cannot see who is looking.

Now ask yourself:
What will happen if you remove B?
Let's see.

```
A --> (void)
```

If you remove B, then the outgoing arrow of A will direct into the void.
So, A surely will detect that something has changed, and this means that A somewho depends on B.
You cannot remove B without A noticing it.
And this is exactly the case in a system landscape in which a system A wants to call system B.
If B is not there anymore, then A cannot do this call, and thus A cannot work correctly.

Now do the cross-check by asking yourself:
What will happen if you remove A instead of B?
This results in the following situation:

```
(void) --> B
```

Hm, from B's perspective not much has changed.
There is still this incoming arrow, and that means that someone might be looking at B.
But as B could not see who has been on the other side of the arrow in the first place, B is in pretty much the same situation as before.
Translated into the world of system landscapes this means that system B still offers some functionality to the outside, even when there is no system A which would call system B.
Apparently, system B does not depend on system A.

---

Now that we have defined the meaning of the direction of a call dependency arrow, let's discuss why you should always have such a direction and why there should be only one (and not two).

If you just provide the connection arrow without any arrow head, you mainly tell the reader that you have no clue about which system needs which other system.
Instead you only say that "somehow" these systems depend on or know each other.
While this is maybe better than nothing, it is not good enough.
If you are already at the point that you can create such a system diagram, you already need to know enough to be able to define which systems need which other systems.

In the end, you must know about these dependencies anyways because otherwise you have no chance to detect if there are dependency cycles in your system landscape.
And because of this, you also don't want to have the arrow heads at both ends of the connection arrow as this would just mean that both systems need each other, and that would directly be such a cycle.
While there might be situations in which such a cycle might be acceptable, it is in general not a good idea to have them.

----

**Example:**
In the diagrams shown below you can see the difference between having arrow heads and having no arrow heads.

![have at least one arrow head](diagrams/connectionarrow-guideline_at-least-one-arrow-head.png)

In the left diagram you can directly see which system calls which other system.
For example, "System D" calls "System E" and "System F", while it is called by "System B" and "System C".
Even without knowing more details about these call dependencies, you can get a first impression on which system might be the entry point of the whole landscape (it is "System A" because there are only outgoing dependency arrows), and which system seems to be more of a data sink (it is "System G" as it only has incoming dependency arrows).
Besides, you can directly check if there are any call dependency cycles in this system landscape (there aren't, I double-checked this).

If you compare this with the pendant on the right side, you notice that without arrow heads this important dependency information is missing.
All these systems somehow have a relationship, but you cannot see where the entry points are or if there are any dependency cycles.


### Choose arrow heads to be big enough compared to diagram size (TODO)


### Avoid arrow heads in both directions for call dependencies (TODO)

_TODO. To me having arrow heads in both directions for a call dependency have a strong smell of being lazy or not precise enough. If you really have the same type of dependency in both directions, then make two arrows, one for each direction._


### Attach a bigger dot at the arrow start (TODO)

_TODO. This is especially useful if you cannot avoid that arrows cross each other because then the audience can make a difference between a real connection or just the restriction of the 2D projection._

![slice 07](images/slice7.png)


## Color (TODO)

_TODO: write introduction text to give an overview of what this section and its subsection contains._


### Choose color so that audience's attention will be guided to the most important diagram elements first (TODO)

![slice 21](images/slice21.png)

_TODO: An additional way to put emphasis on certain shapes (boxes and arrows) you can give them an outline border which is located behind the actual shapes. This can be handy if you want to tell the audience that some parts of your system landscape will be changed, added, or deleted. This additional outlone color is especially useful for the connection arrows because if you would change their fill color ... well, they don't have any fill color, do they? But if you do this, then you must add this part of your visual language to the legend._

![borders](images/visual-tips-for-diagrams_borders.png)


### Color styles (TODO)

![slice 19](images/slice19.png)


#### Black border, normal fill (TODO)


#### Black border, inverted fill (TODO)


#### No border, inverted fill (TODO)


## Layout of boxes and their connection arrows (TODO)

_TODO: write introduction text to give an overview of what this section and its subsection contains. This section is actually the "Grand Finale" of this whole article: All the tips for single aspects like boxes or arrows or colors only make sense if we finally put everything together in one complete diagram. And this section here does exactly this._


### Apply a "hidden grid" when positioning boxes (TODO)


### Flow either top-to-down or left-to-right (TODO)

![slice 11](images/slice11.png)
![slice 12](images/slice12.png)


### Place boxes in such a way to minimize the amount of corners in the connection arrows (TODO)


### Try to avoid crossing connection arrows (TODO)


### Never ever allow overlapping connection arrows (TODO)

![slice 10](images/slice10.png)


### Don't start or end different connection arrows at the same point (TODO)

![slice 09](images/slice9.png)


### Connection routing path styles (TODO)

![slice 08](images/slice8.png)


### Choose gap between boxes (TODO)

![slice 13](images/slice13.png)


## Closing words (TODO)

- _Thank the audience for spending their time._

- _Hope that it has been useful for the audience._

- _Invite audience to provide feedback._

- _Add contact information._

- _Recommend my favorite graphical application for creating system diagrams (which is draw.io).
Make clear that I am not related to draw.io in any way.
This is not advertisement._
