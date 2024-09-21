**It ensures that only one element in the group is focusable at any time**, allowing users who rely on keyboards (such as screen readers) to navigate more intuitively.

```typescript
const RovingTabindex = () => {
  // State to keep track of the focused element
  const [focusIndex, setFocusIndex] = useState(0);
  const buttonsRef = useRef([]);  // Store references to the button elements
  
  const items = ['Home', 'About', 'Services', 'Contact'];

  // Handle keydown events
  const handleKeyDown = (e, index) => {
    switch (e.key) {
      case 'ArrowRight':
	      // Go to next item, wrap around
        setFocusIndex((focusIndex + 1) % items.length); 
        break;
      case 'ArrowLeft':
	      // Go to previous item, wrap around
        setFocusIndex((focusIndex - 1 + items.length) % items.length); 
        break;
      default:
        break;
    }
  };

  // Focus on the active button whenever focusIndex changes
  React.useEffect(() => {
    if (buttonsRef.current[focusIndex]) {
      buttonsRef.current[focusIndex].focus();
    }
  }, [focusIndex]);

  return (
    <div role="tablist" aria-label="Sample Tabs">
      {items.map((item, index) => (
        <button
          key={index}
          // Assign reference to each button
          ref={(el) => (buttonsRef.current[index] = el)} 
          role="tab"
          // Roving tabindex logic
          tabIndex={focusIndex === index ? 0 : -1}  
          aria-selected={focusIndex === index}
          // Handle arrow key navigation
          onKeyDown={(e) => handleKeyDown(e, index)}   
        >
          {item}
        </button>
      ))}
    </div>
  );
};

export default RovingTabindex;

```


