### <a name="multiple-items-in-a-single-tablelayoutpanel-cell-may-be-rearranged"></a><span data-ttu-id="27909-101">단일 TableLayoutPanel 셀에 있는 여러 항목이 다시 배열될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27909-101">Multiple items in a single TableLayoutPanel cell may be rearranged</span></span>

|   |   |
|---|---|
|<span data-ttu-id="27909-102">설명</span><span class="sxs-lookup"><span data-stu-id="27909-102">Details</span></span>|<span data-ttu-id="27909-103">.NET Framework 4.5에서 여러 항목이 동일한 <xref:System.Windows.Forms.TableLayoutPanel?displayProperty=name> 셀에 배치되면 .NET Framework 4.0과 다른 순서로 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27909-103">In the .NET Framework 4.5, if multiple items are placed in the same <xref:System.Windows.Forms.TableLayoutPanel?displayProperty=name> cell, they may be displayed in a different order than they were in the .NET Framework 4.0.</span></span>|
|<span data-ttu-id="27909-104">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="27909-104">Suggestion</span></span>|<span data-ttu-id="27909-105">이 동작은 .NET Framework 4.5에 대한 서비스 업데이트에서 되돌려졌습니다.</span><span class="sxs-lookup"><span data-stu-id="27909-105">This behavior was reverted in a servicing update for the .NET Framework 4.5.</span></span> <span data-ttu-id="27909-106">이 문제를 해결하려면 .NET Framework 4.5를 업데이트하거나 .NET Framework 4.5.1 이상으로 업그레이드하십시오.</span><span class="sxs-lookup"><span data-stu-id="27909-106">Please update the .NET Framework 4.5, or upgrade to .NET Framework 4.5.1 or later, to fix this issue.</span></span> <span data-ttu-id="27909-107">또는 동일한 <xref:System.Windows.Forms.TableLayoutPanel?displayProperty=name> 셀에서 여러 항목이 모호하지 않도록 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="27909-107">Alternatively, avoid the ambiguous case of multiple items in the same <xref:System.Windows.Forms.TableLayoutPanel?displayProperty=name> cell.</span></span>|
|<span data-ttu-id="27909-108">범위</span><span class="sxs-lookup"><span data-stu-id="27909-108">Scope</span></span>|<span data-ttu-id="27909-109">부</span><span class="sxs-lookup"><span data-stu-id="27909-109">Minor</span></span>|
|<span data-ttu-id="27909-110">버전</span><span class="sxs-lookup"><span data-stu-id="27909-110">Version</span></span>|<span data-ttu-id="27909-111">4.5</span><span class="sxs-lookup"><span data-stu-id="27909-111">4.5</span></span>|
|<span data-ttu-id="27909-112">형식</span><span class="sxs-lookup"><span data-stu-id="27909-112">Type</span></span>|<span data-ttu-id="27909-113">런타임</span><span class="sxs-lookup"><span data-stu-id="27909-113">Runtime</span></span>|
|<span data-ttu-id="27909-114">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="27909-114">Affected APIs</span></span>|<ul><li><xref:System.Windows.Forms.TableLayoutControlCollection.Add(System.Windows.Forms.Control%2CSystem.Int32%2CSystem.Int32)?displayProperty=nameWithType></li></ul>|
|<span data-ttu-id="27909-115">분석기</span><span class="sxs-lookup"><span data-stu-id="27909-115">Analyzers</span></span>|<ul><li><span data-ttu-id="27909-116">CD0098</span><span class="sxs-lookup"><span data-stu-id="27909-116">CD0098</span></span></li></ul>|
