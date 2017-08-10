# ループの高速化

jump→「後処理」→jumpしてループする場合、「後処理」の部分をループ先頭の手前に書いて、
ループ初回だけ「後処理」をjumpで飛ばすようにしたら、同じ行数でステップ数を削減できる。

Level 9 高速化前（28ステップ）
```
A:
  inbox
  jump if zero B
  jump A
B:
  outbox
  jump A
```

Level 9 高速化後（25ステップ）
```
  jump B
A:
  outbox
B:
  inbox
  jump if zero A:
  jump B
```
