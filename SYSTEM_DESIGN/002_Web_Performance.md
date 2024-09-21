## <span style="color: #2196F3;">FCP</span>

*First contentful paint: From user enters on the web till something is rendered. Ex: Title

**HOW TO IMPROVE**:
1. Implement CDN
2. Compress server response
## <span style="color: #2196F3;">LCP</span>

*Largest contentful paint: The largest content rendered. Ex: Images*

*TIMES*
1. Good: 2.5s or less
2. Medium: between 2.5s and 4s
3. Bad: more than 4s

**HOW TO IMPROVE**:
1. Defer resources
2. Optimize images (loading='lazy')
3. Reduce request overhead

How to implement **lazy load** with intersection observer:
**[[002_Web_Performance_lazy_load]]**

How to implement different **images sizes** depending on the viewport:
[[002_Web_Performance_image_media]]

```typescript
<img src="picture-900.jpg"
	srcset="
		picture-600.jpg 600w, 
		picture-900.jpg 900w" 
	sizes="(max-width: 600px) 600px, (max-width: 900) 900px"/>
```

*Extra:* How to minify images: [[002_Web_Performance_image_min]]
## <span style="color: #2196F3;">CLS</span>

*Comulative layout shift: The total movement distance and impact of page elements during the entire lifetime of the document loaded. Ex: buttons being pushed down after an image is loaded*

*TIMES*
1. Good: 100ms or less
2. Medium: between 100ms and 250ms
3. Bad: more than 250ms

**HOW TO IMPROVE**:
1. Aspect-ratio  

## <span style="color: #2196F3;">FID</span>  

*First input delay: Browser time delay between the user's first click and the execution of application code*

*TIMES*
1. Good: 100ms or less
2. Medium: between 100ms and 300ms
3. Bad: more than 300ms

## <span style="color: #2196F3;">METRICS</span>  

1. Lab data
2. Synthetic data (test servers - APM tools)
3. Field data (monitoring users - RUM tools - requestmetrics.com)

crux-compare.netlify.app