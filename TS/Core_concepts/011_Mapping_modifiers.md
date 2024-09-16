## <span style="color: #2196F3;">Partial</span>

*All properties are optional, undefined*

```typescript
type Partial<T> = {
	[P in keyof T]?: T[P] 
}
```

## <span style="color: #2196F3;">Required</span>

*All properties are required, not optional, not undefined*

```typescript
type Partial<T> = {
	[P in keyof T]-?: T[P] 
}
```

## <span style="color: #2196F3;">Readonly</span>

*All properties are readonly, can not be modified*

```typescript
type Readonly<T> = {
	readonly [P in keyof T]: T[P] 
}
```
