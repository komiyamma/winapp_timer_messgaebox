# WinTimerMessageBox

指定した時間で自動的に閉じるメッセージボックスをコマンドラインから表示するWindows用ツールです。

## 概要

`WinTimerMessageBox` は、Windowsの標準的なメッセージボックスを、指定したタイムアウト時間付きで表示するためのシンプルなコマンドラインユーティリティです。バッチファイルやスクリプトから、一時的な通知を手軽に行いたい場合に便利です。

## 使い方

```
WinTimerMessageBox.exe [本文] [タイトル] [フラグ] [表示ミリ秒]
```

### 引数

- `[本文]` (必須)
  - メッセージボックスに表示するテキストです。スペースを含む場合はダブルクォーテーション(`"`)で囲んでください。

- `[タイトル]` (任意)
  - メッセージボックスのタイトルバーに表示するテキストです。デフォルトは空です。スペースを含む場合はダブルクォーテーション(`"`)で囲んでください。

- `[フラグ]` (任意)
  - メッセージボックスのボタンの種類やアイコンを指定する数値フラグです。デフォルトは `0` (`MB_OK`) です。詳細は後述します。

- `[表示ミリ秒]` (任意)
  - メッセージボックスが自動的に閉じるまでの時間（ミリ秒単位）です。デフォルトは `3000` (3秒) です。

### 使用例

- 最もシンプルな例（OKボタンのみ、3秒で閉じる）
  ```
  WinTimerMessageBox.exe "処理が完了しました。"
  ```

- タイトルとアイコン付きの例（「はい/いいえ」ボタン、警告アイコン、10秒で閉じる）
  - `MB_YESNO` (4) + `MB_ICONWARNING` (48) = `52`
  ```
  WinTimerMessageBox.exe "本当に実行しますか？" "最終確認" 52 10000
  ```

## フラグの詳細

`フラグ`引数には、メッセージボックスの挙動を制御するための数値を指定します。これらの数値は、ボタンの種類、アイコン、デフォルトボタンなどを定義する定数の組み合わせ（合計値）です。

例えば、「はい/いいえ/キャンセル」ボタン (`MB_YESNOCANCEL` = `3`) と「質問」アイコン (`MB_ICONQUESTION` = `32`) を表示したい場合は、`3 + 32 = 35` を指定します。

### 主なフラグ

| ボタンの種類         | 値 | 説明                               |
| -------------------- | -- | ---------------------------------- |
| `MB_OK`              | 0  | 「OK」ボタン                       |
| `MB_OKCANCEL`        | 1  | 「OK」「キャンセル」ボタン         |
| `MB_YESNO`           | 4  | 「はい」「いいえ」ボタン           |
| `MB_YESNOCANCEL`     | 3  | 「はい」「いいえ」「キャンセル」ボタン |
| `MB_RETRYCANCEL`     | 5  | 「再試行」「キャンセル」ボタン     |

| アイコンの種類       | 値 | 説明                               |
| -------------------- | -- | ---------------------------------- |
| `MB_ICONERROR`       | 16 | 停止アイコン (エラー)              |
| `MB_ICONQUESTION`    | 32 | 疑問符アイコン (質問)              |
| `MB_ICONWARNING`     | 48 | 警告アイコン (注意)                |
| `MB_ICONINFORMATION` | 64 | 情報アイコン                       |

全ての利用可能なフラグについては、Microsoftの公式ドキュメントを参照してください。
- [MessageBox function (winuser.h) - Microsoft Docs](https://learn.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-messagebox)

## ビルド方法

このプロジェクトはVisual Studioでビルドできます。

1.  `WinTimerMessageBox.src/WinTimerMessageBox.sln` ファイルをVisual Studio (2017以降を推奨) で開きます。
2.  ソリューションをビルドします。
3.  `WinTimerMessageBox.src/Release/WinTimerMessageBox.exe` または `WinTimerMessageBox.src/x64/Release/WinTimerMessageBox.exe` に実行ファイルが生成されます。

## ライセンス

このソフトウェアは **BSD 3-Clause License** の下で公開されています。
詳細は `License.txt` をご確認ください。

## 作者

- Akitsugu Komiyama
- Microsoft Corporation
