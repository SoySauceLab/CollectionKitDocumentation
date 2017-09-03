
## Composing

One of the distinct feature of CollectionKit is the ability to combine multiple providers into one. Each providers still maintains its own data, view, & layout. This makes collection far more flexible and easy to reuse. 

Use `CollectionComposer` class to combine multiple providers into one.

```swift

let provider1 = CollectionProvider(
    data: [1，2，3, 4],
    viewUpdater: { (label: UILabel, index: Int, data: Int) in
        label.backgroundColor = .red
        label.layer.cornerRadius = 8
        label.textAlignment = .center
        label.text = "\(data)"
    },
    layout: FlowLayout(padding: 10),
    sizeProvider: { (index: Int, data: Int, collectionSize: CGSize) -> CGSize in
        return CGSize(width: 50, height: 50)
    }
)

let provider2 = CollectionProvider(
    data: ["A", "B"],
    viewUpdater: { (label: UILabel, index: Int, data: String) in
        label.backgroundColor = .blue
        label.layer.cornerRadius = 8
        label.textAlignment = .center
        label.text = data
    },
    layout: FlowLayout(padding: 10),
    sizeProvider: { (index: Int, data: String, collectionSize: CGSize) -> CGSize in
        return CGSize(width: 230, height: 50)
    }
)

collectionView.provider = CollectionComposer(
    layout: FlexLayout(padding: 20, justifyContent: .center, alignItems: .center),
    provider1,
    provider2
)
```

![](https://cdn.rawgit.com/SoySauceLab/CollectionKit/c36d783/Resources/example2.svg)

## Make reusable provider class

You can easily reuse provider implementation by making reusable provider class. 
Here is the same example that uses a custom provider class.

```swift
class RoundedLabelCollectionProvider<Data>: CollectionProvider<Data, UILabel> {
    init(data: [Data], color: UIColor, cellSize: CGSize) {
        super.init(
            data: data,
            viewUpdater: { (label: UILabel, index: Int, data: Data) in
                label.backgroundColor = color
                label.layer.cornerRadius = 8
                label.textAlignment = .center
                label.text = "\(data)"
            },
            layout: FlowLayout(padding: 10),
            sizeProvider: { (index: Int, data: String, collectionSize: CGSize) -> CGSize in
                return cellSize
            }
        )
    }
}

collectionView.provider = CollectionComposer(
    layout: FlexLayout(padding: 20, justifyContent: .center, alignItems: .center),
    RoundedLabelCollectionProvider(data: [1, 2, 3, 4], color: .red, cellSize: CGSize(width: 50, height: 50)),
    RoundedLabelCollectionProvider(data: ["A", "B"], color: .blue, cellSize: CGSize(width: 230, height: 50))
)
```