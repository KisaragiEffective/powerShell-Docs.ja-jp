# <a name="new-guid"></a>New-Guid
スクリプトを記述しているときには (または、おそらく DSC リソースを記述しているときにも)、多くの場合、一意の識別子が必要になることがあります。 GUID はこの用途に適しており、.NET Framework の Guid クラスを呼び出せば、簡単に生成できます。しかし、これを実行するコマンドレットがあれば、.NET Framework クラスをまだ使い慣れていないエンド ユーザーに使ってもらえます。

PS C:\\&gt; New-Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
