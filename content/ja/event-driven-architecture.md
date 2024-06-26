---
title: イベント駆動アーキテクチャ
status: Completed
category: コンセプト
tags: ["アーキテクチャ", "", ""]
---

イベント駆動アーキテクチャは、イベントの作成、処理、および消費を促進するソフトウェアアーキテクチャです。
イベントとは、アプリケーションの状態に対する任意の変更を指します。
例えば、ライドシェアリングアプリで乗車を依頼することは、イベントを代表しています。
このアーキテクチャは、イベントがそのソース(乗車を要求するアプリ)から望ましいレシーバー(近くの利用可能なドライバーのアプリ)へ適切にルーティングされる構造を作り出します。

## 解決すべき問題はなんですか

より多くのデータがリアルタイムになるにつれて、イベントがキャプチャされ、イベントリクエストを処理する必要がある適切な[サービス](/ja/service/)へ正確にルーティングされる信頼性の高い方法を見つけることがますます困難になります。
イベントを処理する従来の方法は、メッセージが適切にルーティングされたか、あるいは実際に送信または受信されたかを保証する方法がないことがしばしばあります。
アプリケーションがスケールするにつれて、イベントをオーケストレーションすることがより困難になります。

## どのように役に立つのでしょうか

イベント駆動アーキテクチャは、すべてのイベントのためのセントラルハブ(例えばKafka)を確立します。
次に、イベントプロデューサー(ソース)とコンシューマー(レシーバー)を定義し、セントラルハブがイベントの流れを保証します。
このアーキテクチャは、サービス同士が疎結合のまま、イベントがプロデューサーからコンシューマーに適切にルーティングされることを保証します。
プロデューサーは、通常はHTTPプロトコルによって受信イベントを取り、イベント情報をルーティングします。
