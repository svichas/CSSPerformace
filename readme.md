# CSS Performance

This repository is about how CSS makes your website faster or how CSS might slow down your website. Website performance is one of the most important feature of your website for the end user. Also consider that CSS one of the biggest contributor to slow render times and if your site takes forever to load, chances are your users aren't gonna wait for it to finish loading.

## Table contents

- [Render-tree Construction](render-tree-construction)
- [CSS selectors performance](#)
- [CSS load time performance](#css-load-time-performance)
- Chrome developer tools
- CSS syntax to avoid
- CSS Animation efficiency
- [Contributors](#contributors)
- [Sources](#sources)


## CSS selectors performance
We humans read left to right but browsers read CSS selectors from right to left. For an in-depth reason as to why they browsers do this [discussion](https://stackoverflow.com/questions/5797014/why-do-browsers-match-css-selectors-from-right-to-left)
It's more efficient for a browser to start at the right-most element (the one it knows it wants to style) and work its way back up the DOM tree than it is to start high up the DOM tree and take a journey down that might not even end up at the right-most selector–also known as the key selector.
- Use single class selectors.
- Don't use star(*) as a child selector.

> Roughly 50% of the time used to calculate the computed style for an element is used to match selectors...
[csswz.it/2GIs8l4](https://csswz.it/2GIs8l4)


## CSS load time performance
CSS is a render blocking resource. What to do about it?

- Don't use @import with CSS instead use <link/> in HTML

Example:
main.css just downloads fine but as soon as it opens this CSS file, main.css says go download those 4 files. We are creating long request chains and that increases render time by quite a lot. Web browsers can't start rendering until he gets all request file from the start.
[img/Screenshot_2.png]()

- Inline your CSS in HTML
The obvious and immediate caveat is that now the whole HTML document is huge! But downloading a large HTML document is bad because no other resources (images for example) can be downloaded in parallel whilst the browser is working on rendering the page with what it's downloaded so far.
`html
<style>
.site-header {height: 55px; background-color: #fff;} ...
</style>
`

## Contributors
- Stefanos Vichas

##Sources:
- https://csswizardry.com/2011/09/writing-efficient-css-selectors/
- https://developer.mozilla.org/en-US/docs/Web/CSS/Descendant_selectors
- https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css
- [Harry Roberts: FaCSSt—CSS and Performance](https://www.youtube.com/watch?v=2Rn8an74khk)
