```typescript
// Container folder
export default function ListingsContainer() {
	const [data, setData] = React.useState(null)
	
	React.useEffect(() => { ... })
	
	if (!data) return null
	
	return <ListingsPresentation listings={data.listings}/>
}
// Presentation folder
export default function ListingsPresentation(props) {
	return (
		<ListingsGrid>
			{props.listings.map(listing) => {
				<Listing key={listings.id} listings={listings} />
			})}	
		</ListingsGrids>
	)
}
```