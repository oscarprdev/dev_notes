```typescript
async function getNewMsgs() {
	try {
		...
	} catch {
		...
	}
}

let timeToMakeNextRequest = 0
// Recursive function polling
async function rafTimer(time) {
	if (timeToMakeNextRequest <= time) {
		await getNewMsgs()
		timeToMakeNextRequest = time + INTERVAL // add interval time to next req
	}
	requestAnimationFrame(refTimer) 
}
	// Running after browser runner has been completed
	requestAnimationFrame(refTimer)
```

## <span style="color: #2196F3;">Backoff & retry</span>

*Calling again after request failure*

```typescript
async function getNewMsgs() {
	try {
		...
		if (res.status >= 400) {
			throw new Error('Some error message')
		}
		failedTries = 0 // Restore counter
	} catch (e) {
		failedTries++ // Add 1 to failure counter
	}
}

let BACKOFF = 5000 // ms to request again on failure
let timeToMakeNextRequest = 0
let failedTries = 0 // Failure requests counter
async function rafTimer(time) {
	if (timeToMakeNextRequest <= time) {
		await getNewMsgs()
		timeToMakeNextRequest = time + INTERVAL + failedTries * BACKOFF
	}
	
	requestAnimationFrame(refTimer) 
}
	requestAnimationFrame(refTimer)
```