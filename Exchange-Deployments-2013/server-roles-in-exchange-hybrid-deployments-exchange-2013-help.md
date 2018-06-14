﻿---
title: 'Exchange ハイブリッド展開のサーバー役割: Exchange 2013 Help'
TOCTitle: Exchange ハイブリッド展開のサーバー役割
ms:assetid: 7a7eaf17-d2b0-4d62-90a2-45a0d2faca54
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ659051(v=EXCHG.150)
ms:contentKeyID: 49894951
ms.date: 01/11/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange ハイブリッド展開のサーバー役割

 

_**適用先:**Exchange Server 2013, Exchange Server 2016_

_**トピックの最終更新日:**2016-12-09_

Exchange 2013 と Exchange 2016 に基づいて、ハイブリッド展開を構成できます。ハイブリッド展開をサポートするように構成する必要がある役割は、使用している Exchange のバージョンによって異なります。

## Exchange 2016 ハイブリッド展開

Exchange 2016 組織内でハイブリッド展開を構成する場合、既存の Exchange 組織に追加の Exchange サーバーをインストールする必要はありません。メールボックス サーバーが、既存の Exchange 2016 組織と Exchange Online 組織との間で通信を調整します。この通信には、社内組織と Exchange Online 組織間のメッセージ トランスポート機能およびメッセージング機能が使用されます。ハイブリッド展開機能の信頼性と可用性を向上するために、社内組織に 1 台以上の Exchange サーバーをインストールすることを強くお勧めします。

Exchange 2016 には、必須のサーバーの役割であるメールボックスの役割だけが割り当てられます。オンプレミス受信メールボックスのホスティングに加えて、メールボックスの役割は、Exchange Online でハイブリッド展開をサポートするために必要なすべての機能を実行します。これには、オンプレミス組織と Exchange Online 組織間のセキュリティで保護されたメール メッセージだけでなく、ハイブリッド展開でのトランスポート ルール、ポリシーのジャーナリング、およびユーザー メールボックスへのメッセージ配信の処理も含まれます。空き時間情報の共有など、すべてのクライアント接続機能と組織上の関係機能もメールボックス サーバーで処理されます。

Exchange 2016 のキャパシティ プランニングの詳細については、「[Exchange 2016 展開のサイジング](http://go.microsoft.com/fwlink/p/?linkid=301990)」を参照してください。

## Exchange 2013 ハイブリッド展開

Exchange 2013 組織内でハイブリッド展開を構成する場合、既存の Exchange 組織に追加の Exchange サーバーをインストールする必要はありません。クライアント アクセス サーバーとメールボックス サーバーが、既存の Exchange 2013 組織と Exchange Online 組織との間で通信を調整します。この通信には、社内組織と Exchange Online 組織間のメッセージ トランスポート機能およびメッセージング機能が使用されます。ハイブリッド展開機能の信頼性と可用性を向上するために、社内組織に 1 台以上の Exchange サーバーをインストールすることを強くお勧めします。

ここでは、ハイブリッド展開における Exchange 2013 サーバーの役割について簡単に概説します。

  - **クライアント アクセス サーバーの役割**   クライアント アクセス サーバーの役割によって提供される機能は、ハイブリッド展開をサポートするために必要な機能が若干追加されますが、基本的には Exchange 2013 組織内のクライアント アクセス サーバーによって一般的に提供される機能と同じです。クライアント アクセス サーバーは、社内組織と Exchange Online 組織との間で送信された、セキュリティ保護されたすべてのメール メッセージ、およびハイブリッド展開でのトランスポート ルール、ポリシーのジャーナリング、およびユーザー メールボックスへのメッセージ配信も処理します。既定では、専用受信コネクタはクライアント アクセス サーバー上で構成され、セキュリティ保護されたハイブリッド メール トランスポートがサポートされます。Outlook クライアント アクセス、Outlook Web App、および Outlook Anywhere などのすべてのクライアント接続は、クライアント アクセス サーバーの役割を介します。空き情報の共有など、社内組織と Exchange Online 組織間の組織上の関係機能も、クライアント アクセス サーバーの役割によって処理されます。
    
    詳細については、「[クライアント アクセス サーバー](https://technet.microsoft.com/ja-jp/library/dd298114\(v=exchg.150\))」を参照してください。

  - **メールボックス サーバーの役割**   メールボックス サーバーの役割は社内受信者メールボックスをホストし、社内クライアント アクセス サーバーを経由してプロキシで Exchange Online 組織と通信します。既定では、専用送信コネクタはメールボックス サーバーの役割で構成され、セキュリティ保護されたハイブリッド メール トランスポートがサポートされます。
    
    詳細については、「[メールボックス サーバー](https://technet.microsoft.com/ja-jp/library/jj150491\(v=exchg.150\))」を参照してください。

必要なハイブリッド展開構成に応じて、Exchange 2013 サーバーに、片方または両方のサーバーの役割をインストールする必要があります。

  - **単一の Exchange サーバー**   社内組織に単一の Exchange サーバーをインストールする場合は、単一のサーバーにクライアント アクセス サーバーとメールボックス サーバーの両方の役割をインストールする必要があります。

  - **複数の Exchange サーバー**   社内組織に複数の Exchange サーバーをインストールする場合は、社内組織内にある別々のサーバーにサーバーの役割をインストールできます。たとえば、メールボックスの役割とクライアント アクセスの役割がインストールされている 1 台の Exchange サーバーをインストールして、クライアント アクセス サーバーの役割のみがインストールされている別の Exchange サーバーをインストールすることができます。ただし、ベスト プラクティスであり推奨されるサーバーの構成は、社内組織に展開されている*各*サーバーにクライアント アクセス サーバーとメールボックス サーバーの両方の役割をインストールする構成です。

Exchange 2013 容量プランニングの詳細については、「[容量計画での複数のサーバーの役割の構成について](http://go.microsoft.com/fwlink/?linkid=266576)」を参照してください。

## ハイブリッドの展開での Exchange サーバーの機能

Exchange サーバーは、ハイブリッド展開の社内組織にとって重要な機能をいくつか提供します。

  - **フェデレーション**Exchange サーバーにより、Microsoft Federation Gateway との間の社内組織のフェデレーションの信頼を作成することができます。Microsoft Federation Gateway は、社内組織と Office 365 組織間の信頼ブローカーとして機能する、マイクロソフトが無償で提供するクラウドベースのサービスです。フェデレーションは、社内組織と Exchange Online 組織間の組織の関係を作成するうえで必須です。
    
    詳細については、「[フェデレーション](https://technet.microsoft.com/ja-jp/library/dd335047\(v=exchg.150\))」を参照してください。

  - **組織上の関係**   クライアント アクセスの役割を持つ Exchange 2013 サーバーとメールボックスの役割を持つ Exchange 2016 サーバーにより、オンプレミス組織と Exchange Online 組織間の組織上の関係を作成できます。組織上の関係は、ハイブリッド展開においてその他の多くのサービス (予定表の空き時間情報の共有、メッセージ追跡、社内組織と Exchange Online 組織間でのメールボックスの移動など) に必要です。
    
    詳細については、「[共有](https://technet.microsoft.com/ja-jp/library/dd638083\(v=exchg.150\))」を参照してください。

  - **メッセージ トランスポート**   クライアント アクセス サーバーとメールボックス サーバーの役割がインストールされている Exchange サーバーは、ハイブリッド展開でのメッセージ トランスポートを担当します。送信/受信コネクタを使用して、外部の受信メッセージ用の接続エンドポイントとして機能し、さらに送信メッセージをインターネットおよび Exchange Online 組織に配信します。
    
    詳細については、「[Exchange ハイブリッド展開でのトランスポート オプション](transport-options-in-exchange-hybrid-deployments-exchange-2013-help.md)」を参照してください。

  - **メッセージ トランスポート セキュリティ**   クライアント アクセス サーバーとメールボックス サーバーの役割がインストールされている Exchange サーバーは、Exchange のドメイン セキュリティ機能を使用して、社内組織と Exchange Online 組織間のメッセージ通信のセキュリティ保護を支援します。メッセージ通信に対して相互トランスポート層セキュリティ認証および暗号化を使用することによって、セキュリティを強化できます。
    
    詳細については、「[ドメイン セキュリティについて](http://go.microsoft.com/fwlink/p/?linkid=266581)」を参照してください。

  - **Outlook on the web (Exchange 2013 では Outlook Web App と呼ばれる)**   クライアント アクセスの役割を持つ Exchange 2013 サーバーとメールボックスの役割を持つ Exchange 2016 サーバーは、オンプレミス メールボックスと Exchange Online メールボックスへの外部接続用の単一の URL エンドポイントの構成をサポートします。オンプレミス メールボックスの場合、Exchange サーバーは、Web 上の Outlook 要求を処理するように構成されます。Exchange Online 組織メールボックスの場合、Exchange サーバーは、Web 上の Outlook エンドポイントへのリンクを Exchange Online 組織に自動的に表示するように構成されます。
    
    詳細については、「[Outlook Web App](https://technet.microsoft.com/ja-jp/library/jj657718\(v=exchg.150\))」を参照してください。
