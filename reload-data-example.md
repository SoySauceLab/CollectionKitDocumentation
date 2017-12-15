## Reload Data

Reload data is a quite common task for collection UI components. It's quite easy for `CollectionKit` to
reload your new set of data.

Whenever you create your `CollectionProvider`, you need to set a `dataProvider` which vends data for
your `collectionView`.  `CollectionKit` has an `ArrayDataProvider` at your dispense, which can fulfill
your needs most of the time. It has a `data` property, which you can update directly when a new set of
data arrives. 

One thing to notice is that `ArrayDataProvider` has confirmed to `CollectionReloadable` protocol. When
you update that dataProvider's `data`, collectionView will get reloaded automatically.

```Swift
import CollectionKit

class yourViewController: UIViewController {
  let dataProvider = ArrayDataProvider<YourDataType>(data: YourDataArray) { (_, data) in
    // Your data identifier based on data
    return identifier
  }

  override func viewDidLoad() {
    super.viewDidLoad()
    let provider = CollectionProvider(
      dataProvider: dataProvider,
      viewUpdater: yourViewUpdater
    )
    provider.layout = yourLayout
    provider.sizeProvider = yourSizeProvider
    collectionView.provider = provider
  }

  func updateData(_ data: [YourDataType]) {
    dataProvider.data = data
    // collectionView will update its views automatically on the next update cycle.
    // If you need to get an up-to-date contentSize immediately, you can call `reloadData()` directly on collectionView.
  }
}
```

For more detailed code, you can refer to [Reload Data Example](https://github.com/SoySauceLab/CollectionKit/blob/master/Examples/ReloadDataExample/ReloadDataViewController.swift)