# Front End Development Libraries
These libraries are commonly used to speed up development of websites. I think I can get a website up and running and have more features available in it once I learn these technologies.  
Since this is an area that is rapidly evolving, I should focus on the core concepts behind them (which should be few) and learn them well.

## Bootstrap
A responsive CSS framework. You can design your site in such a way that it will look similar on screens of different widths.

### The meta viewport tag
You just need `<meta name="viewport" content="width=device-width, initial-scale=1">` for a responsive site. This is also required by Bootstrap. This is what it means:
* `initial-scale=1` sets the default zoom to 1, which means that each **CSS pixel** (the one devs use when they put x: 30px;) will be equal to a **viewport pixel** (controlled by the browser)
* `width=device-width` means the website width be equal to the device screen width. This option is basically telling the browser not to zoom around your website or feed it 

### Breakpoints
Also known as media query extends. A breakpoint is the conditions for a media query to be executed. For Bootstrap these are device widths (e.g. >=576px, >=768px etc). By default, the `xs` (width >= 0) breakpoint media queries are applied.  
Bootstrap uses `min-width` breakpoints since its meant for developers to develop for smaller devices first and then change accordingly as screen width increases.

### Containers
The basic unit in Bootstrap. They contain content and are responsive. The container classes are : 
* `container` which is a fixed width container. It has a specific `max-width` for each breakpoint.
* `container-fluid` has `width: 100%` for all breakpoints
* `container-{breakpoint_name}` has `width: 100%` till that breakpoint (inclusive) and then acts like `container`

### Grid
The Bootstrap grid is differnent from the CSS grid. This one is built upon flexboxes. It can contain rows, each of which are 12 columns wide. A grid is often placed in a container. You can have grids inside grids. The column elements, divs with the class `col` have equal widths but you can also set it for each one by changing the class to `col-{number_of_columns_to_use}` or even `col-auto` to fit the content.  
To create columns that start out stacked, occupying 100% row width and then fitting into a row you can use `col-{breakpoint}` which will go from stacked to fitting in a row once the breakpoint is crossed.  
You can control stacking at different device sizes by adding multiple classes, like this:
```html
  <!-- Columns start at 50% wide on mobile and bump up to 33.3% wide on desktop -->
  <div class="row">
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
  </div>
```  
The hierarchy of Bootstrap’s grid goes from container to row to column to your content.

There are also controls for columns and gutters which can help you implement the layout for your site in good detail. I understand it but I will "get it" only once I use it for something. Can't wait to do that!

## SASS
A language that extends CSS by providing features such as mixins (which are sort of like functions that can be included in multiple style declarations), conditions with if-else, for and while loops, multiple files, and a lot more! You can write less and more maintainable CSS this way!