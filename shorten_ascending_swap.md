# 昇順スワップのコード長を短縮

大小比較用に sub した結果をそのまま利用する。文字には使えない。

短縮前（9行）
```
  copyto LOW
  sub HIGH
  jump if neg A
  copyfrom HIGH   ; 素直な入れ替えには6ステップかかる
  copyto TMP
  copyfrom LOW
  copyto HIGH
  copyfrom TMP
  copyto LOW
A:
```

短縮後（8行）
```
  copyto LOW
  sub HIGH
  jump if neg A
  copyto TMP
  copyfrom LOW
  copyto HIGH
  sub TMP
  copyto LOW
A:
```
