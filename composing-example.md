
Use `CollectionComposer` to combine multiple providers into one. You can also supply layout objects to Provider & Composer.

```swift
provider1.layout = FlowLayout(padding: 10)

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

<img src="https://cdn.rawgit.com/SoySauceLab/CollectionKit/c36d783/Resources/example2.svg" />