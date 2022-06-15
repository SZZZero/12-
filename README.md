# 12_202116014

알림 앱, 메모장 앱 등 아이폰 앱에서 자주 보고 익숙하게 사용하고 있는 '목록' 기능은 테이블 뷰 컨트롤러를 이용해서 구현할 수 있다.
목록 기능은 항목을 추가할 수 있는 추가 버튼 기능뿐만 아니라 항목을 삭제하거나 이동할 수 있는 기능, 항목을 선택하면 내용을 볼 수 있는 기능을 구현한다.

### 테이블 뷰 컨드롤러

테이블 뷰 컨트롤러는 사용자에게 목록 형태의 정보를 제공해 줄 뿐만 아니라 목록의 특정 항목을 선택하여 세부 사항을 표시할 때 유용하다.   
즉 데이터를 목록 형태로 보여 주기 위한 가장 좋은 방법이다.  

테이블 뷰 컨트롤러를 사용하면 어느 정도는 비슷한 동작을 추구하기 때문에 테이블 뷰 컨트롤러를 상속받은 컨트롤러가 자주 사용하는 함수를 주석 처리하여 미리 제공한다.


### 12장 코드 설명


```
override func numberOfSections(in tableView: UITableView) -> Int {
        // #warning Incomplete implementation, return the number of sections
        return 1
    }
```
보통은 테이블 안에 섹션이 한 개이므로 **numberOfSections** 의 리턴 값을 1로 지정합니다.

```
    override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        // #warning Incomplete implementation, return the number of rows
        return items.count
    }
```
섹션당 열의 개수는 **Items의 개수**이므로 tableView(_ tableView: UITableView, numberOfRowsInSection section: Int)
-> Int 함수의 리턴 값을 items.count로 합니다.

```
override func tableView(_ tableView: UITableView, moveRowAt fromIndexPath: IndexPath, to: IndexPath)
{ let itemToMove = items[(fromIndexPath as NSIndexpath).row]
  let itemImageToMove = itemsImageFile[(fromIndexPath as NSIndexPath).row]
  items.remove(at: (fromIndexPath as NSIndexPath).row)
  itemsImageFile.remove(at: (fromIndexPath as NSIndexPath).row)
  items.insert(itemToMove, at: (to as NSIndexPath).row)
  itemsImageFile.insert(itemImageToMove, at: (to as NSIndexPath).row) }
```

**itemToMove** 이동할 아이템의 위치를 저장합니다.   
**remove** 이동할 아이템을 삭제한다. 아이템 뒤의 아이템들의 인덱스가 재정렬됩니다.   
**insert** 삭제된 아이템의 이미지를 이동할 위치로 삽입합니다.   


