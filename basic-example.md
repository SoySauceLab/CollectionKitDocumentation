## Build your first provider

A provider is anything that implements `AnyCollectionProvider`. The simpliest way to build is 
by using `CollectionProvider` class. To build a basic provider, here is what you need:

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

