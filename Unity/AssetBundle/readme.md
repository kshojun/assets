# 概要
- unity上でインポートしたアセットをランタイムで動的読み込みするための仕組み
- いわゆるダウンロードコンテンツ
- ビルドされたアプリのサイズを削減できる

# size制限
iOS 150MB
Android 100MB

# AssetBundleの構成要素
- AssetBundle Name/Variant
- AssetBundle Manifest
- Streamed Scene AssetBundle
- UnityWebRequestAssetBundle
- AssetBundleCreateRequest
- AssetBundleRequest
- BuildPipeline.BuildAssetBundles
- Caching
- AssetBundle Build

# AssetBundle
- UnityEngine.AssetBundleでAssetを取り出す
- LZ4のアルゴリズムでAssetを固めたバイナリファイル（テキスチャー、シーンとか）
- アセットをハッシュ化したAssetFileHashを持つ
- クラス構造をハッシュ化したTypeTreeHashもある



