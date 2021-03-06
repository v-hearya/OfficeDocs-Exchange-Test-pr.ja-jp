﻿---
title: '承認済みドメイン: Exchange 2013 Help'
TOCTitle: 承認済みドメイン
ms:assetid: c1839a5b-49f9-4c53-b247-f4e5d78efc45
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Bb124423(v=EXCHG.150)
ms:contentKeyID: 49896454
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# 承認済みドメイン

 

_**適用先:** Exchange Server 2013_

_**トピックの最終更新日:** 2016-06-16_

承認済みドメインとは、Microsoft Exchange Server 2013 組織が電子メールを送受信する、任意の SMTP 名前空間です。承認済みドメインには、Exchange 組織が権限を持つこれらのドメインが含まれます。Exchange 組織は、承認済みドメイン内の受信者に対するメール配信を処理するときの権限を持っています。また、承認済みドメインには、Exchange 組織がメールを受信してから、受信者に配信するために組織の外部の電子メール サーバーに中継するドメインも含まれます。

**目次**

承認済みドメインの構成

権限のあるドメイン

中継ドメイン

内部の中継ドメイン

外部の中継ドメイン

承認済みドメインおよび電子メール アドレス ポリシー

## 承認済みドメインの構成

承認済みドメインは、Exchange 組織のグローバル設定として構成されます。Exchange 組織がメッセージを中継または配信するすべてのドメインを、組織内の承認済みドメインとして構成する必要があります。

承認済みドメインは 3 種類あります: 権限のあるドメイン、内部の中継ドメイン、外部の中継ドメインこれらの承認済みドメインの種類について、以降のセクションで詳細に説明します。


> [!NOTE]
> 境界ネットワークでエッジ トランスポート サーバーを購読している場合は、Exchange 組織内のメールボックス サーバーに承認済みドメインを構成します。承認済みドメインの構成は、EdgeSync 同期の際にエッジ トランスポート サーバーにレプリケートされます。詳細については、「<A href="edge-subscriptions-exchange-2013-help.md">エッジ サブスクリプション</A>」を参照してください。



## 権限のあるドメイン

組織には、1 つ以上の SMTP ドメインがあります。組織の電子メール ドメインのセットは権限のあるドメインです。Exchange 2013 では、Exchange 組織がこの SMTP ドメインで受信者のメールボックスをホストするとき、承認済みドメインは権限があると見なされます。

既定では、最初の Exchange 2013 メールボックス サーバーがインストールされたとき、1 つの承認済みドメインが Exchange 組織の権限のあるドメインとして構成されます。既定の承認済みドメインは、フォレスト ルート ドメインの完全修飾ドメイン名 (FQDN) です。内部ドメイン名が外部ドメイン名と異なることがよくあります。たとえば、外部ドメイン名が contoso.com であるにもかかわらず、内部ドメイン名が contoso.local である場合があります。組織の DNS メール エクスチェンジャー (MX) のレコードは、contoso.com を参照します。contoso.com は、電子メール アドレス ポリシーを作成したときにユーザーに割り当てた SMTP 名前空間です。外部ドメイン名に一致する承認済みドメインを作成する必要があります。

詳細については、次を参照してください。

  - [Exchange 組織内の承認済みドメインを権限ありとして構成する](configure-an-accepted-domain-within-your-exchange-organization-as-authoritative-exchange-2013-help.md)

  - [複数の権限のあるドメインのメールを受け付けるように Exchange を構成する](configure-exchange-to-accept-mail-for-multiple-authoritative-domains-exchange-2013-help.md)

## 中継ドメイン

一般的に、インターネットに直接接続されたほとんどのメッセージング サーバーは、それらのサーバーを介して他のドメインを中継できないように構成されています。ただし、パートナーまたは関連子会社による Exchange サーバーを介した電子メールの中継を許可することが必要な場合があります。Exchange 2013 では、承認済みドメインを中継ドメインとして構成できます。組織が電子メール メッセージを受信して、その後、別の電子メール サーバーにメッセージを中継します。

中継ドメインを内部の中継ドメインまたは外部の中継ドメインとして構成できます。これらの 2 つの中継ドメインの種類について、以降のセクションで詳細に説明します。

## 内部の中継ドメイン

内部の中継ドメインを構成する場合、このドメイン内の一部またはすべての受信者には、この Exchange 組織のメールボックスがありません。インターネットからのメールは、この Exchange 組織のトランスポート サーバーを介して、このドメインに中継されます。この構成はここで説明されているシナリオで使用します。

組織は、複数の異なるメッセージング システム間で同じ SMTP アドレス スペースを共有する必要があることがあります。たとえば、Exchange とサードパーティのメッセージング システムとの間で、または異なる複数の Exchange フォレストに構成された Active Directory 環境の間で SMTP アドレス スペースを共有することが必要な場合があります。このようなシナリオでは、各電子メール システムのユーザーは電子メール アドレスの一部として同じドメイン サフィックスを持ちます。

このようなシナリオをサポートするには、内部の中継ドメインとして構成された承認済みドメインを作成する必要があります。また、メールボックス サーバー上に送信元があり、共有アドレス スペースに電子メールを送信するように構成された送信コネクタを追加する必要があります。承認済みドメインが権限を持つドメインとして構成されていて、Active Directory に受信者が見つからない場合は、配信不能レポート (NDR) が送信者に返されます。内部の中継ドメインとして構成されている承認済みドメインでは、最初に Exchange 組織内の受信者への配信が試みられます。受信者が見つからない場合は、メッセージは、最も近いアドレス スペースに一致する送信コネクタにルーティングされます。

組織に 2 つ以上のフォレストが含まれ、グローバル アドレス一覧 (GAL) 同期を構成する場合は、1 つのフォレストの SMTP ドメインが 2 番目のフォレストで内部の中継ドメインとして構成されます。内部の中継ドメイン内の受信者宛てのインターネットからのメッセージは、同じ組織内のメールボックス サーバーに中継されます。メールボックス サーバーが受信すると、受信者のフォレスト内でメールボックス サーバー宛てのメッセージはルーティングされます。SMTP ドメイン宛ての電子メールを Exchange 組織によって確実に受信するため、SMTP ドメインを内部の中継ドメインとして構成します。組織のコネクタの構成はメッセージのルーティングの方法を決定します。

詳細については、「[Exchange 組織外のメールボックスで部署用に承認済みドメインを構成する](configure-an-accepted-domain-for-a-business-unit-with-mailboxes-outside-your-exchange-organization-exchange-2013-help.md)」を参照してください。

## 外部の中継ドメイン

外部の中継ドメインを構成するとき、メッセージは Exchange 組織外の電子メール サーバーおよび組織の境界ネットワーク外に中継されます。

詳細については、「[独立した部署の承認済みドメインの構成](configure-an-accepted-domain-for-an-independent-business-unit-exchange-2013-help.md)」を参照してください。

## 承認済みドメインおよび電子メール アドレス ポリシー

電子メール アドレス ポリシーで SMTP アドレス スペースを使用するには、事前に承認済みドメインを構成する必要があります。承認済みドメインを作成するとき、アドレス スペースにワイルドカード文字 (\*) を使用して、Exchange 組織によって SMTP アドレス スペースのすべてのサブドメインを許可することもできます。たとえば、contoso.com とそのサブドメインを承認済みドメインとしてを構成するには、SMTP アドレス スペースとして **\*.contoso.com** と入力します。承認済みドメイン エントリは自動的に電子メール アドレス ポリシーで使用可能です。

電子メール アドレス ポリシーで使用されている承認済みドメインを削除した場合、ポリシーは無効になり、その SMTP ドメインで電子メール アドレスを持つ受信者は電子メールの送受信ができなくなります。

