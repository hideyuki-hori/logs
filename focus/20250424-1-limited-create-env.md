# 目的

2025/04/24

limitedの目的を改めて整理する。

# chrome extensionの開発

一日の大半がchromeでの作業なので、気軽に拡張機能が作りたい。


# templateを使った表現の模索

webglはボイラープレートが多いためthreejsをつかっていた。
またかっこいい表現というのはある程度パターン化されており、手作りだろうがテンプレだろうが結局作るものは同じである。

一方でテンプレを使った場合拡張性が下がってしまう欠点もある。
なので今回 limited ではテンプレ以上のことをしない(できない)ということにする。

# 構成

- react
- tailwind
- r3f
- drei
- three

後でpostprocessingとか入れるかもしれないが、ベースは完成。
