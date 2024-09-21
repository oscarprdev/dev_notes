## <span style="color: #2196F3;">Picture format</span>

```typescript
<picture>
	<source srcset="large.jpg" media="(min-width: 1200px)" />
	<source srcset="medium.jpg" media="(min-width: 600px)" />
	<img src="small.jpg" 
	alt="" />
</picture>
```

## <span style="color: #2196F3;">Image format</span>

```typescript
<img 
	srcset="large.jpg 1200w, medium.jpg 600w, small.jpg 300w" 
	sizes="(min-width: 1200px) 100vw, (min-width: 600px) 50vw, 100vw" 
	src="small.jpg" 
	alt="" />
```
