# jQuery ToggleAction Plugin

A jQuery plugin that allows binding event handlers that should be executed consecutively when the event occurs in succession. I made this plugin to accommodate the deprecation of the [.toggle()](http://api.jquery.com/toggle-event/) function as of jQuery 1.8

### Description

`.toggleAction( eventType [, eventData ], handler ... )`

## Usage

Toggle an element's background color between red, blue and green every time the element is clicked:

```javascript
$('#element').toggleAction('click', function() {
    $(this).css({"background-color":"#f00"});
}, function() {
    $(this).css({"background-color":"#0f0"});
}, function() {
    $(this).css({"background-color":"#00f"});
}
```
    
By default, bindings can be stacked; if you call .toggleAction() on an element multiple times with the same event type, the effects combine. For example, if you first called the function above, and then called

```javascript
$('#element').toggleAction('click', function() {
    $(this).css({"color":"#000"});
}, function() {
    $(this).css({"color":"#fff"});
}
```
    
The element would toggle its background color between red, green and blue, and change the text color between black and white on every click.

To clear all existing bindings of the same event type, or in other words, disable the so-called stacking, use the `clear: true` option:

```javascript
$('#element').toggleAction('click', {
    clear: true
}, function() {
    ...
}
```
