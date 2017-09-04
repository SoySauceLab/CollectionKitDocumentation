## Custom View and Data

You can provide custom view and data to `CollectionProvider` to make it suit your needs, and thanks to *swift*'s *generic*, it is quite easy to provide your custom type.

Here is a code snippet.

```swift
let provider = CollectionProvider(
    data: articles,
    // You can specify view and data type according to your need.
    viewUpdater: { (view: ArticleView, data:ArticleData, at: Int) in
        // Use your data update view.
        view.populate(article: data)
    },
    layout: FlowLayout(insets: UIEdgeInsets(top: 20, left: 16, bottom: 20, right: 16), padding: 30),
    sizeProvider: { (_, view, size) -> CGSize in
        return CGSize(width: size.width, height: 200)
    })
// Assign provider to collectionView.
collectionView.provider = provider

```