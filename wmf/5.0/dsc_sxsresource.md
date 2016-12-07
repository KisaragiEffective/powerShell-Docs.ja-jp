# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>DSC リソースのサイド バイ サイドのモジュール バージョン管理サポート

DSC リソースに含まれるモジュールは、サイド バイ サイドでインストールして、システムにインストールされるリソースの特定のバージョンを DSC 構成が使うようにできます。

詳細については、「[複数のバージョンがあるリソースの使用](https://msdn.microsoft.com/powershell/dsc/sxsresource)」を参照してください。

## <a name="known-issues"></a>既知の問題

このリリースでは、サイド バイ サイドのインストールについて次に挙げる既知の問題があります。

-   同じ構成内で DSC リソースの 2 つの異なるバージョンを使うことはサポートされていません。

