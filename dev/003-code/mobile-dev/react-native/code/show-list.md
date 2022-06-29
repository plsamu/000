# Show list

## Method 1

```
const ListScreen: () => JSX.Element = () => {

    // const numbers: ItemTypeArr = [{ proper: '3' }]

    const numbers = [
        { proper: '3' },
        { proper: '19' },
        { proper: '42' }
    ]

    return (
        <FlatList
            data={numbers}
            renderItem={(el) => (
                <Text>{el.item.proper}</Text>
            )}
        />
    )
}
```

## Method 2

```
<FlatList
    data={numbers}
    renderItem={(el) => <Text>{el.item.proper}</Text> }
/>
```

## Method 3

```
<FlatList
    data={numbers}
    renderItem={(el) => { return <Text>{el.item.proper}</Text>} }
/>
```
