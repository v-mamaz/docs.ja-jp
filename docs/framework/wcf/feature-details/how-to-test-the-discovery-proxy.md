---
title: '方法: 探索プロキシをテストします。'
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 3c159481813266386706b34d172bbf9614a8253d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590514"
---
# <a name="how-to-test-the-discovery-proxy"></a>方法: 探索プロキシをテストします。
これは、探索プロキシの実装方法に関する 4 つのトピックのうちの 4 番目のトピックです。 前のトピックで[方法。探索プロキシを使用して、サービスを検索するクライアント アプリケーションの実装](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)、探索プロキシを使用して、サービスを検索して、サービスを呼び出している WCF クライアント アプリケーションを実装します。 このトピックでは、探索プロキシ、サービス、およびクライアント アプリケーションが予期したとおりに動作することを確認する方法について説明します。  
  
### <a name="run-the-discovery-proxy"></a>探索プロキシの実行  
  
1.  管理者としてコマンド プロンプトを開きます。  
  
2.  示すダイアログが表示されます。Windows ファイアウォールには、このプログラムの一部の機能がブロックされています。 このメッセージを表示する場合は、クリックして、**ブロック解除**ボタンをクリックします。  
  
3.  コマンド プロンプトから、探索プロキシ DiscoveryProxy.exe を実行します。  
  
4.  「`Proxy started. Hit Enter to exit`」というテキストが表示されます。  
  
### <a name="run-the-discoverable-service"></a>探索サービスの実行  
  
1.  管理者としてコマンド プロンプトを開きます。  
  
2.  コマンド プロンプトから、探索サービス Service.exe を実行します。  
  
3.  DiscoveryProxy.exe により、次のテキストが表示:`******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******`します。  
  
### <a name="run-the-client-application"></a>クライアント アプリケーションの実行  
  
1.  コマンド プロンプトを開きます。  
  
2.  コマンド プロンプトから、client.exe アプリケーションを実行します。  
  
3.  数秒後に、クライアント アプリケーションは、次のテキストを表示します。サービスのエンドポイントに接続します。  
  
4.  Service.exe し、次のテキストが表示されます。受信した要求を案内するには、私は応答します。  
  
5.  Client.exe し、次のテキストが表示されます。こんにちは Client!  
  
### <a name="shut-down-the-applications"></a>アプリケーションのシャットダウン  
  
1.  クライアント アプリケーションをシャットダウンします。  
  
2.  サービスをシャットダウンします。 探索プロキシにより、次のテキストが表示されます。`******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`  
  
3.  探索プロキシをシャットダウンします。  
  
## <a name="see-also"></a>関連項目
- [WCF Discovery の概要](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [方法: 探索プロキシを実装します。](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [方法: 探索プロキシで登録される探索可能なサービスを実装します。](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [方法: 探索プロキシを使用して、サービスを検索するクライアント アプリケーションを実装します。](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
