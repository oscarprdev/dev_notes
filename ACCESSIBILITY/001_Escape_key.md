*On showing something floating and use press escape key, parent component should be focused

```typescript

function AccessibleFloatComponent() {
	const [isVisible, setIsVisible] = useState(false)
	1. Ref to handler button
	const toggleButton = useRef()
	
	2. Create toggle method based on event code
	function toggleVisibility(event) {
		if (event.code === 'Enter' && || event.code === 'Space') {
			event.preventDefault()
			setIsVisible(!isVisible)
		}
	}
	
	3. Hanlde Escape button and focus again handler button
	function handleKeyDown(event) {
		if (event.code === 'Escape' && isComponentShowing) {
			setIsVisible(!isVisible)
			
			if (toggleButton && toggleButton.current) {
				toggleButton.current.focus()
			}
		}
	}

	return <div 
		onKeyDown={handleKeyDown} // Key down on parent component
		onMouseEnter={toggleVisibility}
		onMouseLeave={toggleVisibility}
		>
			<p>Some Text</p>
			<button 
				aria-label='toggle-button'
				aria-expanded={isVisible ? 'true' : 'false'}
				ref={toggleButton} // Ref button
				onKeyDown={toggleVisibility}> // Method to toggle visibility
				<Icon/>
			</button>
		</div>
}
```
