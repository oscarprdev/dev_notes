```typescript
type Fetch = typeof fetch
export class FooApi {
	constructor(private fetch: Fetch) {} // Dependency injection of fetch
	
	async requestSomething() {
		const response = await this.fetch('url')
		...
	}
}

// tests
it("...", async ({ expect }) => 
	1. Create mock fetch helper
	const fetchmock = vi.fn<Parameters<Fetch>, ReturnType<Fetch>>(mockPromise)
	
	const api = new FooApi(fetchMock)
	2. Set as promise
	const responsePromise = api.requestSomething()
	
	expect(fetchmock).toHavebeenCalledWith(
		"url from api class",
		headers: {"same headers"}
	)
	
	3. Mock the resolve response
	fetchmock.mock.result[0].value.resolve(new Response('"RESPONSE"'))
	expect(await responsePromise).toEqual("RESPONSE")
})

// Helper function to mock promises
function mockPromise<T>() {
	let resolve!: (value: T) => void
	let reject!: (error: any) => void
	
	const promise = new Promise((res, rej) => {
		resolve = res
		reject = rej
	}) as Promise<T> & { resolve: typeof resolve, reject: typeof reject}
	
	promise.resolve = resolve
	promise.reject = reject
	return promise
}
```