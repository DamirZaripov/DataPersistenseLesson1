# DataPersistenseLesson1
PropertyList, NSCoding, NSKeyedArchiver

## ДЗ: 

Ваш менеджер по работе с новостями сейчас является синглтоном, но как я говорил, синглтон не очень гуд вещь. 
Поэтому: 
1) Реализация вашего менеджера должна сохранять/считывать/искать модели, которые будут хранится с помощью NSCoding + UserDefaults. 
2) Ваш менеджер может не быть дженериком, пока работаем только с новостями вашей страницы. 
3) Соотвественно теперь вам не нужно держать static инстанс на экземпляр менеджера, так что убираем синглтон. 
4) Теперь везде где нужно использовать ваш менеджер по работе с данными, добавьте его в нужный класс типа:     
```swift 
var dataManager: DataManager! 
```
где DataManager - это протокол вашего менеджера. А потом уже во viewDidLoad приравниваете туда реализацию менеджера. Типа:  
```swift
override func viewDidLoad() {
        super.viewDidLoad()
    dataManager = DataManagerImplementation() 
}
```
тем самым вы будете в нужных местах работать через оболочку-протокол, а не через имплементацию. 

Ну и соотвественно все должно работать как было, но через этот ваш менеджер, сохраняя/обновляя ваши модели :) 
