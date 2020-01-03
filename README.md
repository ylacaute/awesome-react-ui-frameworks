
# Awesome React UI Frameworks

**WORK IN PROGRESS**

This is a **QUICK AND DIRTY** React UI framework comparison. I didn't spend so much time to write this page, don't take 
it seriously ! Many things have not be analyzed like I18N or SSR support, JS vs Typescript, Design process, how
easy it is to integrate those frameworks... 

## Introduction

Some frameworks has been eliminated immediately:
 - No online demo
 - Bad documentation
 - Open-source part too small
 - Dead frameworks

What have been (not deeply) checked:
 - The source code for a damn simple button
 - The generated code for a damn simple button
 - Icon management
 - Theming support

Notes:
 - When I speak about Tag, I speak about the dynamic html tag the component should use, usually given by user props.
 - When I speak about Ref, I speak about the ref on the child dom element, which is directly accessible from the used component.
 - When I speak about true CSS theming, I speak about the capacity to change a web site just by changing the CSS import (not changing it by JS code).

## Frameworks comparison

| Framework | Stars | Style | Icon | Completeness | Comment |
|-----------|-------|-------|------|--------------|---------|
|[Evergreen](https://evergreen.segment.com)|[9k](https://github.com/segmentio/evergreen/tree/master/src/buttons/src)|doc <style>, ugly generated CSS classes|integrated SVG|⋆|Clean industrial design, Designer framework, theming not supported, not pragmatic framework|
|[Material UI](https://material-ui.com/)|[53k](https://github.com/mui-org/material-ui/blob/master/packages/material-ui/src/Button/Button.js)|doc <style>, clean CSS classes with prefix|integrated SVG|⋆⋆|Material design, classic components, TS, great doc, heavy framework, no less nor sass, use Tag|
|[Ant Design](https://ant.design/)|[55k](https://github.com/ant-design/ant-design/blob/master/components/button/button.tsx)|CSS file, clean classes, prefixed|integrated SVG|⋆⋆|Minimalist design, TS, less, I18N, great chart extension|
|[Reactstrap](https://reactstrap.github.io/)|[9k](https://github.com/reactstrap/reactstrap/blob/master/src/Button.js)|bootstrap CSS file|no icon|⋆|Bootstrap design, Bootstrap as components, no less nor sass, use Tag|
|[React Boostrap](https://react-bootstrap.github.io)|[17k](https://github.com/react-bootstrap/react-bootstrap/blob/master/src/Button.js)|doc <style>|no icon|⋆|Bootstrap design, Bootstrap as components, no less nor sass, use Tag|
|[MDBoostrap](https://mdbootstrap.com/)|[1k](https://github.com/mdbootstrap/React-Bootstrap-with-Material-Design/blob/master/src/components/Button/Button.js)|CSS file, clean classes, no prefix|Icon font|⋆⋆|Material design, Bootstrap as components, no less nor sass, use Tag|
|[Primereact](https://www.primefaces.org/primereact)|[1k](https://github.com/primefaces/primereact/blob/master/src/components/button/Button.js)|CSS file, clean classes, prefixed|Icon font|⋆⋆⋆|Clean design, True theming support, many components, charts, a little bit late on tech|
|[Semantic UI](https://react.semantic-ui.com/)|[10k](https://github.com/Semantic-Org/Semantic-UI-React/blob/master/src/elements/Button/Button.js)|CSS file, clean classes, no prefix|Icon font|⋆⋆|Clean industrial design, use less for theming, use of Tag, a little bit late on tech|
|[Blueprint](https://blueprintjs.com/)|[15k](https://github.com/palantir/blueprint/blob/develop/packages/core/src/components/button/buttons.tsx)|CSS file, clean classes, prefixed|integrated SVG|⋆⋆|Clean industrial design, TS, use sass, no ref no tag|


**And the winner is... Primereact !**

I will try it, and update this page later.


## Others React UI Frameworks

- **Carbon Design system** (IBM) sounds correct but the design is not very nice
- **Atlaskit** (Atlassian) uses <style>, very minimalist design
- **Onsen UI** uses <style> but seems great, low design but nice support for mobiles 
- **UI Fabric** (Microsoft) uses <style>, low design
- **Gestalt** (Pinterest) only css modules, unreadable classes, forget CSS theming
- **Elemantal UI**, clean, but exactly like bootstrap, without bootstrap, no gain


## Philosophical though

## Icons

Ideally, the CSS should change your web site style, and it includes icons. That's means:
 - the content should describe the situation
 - the CSS should pick the right icon for this situation

Example of bad CSS usage which is defining the target icon rather than the content:
```html
  <i class="icon cross" />
```
This is exactly the same as:
```html
  <i class="red" />
  <i class="align-left" />
```
That is why a lot of web frameworks, like Boostrap, are not well designed. They do not respect the separation
of concern content Vs style. The situation is understandable, we gain simplicity. Almost no one need a powerful
theming system, nowadays a theme is almost resumed to a set of colors.

This is what we should do:
```html
  <i class="icon delete-user" />
```
With:
```scss
  .icon {
    .delete-user {
       // Define here, depending your CSS theme, what the icon looks like
    }
  }
  
```
Or with component:
```html
  <Icon type="delete-user" /> or even
  <DeleteUserIcon />
```

That is a problem for the component industry: they can't know the "situation" (here "delete-user") so they can't
bring us something correct as "a component". Unless... you start to use JS theming. If you bring the Icon as a
JS variable (from a JS theme), you don't care anymore to use a specific icon component as you can change it when
you change theme.

That is how I understand the situation today, but I am not sure to really understand the craziness of the
frontend development...


### Integrated SVG

| PROS | CONS |
|------|------|
|<ul><li>no http request</li><li>light</li><li>themable (color, animation...)</li></ul>|<ul><li>no true CSS theming (can't change icon with CSS, need JS theming)</li></ul>|

### Pure CSS icon

Same as integrated SVG, but with lower rendering quality.

### Font icon

| PROS | CONS |
|------|------|
|<ul><li>single http request</li><li>light</li><li>true CSS theming</li></ul>|<ul><li>partial theming (single color)</li></ul>|

 
 

