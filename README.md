# megamenu-js-bs4
Last responsive megamenu you'll ever need + Bootstrap4

Updated: November 21, 2019 

![Image of the Megamenu-JS](https://github.com/OrangeWacko/megamenu-js/blob/master/mega-menu-js.jpg)

## huge thanks to Michele Maietta (https://github.com/doppiam) for all contribution in this project.


## Features
- Bootstrap4 support
- Cross-browser compatibility
- No classes! (for dropdowns or lists)
- Smart - knows when to show megamenu, and when to show a normal dropdown
- 100% responsive, works on all devices
- Seamless wordpress integration
- Super fast
- Uses jquery animations (IE8 compatible)
- Easy to use
- Written in LESS (easy to abuse)
- Uses ionicons
- Super small
- Free to use and abuse (MIT licence)


## Demos
Download and open index.html **or:**
#### Live Demo
Live demo on Codepen:
[megamenu.js demo](https://codepen.io/orange_wacko/pen/wvvZaBK)



## Installation
1) This version uses Bootstrap4 CSS for the Demo index.html, so include the stylesheet from CDN: 
```
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
```
1.1) Copy CSS from **style.css** or **style.less**

1.2) megamenu.js uses [ionicons](http://ionicons.com/) for icons, so include stylesheet in your project: 
```
<link rel="stylesheet" href="css/ionicons.min.css">
```

2) Include jquery just before closing body tag `</body>`
```
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/1.12.0/jquery.min.js"></script>
```

3) Include **megamenu.js** **below** jquery
```
<script src="js/megamenu.js"></script>
```

4) Wrap your menus HTML in megamenu.js wrappers and see the magic :)

```
<div class="menu-container">
        <div class="menu">
                <ul>
                  <li><a>Link</a></li>
                  <li>
                    <a>Mega Link</a>
                    <div class="mega-menu"><!-- Whatever, basic html menu(lists)! Dont worry megamenu.js will know --></div>
                  </li>
                </ul>
        </div>
    </div>
```


## Usage and jquery explanation
This version uses Bootstrap4 to build HTML content inside the Mega-menu HTML containers. 
Its made with HTML
schematic logic in mind. Because of that **does not require custom walkers with wordpress**.
When jquery triggers for mobile menu, its appending HTML for mobilemenu so there is no need for checkboxes or anything else.
The menu is 100% autonomous, and smart.
#### Why is megamenu.js smart
megamenu.js knows if the dropdowns are too big and then shows them as megamenu. But if there is no need for a megamenu,
jquery is triggering a normal, classic dropdown menu. In real world, you maybe wont need all of the menus to be a megamenu, but
because of a attempt of a complete automation, the menu decides when and when not to show a menu as a megamenu.
#### Conditions integrated into megamenu.js
- **Classic dropdown menu**, when there is no need for a megamenu **(dropdowns LI element does not have another child)**
- **Megamenu**, when there are many levels of dropdowns **(dropdowns LI element has another child and so on)**
- **Megamenu with empty sub**, mixed condition of two before **(some LI elements have another child, some dont)**


## Wordpress integration
Since megamenu.js is not using classes for displaying drodowns, wordpress integration is seamless. That means custom walkers are not needed!
Wordpress is adding classes to every UL and LI element by default, so first thing you need to do is clear menu from classes.

**1)** In your functions.php add these lines ([taken from HTML5blank by @toddmotto](https://github.com/toddmotto/html5blank))

```
// Remove the <div> surrounding the dynamic navigation to cleanup markup
function my_wp_nav_menu_args($args = '')
{
    $args['container'] = false;
    return $args;
}
// Remove Injected classes, ID's and Page ID's from Navigation <li> items
function my_css_attributes_filter($var)
{
    return is_array($var) ? array() : '';
}

add_filter('wp_nav_menu_args', 'my_wp_nav_menu_args'); // Remove surrounding <div> from WP Navigation
add_filter('nav_menu_css_class', 'my_css_attributes_filter', 100, 1); // Remove Navigation <li> injected classes
add_filter('nav_menu_item_id', 'my_css_attributes_filter', 100, 1); // Remove Navigation <li> injected ID
add_filter('page_css_class', 'my_css_attributes_filter', 100, 1); // Remove Navigation <li> Page ID's

```

That clears the menu from everything wordpress has added and from this point the menu is like you are doing a static version.

**2)** Then simply wrap the wordpress menu with megamenu.js wrappers!

```
<div class="menu-container">
    <div class="menu">
      <?php wp_nav_menu(); ?>
    </div>
</div>
```

## Made with (thanks)
- [LESS](http://lesscss.org/)
- [Jquery](http://jquery.com/)
- [Ionicons](http://ionicons.com/)
- [Codepen](http://codepen.io)
- [Wordpress](https://codex.wordpress.org/)
- [HTML5Blank](https://github.com/toddmotto/html5blank)
- [Stackoverflow](stackoverflow.com)
