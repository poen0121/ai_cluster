## 採用 C語言 開發類神經元矩陣

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


### 演算法  : 
```
Is = 收訊通道訊號

Iw = 收訊通道權重 (目的 : 轉換訊號壓力)

dIw = 收訊通道偏差權重

uIw = 更新收訊通道權重

Ow = 輸出通道權重 (目的 : 放大內部壓力訊號)

dOw = 輸出通道偏差權重

uOw = 更新輸出通道權重

Os = 輸出通道訊號

Sp = 訊號壓力

iSp = 內部訊號壓力

√ 平方根符號

└ ┘ 高斯符號 floor 無條件捨去小數

|| 絕對值符號

運算式 :

Sp = └(Is / Iw)┘

dIw = └(√Sp)┘ - Iw

iSp = Iw * └((Iw + dIw) / Iw)┘

uIw = Iw + └(√iSp / Iw)┘

Os = iSp * Ow

dOw = └(√iSp)┘ - Ow

uOw = Ow +└(√(|dOw| * (Ow + dOw)) / Ow)┘

基本機制 :

Iw , Ow 權重初始為 1,1

Iw , Ow 權重需要被記錄更新來自 uIw , uOw
```
