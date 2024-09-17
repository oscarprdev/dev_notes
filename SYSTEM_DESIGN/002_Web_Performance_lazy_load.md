```typescript
<img src="" data-src="current url" /> // Set data-src and src empty

// Select all elements with data-src
let lazyEls = [].slice.call(document.querySelectorAll("[data-src]"))

// Add the data-src to src
function load(el) {
	let src = el.getAttribute("data-src")
	let srcSet = el.getAttribute("data-srcset")
	
	if (src) { el.attribute("src", src) }
	if (srcset) { el.attribute("srcset", srcSet) }
	el.removeAttribute("data-src")
	el.removeAttribute("data-srcset")
}

// If element is intersecting load element swaping the data-src to src
if ("InterserctionObserver" in window) {
	let lazyObserver = new IntersectionObserver((entries) => {
		entries.forEach((entry) => {
			if (entry.isIntersecting) {
				let el = entry.target
				load(el)
				lazyObserver.unobserve(el)
			}
		})
	})
}
```