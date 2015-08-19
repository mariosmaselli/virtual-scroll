virtual-scroll
=====

Custom scroll event with inertia/momentum, touch (works on <=iOS7) and keyboard compatible.
This is a fork of Bartek Drozdz VirtualScroll util. See his [article](http://www.everyday3d.com/blog/index.php/2014/08/18/smooth-scrolling-with-virtualscroll/)) for a complete description.

### Goals of the fork
- Easier to add in a CommonJS / require environment
- Enable to create several distinct instances by using a prototype rather than a singleton
- Add some extra features
- modules (using a dedicated Emitter for instance)

### Installation
`npm i virtual-scroll -S`

### Usage & API
For in-depth usage and tutorial, you can check Bartek's article (link above).

- `new VirtualScroll(options)`
Return a new instance of VirtualScroll. See the options below.

- `instance.on(fn, context)`
Listen to the scroll event using the specified function (fn) and optional context.

- `instance.off(fn, context)`
Remove the listener.

- `instance.destroy()`
Will remove all events and unbind the DOM listeners.

Events note:
Each instance will listen only once to any DOM listener. These listener are enabled/disabled automatically. However, it's a good practice to always call `destroy()` on your VirtualScroll instance, especially if you are working with a SPA.

### Options
- mouseMultiplier: General multiplier for all mousewheel (including Firefox). *Default to 1.*
- touchMultiplier: Mutiply the touch action by two making the scroll a bit faster than finger movement. *Default is 2.*
- firefoxMultiplier: Firefox on Windows needs a boost, since scrolling is very slow. *Default is 15.*
- keyStep: How many pixels to move with each key press. *Default is 120.*
- preventTouch: If true, automatically call `e.preventDefault` on touchMove. *Default is false.*
- limitInertia: if true, will leverage [Lethargy](https://github.com/d4nyll/lethargy) to avoid everlasting scroll events (mostly on Apple Mouse, Trackpad, and free-wheel mouse). *Default is false.*

## Todo
- In-depth tests
- Possibility to pass a 'keys' options (bind other keyboard keys)
- Add a "direction" option to force a single direction?