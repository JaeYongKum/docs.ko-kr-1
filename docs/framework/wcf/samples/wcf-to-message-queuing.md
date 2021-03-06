---
title: Windows Communication Foundation에서 메시지 큐로
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: ea0723d178b37b1ff2581981f8f49a6953c913cc
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777524"
---
# <a name="windows-communication-foundation-to-message-queuing"></a>Windows Communication Foundation에서 메시지 큐로
이 샘플 응용 프로그램을 Windows Communication Foundation (WCF) 메시지 큐 (MSMQ) 응용 프로그램에 메시지를 보내는 방법을 보여 줍니다. 이 서비스는 자체적으로 호스트되는 콘솔 응용 프로그램으로서 이를 사용하여 서비스에서 대기된 메시지를 받는 것을 볼 수 있습니다. 서비스 및 클라이언트가 동시에 실행될 필요는 없습니다.  
  
 서비스는 큐로부터 메시지를 받아 주문을 처리합니다. 다음 샘플 코드에서 보여 주는 것처럼 서비스는 트랜잭션 큐를 만들고 메시지 수신 메시지 처리기를 설정합니다.  

```csharp
static void Main(string[] args)  
{  
    if (!MessageQueue.Exists(  
              ConfigurationManager.AppSettings["queueName"]))  
       MessageQueue.Create(  
           ConfigurationManager.AppSettings["queueName"], true);  
        //Connect to the queue  
        MessageQueue Queue = new   
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);  
    Queue.ReceiveCompleted +=   
                 new ReceiveCompletedEventHandler(ProcessOrder);  
    Queue.BeginReceive();  
    Console.WriteLine("Order Service is running");  
    Console.ReadLine();  
}  
```

 큐에 메시지가 수신되면 메시지 처리기 `ProcessOrder`가 호출됩니다.  

```csharp
public static void ProcessOrder(Object source,  
    ReceiveCompletedEventArgs asyncResult)  
{  
    try  
    {  
        // Connect to the queue.  
        MessageQueue Queue = (MessageQueue)source;  
        // End the asynchronous receive operation.  
        System.Messaging.Message msg =   
                     Queue.EndReceive(asyncResult.AsyncResult);  
        msg.Formatter = new System.Messaging.XmlMessageFormatter(  
                                new Type[] { typeof(PurchaseOrder) });  
        PurchaseOrder po = (PurchaseOrder) msg.Body;  
        Random statusIndexer = new Random();  
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];  
        Console.WriteLine("Processing {0} ", po);  
        Queue.BeginReceive();  
    }  
    catch (System.Exception ex)  
    {  
        Console.WriteLine(ex.Message);  
    }  
  
}  
```

 서비스는 MSMQ 메시지 본문으로부터 `ProcessOrder`를 추출하고 주문을 처리합니다.  
  
 다음 샘플 구성에서 보여 주는 것처럼 MSMQ 큐 이름은 구성 파일의 appSettings 섹션에 지정됩니다.  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  큐 이름은 로컬 컴퓨터에 점(.)을, 그 경로에는 백슬래시 구분 기호를 사용합니다.  
  
 다음 샘플 코드에서 보여 주는 것처럼 클라이언트가 구매 주문을 만들고 트랜잭션 범위 내에서 구매 주문을 제출합니다.  

```csharp
// Create the purchase order  
PurchaseOrder po = new PurchaseOrder();  
// Fill in the details  
...  
  
OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");  
  
MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    client.SubmitPurchaseOrder(ordermsg);  
    scope.Complete();  
}  
Console.WriteLine("Order has been submitted:{0}", po);  
  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```

 클라이언트는 큐에 MSMQ 메시지를 보내기 위해 사용자 지정 클라이언트를 사용합니다. 수신 하 고 메시지를 처리 하는 응용 프로그램을 MSMQ 응용 프로그램 및 WCF 응용 프로그램이 아닙니다. 있으므로 두 응용 프로그램 간의 암시적인 서비스 계약은 없습니다 됩니다. 따라서 이 시나리오에서는 Svcutil.exe 도구를 사용하여 프록시를 만들 수 없습니다.  
  
 사용자 지정 클라이언트는 기본적으로 사용 하는 모든 WCF 응용 프로그램에 대해 동일 합니다 `MsmqIntegration` 메시지를 보내는 바인딩. 다른 클라이언트와 달리, 여기에는 서비스 작업 범위가 포함되지 않으며 메시지 제출 작업으로만 한정됩니다.  

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
  
public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor  
{  
    public OrderProcessorClient(){}  
  
    public OrderProcessorClient(string configurationName)  
        : base(configurationName)  
    { }  
  
    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)  
        : base(binding, address)  
    { }  
  
    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
    {  
        base.Channel.SubmitPurchaseOrder(msg);  
    }  
}  
```

 샘플을 실행하면 클라이언트 및 서비스 동작이 서비스 콘솔 창과 클라이언트 콘솔 창에 모두 표시됩니다. 서비스에서 클라이언트가 보내는 메시지를 받는 것을 볼 수 있습니다. 서비스와 클라이언트를 종료하려면 각 콘솔 창에서 Enter 키를 누릅니다. 큐를 사용하므로 클라이언트와 서비스가 동시에 실행 중일 필요는 없습니다. 예를 들어 클라이언트를 실행하고 종료한 다음 서비스를 다시 시작해도 메시지를 받을 수 있습니다.  
  
> [!NOTE]
>  이 샘플을 사용하려면 메시지 큐를 설치해야 합니다. 설치 지침을 참조 하세요 [메시지 큐](https://go.microsoft.com/fwlink/?LinkId=94968)합니다.  
  
### <a name="to-setup-build-and-run-the-sample"></a>샘플을 설치, 빌드 및 실행하려면  
  
1.  수행 했는지 확인 합니다 [Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)합니다.  
  
2.  서비스가 처음 실행되는 경우 서비스에서는 큐가 있는지 확인하고 큐가 없으면 큐를 만듭니다. 서비스를 처음 실행하여 큐를 만들거나 MSMQ 큐 관리자를 통해 큐를 만들 수 있습니다. Windows 2008에서 큐를 만들려면 다음 단계를 수행하세요.  
  
    1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]에서 서버 관리자를 엽니다.  
  
    2.  확장 된 **기능** 탭 합니다.  
  
    3.  마우스 오른쪽 단추로 클릭 **개인 메시지 큐**, 선택한 **새로 만들기**합니다 **개인 큐**합니다.  
  
    4.  확인 합니다 **트랜잭션** 상자입니다.  
  
    5.  입력 `ServiceModelSamplesTransacted` 새 대기열의 이름으로 합니다.  
  
3.  C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)의 지침을 따릅니다.  
  
4.  단일 컴퓨터 구성에서 샘플을 실행 하려면의 지침을 따릅니다 [Windows Communication Foundation 샘플 실행](../../../../docs/framework/wcf/samples/running-the-samples.md)합니다.  
  
### <a name="to-run-the-sample-across-computers"></a>다중 컴퓨터 구성에서 샘플을 실행하려면  
  
1.  언어별 폴더의 \service\bin\ 폴더에서 서비스 컴퓨터로 서비스 프로그램 파일을 복사합니다.  
  
2.  언어별 폴더의 \client\bin\ 폴더에서 클라이언트 프로그램 파일을 클라이언트 컴퓨터로 복사합니다.  
  
3.  Client.exe.config 파일에서 클라이언트 엔드포인트 주소를 변경하여 "." 대신 서비스 컴퓨터 이름을 지정합니다.  
  
4.  서비스 컴퓨터의 명령 프롬프트에서 Service.exe를 실행합니다.  
  
5.  클라이언트 컴퓨터의 명령 프롬프트에서 Client.exe를 실행합니다.  
  
> [!IMPORTANT]
>  컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다. 계속하기 전에 다음(기본) 디렉터리를 확인하세요.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  이 디렉터리가 없으면로 이동 [Windows Communication Foundation (WCF) 및.NET Framework 4 용 Windows WF (Workflow Foundation) 샘플](https://go.microsoft.com/fwlink/?LinkId=150780) 모든 Windows Communication Foundation (WCF)를 다운로드 하 고 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 샘플. 이 샘플은 다음 디렉터리에 있습니다.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a>참고 항목  
 [방법: WCF 엔드포인트 및 메시지 큐 응용 프로그램과 메시지 교환](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [메시지 큐](https://go.microsoft.com/fwlink/?LinkId=94968)
