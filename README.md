#Quickdroppable

Quickdroppable is a jQuery plugin that offers basic drag & drop HTML5 functionality with support for touch/mobile.  `draggable` elements can be dragged and dropped by the user into `droppable` elements, where they will be appended/inserted.

For a basic set up, use jQuery selectors to assign quickdroppable to your `draggable` and `droppable` html elements.  You must assign both `draggable` and `droppable` elements for Quickdroppable to work.

```html
<div id="draggable"></div>
<div id="droppable"></div>

<script>
  (function(){
  $(document).ready(function(){
    $('#draggable').quickdroppable('draggable');
    $('#droppable').quickdroppable('droppable');
  });
  })(jQuery);
</script>
```


Quickdroppable has a wrapper around touch events that we will emit simulated mouse events, so the same drag/drop functionality will also work on mobile.

Quickdroppable accepts the following parameters:

```text
type = 'draggable' or 'droppable'
options = {
	dragAssure: selector for drag target - might be parent of what was clicked,
	dropAssure: selector for drop target - might be parent of where it was dropped,
	dropCondition: selector for drop condition,
	insertBefore: selector for insert of dragged into drop,
	dragRemoveClass: class to add to drag/target element,
	dragAddClass: class to remove from drag/target element,
	dropRemoveClass: class to remove from drop element,
	dropAddClass: class to add to drop element
}
callback = will be executed before drag/drop event finished
```

If you do not have any special options but you do have a callback, you must pass an empty object before the callback when you assign quickdroppable.

```js
(function(){
	$(document).ready(function(){
		$('#draggable').quickdroppable('draggable', {}, function(){
			alert("I'm being dragged!");
		});
		$('#droppable').quickdroppable('droppable', {}, function(){
			alert("I was dropped!");
		});
	});
})(jQuery);
```

##Options for `draggable` elements
`dragAssure`, `dragRemoveClass`, and `dragAddClass` are meant as options for `draggable` elements.

 - `dragAssure` is the selector for the `draggable` item.  It ensures that when a user clicks on a child of of a `draggable` element, the `dragStart` event still fires.  Quickdroppable will look through 20 layers of children to try to find a matching selector to `dragAssure`.

 ```html
<div id="draggable">
	<p>If a user clicks me instead of my parent, the draggable event will still fire because the targetAssure option has been set to bubble up until it finds `#draggable`.</p>
</div>
<div id="droppable"></div>

<script>
  (function(){
  $(document).ready(function(){
    $('#draggable').quickdroppable('draggable', {targetAssure: '#draggable'});
    $('#droppable').quickdroppable('droppable');
  });
  })(jQuery);
</script>
 ```

  - `dragRemoveClass` and `dragAddClass` will add and remove classes to the `draggable` element when a drag event is started.  The classes are triggered by 




