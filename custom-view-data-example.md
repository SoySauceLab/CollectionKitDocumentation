## CollectionView with Custom View and Data Type

`CollectionProvider` uses *generic*, so you can provide `CollectionProvider` with custom view and data type to make it suit your needs.

For example, we have a `ArticleView` type which can be populated with `ArticleData`, you can construct your collection provider like following:

```swift

// Assume your view controller has a stored property `collectionView`, which is
// an instance of `CollectionView`.

override func viewDidLoad() {
  super.viewDidLoad()

  let articles: [ArticleData] = [articleOne, articleTwo]
  let provider = CollectionProvider(
    data: articles,
    // You can specify view and data type according to your need.
    viewUpdater: { (view: ArticleView, data: ArticleData, at: Int) in
      // Use your data update view.
      view.populate(article: data)
    }
  )
  provider.layout = FlowLayout(lineSpacing: 30)
  provider.sizeProvider = { (_, view, size) -> CGSize in
    return CGSize(width: size.width, height: 200)
  }
  // Assign provider to collectionView.
  collectionView.provider = provider
}

```

Now, your collectionView will use your `ArticleData` to populate your `ArticleView` and lay them out.