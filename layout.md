
## Layout

### FlowLayout

Flow layout is the default layout used in CollectionKit. Is is similar to UIKit's `UICollectionViewFlowLayout`.
It display cells one after another from left to right, top to bottom. Like `UICollectionViewFlowLayout` it support `lineSpacing` and `interitemSpacing` to adjust the spacing between items. It also supports `justifyContent`, `alignItems`, and `alignContent` to handle left over space.

### WaterfallLayout

Pinterest-like layout. display few columns of item, each column has the same width.

ex.

```swift
WaterfallLayout(columns: 2)
```

### RowLayout

Display a row of content. `RowLayout` has the extra functionality where items can fill up the remaining space in a row. Use this when you want some perticular items to fill the remaining space.

### InsetLayout

Add extra spacing to a specific layout.

ex.

```swift
InsetLayout(FlowLayout(), insets: UIEdgeInset(top: 30, left: 0, bottom: 0, right: 0))
```

You can also use the shorthand method defined on CollectionLayout.

```swift
WaterfallLayout().inset(by: UIEdgeInset(top: 30, left: 0, bottom: 0, right: 0))
```

Inset layout also supports dynamic inset based on the collection view size. Just pass in a function that returns coresponding inset from a given size.

```swift
InsetLayout(WaterfallLayout()) { size in
    if size.width >= 768 {
        return UIEdgeInset(top: 50, left: 50, bottom: 50, right: 50)
    } else {
        return .zero
    }
}
```

### TransposeLayout

Transpose the x axis with the y axis of a specific layout.

ex.

```swift
TransposeLayout(RowLayout())
```

gives a vertical column layout that supports flexible items.

##### Shorthand

```swift
RowLayout().transposed()
```

