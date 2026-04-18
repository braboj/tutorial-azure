## Chapter 11: Cost Management and Optimization

---

### 📚 What You'll Learn in This Chapter

By the end of this chapter, you'll understand:

- ✓ Factors affecting Azure costs
- ✓ Pricing Calculator vs TCO Calculator
- ✓ Cost Management tools
- ✓ Cost optimization strategies
- ✓ Reserved Instances savings
- ✓ Azure Hybrid Benefit
- ✓ Top 20 money-saving tips

**Time needed:** 25-30 minutes  
**Difficulty:** Moderate 🟡

**Why this matters:** Cost management is crucial for AZ-900 exam and real-world Azure usage!

---

## Understanding Azure Pricing

### What Affects Your Bill?

```
┌──────────────────────────────────────────────────────────────┐
│ 6 FACTORS THAT AFFECT COSTS                                  │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│ 1. RESOURCE TYPE                                             │
│    VM costs more than storage                                │
│    Premium SSD costs more than Standard HDD                  │
│                                                              │
│ 2. USAGE (Pay-as-you-go)                                     │
│    • VMs: Per hour running                                   │
│    • Storage: Per GB stored                                  │
│    • Bandwidth: Per GB transferred                           │
│                                                              │
│ 3. REGION                                                     │
│    East US: $100/month                                       │
│    West Europe: $115/month (15% more expensive!)             │
│                                                              │
│ 4. BANDWIDTH (Data Transfer)                                 │
│    • Data IN to Azure: FREE ✓                               │
│    • Data OUT of Azure: $0.087/GB ❌                        │
│    • Within same region: FREE ✓                             │
│                                                              │
│ 5. RESERVED INSTANCES                                        │
│    Pay upfront = 40-70% discount!                            │
│    1-year or 3-year commitment                               │
│                                                              │
│ 6. AZURE HYBRID BENEFIT                                      │
│    Use existing Windows licenses                             │
│    Up to 80% savings on VMs!                                 │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### Pricing Examples

```
EXAMPLE 1: STANDARD VM (Pay-as-you-go)

┌──────────────────────────────────────────────────────────────┐
│ VM Size: Standard_D2s_v3                                     │
│ • 2 vCPUs                                                    │
│ • 8 GB RAM                                                   │
│ • Windows Server                                             │
│                                                              │
│ REGION COMPARISON:                                            │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ East US:        $0.096/hour = $70/month (730 hrs)     │   │
│ │ West US:        $0.096/hour = $70/month               │   │
│ │ West Europe:    $0.106/hour = $77/month (+10%)        │   │
│ │ Brazil South:   $0.134/hour = $98/month (+40%!)       │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ SAME VM, DIFFERENT PRICES! Choose region wisely! 💡          │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

```
EXAMPLE 2: STORAGE COSTS

┌──────────────────────────────────────────────────────────────┐
│ 1 TB (1,000 GB) of Data                                      │
│                                                              │
│ TIER COMPARISON (Per Month):                                 │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ HOT TIER:                                              │   │
│ │ Storage: $18.40/month                                  │   │
│ │ Good for: Frequent access                              │   │
│ │                                                        │   │
│ │ COOL TIER:                                             │   │
│ │ Storage: $10.00/month (46% cheaper!)                   │   │
│ │ Good for: Monthly access                               │   │
│ │                                                        │   │
│ │ ARCHIVE TIER:                                          │   │
│ │ Storage: $2.00/month (89% cheaper!) 💰                 │   │
│ │ Good for: Yearly access                                │   │
│ │ Note: Retrieval takes up to 15 hours                   │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ SMART MOVE: Use lifecycle management to auto-move data!      │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## Cost Management Tools

### 1. Pricing Calculator

**Estimate costs BEFORE deploying!**

┌─────────────────────────────────────────────────────────────────┐
│ 📖 SIMPLE TERMS                                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│ PRICING CALCULATOR:                                             │
│ "How much will my Azure solution cost per month?"              │
│                                                                 │
│ Use: BEFORE you deploy anything                                │
│                                                                 │
│ Link: azure.microsoft.com/pricing/calculator                   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘

```
HOW TO USE PRICING CALCULATOR:

┌──────────────────────────────────────────────────────────────┐
│ EXAMPLE: Estimate E-Commerce Website Costs                   │
│                                                              │
│ Step 1: Add products                                         │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ + Add Virtual Machines (2 VMs)                         │   │
│ │ + Add Azure SQL Database                               │   │
│ │ + Add Blob Storage (100 GB)                            │   │
│ │ + Add Load Balancer                                    │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ Step 2: Configure each                                       │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ VMs: Standard_D2s_v3, East US, Windows                 │   │
│ │ SQL Database: General Purpose, 100 GB                  │   │
│ │ Storage: Hot tier                                      │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ Step 3: Get estimate                                         │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ MONTHLY COST ESTIMATE:                                 │   │
│ │                                                        │   │
│ │ VMs (2x):           $140                               │   │
│ │ SQL Database:       $200                               │   │
│ │ Blob Storage:       $2                                 │   │
│ │ Load Balancer:      $18                                │   │
│ │ Bandwidth:          $10                                │   │
│ │ ────────────────────────                               │   │
│ │ TOTAL:              $370/month                         │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ Step 4: Optimize!                                            │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Try different options:                                 │   │
│ │ • Smaller VMs? → $280/month                            │   │
│ │ • Reserved Instances? → $220/month                     │   │
│ │ • Different region? → $350/month                       │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### 2. TCO Calculator

**Compare on-premises vs Azure costs!**

┌─────────────────────────────────────────────────────────────────┐
│ 📖 SIMPLE TERMS                                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│ TCO = Total Cost of Ownership                                  │
│                                                                 │
│ Question: "Should we move to Azure? Will we save money?"       │
│                                                                 │
│ Shows 3-5 year comparison of costs                             │
│                                                                 │
│ Link: azure.microsoft.com/pricing/tco                          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘

```
TCO CALCULATOR EXAMPLE:

┌──────────────────────────────────────────────────────────────┐
│ SCENARIO: Company with 50 Servers On-Premises                │
│                                                              │
│ ON-PREMISES COSTS (5 Years):                                  │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Server Hardware:           $500,000                    │   │
│ │ Storage Hardware:          $200,000                    │   │
│ │ Network Equipment:         $100,000                    │   │
│ │ Datacenter Space Rent:     $150,000                    │   │
│ │ Electricity:               $180,000                    │   │
│ │ Cooling:                   $120,000                    │   │
│ │ IT Staff (3 people):       $900,000                    │   │
│ │ Maintenance/Support:       $250,000                    │   │
│ │ ────────────────────────                               │   │
│ │ TOTAL (5 years):           $2,400,000                  │   │
│ │ Per year:                  $480,000                    │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ AZURE COSTS (5 Years):                                        │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ 50 VMs (Reserved):         $720,000                    │   │
│ │ Storage:                   $120,000                    │   │
│ │ Networking:                $60,000                     │   │
│ │ Reduced IT Staff (1):      $300,000                    │   │
│ │ ────────────────────────                               │   │
│ │ TOTAL (5 years):           $1,200,000                  │   │
│ │ Per year:                  $240,000                    │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ 💰 SAVINGS: $1,200,000 over 5 years (50% reduction!)         │
│                                                              │
│ PLUS BENEFITS:                                                │
│ • No hardware to maintain                                    │
│ • No datacenter to manage                                    │
│ • Easier to scale                                            │
│ • Better disaster recovery                                   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### 3. Cost Analysis

**Track actual spending!**

```
┌──────────────────────────────────────────────────────────────┐
│ COST ANALYSIS (After Deployment)                             │
│                                                              │
│ VIEW YOUR SPENDING:                                           │
│                                                              │
│ BY SERVICE:                                                   │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Virtual Machines:    $450/month  (60%)  ████████████   │   │
│ │ SQL Database:        $200/month  (27%)  █████          │   │
│ │ Storage:             $50/month   (7%)   ██             │   │
│ │ Networking:          $45/month   (6%)   █              │   │
│ │ ──────────────────────────────────────                │   │
│ │ TOTAL:               $745/month                        │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ BY TAG (Department):                                          │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Marketing:           $300/month                        │   │
│ │ Engineering:         $250/month                        │   │
│ │ Sales:               $150/month                        │   │
│ │ HR:                  $45/month                         │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ TRENDS:                                                       │
│ ┌────────────────────────────────────────────────────────┐   │
│ │  Cost                                                  │   │
│ │  $800│                                           ╱─    │   │
│ │      │                                      ╱────      │   │
│ │  $600│                             ╱────────           │   │
│ │      │                    ╱────────                    │   │
│ │  $400│           ╱────────                             │   │
│ │      │  ────────                                       │   │
│ │  $200│                                                 │   │
│ │      └────────────────────────────────────────         │   │
│ │      Jan  Feb  Mar  Apr  May  Jun                      │   │
│ │                                                        │   │
│ │ Spending increasing! Need optimization! ⚠️             │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### 4. Budgets

**Set spending limits and get alerts!**

```
┌──────────────────────────────────────────────────────────────┐
│ CREATE A BUDGET                                              │
│                                                              │
│ EXAMPLE: Monthly Budget of $1,000                            │
│                                                              │
│ ALERT THRESHOLDS:                                             │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Alert 1: 50% of budget ($500)                          │   │
│ │ → Email to team lead                                   │   │
│ │                                                        │   │
│ │ Alert 2: 80% of budget ($800)                          │   │
│ │ → Email to manager + team lead                         │   │
│ │ → Slack notification                                   │   │
│ │                                                        │   │
│ │ Alert 3: 100% of budget ($1,000)                       │   │
│ │ → Email to director                                    │   │
│ │ → Emergency meeting scheduled                          │   │
│ │ → Review all spending                                  │   │
│ │                                                        │   │
│ │ Alert 4: 120% of budget ($1,200)                       │   │
│ │ → Auto-shutdown non-critical resources (optional)      │   │
│ │ → Executive notification                               │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ CURRENT MONTH:                                                │
│ ┌────────────────────────────────────────────────────────┐   │
│ │  Day 20:  Spent $750                                   │   │
│ │  Progress: ███████████░░░░░  75%                       │   │
│ │  Budget:   $1,000                                      │   │
│ │  Status:   On track ✓                                  │   │
│ │  Forecast: Will finish at $937 (within budget!)        │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## Cost Optimization Strategies

### 1. Reserved Instances

**Commit and save 40-70%!**

```
┌──────────────────────────────────────────────────────────────┐
│ RESERVED INSTANCES SAVINGS                                   │
│                                                              │
│ EXAMPLE VM: Standard_D2s_v3 (2 vCPU, 8GB RAM)                │
│                                                              │
│ PAY-AS-YOU-GO (No Commitment):                               │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Cost: $70/month × 12 = $840/year                       │   │
│ │ Flexibility: Cancel anytime ✓                          │   │
│ │ Savings: None                                          │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ 1-YEAR RESERVED:                                             │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Cost: $42/month × 12 = $504/year                       │   │
│ │ Savings: $336/year (40% discount!) 💰                  │   │
│ │ Commitment: Must pay for full year                     │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ 3-YEAR RESERVED:                                             │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Cost: $25/month × 36 = $900 total                      │   │
│ │ Pay-as-you-go cost: $2,520 (36 months)                 │   │
│ │ Savings: $1,620 (64% discount!) 💰💰                   │   │
│ │ Commitment: Must pay for 3 years                       │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ WHEN TO USE:                                                  │
│ ✅ Production workloads running 24/7                        │
│ ✅ Predictable usage                                        │
│ ✅ Long-term projects                                       │
│                                                              │
│ WHEN NOT TO USE:                                              │
│ ❌ Dev/test environments (use pay-as-you-go)                │
│ ❌ Unpredictable workloads                                  │
│ ❌ Short-term projects (<1 year)                            │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### 2. Azure Hybrid Benefit

**Use existing licenses, save up to 80%!**

```
┌──────────────────────────────────────────────────────────────┐
│ AZURE HYBRID BENEFIT                                         │
│                                                              │
│ IF YOU HAVE: Windows Server licenses with Software          │
│ Assurance or SQL Server licenses                            │
│                                                              │
│ THEN: Bring them to Azure for HUGE savings!                  │
│                                                              │
│ EXAMPLE: Windows Server VM                                   │
│                                                              │
│ WITHOUT HYBRID BENEFIT:                                      │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Windows VM: $70/month                                  │   │
│ │ (Includes Windows license)                             │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ WITH HYBRID BENEFIT:                                         │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Base VM: $14/month                                     │   │
│ │ (Use your existing license!)                           │   │
│ │ Savings: $56/month = $672/year per VM! 💰              │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ 10 VMs with Hybrid Benefit = $6,720/year savings! 🎉         │
│                                                              │
│ COMBINED SAVINGS (Reserved + Hybrid Benefit):                │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Pay-as-you-go: $70/month                               │   │
│ │ 3-year Reserved: $25/month                             │   │
│ │ + Hybrid Benefit: $5/month                             │   │
│ │                                                        │   │
│ │ TOTAL SAVINGS: 93%! ($70 → $5) 💰💰💰                  │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### Top 20 Cost Optimization Tips

```
┌──────────────────────────────────────────────────────────────┐
│ TOP 20 WAYS TO REDUCE AZURE COSTS                            │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│ 1. ⭐ DELETE UNUSED RESOURCES                                │
│    Check for orphaned disks, old VMs, test environments      │
│    Impact: HIGH - Often 30-50% savings!                      │
│                                                              │
│ 2. ⭐ AUTO-SHUTDOWN DEV/TEST VMs                             │
│    Shutdown at 6 PM, restart at 8 AM                         │
│    Impact: HIGH - Save 50%+ on these VMs                     │
│                                                              │
│ 3. ⭐ RESERVED INSTANCES                                     │
│    1-year = 40%, 3-year = 60-70% savings                     │
│    Impact: VERY HIGH for production workloads                │
│                                                              │
│ 4. RIGHT-SIZE VMs                                            │
│    Using 4-core at 20% CPU? Downgrade to 2-core             │
│    Impact: MEDIUM - 30-50% per right-sized VM                │
│                                                              │
│ 5. USE SPOT VMs                                              │
│    Up to 90% discount for interruptible workloads            │
│    Impact: VERY HIGH for batch jobs                          │
│                                                              │
│ 6. STORAGE TIERS                                             │
│    Move old data: Hot → Cool → Archive                       │
│    Impact: HIGH - Up to 90% on archived data                 │
│                                                              │
│ 7. AZURE HYBRID BENEFIT                                      │
│    Use existing Windows/SQL licenses                         │
│    Impact: VERY HIGH - Up to 80% savings                     │
│                                                              │
│ 8. CHOOSE CHEAPER REGIONS                                    │
│    East US often cheaper than West Europe                    │
│    Impact: MEDIUM - 10-30% difference                        │
│                                                              │
│ 9. DELETE OLD SNAPSHOTS                                      │
│    Monthly cleanup of disk snapshots                         │
│    Impact: MEDIUM - Can add up quickly                       │
│                                                              │
│ 10. USE MANAGED DISKS                                        │
│     Avoid expensive unmanaged storage accounts               │
│     Impact: LOW-MEDIUM                                       │
│                                                              │
│ 11. REDUCE BANDWIDTH                                         │
│     Keep resources in same region                            │
│     Impact: MEDIUM for high-traffic apps                     │
│                                                              │
│ 12. DEV/TEST PRICING                                         │
│     Special discounts for non-production                     │
│     Impact: MEDIUM - Up to 50% off                           │
│                                                              │
│ 13. USE TAGS                                                 │
│     Track spending by project/department                     │
│     Impact: LOW (visibility, not savings)                    │
│                                                              │
│ 14. AZURE ADVISOR RECOMMENDATIONS                            │
│     Free tool finds waste automatically                      │
│     Impact: VARIES - Easy wins!                              │
│                                                              │
│ 15. SCALE DOWN DURING OFF-HOURS                              │
│     Reduce instances at night/weekends                       │
│     Impact: MEDIUM - 30% savings                             │
│                                                              │
│ 16. USE SMALLER DATABASES                                    │
│     Start small, scale up as needed                          │
│     Impact: MEDIUM                                           │
│                                                              │
│ 17. ENABLE COMPRESSION                                       │
│     Reduce storage and bandwidth usage                       │
│     Impact: LOW-MEDIUM                                       │
│                                                              │
│ 18. LIFECYCLE MANAGEMENT                                     │
│     Auto-move aging data to cheaper tiers                    │
│     Impact: HIGH for large data sets                         │
│                                                              │
│ 19. CONSOLIDATE RESOURCES                                    │
│     Run multiple apps on same VM if possible                 │
│     Impact: MEDIUM                                           │
│                                                              │
│ 20. SET BUDGETS & ALERTS                                     │
│     Prevent overspending before it happens                   │
│     Impact: HIGH (prevention)                                │
│                                                              │
└──────────────────────────────────────────────────────────────┘

PRIORITY ORDER (Do these first!):
1. Delete unused resources (biggest impact!)
2. Reserved Instances for production
3. Auto-shutdown dev/test VMs
4. Azure Hybrid Benefit if you have licenses
5. Right-size oversized VMs
```

---

### Real-World Cost Optimization Example

```
CASE STUDY: Tech Startup

┌──────────────────────────────────────────────────────────────┐
│ BEFORE OPTIMIZATION:                                         │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Monthly Cost: $5,000                                   │   │
│ │                                                        │   │
│ │ • 10 Production VMs (24/7):         $2,000             │   │
│ │ • 15 Dev/Test VMs (24/7):           $1,500             │   │
│ │ • 500 GB Hot Storage:               $90                │   │
│ │ • 5 TB Archive Data in Hot:         $900               │   │
│ │ • SQL Database (over-provisioned):  $400               │   │
│ │ • 2 Unused VMs (forgotten):         $110               │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ OPTIMIZATIONS APPLIED:                                        │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ 1. Reserved 10 Production VMs (3-year) → Save $800     │   │
│ │ 2. Auto-shutdown Dev VMs (14hrs/day) → Save $750       │   │
│ │ 3. Move archive to Archive tier → Save $810            │   │
│ │ 4. Right-size SQL Database → Save $200                 │   │
│ │ 5. Delete 2 unused VMs → Save $110                     │   │
│ │ 6. Applied Hybrid Benefit → Save $400                  │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ AFTER OPTIMIZATION:                                           │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Monthly Cost: $1,930                                   │   │
│ │                                                        │   │
│ │ Monthly Savings: $3,070 (61% reduction!) 💰            │   │
│ │ Annual Savings: $36,840                                │   │
│ │                                                        │   │
│ │ Time to implement: 4 hours                             │   │
│ │ ROI: Immediate                                         │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### 📝 Chapter Summary

✅ **Cost Factors**
- Resource type, usage, region, bandwidth
- Reserved Instances (40-70% savings)
- Azure Hybrid Benefit (up to 80% savings)

✅ **Planning Tools**
- Pricing Calculator: Estimate before deploying
- TCO Calculator: On-prem vs Azure comparison
- Shows 3-5 year costs

✅ **Monitoring Tools**
- Cost Analysis: Track actual spending
- Budgets: Set limits and alerts
- Azure Advisor: Find optimization opportunities

✅ **Top Savings Strategies**
1. Delete unused resources (biggest impact!)
2. Reserved Instances (40-70% off)
3. Auto-shutdown dev/test VMs (50% off those)
4. Right-size VMs
5. Azure Hybrid Benefit

✅ **Storage Optimization**
- Hot: $0.018/GB (frequent access)
- Cool: $0.010/GB (monthly access)
- Archive: $0.002/GB (yearly access - 89% cheaper!)

---

### 🎯 Practice Questions

**Question 1:**
Which tool estimates costs BEFORE deploying?

A) Cost Analysis  
B) Pricing Calculator  
C) Budgets  
D) Azure Advisor

**Question 2:**
Reserved Instances (3-year) save approximately:

A) 20%  
B) 40%  
C) 60-70%  
D) 90%

**Question 3:**
Data transfer OUT of Azure costs money, but what's FREE?

A) Data OUT  
B) Data IN  
C) Both  
D) Neither

**Question 4:**
Archive storage tier costs how much per GB/month?

A) $0.018  
B) $0.010  
C) $0.002  
D) $0.001

**Question 5:**
What compares on-premises vs Azure costs over 3-5 years?

A) Pricing Calculator  
B) TCO Calculator  
C) Cost Analysis  
D) Budgets

---

### ✍️ Practice Answers

**Question 1: B** - Pricing Calculator

*Explanation:* Pricing Calculator is for BEFORE deployment (estimating). Cost Analysis is AFTER (tracking actual spending). Know the difference!

**Question 2: C** - 60-70%

*Explanation:* 1-year Reserved = ~40% savings, 3-year Reserved = 60-70% savings. This is heavily tested! Remember: longer commitment = bigger discount.

**Question 3: B** - Data IN

*Explanation:* Data coming INTO Azure is FREE. Data going OUT (egress) costs $0.087/GB. Data within same region is also FREE.

**Question 4: C** - $0.002

*Explanation:* Know these prices! Hot = $0.018, Cool = $0.010, Archive = $0.002. Archive is 89% cheaper than Hot but has 15-hour retrieval time.

**Question 5: B** - TCO Calculator

*Explanation:* TCO (Total Cost of Ownership) Calculator compares on-prem vs cloud over multiple years. Pricing Calculator is just for Azure estimates.

---

### 🔖 Quick Reference Card

```
┌──────────────────────────────────────────────────────────────┐
│ COST MANAGEMENT CHEAT SHEET                                  │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│ BEFORE DEPLOYMENT:                                            │
│ • Pricing Calculator: Estimate Azure costs                  │
│ • TCO Calculator: On-prem vs Azure (3-5 years)              │
│                                                              │
│ AFTER DEPLOYMENT:                                             │
│ • Cost Analysis: Track actual spending                      │
│ • Budgets: Set limits, get alerts                           │
│ • Azure Advisor: Find savings opportunities                  │
│                                                              │
│ BIG SAVINGS:                                                  │
│ • Reserved (1yr): 40% off                                   │
│ • Reserved (3yr): 60-70% off                                │
│ • Hybrid Benefit: Up to 80% off                             │
│ • Spot VMs: Up to 90% off                                   │
│                                                              │
│ STORAGE TIERS:                                                │
│ • Hot: $0.018/GB (frequent)                                 │
│ • Cool: $0.010/GB (monthly)                                 │
│ • Archive: $0.002/GB (yearly)                               │
│                                                              │
│ BANDWIDTH:                                                    │
│ • Data IN: FREE ✓                                           │
│ • Data OUT: $0.087/GB                                       │
│ • Same region: FREE ✓                                       │
│                                                              │
│ TOP 3 TIPS:                                                   │
│ 1. Delete unused resources                                  │
│ 2. Use Reserved Instances                                   │
│ 3. Auto-shutdown dev/test VMs                               │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

**End of Chapter 11** ✓  
**Final chapter complete!** 🎉
-e 

---


