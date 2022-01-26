# Chapter1 資料結構與演算法

## 1-1 資料結構
### 程式設計最佳化方法論
考慮資料間的特性與相互關係, 選用最適資料結構,
達到加快執行速度與減少記憶體佔用空間等目的.

在要求電腦解決問題時, 我們會去選用電腦能接受的模式(資料結構)來規劃程式, 
資料結構的研究等於解決方法的研究, 故資料結構與演算法密不可分.

### 資料(Data)與資訊(Information)
Data --- Data Processing ---> Information
       
### 資料型態(Data Type)
#### 基本資料型態(Primitive Data Type)
- a.k.a Scalar Data Type
- int, float, char, ...

#### 結構化資料型態(Structured Data Type)
- string, array, pointer, list, file, ...

#### 抽象資料型態(Abstract Data Type, ADT)
可將其視為資料與行為的集合, ADT本身便包含了處理資料的行為, 故ADT又可稱為**容器**.
ADT在電腦中表現的精神為, 資訊隱藏, 與特定關係模式.
其重點在於該資料集合的**介面**, 內部的行為則可以自行定義, 或以不同的方式實作.

堆疊(Stack)便是一種ADT, 其特色為**後進先出**, 並其介面定義了以下3種行為
- push 將資料放至Stack頂端
- pop 將Stack頂端的資料取出
- peek 取得Stack頂端的資料, 但不將其取出

Stack示意圖如下[1]
![Stack示意圖](https://imgur.com/g9CmLts.jpg)

## 1-2 演算法
### 演算法的定義
在**有限**步驟內解決數學問題的程式
```csvpreview {header="true"}
演算法特性, 內容與說明
輸入(Input), 0個以上輸入資料 必須清楚定義
輸出(Output), 至少一個
明確性(Definiteness), 每一個指令或步驟必行簡潔明確不含糊
有限性(Finiteness), 在有限步驟後一定會結束 不會產生無窮迴路
有效性(Effectiveness), 步驟清楚且可行 能讓使用者用紙筆計算求出答案
```
常用的演算法表達形式如下
- 一般文字描述: 以文字說明演算法步驟
- 虛擬碼(Pseudo Code): 經常使用的有SPARKS, PASCAL-LIKE等語言
- 表格或圖形: 如陣列, 樹狀圖, 矩陣圖等
- 流程圖(Flow Diagram): 常見的表示法, 必須使用某些圖形符號來區分不同類型的步驟
- 以可讀性高的高階語言如python, Java, C#, ...來表示(也常拿來驗證)

## 1-3 演算法效能分析
以執行時間與占用記憶體大小來評估

### 空間複雜度 (Space Complexity)
硬體發展日新月異, 故應以演算法的執行時間為主要評估與分析的依據

### 時間複雜度 (Time Complexity)
詳細定義如下:
$$
\text{在理想狀態下的計算機中, 定義} \\T(n) \\\text{來表示程式執行費時, 其中} n \text{代表資料輸入量}
$$
$$
\begin{array}{c|c}
描述方法 & 意義 \\
\hline
O() & \text{最大執行時間 (Best Case Executing Time)} \\
\Omega () & \text{最小執行時間 (Worse Case Executing Time)} \\ 
\Theta () & \text{若}O()\text{與}\Omega ()\text{的 order 相同, 可以}\Theta ()描述精確的時間複雜度
\end{array}
$$
現令$f(n)$為執行時間的成長率 (rate of growth), 則$f(n)$不同條件下時間複雜度描述方式如下表
$$
\begin{array}{c|c|l}
\text{條件} & \text{描述方式} \\
\hline
T(n)\le cf(n) & f(n)=O(...) \\
T(n)\ge cf(n) & f(n)=\Omega(...) \\
c_1f(n)\le T(n)\le c_2f(n) & f(n)=\Theta(...) 
\end{array}
$$
其中 $f(n)=O(...)$ 讀作 Big-O of f(n) is ...

討論時間複雜度時, 習慣以**最大**執行時間/Big-O來表示

#### 範例
-- 假如執行時間 $T(n)=3n^3+2n^2+5n$, 時間複雜度為 $O(n^3)$

-- $T(n)=\sum_{1\le i\le n} i=\frac{n(n+1)}{2}$, 時間複雜度為$O(n^2)$

-- 考慮下列虛擬碼的執行次數
```
x ← x+1
// 1次
```
```
for i ← 1 to n do
    x ← x+1
end for
// n次
```
```
for i ← 1 to n do
    for j ← 1 to m do
        x ← x+1
    end for
end for
// n*m次
```

-- 求下列算法中 x ← x+1 的執行次數與時間複雜度
```
for i ← 1 to n do
    j ← i
    for k ← j+1 to n do
        x ← x+1
    end for
end for
//
```
Ans: $n(n-1)/2$ 次, 時間複雜度為 $O(n^2)$

-- 求下列程式的執行時間
```
k ← 100000
while k<>5 do 
    k ← k/10
end while
// <> means unequal, !=
```
Ans: 因k永不等於5, 故執行時間為無限長

#### 時間複雜度總結
時間複雜度只是**執行次數**的概略估計, 其本身便是一種以**漸進表示執行時間**的方式, 常見的 Big-O 如下表
$$
\begin{array}{c|l}
O(...) & \text{特色與說明} \\
\hline
O(1) & \text{常數時間 (constant time)執行時間無關資料大小} \\
O(\log_2{n}) & \text{對數時間 (logarithmic time)} \\
O(n) & \text{線性時間 (linear time)} \\
O(n\log_2{n}) &  \text{線性乘對數時間 (Quasilinear time/log-linear time)} \\
O(n^2) &  \text{平方時間 (quadratic time)} \\
O(n^3) &  \text{立方時間 (cubic time)} \\
O(2^n) &  \text{指數時間 (exponential time)} \\
O(n!) & \text{階乘時間 (factorial time)}
\end{array}
$$
時間成長趨勢如下圖[3]
![bigO](https://imgur.com/rLQDaQU.jpg)

#### Big-O 練習
$$
\begin{array}{c|c}
f(n) & \text{time complexity} \\
\hline
n^2\log n+\log n & O(n^2\log n) \\
8\log \log n & O(\log \log n) \\
\log n^2 & O(\log n) \\
4\log \log n & O(\log \log n) \\
n/100+1000/n^2 & O(n) \\
n! & O(n!)
\end{array}
$$

## 1-4 常見演算法
學習知名演算法的技巧與觀念, 了解其複雜度, 比較各演算法之優劣, 未來撰寫演算法時亦可用來分析其效能
### 分治法 (Divide and conquer)
分治法唯一種精神, 旨在以相同的概念將大問題分解成數個子問題, 子問題可再進一步分解, 直到這些子問題的解法足夠簡單, 再分別解決. 分治法的應用有
- 遞迴 (recursion)
- 快速排序法 (quick sort) :construction:施工中, 未來補上圖示	:construction:
- 大數乘法 	:construction:施工中, 未來補上圖示	:construction:
### 遞迴 (recursion) [4]
遞迴函式要定義以下2種條件至少各一個
- recursive case
藉由遞迴產生結果
- base case
input(s)滿足某些條件使得遞迴函式產生未經遞迴的結果(return), 故base case也稱作terminating case.
面對複雜的遞迴問題, 滿足 base case 的 tail recursion 往往會是最佳化遞迴效能的關鍵.

另根據遞迴呼叫的方式可再分成
- 直接遞迴 (Direct Recursion)
遞迴函式$f1()$中, 直接呼叫遞迴函式$f1()$本身
- 間階遞迴 (Indirect Recursion)
遞迴函式$f1()$中, 會呼叫其他遞迴函式$f2()$, 並在$f2()$遞迴過程中會呼叫$f1()$

遞迴範例 - Factorial
```csharp
static int Fac(int n)
{
    if (n==0) // base case
        return 1;
    else // recursive case
        return n * fac(n-1);
}
```

遞迴範例 - Fibonacci number
```csharp
static int Fibo(int n)
{
    if (n==0) // base case
        return 0;
    else if (n==1) // base case
        return 1;
    else // recursive case
        return Fibo(n-1)+Fibo(n-2)    
}
```
在實作遞迴時會應用到堆疊的資料結構概念, 可以參考 Chapter4 - Stack. (還不懂 stack 跟 recursion 的關係@@)

### 貪心法 (Greedy algorithm)
將問題拆解成數個子問題, 在解決子問題的過程都採取當下最有利解法, 不斷的改進答案來逼近最佳解. 當達到終止條件時停止, 來盡可能的得到最佳解. 貪心法無法保證能找到最佳解, 其原因為在某些步驟過早作決定. 經常用在以下問題類型
- 圖形最小生成樹(MST) :construction:施工中:construction:
- 最短路徑 :construction:施工中:construction:
- 霍哈夫曼編碼 :construction:施工中:construction:

貪心法範例 - 找零的最小硬幣數
找零金額為7414, 現有四種硬幣種類 50, 10, 5, 1. 貪心法邏輯為"**相同金額下, 最大面額的硬幣有最小的硬幣數**"
```csharp
Dictionary<int, int> coinValues = new Dictionary<int, int>()
{
    { 1, 50 },
    { 2, 10 },
    { 3, 5 },
    { 4, 1 }
}
int change = 7414, n_coins = 0, step = 1;
while (change>0 && step<5)
{
    n_coins += change/coinValues[step];
    change %= coinValue[step];
    step++;
}
```

### 動態規劃法 (Dynamic Programming Algorithm, DPA)
類似於分治法, 將大問題拆成子問題, 但將子問題解決後的答案存起來. 當大問題或其他子問題與已解決的子問題有關, 便可直接取用儲存的答案, 而不是重新算一次.

動態規劃範例 - Fibonacchi number
```csharp
class Fibo_Slover
{
    private int[] fibos;

    public Fibo_Slover()
    {
        this.fibos = new int[1000];
    }

    private int Fibo_recursive(int n)
    {
        if (this.fibos[n] != 0)
            return this.fibos[n];
        else if (n == 0)
            return 0;
        else if (n == 1)
            return 1;
        else
        {
            this.fibos[n-2] = Fibo_recursive(n-2);
            this.fibos[n-1] = Fibo_recursive(n-1);
            this.fibos[n] = this.fibos[n-1] + this.fibos[n-2];
            return this.fibos[n];
        }
    }

    public int Get_n(int n)
    {
        return this.Fibo_recursive(n);
    }
}
```
當然也能將Fibonacci()寫成函式, 再讓他去讀寫儲存子問題答案的fibos[], 但我不喜歡讓函示去改外部的物件, 將外部物件作為引數讀入也會讓程式變得很冗.
且我不會想讓其他外部函示修改到儲存子答案的fibos[], 故使用封裝的形式將Fibonacci number的求解過程及儲存陣列包在一起.

### 疊代法 (Iterative method)
主要用於解決無exact solution的問題, 疊代法不期望一次就得到解, 而是藉由疊代逼近的方式來求解. 
故疊代法優先考慮的是**疊代過程是否收斂**及演算法的**收斂條件為何**, 再來才會考慮收斂求解的速度.

疊代法範例 - Bisection method
Bisection method是高中就學過, 利用intermediate value theorem來對連續函數勘根的演算法, 實作過程中會不斷的將勘根區間砍半, 直到滿足terminating condition. 這就是標準的疊代演算法.
```csharp
static double FindRoot (Func<double,double> F, double lowerBound, double upperBound, double maxErr)
{
    double a = new double(), b = new double(), c = new double();
    do
    {
        Random rnd = new Random();
        a = rnd.NextDouble()*(upperBound-lowerBound) + lowerBound;
        b = rnd.NextDouble()*(upperBound-lowerBound) + lowerBound;
    }while (F(a)*F(b) > 0);

    while (Math.Abs(a-b) > maxErr)
    {
        c = (a+b) / 2;
        if (F(a)*F(c) > 0) { a = c; }
        else { b = c; }
    }
    return c;
}
```

### 窮舉法
又稱暴力搜尋, 舉出所有可能的解並一一比對. 優點是一定能找到正確解, 缺點是速度太慢, 且在可能解是連續變化/無窮的情況下, 速度慢的缺點更明顯.
以疊代法用於勘根來與窮舉法比對, 若搜尋區間大小相同為100, 要求精度皆為1, 則
$$
\begin{array}{c|c}
& \text{最大運算次數} \\
\hline
\text{疊代法} &  \text{因每次區間會砍半, 疊代運算 }Round(\log_2 (100/1))+1=7 \\
& \text{次後, 勘根區間(精度)就小於1} \\
\hline
\text{窮舉法} & \text{為確保精度小於1, 需要舉出並運算至少}100/1=100\text{個可能解}
\end{array}
$$

不過窮舉的概念還是可以利用在解決**夠簡單的子問題**上, 特別是搭配回溯法(Backtracting), 利用窮舉判斷目前的路徑是否能達到設定目標. 經典的問題有迷宮, 八皇后.

## 1-5 程式設計簡介
程式設計不只是跑出正確的結果就好, 還要考量
- 運算效能 : 時空間複雜度
- 高可讀性
- 方便協作及日後維護

我們可以利用**演算法**改進運算效能, 利用**資料架構**規劃程式架構維持高可讀性與方便協作與維護, 這些才是**程式設計**的真正意義.

程式語言沒有最好, 只有最適合, 一般評斷程式語言好壞的標準如下
- 可讀性(Readability)高 : 自己寫的程式過一陣子來看都要花時間理解架構與邏輯了, 更何況要與他人協作, 長久維護的情況.
- 平均成本低 : 成本包含了執行/編譯/維護/學習/除錯/更新.
- 可靠度高 : 程式要夠robust, 不要動不動就爆掉, 並且要考量邊緣測資確保結果一定是正確的.
- 可撰寫性高 : 可看作可維護性+可變更性的綜合, 程式不要牽一髮動全身.

### 設計步驟
如同分治法, 我們也可將撰寫程式視為一個主問題, 將其分為以下幾點子問題, 定義好子問題的題幹與需求, 再逐步完成.
1. 需求認識 (requirements) : 
理解問題, 如輸入輸出為何? 
理解限制/目標, 如是否要長時間維護? 使用者背景? 運行環境限制?
2. 設計規劃 (design and plan)
根據需求選出可行的資料結構與演算法
3. 分析討論 (analysis and discussion)
分析各種設計的優缺點, 並尋找是否有其他設計方法, 決定最適合的設計.
4. 編寫程式 (coding) 
考量前述的幾項特性, 然後不要寫糞扣. 不過初期可以寫糞一點, 驗證成功後再來改, 如果一開始寫太糞也會改得很痛苦.
5. 測試驗證 (verification)
確認是否符合第一點的需求, 並檢查是否Logic error, Robustness[5], Side Effect[6].

## 章節練習
1. 以下程式碼是否嚴謹的表現出演算法的意義?
```
count = 0;
while(count<>3)
```
:::spoiler My Ans
(X)
章節1-2提及演算法五條件, 輸入, 輸出, 明確, 有效, 有限. 該程式片段無任一項符合.
:::
\
2. 以下程式碼迴圈的部分, 實際執行次數與時間複雜度?
```
for i ← 1 to n
    for j ← i to n
        for k ← j to n
        end for
    end for
end for
```
:::spoiler My Ans
$n(n-1)(n-2)\text{次, }O(n^3)$
:::
\
3. 證明 $f(n)=a_mn^m +...+a_1n+a_0\text{, 則 }f(n)=O(n^m)$
:::spoiler My Ans
沒有靈感, 未完成
$$
\begin{array}{rc}
\text{Consider that} & g(n) = a_{m-1}n^{m-1}+...+a_1n+a_0 \\
let & h(n) = cn^m + g(n)\text{, where }c\ge 0 \\
then & \{h(n)\ge g(n)|\forall n\ge 0\} \\
let & i(n) = f(n) - h(n) \\
then & i(n) = (a_m-c)n^m\text{, where }c\ge 0 \\
& i(n) - f(n) = -h(n)
\end{array} 
$$
:::
\
4. 以下程式碼函式 F(i,j,k) 的執行次數?
```
for k ← 1 to n
    for i ← 0 to k-1
        for j ← 0 to k-1
            if i<>j then F(i,j,k)
        end for
    end for
end for
```
:::spoiler My Ans
$1+2+3+...+n = \frac{n(n+1)}{2}\text{次}$
:::
\
5. 以下程式碼的 Big-O 為何?
```
total = 0
for i ← 1 to n
    total ← total+i·i
end for
```
:::spoiler My Ans
$O(n)$
:::
\
6. 解釋 Nonpolynomial Problem 的意義
:::spoiler My Ans
$$
f(x)\notin S \text{ , where S = $\{O(n^c)|c\in\Re\}$ }
$$
:::
\
7. 名詞解釋 (1) $O(n)$, (2) 抽象資料型 (Abstract Data Type)
:::spoiler My Ans
Time complexity is linear

ADT將相同類型的資料, 對外的介面, 及內部資料的處理方式包在一起, 類似OOP的封裝的概念.
:::
\
8. 結構化程式設計與物件導向程式設計的特性為何? 簡述之
:::spoiler My Ans
結構化:
**由大至小**或**由小至大**將程式分為數個模組的設計方式. 模組分割得當可以增加程式可讀性, 及程式開發效率.

OOP:
是一種精神, 一種思考模式, 依據需求定義類別, 藉由物件間的互動來完成程式功能. 花時間規劃類別雖然會降低開發速度, 但因其思考模式類似現實世界的運行方式, 且可將大部分功能模組化, 所以大幅度增加程式的Readability, Reusability, Changeability[9].
:::
\
9. 以演算法實作下列函式$f(n)$
$$
f(n) = 
\begin{cases}
n^n & , \text{if $n\ge 1$} \\
1 & , \text{otherwise}
\end{cases}
$$
:::spoiler My Ans
```
result ← 1
if n ≥ 1
    for i ← 1 to n
        result ← result * n
    end for
end if
return result
```
但如果n不是整數程式會壞掉= =, 不清楚浮點數的指對數表示如何實作的
:::
\
10. 演算法必須符合哪五條件?
:::spoiler My Ans
輸入, 輸出, 明確, 有效, 有限
:::
\
11. 評斷程式語言好壞標準?
:::spoiler My Ans
可讀性高, 各種成本低, 可靠度高, 可撰寫性高
:::
\
12. 分治法核心精神?
:::spoiler My Ans
將大問題分成夠簡單的子問題, 個別解決
:::
\
13. 遞迴必要條件?
:::spoiler My Ans
base case, recursive case至少各有一個
:::
\
14. 貪心法核心概念?
:::spoiler My Ans
將問題分階段, 在各階段皆以當下最佳解來運算, 非所有問題都可找到最佳解.
:::
\
15. 動態規劃與分治法的差異?
:::spoiler My Ans
動態規劃:
若子問題間或子問題與大問題類似, 解決子問題的同時儲存其結果, 並將其結果用在解決其他子問題或大問題上, 來減少運算時間.

分治法沒有提到, 儲存重複出現問題之結果, 這個概念.
:::
\
16. 簡述疊代法
:::spoiler My Ans
設計疊代的行為, 確保其收斂性及收斂條件, 來逐步逼近/找出解.
:::
\
17. 窮舉法核心概念為何?
:::spoiler My Ans
考量所有可能的解, 找出符合的解或比對出最佳解, 很花時間.
:::
\
18. 回溯法核心概念為何?
:::spoiler My Ans
利用窮舉法在程式進行到一個階段時, 判斷是否現在條件不可能有合理的解. 若已知無解, 不儲存當前結果, 返回上一步.
:::


###### 1-5-2 結構化程式設計, 1-5-3 OOP略, 另外寫比較清楚(還沒寫, 懶得寫)

##### 心得及其他
1. 本章虛擬碼格式參考自[7], 原書[2]的虛擬碼種類多變, 且未解釋其虛擬碼撰寫格式
2. 資料結構可以提供一些"模板", 方便我們去設計自己的算法
3. 程式語言沒有最好這項描述, 其實跟系統設計非常像, 一個目標(績效)往往受許多機制影響. 作為**工程師**我們要清楚理解各機制間的Trade-off, 還要根據需求/spec設計出最有**價值**的成品, 不單只是效能/solution最好那麼單純.


## 參考資料
[1] [Swift Stack Implementation](https://www.journaldev.com/21287/swift-stack-implementation)
[2] 吳燦銘, 胡昭民, 圖解資料結構 使用C#
[3] [Big 'O' Notation](https://www.amitshahi.dev/blog/2019-06-23-big-o-notation/)
[4] [wiki - Recursion](https://en.wikipedia.org/wiki/Recursion_(computer_science))
[5] [wiki - Robustness](https://en.wikipedia.org/wiki/Robustness_(computer_science))
[6] [wiki - Side effect](https://en.wikipedia.org/wiki/Side_effect_(computer_science))
[7] [Pseudocode Conventions](https://link.springer.com/content/pdf/bbm%3A978-1-4471-5173-9%2F1.pdf)
[8] [Latex tutorial](https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference)
[9] [Changeability](https://spin.atomicobject.com/2018/12/05/first-principle-of-programming/)

###### tags: `note` `圖解資料結構筆記`