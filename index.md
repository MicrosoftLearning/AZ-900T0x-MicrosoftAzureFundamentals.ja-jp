---
title: オンライン ホステッド インストラクション
permalink: index.html
layout: home
ms.openlocfilehash: c8816b7d9de9c19fbd4c6b3f373d6e4336c6ca5a
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908666"
---
# <a name="content-directory"></a>コンテンツ ディレクトリ

各チュートリアルへのハイパーリンク。 講師は、このチュートリアルをデモンストレーションまたは受講者用ラボとして使用できます。 

## <a name="walkthroughs"></a>チュートリアル

{% assign wts = site.pages | where_exp:"page", "page.url contains '/Instructions/Walkthroughs'" %}
| モジュール | チュートリアル |
| --- | --- | 
{% for activity in wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

