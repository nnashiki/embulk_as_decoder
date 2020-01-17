# 事前準備

## gemのinstall 

```
embulk gem install embulk-parser-none
embulk gem install embulk-decoder-commons-compress
```

## 用意したunzip_charset_test_sjis.csv.zip の中身がsjisのcsvである確認

```
$ unzip unzip_charset_test_sjis.csv.zip 
Archive:  unzip_charset_test_sjis.csv.zip

$ nkf --guess unzip_charset_test_sjis.csv
Shift_JIS (CRLF)

$ cat unzip_charset_test_sjis.csv
���O,�^�C�v
�q�g�J�Q,�ق̂�
�[�j�K��,�݂�
�t�V�M�_�l,����%                      

$ rm unzip_charset_test_sjis.csv
```

# embulk runでunzip and 文字コード変換をしてみる 

```
$ embulk run embulk_test.yaml

# result.csvが作成される 

$ nkf --guess result.csv 
UTF-8 (LF)

$ cat result.csv
名前,タイプ
ヒトカゲ,ほのお
ゼニガメ,みず
フシギダネ,くさ
```


