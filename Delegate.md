# Delegate

## 實作兩個頁面的 UIAlert 連接

```swift

// FirstViewController

import UIKit

protocol AlertDelegate: AnyObject {
    func showAlertOnFirstVC()
}

class FirstViewController: UIViewController, AlertDelegate {

    override func viewDidLoad() {
        super.viewDidLoad()
    }
    
    func showAlertOnFirstVC() {
        let alertController = UIAlertController(title: "第二個警告", message: "這是第二個警告訊息", preferredStyle: .alert)
        let okAction = UIAlertAction(title: "確定", style: .default, handler: nil)
        alertController.addAction(okAction)
        present(alertController, animated: true, completion: nil)
    }
    
    override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
        if let nextVC = segue.destination as? SecondViewController {
            nextVC.delegate = self
        }
    }
}
```

```swift

// SecondViewController

import UIKit

class SecondViewController: UIViewController, AlertDelegate {
    func showAlertOnFirstVC() {
        let alertController = UIAlertController(title: "第一個警告", message: "這是第一個警告訊息", preferredStyle: .alert)
        let okAction = UIAlertAction(title: "確定", style: .default, handler: { [weak self] _ in
            self?.dismiss(animated: true, completion: nil)
            self?.delegate?.showAlertOnFirstVC()
        })
        
        alertController.addAction(okAction)
        
        present(alertController, animated: true, completion: nil)
    }
    
    weak var delegate: AlertDelegate?
    
    @IBAction func alertButtonTapped(_ sender: Any) {
        showAlertOnFirstVC()
    }
    
    override func viewDidLoad() {
        super.viewDidLoad()
    }
}
```
此方法是使用 delegate 來達到在後一個 VC 執行某些操作後，退回前一頁的時候，接續跳出 UIAlert 的需求。
