## <span style="color: #2196F3;">Optional chaining</span>

*Check if value is undefined or null = ?*

```typescript
type Payment = {
	value: number
}

type Invoice = {
	payment?: Payment
}

type Foo = {
	invoice?: Invoice
}

// Not best approach
function getPaymentValue(foo: Foo): number | undefined {
	const {invoice} = foo
	if (!invoice) return
	
	const {payment} = invoice
	if (!payment) return
	
	const {value} = payment
	if (!value) return
	
	return value
}

// Best approach
function getPaymentValue(foo: Foo): number | undefined {
	return foo?.invoice?.payment?.value
}
```

## <span style="color: #2196F3;">Nullish coalesing</span>

*Check truthy values = ??*

```typescript
type Foo = {
	val: 0 | 1 | 2
}

// 0 is not managed
function useFoo(foo: Foo) {
	return foo.val || 100 // 1 | 2 | 100
}

// 0 is valid
function useFoo(foo: Foo) {
	return foo.val ?? 100 // 0 | 1 | 2 | 100
}
```
