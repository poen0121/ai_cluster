## Neurons

### 基礎程式  : 
```
* generate.exe : 創建座標神經元目錄。
* dendrite.exe : 訊號輸入至座標神經元。
* connect.exe : 神經元連結處理。
* neuron.exe : 神經元執行訊號處理。
* matrix.exe : 矩陣創建座標神經元目錄。
* active.exe : 持續激活神經元訊號。
* wake.exe : 矩陣神經元逐層喚醒執行訊號處理。
* interface.exe : 矩陣神經元邊緣層訊號輸入介面。
* cut.exe : 切除矩陣神經元軸突連結。
* carve.exe : 編輯矩陣神經元狀態。
```

### 調用方式  : 
```
* generate.exe : $ ./generate {目標x座標} {目標y座標} {目標z座標} {神經元類型(0=input，1=middle，2=output)}
* dendrite.exe : $ ./dendrite {目標x座標} {目標y座標} {目標z座標} {輸入訊號} {來源ID} {來源流水號}
* connect.exe : $ ./connect {目標x座標} {目標y座標} {目標z座標} {基準位移單位}
* neuron.exe : $ ./neuron {目標x座標} {目標y座標} {目標z座標}。
* matrix.exe : $ ./matrix {矩陣半徑}。
* active.exe : $ ./active {目標x座標} {目標y座標} {目標z座標} {持續訊號}。
* wake.exe : $ ./wake {矩陣半徑}。
* interface.exe : $ ./interface {矩陣半徑} {像素單位訊號}。
* cut.exe : $ ./cut {目標x座標} {目標y座標} {目標z座標}
* carve.exe : $ ./carve {目標x座標} {目標y座標} {目標z座標} {啟用狀態 (0=sleep，1=work)}。
```

### 使用步驟  : 
```
步驟 1 : 使用 matrix.exe 創建基礎矩陣神經元模型
步驟 2 : 使用 wake.exe 偵聽並喚醒神經元執行訊號處理
步驟 3 : 使用 interface.exe 創建矩陣神經元邊緣層訊號輸入介面
```
