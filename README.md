# ajaxe
jQuery AJAX framework inspired by bootstrap's html attribute triggers

* [How it works](#how-it-works)
* [Example](#example)
* [Usage](#usage)
	* [Via data attributes](#via-data-attributes)
	* [Via JavaScript](#via-javascript)
	* [Options](#options)
	* [Methods](#methods)
	* [Events](#events)

## How it works

The ajaxe framework is used to automate basic ajax calls. Forms, classes and data attributes are used to configure requests and responses.

## Example

```html
<form action="/search.php" method="GET" class="ajaxe" data-trigger="submit">
    <input type="hidden" name="id" value="123">
    <input type="text" name="search" placeholder="e.g. Cats">
    <input type="submit" value="Search">
</form>

<select name="search" class="ajaxe" data-trigger="change" data-action="/search.php">
    <option value="">Search a category</option>
    <option value="cats">Cats</option>
    <option value="dogs">Dogs</option>
    <option value="birds">Birds</option>
</select>

<button class="ajaxe" data-trigger="click" data-action="/search.php">
    <input type="hidden" name="id" value="123">
    <input type="hidden" name="search" value="cats">
    Search Cats
</button>
```

## Usage

Ajaxe utilizes a few classes to handle the heavy lifting:

* `.ajaxe` attaches ajaxe to listen on this element

### Via data attributes

Just add `data-trigger="event"` to tell ajaxe which JavaScript event to listen for.

### Via JavaScript

Enable manually with:

```javascript
$('.ajax-form').ajaxe();
```

### Options

Options can be passed via data attributes or JavaScript. For data attributes, append the option name to `data-`, as in `data-action=""`.

Name      | Type     | Default  | Description
----------|----------|----------|------------
action    | URI      | Page URL | The URI where the ajax call is sent.
animation | integer  | 400      | Slide animation time in milliseconds.
confirm   | string   | none     | Message to confirm before sending ajax call.
content   | selector | none     | Where to put the returned content on success.
feedback  | selector | none     | Where to put any feedback messages.
method    | string   | post     | Http method to use for ajax call.
timeout   | integer  | 10000    | Time to wait before closing the feedback container.
type      | string   | json     | Type of ajax response from the server

### Methods

### Events

Event Type               | Description
------------------------:|------------
success.ajaxe            | This event is fired after a successful ajax call
error.ajaxe              | This event is fired on an ajax error
expand.feedback.ajaxe    | This event fires immediately when the feedback element begins expanding.
expanded.feedback.ajaxe  | This event is fired after the feedback element is finished expanding.
collapse.feedback.ajaxe  | This event fires immediately when the feedback element begins to collapse.
collapsed.feedback.ajaxe | this event is fired after the feedback element is finished collapsing.


```javascript
$('#my-ajax-form').on('success.ajaxe', function() {
    // do something...
});

$('#my-feedback').on('expanded.feedback.ajaxe', function() {
    // do something...
});
```
