---
wts:
  title: 03 - Azure Container Instances をデプロイする (10 分)
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 0616be96840b14f7580c7d2b16cb43b211c6e3a2
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908623"
---
# <a name="03---deploy-azure-container-instances-10-min"></a>03 - Azure Container Instances をデプロイする (10 分)

このチュートリアルでは、Azure portal で Azure Container Instances (ACI) を使用して、コンテナーを作成、構成、デプロイします。 このコンテナーは、静的な HTML ページを表示する「ACI Web アプリケーションへようこそ」です。 

# <a name="task-1-create-a-container-instance"></a>タスク 1:コンテナー インスタンスを作成する 

このタスクでは、Web アプリケーションの新しいコンテナー インスタンスを作成します。  

1. [Azure portal](https://portal.azure.com) にサインインします。

2. 「**すべてのサービス**」ブレードで「**コンテナー インスタンス**」を検索して選択し、 **「+ 追加」、「+ 作成」、「+ 新規」** のいずれかをクリックします。 

3. 新しいコンテナー　インスタンスについて、次の基本的な詳細を入力します (その他の情報は既定値のままにします)): 

    | 設定| 値|
    |----|----|
    | サブスクリプション | ***提供された既定値を使用する*** |
    | Resource group | **新しいリソース グループの作成** |
    | コンテナー名| **mycontainer**|
    | リージョン | **(米国) 米国東部** |
    | イメージのソース| **Docker Hub またはその他のレジストリ**|
    | イメージの種類| **Public**|
    | Image| **mcr.microsoft.com/azuredocs/aci-helloworld**|
    | OS の種類| **Linux** |
    | サイズ| ***既定値のままにする***|


4. ネットワーク タブを構成します (**xxxxx** をグローバルに一意になるように文字と数字に置き換えます)。 その他の設定はすべて、既定値のままにします。

    | 設定| 値|
    |--|--|
    | DNS 名ラベル| **mycontainerdnsxxxxx** |

    
    **注**:コンテナーは、dns-name-label.region.azurecontainer.io でパブリックからアクセスできるようになります。 デプロイ後に **DNS 名ラベルは使用できません** というエラー メッセージが表示された場合、別の DNS 名ラベル (xxxxxを置き換えます) を指定して再びデプロイします。 

5. 「**確認および作成**」を選択して、自動検証プロセスを開始します。

6. 「**作成**」を選択してコンテナー インスタンスを作成します。 

7. デプロイ ページと「**通知**」ページを監視します。 


# <a name="task-2-verify-deployment-of-the-container-instance"></a>タスク 2:コンテナー インスタンスのデプロイを確認する

このタスクでは、ウェルカム ページが表示されることを確認して、コンテナー インスタンスが実行されていることを確認します。

1. デプロイが完了したら、「デプロイ」ブレードで「**リソースに移動**」リンクを使用するか、「通知」領域でリソースにリンクします。

2. **mycontainer** の「**概要**」ブレードで、「**状態**」が「**実行中**」であることを確認します。 

3. 完全修飾ドメイン名 (FQDN) を見つけます。

    ![FQDN が強調表示された、Azure Portal で新しく作成されたコンテナーの概要ペインのスクリーンショット。 ](../images/0202.png)

2. コンテナーの FQDN を新しい Web ブラウザー タブにコピーして、**Enter** キーを押します。 ウェルカム ページが表示されます。 

    ![Web ブラウザーに表示される ACI ウェルカム メッセージのスクリーンショット。](../images/0203.png)


**お疲れさまでした。** Azure portal を使用して、Azure Container Instances のコンテナーにアプリケーションを正常にデプロイしました。

**注**:追加コストを回避するには、オプションでこのリソース グループを削除します。 リソース グループを検索し、リソース グループをクリックして、「**リソース グループの削除**」をクリックします。 リソース グループの名前を確認し、「**削除**」をクリックします。 **通知** を監視して、削除の進行状況を確認します。
