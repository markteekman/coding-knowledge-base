The Intersection Observer API provides a way to asynchronously observe changes in the intersection of a target element with an ancestor element or with a top-level document's viewport. It's usually a great way to add classes to intersecting elements which can be used to animate elements when they enter the users viewport.

>[More about the Intersection Observer on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API)

## Basic usage

```js
const observer = new IntersectionObserver((entries) => {
	entries.forEach((entry) => {
		if (entry.isIntersecting) {
			entry.target.classList.add('is-visible')
		}
	})
}, { 
	// options
})
	
const elements = document.querySelectorAll('.animate')
	
elements.forEach((element) => {
	observer.observe(element)
})
```