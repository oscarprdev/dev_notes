```typescript
1. Create context
export const ThemeContext = React.createContext(null)

2. Create custom hook
export function useThemeContext() {
	const {theme, setTheme} = React.useContext(ThemeContext)
	
	return {theme, setTheme}
}

3. Create provider
export function ThemeProvider({children}) {
	const [theem, setTheme] = React.useState("light")
	
	return (
		<ThemeContext.Provider value={{theme, setTheme}}>
			{children}
		</ThemeContext.Provider>
	)
}
```