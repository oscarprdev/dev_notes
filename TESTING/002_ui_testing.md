## <span style="color: #2196F3;">Basic</span>

```typescript
test('...', () => {
	render(<Component name='..'/>)
	const foo = screen.getByText(...)
	expect(foo).toBeInTheDocument()
})
```

```typescript
test('...', () => {
	render(<Component/>)
	const foo = screen.getByRole(...)
	expect(foo).toHaveTextContent()
	expect(foo).toHaveAttribute("role", "..")
})
```

## <span style="color: #2196F3;">Event handlers</span>

```typescript
test('...', () => {
	const onClick = jest.fn() // vi.fn()
	render(<Component onClick={onClick}/>)
	
	const element = screen.getByText(...)
	fireEvent.click(element)
	
	expect(onClick).toHaveBeenCalledTimes(1)
})
```

## <span style="color: #2196F3;">Mock service worker</span>

```typescript
const server = setupServer(
	rest.get("/api", (req, res, ctx) => {
		return res(ctx.json({ data: "mock response"}))
	})
)

beforeAll(() => server.listen())
afterEach(() => server.resetHandlers())
afterAll(() => server.close())

test('...', async () => {
	render(<Component />)
	
	const element = screen.getByText(...)
	const out = await waitFor(() => screen.getByRole(...))
	
	expect(out).toHaveTextContent("...")
})
```

## <span style="color: #2196F3;">Custom hooks</span>

```typescript
test('...', async () => {
	const { result } = renderHook(() => useCounter(0))

	act(() => {
		result.current.increment()
	})
	
	expect(result.current.count).toBe(0)
})
```

## <span style="color: #2196F3;">Async Custom hooks</span>

```typescript
test('...', async () => {
	const { result, waitForNextUpdate } = renderHook(() => useCounter(0))
	
	waitForNextUpdate()
	
	expect(result.current).toEqual({ data: 'mock data' })
})
```

## <span style="color: #2196F3;">Redux</span>

```typescript
test('...', async () => {
	render(
		<Provider store={createStore()}>
			<Component/>
		</Provider>
	)
	
	const textElement = screen.getByRole(...)
	const button = screen.getByText(...)
	
	fireEvent.click(button)
	
	expect(textElement).toHaveTextContent("...")
})
```

## <span style="color: #2196F3;">Zustand</span>

```typescript

const originalState = useStore.getState()
beforeEach(() => {
	useStore.setState(originalState)
})

test('...', async () => {
	render(<Component/>)
	
	const textElement = screen.getByRole(...)
	const button = screen.getByText(...)
	
	fireEvent.click(button)
	
	expect(textElement).toHaveTextContent("...")
})
```