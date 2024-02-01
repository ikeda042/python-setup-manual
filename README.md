# Python環境構築
1. vscodeをインストール
   
<a>https://code.visualstudio.com/download</a>
   
2. Pythonをダウンロード
   
<a>https://www.python.org/downloads/</a>

<div align="center">

![Start-up window](images/python_install.png)

</div>

3. Pythonのダウンロードが完了したら、インストール時に"ADD PYTHON to PATH" にチェックを入れる。
   
4. VSCODEの拡張機能 "Python"をインストールする。
   
5. vecodeで拡張子.pyの新規ファイルを作成して、以下のようにコードを書き右上の三角ボタンを押すとターミナルに文字が出力される。（これができれば成功）
   
<div align="center">

![Start-up window](images/python_demo.png)

</div>

# Python PIP を使用できるようにする。
1. 以下をmacターミナルで実行する。
```bash
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
```
2. 1が完了後、以下を続けて実行する。
```bash
python3 get-pip.py
```

1. 試しに３つのモジュールをインストールする。
```bash
pip install matplotlib seaborn numpy
```

# グラフ描画サンプル
以下はMatplotlibでグラフを描画するサンプル。

```python
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
sns.set()

def box_plot_function(data:list[np.ndarray] | list[float|int], 
                      labels:list[str], 
                      xlabel:str, 
                      ylabel:str, 
                      save_name:str) -> None:
    fig = plt.figure(figsize=[10,7])
    plt.boxplot(data,sym="")
    for i, d in enumerate(data, start=1):
        x = np.random.normal(i, 0.04, size=len(d)) 
        plt.plot(x, d, 'o', alpha=0.5)  
    plt.xticks([i+1 for i in range(len(data))], [f"{i}" for i in labels])
    plt.xlabel(xlabel)
    plt.ylabel(ylabel)
    plt.grid(True)
    fig.savefig(f"{save_name}.png",dpi = 500)


data1 = np.random.normal(0, 1, size=100)
data2 = np.random.normal(0, 2, size=100)
data3 = np.random.normal(0, 3, size=100)

data  = [data1, data2, data3]
labels = ["data1", "data2", "data3"]
xlabel = "Samples"
ylabel = "Lengths (pixel)"
save_name = "result"
box_plot_function(data, labels, xlabel, ylabel, save_name)
```

.pyファイルと同じディレクトリに`result.png`が出力されたら成功。


