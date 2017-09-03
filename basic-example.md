## Build your first provider

A provider is anything that implements `AnyCollectionProvider`. The simpliest way to build a provider is by using `CollectionProvider` class. Here is what you need to build a basic provider:

```swift
let provider1 = CollectionProvider(
    data: [1，2，3, 4], // provide an array of data, data can be any type
    viewUpdater: { (label: UILabel, index: Int, data: Int) in
        // update your view according to your data, view can be any subclass of UIView
        label.backgroundColor = .red
        label.layer.cornerRadius = 8
        label.textAlignment = .center
        label.text = "\(data)"
    },
    sizeProvider: { (index: Int, data: Int, collectionSize: CGSize) -> CGSize in
        return CGSize(width: 50, height: 50) // return your cell size
    }
)
```

To display the content, just assign this provider to any instance of `CollectionView`.

```
collectionView.provider = provider1
```

The code above display a simple collection with 4 cells, using default FlowLayout.

It looks something like:  
![](https://cdn.rawgit.com/SoySauceLab/CollectionKit/c36d783/Resources/example1.svg)

`ColllectionProvider` accept the following as initialization parameters:

| Name | Description |
| :--- | :--- |
| data / dataProvider | supply data to collection provider. See CollectionDataProvider.swift for detail. If an array is used, an ArrayDataProvider will be automatically used to supply the array to the collection provider. |
| viewProvider / viewUpdater | supply views to collection provider. See CollectionViewProvider.swift for detail. if \`viewUpdater\` is used, then a \`ClosureViewProvider\` will be automatically construct to supply views and updates them with the \`viewUpdater\` function. |
| layout | layout used the layout the cells. default: FlowLayout |
| sizeProvider | a function that provide cell sizes used during the layout. default: a size provider function that returns the collection view size |
| willReloadHandler | callback that will be called when collection view begins to reload |
| didReloadHandler | callback that will be called when collection view finishes reload |
| tapHandler | callback when a cell is tapped |



