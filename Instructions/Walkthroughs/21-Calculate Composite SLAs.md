---
wts:
  title: 21 - 複合 SLA の計算 (5分)
  module: 'Module 06: Describe Azure cost management and service level agreements'
ms.openlocfilehash: 1d27d18cd1a0b2ad6ab09c7fc65a51d5a8f13711
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907690"
---
# <a name="21---calculate-composite-slas-5-min"></a>21 - 複合 SLA の計算 (5分)

このチュートリアルでは、Azure サービスの可用性 SLA を決定し、アプリケーション複合 SLA ベースの推定可用性を計算します。

このサンプル アプリケーションは、次の Azure サービスで構成されています。 ここでは、高レベルの例を提供することとし、アーキテクチャーの詳細な構成や考慮事項については割愛します。

+ **App Services**:アプリケーションをホストします。
+ **Azure AD B2C**:ユーザー ログインを認証し、プロファイルを管理します。
+ **Application Gateway**:アプリケーション アクセスやスケーリングを管理します。 
+ **Azure SQL Database**:アプリケーション データを格納します。 

# <a name="task-1-determine-the-sla-uptime-percentage-values-for-our-application"></a>タスク 1:アプリケーションの SLA アップタイムのパーセンテージ値を決定します。

1. ブラウザーで、[[Azure サービスの SLA サマリー]](https://azure.microsoft.com/en-us/support/legal/sla/summary/) ページに移動します。

2. **アプリ サービス** の SLA アップタイム値 **99.95%** を見つけます。 **[詳細の表示]** をクリックし、 **[SLA の詳細]** を展開します。 **[月間アップタイム率]** と **[サービス クレジット]** を確認します。

3. SLA Web ページに戻り、 **[Azure Active Directory B2C]** サービスを見つけて、SLA アップタイムの値 **[99.9%]** を確認します。 

4. **Application Gateway** の SLA アップタイム値 **99.95%** を確認します。 

5. Azure SQL データベースでは Premium レベルを使用しますが、ゾーン冗長デプロイ向けには構成されていません。 **[Azure SQL Database]** SLA のアップタイム値 **[99.99%]** を見つけます。 

    **注**:Azure SQL Database の構成とデプロイごとに、アップタイム値が異なります。 デプロイと構成を計画およびコスト管理する際には、必要なアップタイム値を明確にすることが重要です。 アップタイムの変更が小さくても、サービス コストに影響を与える可能性があり、構成の複雑さが増大する可能性があります。 Azure SLA 概要 Web ページで興味を引く他のサービスには、**Virtual Machines**、**ストレージ アカウント**、**Cosmos DB** などがあります。

# <a name="task-2-calculate-the-application-composite-sla-percentage-uptime"></a>タスク 2:アプリケーションの複合 SLA のアップタイム率を計算する

1. アプリケーションを構成するサービスのいずれかが利用できない場合、ユーザーはサインインしてアプリケーションを利用できません。 そのため、アプリケーションの合計アップタイムは次の要素で構成されます。

    **アプリ サービスのアップタイム率** X **Azure AD B2C のアップタイム率** X  **Azure Application Gateway のアップタイム率** X **Azure SQL Database のアップタイム率** = **合計アップタイム率**

    パーセントで表すと次のとおりです。

    **99.95%** X **99.9%** X **99.95%** X **99.99%**  = **99.79%**

    これは、現在のサービスおよびアーキテクチャを使用したアプリケーションの SAL ベースの推定可用性です。

おめでとうございます! サンプル アプリケーションの各サービスの SLA べース アップタイムを決定し、アプリケーションの複合 SLA ベース推定可用性を計算しました。
