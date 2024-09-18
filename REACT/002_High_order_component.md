```typescript
// Component that returns another component adding props 
export default function withLoader(Element, url) {
	return (props) => {
		const [data, setData] = React.useState(null)
		
		React.useEffect(() => { ... })
		
		if (!data) return null
		
		return <Element {...props} data={data}/>
	}
}

function ListingsPresentation(props) 
	if (!props.data.listings.length) return null;
	
	return (
		<ListingsGrid>
			{props.listings.map(listing) => {
				<Listing key={listings.id} listings={listings} />
			})}	
		</ListingsGrids>
	)
}
// Exporting the wrapper with the component that needs the functionality shared
export default withLoader(ListingsPresentation, "url to fetch")
```