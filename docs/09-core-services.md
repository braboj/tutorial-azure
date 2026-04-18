## Chapter 9: Core Azure Services

---

### 📚 What You'll Learn in This Chapter

By the end of this chapter, you'll understand:

- ✓ **Compute Services:** VMs, App Service, Functions, Containers
- ✓ **Storage Services:** Blob, File, Queue, Disk
- ✓ **Database Services:** SQL Database, Cosmos DB, MySQL, PostgreSQL
- ✓ **Networking Services:** VNet, Load Balancer, VPN Gateway
- ✓ When to use each service
- ✓ Pricing and decision frameworks

**Time needed:** 30-35 minutes  
**Difficulty:** Moderate-Advanced 🟡🔴  

**⚠️ CRITICAL:** This is the MOST TESTED chapter on AZ-900! Know these services well!

---

## PART 1: COMPUTE SERVICES

### What is Compute?

┌─────────────────────────────────────────────────────────────────┐
│ 📖 SIMPLE TERMS                                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│ COMPUTE:                                                        │
│ Processing power to run your applications                       │
│                                                                 │
│ Think: The "brain" that executes your code                      │
│                                                                 │
│ Like: CPU in your computer, but in the cloud                    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘

---

### The Four Main Compute Services

```
┌──────────────────────────────────────────────────────────────┐
│ COMPUTE SERVICE COMPARISON                                   │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│ 1. VIRTUAL MACHINES (IaaS)                                   │
│    Full control, manage everything                           │
│    Like: Renting an entire computer                          │
│                                                              │
│ 2. APP SERVICE (PaaS)                                        │
│    Just deploy your code, Azure handles rest                 │
│    Like: Deploying to a managed platform                     │
│                                                              │
│ 3. AZURE FUNCTIONS (Serverless)                              │
│    Code runs only when triggered                             │
│    Like: Pay-per-execution                                   │
│                                                              │
│ 4. CONTAINERS (AKS)                                           │
│    Package app with all dependencies                         │
│    Like: Shipping container for code                         │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

Let's explore each one!

---

## 1. Virtual Machines (VMs)

### What is a Virtual Machine?

**A computer inside a computer!**

```
┌──────────────────────────────────────────────────────────────┐
│ VIRTUAL MACHINE = SOFTWARE COMPUTER                          │
│                                                              │
│ PHYSICAL SERVER (Microsoft's Hardware):                      │
│ ┌────────────────────────────────────────────────────────┐   │
│ │  Hypervisor (Virtualization Software)                  │   │
│ │                                                        │   │
│ │  ┌──────────┐  ┌──────────┐  ┌──────────┐            │   │
│ │  │ VM 1     │  │ VM 2     │  │ VM 3     │            │   │
│ │  │ Windows  │  │ Linux    │  │ Ubuntu   │            │   │
│ │  │ 4 CPU    │  │ 2 CPU    │  │ 8 CPU    │            │   │
│ │  │ 16GB RAM │  │ 8GB RAM  │  │ 32GB RAM │            │   │
│ │  │          │  │          │  │          │            │   │
│ │  │ Your App │  │ Database │  │ Web Srv  │            │   │
│ │  └──────────┘  └──────────┘  └──────────┘            │   │
│ │                                                        │   │
│ │  Each VM thinks it's a real computer!                  │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### When to Use VMs

```
✅ PERFECT FOR:

┌──────────────────────────────────────────────────────────────┐
│ 1. FULL CONTROL NEEDED                                       │
│    Example: Custom software requiring specific OS version    │
│    → Use VMs (can configure exactly as needed)               │
│                                                              │
│ 2. LIFT-AND-SHIFT MIGRATION                                  │
│    Example: Move existing on-premises app to cloud           │
│    → Use VMs (same environment, just in Azure)               │
│                                                              │
│ 3. RUNNING LEGACY APPLICATIONS                               │
│    Example: Old application that requires Windows Server     │
│    2012                                                      │
│    → Use VMs (install exact OS version needed)               │
│                                                              │
│ 4. TESTING/DEVELOPMENT                                       │
│    Example: Need 10 different OS versions for testing        │
│    → Use VMs (create any configuration quickly)              │
│                                                              │
└──────────────────────────────────────────────────────────────┘

❌ NOT IDEAL FOR:

┌──────────────────────────────────────────────────────────────┐
│ • Simple websites (use App Service instead)                  │
│ • Modern cloud-native apps (use containers instead)          │
│ • Event-driven tasks (use Functions instead)                 │
│ • If you don't want to manage OS updates                     │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### VM Pricing Example

```
EXAMPLE: Running a Web Server

┌──────────────────────────────────────────────────────────────┐
│ VM SIZE: Standard_B2s                                        │
│ • 2 vCPUs                                                    │
│ • 4 GB RAM                                                   │
│ • Windows Server 2022                                        │
│                                                              │
│ COST BREAKDOWN:                                               │
│ • VM compute: $0.10/hour                                     │
│ • Storage (128GB SSD): $10/month                             │
│ • Bandwidth (100GB out): $8/month                            │
│                                                              │
│ MONTHLY TOTAL (24/7):                                         │
│ ($0.10 × 730 hours) + $10 + $8 = $91/month                   │
│                                                              │
│ SAVINGS TIP:                                                  │
│ Reserve for 3 years = $30/month (67% savings!) 💰            │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## 2. Azure App Service

### What is App Service?

**Platform for hosting websites and APIs without managing servers!**

┌─────────────────────────────────────────────────────────────────┐
│ 📖 SIMPLE TERMS                                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│ APP SERVICE:                                                    │
│ Upload your code, Azure runs it                                │
│                                                                 │
│ You DON'T manage:                                               │
│ • Operating system                                              │
│ • Web server software                                           │
│ • Security patches                                              │
│ • Hardware                                                      │
│                                                                 │
│ You ONLY manage:                                                │
│ • Your application code                                         │
│ • Application settings                                          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘

---

### App Service vs VM

```
┌──────────────────────────────────────────────────────────────┐
│ HOSTING A WEBSITE - TWO APPROACHES                           │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│ USING VIRTUAL MACHINE (Hard Way):                            │
│                                                              │
│ Step 1: Create VM                                            │
│ Step 2: Install Windows/Linux                                │
│ Step 3: Install web server (IIS/Apache/Nginx)                │
│ Step 4: Configure firewall rules                             │
│ Step 5: Configure SSL certificates                           │
│ Step 6: Upload your website code                             │
│ Step 7: Monitor and maintain everything                      │
│ Step 8: Apply security patches monthly                       │
│ Step 9: Scale manually when traffic increases                │
│                                                              │
│ Time: Hours to set up, ongoing management                    │
│ Your responsibility: Everything ❌                           │
│                                                              │
│ ─────────────────────────────────────────────────────────────│
│                                                              │
│ USING APP SERVICE (Easy Way):                                │
│                                                              │
│ Step 1: Create App Service                                   │
│ Step 2: Upload your website code                             │
│ Step 3: Done! ✓                                              │
│                                                              │
│ Azure automatically:                                          │
│ • Configures web server                                     │
│ • Handles SSL certificates                                  │
│ • Applies security patches                                  │
│ • Scales when needed                                        │
│ • Monitors performance                                      │
│                                                              │
│ Time: 5 minutes to deploy ⚡                                 │
│ Your responsibility: Just your code! ✓                       │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### App Service Features

```
KEY FEATURES:

┌──────────────────────────────────────────────────────────────┐
│ 1. AUTO-SCALING                                              │
│    ┌──────────────────────────────────────────────────────┐ │
│    │ Set rule: "If CPU > 70%, add instance"              │ │
│    │ Traffic spike → Azure adds servers automatically     │ │
│    │ Traffic drops → Azure removes servers automatically  │ │
│    │ You pay only for what you use!                       │ │
│    └──────────────────────────────────────────────────────┘ │
│                                                              │
│ 2. DEPLOYMENT SLOTS                                          │
│    ┌──────────────────────────────────────────────────────┐ │
│    │ Production Slot: Current website (users see this)    │ │
│    │ Staging Slot: New version (for testing)             │ │
│    │                                                      │ │
│    │ Test in staging → Swap to production (instant!)      │ │
│    │ Zero downtime deployment! ✓                          │ │
│    └──────────────────────────────────────────────────────┘ │
│                                                              │
│ 3. CONTINUOUS DEPLOYMENT                                     │
│    ┌──────────────────────────────────────────────────────┐ │
│    │ Connect to GitHub                                    │ │
│    │ Push code → Automatically deployed!                  │ │
│    │ Modern DevOps workflow built-in                      │ │
│    └──────────────────────────────────────────────────────┘ │
│                                                              │
│ 4. MULTIPLE LANGUAGES                                        │
│    ┌──────────────────────────────────────────────────────┐ │
│    │ Supported: .NET, Java, PHP, Python, Node.js, Ruby   │ │
│    │ Use your favorite language!                          │ │
│    └──────────────────────────────────────────────────────┘ │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## 3. Azure Functions (Serverless)

### What are Azure Functions?

**Code that runs ONLY when needed - pay per execution!**

```
┌──────────────────────────────────────────────────────────────┐
│ SERVERLESS COMPUTING                                         │
│                                                              │
│ TRADITIONAL (Always Running):                                 │
│                                                              │
│ ┌──────────┐                                                 │
│ │ Server   │ ← Running 24/7                                  │
│ │ Waiting  │ ← Costs $100/month                              │
│ │ for      │ ← Even when doing nothing!                      │
│ │ requests │ ← Waste of money! 💸                            │
│ └──────────┘                                                 │
│      ↑                                                       │
│ Request comes every hour                                     │
│ (Server idle 59 minutes/hour = 98% waste!)                   │
│                                                              │
│ ─────────────────────────────────────────────────────────────│
│                                                              │
│ SERVERLESS (Pay Per Execution):                              │
│                                                              │
│ [Nothing running]                                             │
│      ↓                                                       │
│ Request arrives!                                             │
│      ↓                                                       │
│ ┌──────────┐                                                 │
│ │ Function │ ← Azure starts function instantly               │
│ │ Runs!    │ ← Processes request                             │
│ └──────────┘ ← Finishes in 200ms                             │
│      ↓                                                       │
│ [Shuts down]                                                 │
│      ↓                                                       │
│ You pay: $0.0001                                             │
│ (Only for 200ms of execution!)                               │
│                                                              │
│ Monthly cost: ~$3 (vs $100 traditional) 💰                   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### Azure Functions Triggers

**What makes a function run?**

```
COMMON TRIGGERS:

┌──────────────────────────────────────────────────────────────┐
│ 1. HTTP TRIGGER                                              │
│    URL called → Function runs                                │
│    Example: API endpoint                                     │
│    https://myfunction.azurewebsites.net/api/process          │
│                                                              │
│ 2. TIMER TRIGGER                                             │
│    Schedule → Function runs                                  │
│    Example: Every day at 2 AM, clean up old files            │
│                                                              │
│ 3. BLOB TRIGGER                                              │
│    File uploaded → Function runs                             │
│    Example: Image uploaded → Auto-resize                     │
│                                                              │
│ 4. QUEUE TRIGGER                                             │
│    Message in queue → Function runs                          │
│    Example: Order placed → Process payment                   │
│                                                              │
│ 5. EVENT GRID TRIGGER                                        │
│    Event happens → Function runs                             │
│    Example: VM created → Send notification                   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### Real-World Function Example

```
SCENARIO: Image Processing Service

┌──────────────────────────────────────────────────────────────┐
│ USER UPLOADS PHOTO TO WEBSITE                                │
│          ↓                                                   │
│ Photo saved to Blob Storage                                  │
│          ↓                                                   │
│ Blob Trigger fires → Function starts!                        │
│          ↓                                                   │
│ Function reads photo                                         │
│          ↓                                                   │
│ Creates 3 versions:                                          │
│ • Thumbnail (100x100)                                        │
│ • Medium (500x500)                                           │
│ • Large (1920x1080)                                          │
│          ↓                                                   │
│ Saves all versions back to Blob Storage                      │
│          ↓                                                   │
│ Function completes (took 800ms)                              │
│          ↓                                                   │
│ Function shuts down                                          │
│                                                              │
│ COST: $0.0008 per image processed                            │
│                                                              │
│ If 10,000 images/month:                                      │
│ Cost = $8/month                                              │
│                                                              │
│ Traditional server: $100/month                               │
│ Savings: $92/month! 💰                                       │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## 4. Azure Kubernetes Service (AKS)

### What are Containers?

**Package your app with everything it needs!**

```
┌──────────────────────────────────────────────────────────────┐
│ THE CONTAINER CONCEPT                                        │
│                                                              │
│ PROBLEM WITH VMs:                                             │
│                                                              │
│ Developer: "Works on my machine!" 🤷                         │
│ Production: "Doesn't work here!" ❌                          │
│                                                              │
│ Why? Different OS versions, libraries, configurations        │
│                                                              │
│ ─────────────────────────────────────────────────────────────│
│                                                              │
│ SOLUTION - CONTAINERS:                                        │
│                                                              │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ CONTAINER = App + Dependencies                         │   │
│ │                                                        │   │
│ │ ┌──────────────────────────────────────────────────┐   │   │
│ │ │ Your Application                                 │   │   │
│ │ ├──────────────────────────────────────────────────┤   │   │
│ │ │ Libraries & Dependencies                         │   │   │
│ │ ├──────────────────────────────────────────────────┤   │   │
│ │ │ Configuration Files                              │   │   │
│ │ └──────────────────────────────────────────────────┘   │   │
│ │                                                        │   │
│ │ Everything needed to run! ✓                            │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ Deploy ANYWHERE:                                              │
│ • Developer laptop ✓                                         │
│ • Test server ✓                                              │
│ • Production ✓                                               │
│ • Cloud ✓                                                    │
│                                                              │
│ Runs identically everywhere! 🎉                              │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### When to Use Containers (AKS)

```
✅ PERFECT FOR:

┌──────────────────────────────────────────────────────────────┐
│ 1. MICROSERVICES ARCHITECTURE                                │
│    ┌──────────────────────────────────────────────────────┐ │
│    │ E-Commerce App:                                      │ │
│    │ • Container 1: User Service                          │ │
│    │ • Container 2: Product Catalog                       │ │
│    │ • Container 3: Shopping Cart                         │ │
│    │ • Container 4: Payment Processing                    │ │
│    │ • Container 5: Order Management                      │ │
│    │                                                      │ │
│    │ Each scales independently! ✓                         │ │
│    └──────────────────────────────────────────────────────┘ │
│                                                              │
│ 2. PORTABLE APPLICATIONS                                     │
│    Develop locally → Test in staging → Deploy to Azure       │
│    Same container, runs identically everywhere               │
│                                                              │
│ 3. MODERN CLOUD-NATIVE APPS                                  │
│    Built for cloud from day one                              │
│    Easy to scale, update, and maintain                       │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## COMPUTE DECISION TREE

**Which compute service should you use?**

```
┌──────────────────────────────────────────────────────────────┐
│ START: What type of application?                             │
│                                                              │
│ Need full OS control?                                        │
│ └─YES→ VIRTUAL MACHINES ✓                                   │
│ └─NO                                                         │
│    ↓                                                         │
│ Is it a web app/API?                                         │
│ └─YES→ APP SERVICE ✓                                        │
│ └─NO                                                         │
│    ↓                                                         │
│ Does it run only when triggered?                             │
│ └─YES→ AZURE FUNCTIONS ✓                                    │
│ └─NO                                                         │
│    ↓                                                         │
│ Need microservices / containers?                             │
│ └─YES→ AKS (Azure Kubernetes Service) ✓                     │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## PART 2: STORAGE SERVICES

### The Four Storage Types

```
┌──────────────────────────────────────────────────────────────┐
│ AZURE STORAGE SERVICES                                       │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│ 1. BLOB STORAGE                                              │
│    Files, images, videos, backups                            │
│    Like: Dropbox or Google Drive                             │
│                                                              │
│ 2. FILE STORAGE                                              │
│    Network file shares (SMB protocol)                        │
│    Like: Network drive at your office                        │
│                                                              │
│ 3. QUEUE STORAGE                                             │
│    Messages between applications                             │
│    Like: Post office for apps                                │
│                                                              │
│ 4. DISK STORAGE                                              │
│    Hard drives for VMs                                       │
│    Like: SSD/HDD in your computer                            │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## 1. Blob Storage

### What is Blob Storage?

┌─────────────────────────────────────────────────────────────────┐
│ 📖 SIMPLE TERMS                                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│ BLOB = Binary Large Object (fancy name for "file")             │
│                                                                 │
│ BLOB STORAGE:                                                   │
│ Unlimited storage for any type of file                         │
│                                                                 │
│ Store: Documents, images, videos, backups, logs, anything!     │
│                                                                 │
│ Access: Via HTTP/HTTPS from anywhere                           │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘

---

### Blob Storage Tiers

**Different prices for different access patterns!**

```
┌──────────────────────────────────────────────────────────────┐
│ STORAGE TIERS                                                │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│ HOT TIER (Frequent Access):                                   │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Use for: Files accessed often (daily/weekly)          │   │
│ │ Example: Website images, active documents              │   │
│ │ Cost: Higher storage, lower access                     │   │
│ │ Price: $0.018/GB/month                                 │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ COOL TIER (Infrequent Access):                               │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Use for: Files accessed rarely (monthly)              │   │
│ │ Example: Old projects, backups                         │   │
│ │ Cost: Lower storage, higher access                     │   │
│ │ Price: $0.010/GB/month                                 │   │
│ │ Min storage: 30 days                                   │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ ARCHIVE TIER (Rarely Access):                                │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ Use for: Long-term storage (yearly/never)             │   │
│ │ Example: Compliance archives, old backups              │   │
│ │ Cost: Cheapest storage, expensive access               │   │
│ │ Price: $0.002/GB/month (90% cheaper!)                  │   │
│ │ Min storage: 180 days                                  │   │
│ │ Retrieval time: Up to 15 hours                         │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### Blob Storage Example

```
SCENARIO: Photo Sharing App

┌──────────────────────────────────────────────────────────────┐
│ SMART STORAGE STRATEGY:                                      │
│                                                              │
│ RECENT PHOTOS (Last 30 days):                                │
│ • Tier: HOT                                                  │
│ • Why: Users view frequently                                 │
│ • 10,000 photos × 2MB = 20GB                                 │
│ • Cost: 20GB × $0.018 = $0.36/month                          │
│                                                              │
│ OLD PHOTOS (30-180 days):                                    │
│ • Tier: COOL                                                 │
│ • Why: Occasionally viewed                                   │
│ • 50,000 photos × 2MB = 100GB                                │
│ • Cost: 100GB × $0.010 = $1.00/month                         │
│                                                              │
│ ARCHIVE (180+ days):                                         │
│ • Tier: ARCHIVE                                              │
│ • Why: Rarely accessed (compliance)                          │
│ • 200,000 photos × 2MB = 400GB                               │
│ • Cost: 400GB × $0.002 = $0.80/month                         │
│                                                              │
│ TOTAL STORAGE COST: $2.16/month                              │
│                                                              │
│ If all in HOT tier: $9.36/month                              │
│ Savings: $7.20/month (77% reduction!) 💰                     │
│                                                              │
│ Use lifecycle management to auto-move files! ✓               │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## 2. File Storage

### What is File Storage?

**Network file share in the cloud!**

```
┌──────────────────────────────────────────────────────────────┐
│ AZURE FILE STORAGE = Cloud Network Drive                     │
│                                                              │
│ TRADITIONAL FILE SERVER:                                      │
│                                                              │
│ Office Network:                                              │
│ \\fileserver\shared\documents\                               │
│      ↑                                                       │
│ Accessed by: Windows PCs, Mac, Linux                         │
│ Everyone sees same files                                     │
│                                                              │
│ ─────────────────────────────────────────────────────────────│
│                                                              │
│ AZURE FILE STORAGE:                                           │
│                                                              │
│ \\mystorageaccount.file.core.windows.net\myshare\            │
│      ↑                                                       │
│ Accessed by: Windows, Mac, Linux, Azure VMs                  │
│ Same experience, but in cloud!                               │
│                                                              │
│ BENEFITS:                                                     │
│ • No server to maintain                                     │
│ • Automatic backups                                         │
│ • Access from anywhere                                      │
│ • Unlimited capacity                                        │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## 3. Queue Storage

### What is Queue Storage?

**Message passing between applications!**

```
┌──────────────────────────────────────────────────────────────┐
│ HOW QUEUE STORAGE WORKS                                      │
│                                                              │
│ SCENARIO: E-Commerce Order Processing                        │
│                                                              │
│ Step 1: Customer places order on website                     │
│         ↓                                                    │
│ Step 2: Website puts message in queue                        │
│         "Order #12345: iPhone, $999"                         │
│         ┌────────────────────────────────────────────────┐   │
│         │ QUEUE                                          │   │
│         │ [Msg1] [Msg2] [Msg3] [Msg4] [Msg5]            │   │
│         └────────────────────────────────────────────────┘   │
│         ↓                                                    │
│ Step 3: Background worker picks up message                   │
│         • Verify payment                                     │
│         • Update inventory                                   │
│         • Send confirmation email                            │
│         • Delete message from queue                          │
│                                                              │
│ WHY USE QUEUES?                                               │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ WITHOUT QUEUE (Direct):                                │   │
│ │ Website → Process order → SLOW! (5 seconds)            │   │
│ │ Customer waits... 🕐                                   │   │
│ │                                                        │   │
│ │ WITH QUEUE:                                            │   │
│ │ Website → Put in queue → Done! (100ms)                │   │
│ │ Customer happy! ✓                                      │   │
│ │ Processing happens in background                       │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ BENEFITS:                                                     │
│ • Decouples components                                      │
│ • Handles traffic spikes                                    │
│ • Reliable message delivery                                 │
│ • Async processing                                          │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## 4. Disk Storage

### What is Disk Storage?

**Virtual hard drives for VMs!**

```
┌──────────────────────────────────────────────────────────────┐
│ DISK TYPES                                                   │
│                                                              │
│ PREMIUM SSD (Fastest, Most Expensive):                       │
│ • Speed: Up to 20,000 IOPS                                   │
│ • Use for: Databases, production VMs                         │
│ • Price: $0.12/GB/month                                      │
│                                                              │
│ STANDARD SSD (Medium Speed, Medium Price):                   │
│ • Speed: Up to 6,000 IOPS                                    │
│ • Use for: Web servers, dev/test                             │
│ • Price: $0.06/GB/month                                      │
│                                                              │
│ STANDARD HDD (Slowest, Cheapest):                            │
│ • Speed: Up to 500 IOPS                                      │
│ • Use for: Backups, archives                                 │
│ • Price: $0.04/GB/month                                      │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## Storage Redundancy Options

**KEY EXAM TOPIC!**

```
┌──────────────────────────────────────────────────────────────┐
│ LRS - Locally Redundant Storage                              │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ 3 copies in SAME datacenter                            │   │
│ │ ┌─────┐  ┌─────┐  ┌─────┐                             │   │
│ │ │Copy1│  │Copy2│  │Copy3│                             │   │
│ │ └─────┘  └─────┘  └─────┘                             │   │
│ │ Protects: Hardware failure ✓                           │   │
│ │ Doesn't protect: Datacenter disaster ❌                │   │
│ │ Durability: 11 nines (99.999999999%)                   │   │
│ │ Cost: $0.018/GB (cheapest)                             │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ ZRS - Zone Redundant Storage                                 │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ 3 copies across 3 AVAILABILITY ZONES                   │   │
│ │  Zone 1    Zone 2    Zone 3                            │   │
│ │ ┌─────┐  ┌─────┐  ┌─────┐                             │   │
│ │ │Copy1│  │Copy2│  │Copy3│                             │   │
│ │ └─────┘  └─────┘  └─────┘                             │   │
│ │ Protects: Zone failure ✓                               │   │
│ │ Doesn't protect: Region disaster ❌                    │   │
│ │ Durability: 12 nines (99.9999999999%)                  │   │
│ │ Cost: $0.025/GB                                        │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ GRS - Geo-Redundant Storage                                  │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ LRS in PRIMARY + LRS in SECONDARY region               │   │
│ │                                                        │   │
│ │ East US (Primary)      West US (Secondary)             │   │
│ │ ┌─────────────┐       ┌─────────────┐                 │   │
│ │ │ 3 copies    │═════► │ 3 copies    │                 │   │
│ │ └─────────────┘ Async └─────────────┘                 │   │
│ │ (Read/Write)          (Read only)                      │   │
│ │                                                        │   │
│ │ Protects: Regional disaster ✓                          │   │
│ │ Durability: 16 nines (99.99999999999999%)              │   │
│ │ Cost: $0.036/GB (2x LRS)                               │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ GZRS - Geo-Zone-Redundant Storage (Best!)                    │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ ZRS in primary + LRS in secondary                      │   │
│ │ Ultimate protection                                    │   │
│ │ Cost: $0.05/GB (most expensive)                        │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
└──────────────────────────────────────────────────────────────┘

**REMEMBER:** More protection = Higher cost!
```

---

## PART 3: DATABASE SERVICES

### The Main Database Services

```
┌──────────────────────────────────────────────────────────────┐
│ 1. AZURE SQL DATABASE (Relational, PaaS)                     │
│    Managed SQL Server                                        │
│    Use for: Traditional business apps                        │
│                                                              │
│ 2. COSMOS DB (NoSQL, Globally Distributed)                   │
│    Multi-model, ultra-fast                                   │
│    Use for: Web, mobile, gaming, IoT                         │
│                                                              │
│ 3. AZURE DATABASE FOR MySQL                                  │
│    Managed MySQL                                             │
│    Use for: Open-source workloads                            │
│                                                              │
│ 4. AZURE DATABASE FOR POSTGRESQL                             │
│    Managed PostgreSQL                                        │
│    Use for: Open-source workloads                            │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## 1. Azure SQL Database

### What is Azure SQL Database?

**Managed SQL Server - Microsoft handles everything!**

```
┌──────────────────────────────────────────────────────────────┐
│ SQL DATABASE (PaaS) vs SQL ON VM (IaaS)                      │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│ AZURE SQL DATABASE (Easy):                                   │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ MICROSOFT MANAGES:                                     │   │
│ │ • Hardware ✓                                           │   │
│ │ • Operating System ✓                                   │   │
│ │ • SQL Server software ✓                                │   │
│ │ • Patches & updates ✓                                  │   │
│ │ • Backups (automatic) ✓                                │   │
│ │ • High availability ✓                                  │   │
│ │ • Replication ✓                                        │   │
│ └────────────────────────────────────────────────────────┘   │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ YOU MANAGE:                                            │   │
│ │ • Database schema                                      │   │
│ │ • SQL queries                                          │   │
│ │ • Data                                                 │   │
│ │ • Access control                                       │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ SLA: 99.99% uptime                                           │
│ Backups: Automatic (retain 7-35 days)                        │
│ Scaling: Click a button (no downtime!)                       │
│                                                              │
│ ─────────────────────────────────────────────────────────────│
│                                                              │
│ SQL ON VM (Hard):                                            │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ YOU MANAGE:                                            │   │
│ │ • Everything except hardware! ❌                       │   │
│ │ • Install SQL Server                                   │   │
│ │ • Apply patches monthly                                │   │
│ │ • Configure backups                                    │   │
│ │ • Set up high availability                             │   │
│ │ • Monitor performance                                  │   │
│ │ • Handle failures                                      │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
│ More work, but more control                                  │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## 2. Cosmos DB

### What is Cosmos DB?

**Globally distributed, super-fast NoSQL database!**

┌─────────────────────────────────────────────────────────────────┐
│ 📖 SIMPLE TERMS                                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│ COSMOS DB:                                                      │
│ Database that exists in multiple regions simultaneously        │
│                                                                 │
│ Key Features:                                                   │
│ • <10ms latency (guaranteed!)                                   │
│ • 99.999% availability (5 nines!)                               │
│ • Global distribution                                           │
│ • Automatic scaling                                             │
│                                                                 │
│ Think: Ultra-fast database that's everywhere                    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘

---

### Cosmos DB Global Distribution

```
┌──────────────────────────────────────────────────────────────┐
│ COSMOS DB WORLDWIDE                                          │
│                                                              │
│  West US               West Europe           Southeast Asia  │
│ ┌─────────┐          ┌─────────┐           ┌─────────┐      │
│ │Cosmos DB│◄────────►│Cosmos DB│◄─────────►│Cosmos DB│      │
│ │ Replica │   Sync   │ Replica │   Sync    │ Replica │      │
│ └─────────┘          └─────────┘           └─────────┘      │
│      ↑                    ↑                      ↑           │
│   US Users          European Users          Asian Users      │
│   (5ms latency)     (8ms latency)          (6ms latency)     │
│                                                              │
│ DATA IS EVERYWHERE = FAST FOR EVERYONE! ⚡                    │
│                                                              │
│ If West US fails → Users automatically routed to             │
│ West Europe (no downtime!) ✓                                 │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### When to Use Each Database

```
DECISION TREE:

┌──────────────────────────────────────────────────────────────┐
│ Need global, multi-region with <10ms latency?                │
│ └─YES→ COSMOS DB ✓                                          │
│ └─NO                                                         │
│    ↓                                                         │
│ Using Microsoft SQL Server skills/tools?                     │
│ └─YES→ AZURE SQL DATABASE ✓                                 │
│ └─NO                                                         │
│    ↓                                                         │
│ Need open-source MySQL?                                      │
│ └─YES→ AZURE DATABASE FOR MYSQL ✓                           │
│ └─NO                                                         │
│    ↓                                                         │
│ Need open-source PostgreSQL?                                 │
│ └─YES→ AZURE DATABASE FOR POSTGRESQL ✓                      │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## PART 4: NETWORKING SERVICES

### Core Networking Services

```
┌──────────────────────────────────────────────────────────────┐
│ 1. VIRTUAL NETWORK (VNet)                                    │
│    Private network in Azure                                  │
│    Like: Your own network in the cloud                       │
│                                                              │
│ 2. LOAD BALANCER                                             │
│    Distributes traffic across VMs                            │
│    Like: Traffic cop directing cars                          │
│                                                              │
│ 3. VPN GATEWAY                                               │
│    Secure connection to on-premises                          │
│    Like: Encrypted tunnel between networks                   │
│                                                              │
│ 4. APPLICATION GATEWAY                                       │
│    Web traffic load balancer                                 │
│    Like: Smart load balancer for websites                    │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## 1. Virtual Network (VNet)

### What is a VNet?

**Your private network in Azure!**

```
┌──────────────────────────────────────────────────────────────┐
│ AZURE VIRTUAL NETWORK                                        │
│                                                              │
│ ┌────────────────────────────────────────────────────────┐   │
│ │ VNet: MyCompanyNetwork (10.0.0.0/16)                   │   │
│ │                                                        │   │
│ │  SUBNET 1: Web Tier (10.0.1.0/24)                      │   │
│ │  ┌──────────┐  ┌──────────┐  ┌──────────┐            │   │
│ │  │ Web VM 1 │  │ Web VM 2 │  │ Web VM 3 │            │   │
│ │  │10.0.1.4  │  │10.0.1.5  │  │10.0.1.6  │            │   │
│ │  └──────────┘  └──────────┘  └──────────┘            │   │
│ │         ↓             ↓             ↓                 │   │
│ │  SUBNET 2: App Tier (10.0.2.0/24)                      │   │
│ │  ┌──────────┐  ┌──────────┐                           │   │
│ │  │ App VM 1 │  │ App VM 2 │                           │   │
│ │  │10.0.2.4  │  │10.0.2.5  │                           │   │
│ │  └──────────┘  └──────────┘                           │   │
│ │         ↓             ↓                                │   │
│ │  SUBNET 3: Database Tier (10.0.3.0/24)                 │   │
│ │  ┌──────────┐                                          │   │
│ │  │ SQL DB   │                                          │   │
│ │  │10.0.3.4  │                                          │   │
│ │  └──────────┘                                          │   │
│ │                                                        │   │
│ │ All resources can talk to each other privately!        │   │
│ │ Isolated from other customers ✓                        │   │
│ │ Secure ✓                                               │   │
│ └────────────────────────────────────────────────────────┘   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## 2. Load Balancer

### What is a Load Balancer?

**Distributes traffic evenly across multiple servers!**

```
┌──────────────────────────────────────────────────────────────┐
│ LOAD BALANCER IN ACTION                                      │
│                                                              │
│         ┌──────────────────┐                                 │
│         │  LOAD BALANCER   │                                 │
│         │   (Public IP)    │                                 │
│         └──────────────────┘                                 │
│                  │                                           │
│       Traffic distributed evenly                              │
│                  │                                           │
│     ┌────────────┼────────────┐                             │
│     │            │            │                             │
│     ↓            ↓            ↓                             │
│ ┌────────┐  ┌────────┐  ┌────────┐                         │
│ │ VM 1   │  │ VM 2   │  │ VM 3   │                         │
│ │ 33%    │  │ 33%    │  │ 34%    │                         │
│ │ Healthy│  │ Healthy│  │ Healthy│                         │
│ └────────┘  └────────┘  └────────┘                         │
│                                                              │
│ WHAT IF VM 2 FAILS?                                          │
│                  │                                           │
│     ┌────────────┼────────────┐                             │
│     │            │            │                             │
│     ↓            ✗            ↓                             │
│ ┌────────┐  ┌────────┐  ┌────────┐                         │
│ │ VM 1   │  │ VM 2   │  │ VM 3   │                         │
│ │ 50%    │  │ FAILED │  │ 50%    │                         │
│ │ Healthy│  │  ❌    │  │ Healthy│                         │
│ └────────┘  └────────┘  └────────┘                         │
│                                                              │
│ Load Balancer detects failure                                │
│ Automatically removes VM 2 from rotation                     │
│ Traffic goes to healthy VMs only ✓                           │
│ Users don't notice! ✓                                        │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

### 📝 Chapter Summary

**This was the BIGGEST chapter - you learned:**

✅ **Compute Services**
- VMs: Full control, manage everything
- App Service: PaaS for web apps
- Functions: Serverless, pay per execution
- AKS: Containers and microservices

✅ **Storage Services**
- Blob: Files, images, videos (Hot/Cool/Archive tiers)
- File: Network file shares (SMB)
- Queue: Messaging between apps
- Disk: VM hard drives

✅ **Database Services**
- SQL Database: Managed SQL Server (PaaS)
- Cosmos DB: Global, <10ms latency, NoSQL
- MySQL/PostgreSQL: Open-source databases

✅ **Networking Services**
- VNet: Private network in Azure
- Load Balancer: Distributes traffic
- VPN Gateway: Connect to on-premises
- Application Gateway: Web load balancer

✅ **Storage Redundancy**
- LRS: Same datacenter (11 nines)
- ZRS: Across zones (12 nines)
- GRS: Cross-region (16 nines)
- GZRS: Best of both (most expensive)

---

### 🎯 Practice Questions

**Question 1:**
Which compute service requires NO server management?

A) Virtual Machines  
B) App Service  
C) Azure Functions  
D) Both B and C

**Question 2:**
Which storage tier costs $0.002/GB/month but has 15-hour retrieval time?

A) Hot  
B) Cool  
C) Archive  
D) Premium

**Question 3:**
Cosmos DB guarantees latency of:

A) <50ms  
B) <10ms  
C) <100ms  
D) <5ms

**Question 4:**
Which redundancy option protects against regional disasters?

A) LRS  
B) ZRS  
C) GRS  
D) None

**Question 5:**
What's the main difference between App Service and Azure Functions?

A) Language support  
B) App Service runs continuously, Functions run on-demand  
C) Cost  
D) Operating system

---

### ✍️ Practice Answers

**Question 1: D** - Both App Service and Azure Functions

*Explanation:* Both are PaaS/Serverless offerings where you don't manage servers. VMs require you to manage the OS and everything. This is a key service model difference!

**Question 2: C** - Archive

*Explanation:* Archive tier is the cheapest ($0.002/GB vs $0.010 Cool and $0.018 Hot) but requires up to 15 hours to retrieve data. Use for long-term storage that's rarely accessed.

**Question 3: B** - <10ms

*Explanation:* Cosmos DB guarantees <10ms read latency globally. This is one of its key differentiators and is heavily tested on the exam!

**Question 4: C** - GRS (Geo-Redundant Storage)

*Explanation:* GRS replicates to a secondary region 300+ miles away, protecting against regional disasters. LRS is same datacenter, ZRS is same region different zones. GZRS also protects but wasn't in the options.

**Question 5: B** - App Service runs continuously, Functions run on-demand

*Explanation:* App Service runs 24/7 (you pay per hour). Functions run only when triggered (pay per execution). This is THE key difference between them!

---

### 🔖 Quick Reference Card

```
┌──────────────────────────────────────────────────────────────┐
│ CORE AZURE SERVICES CHEAT SHEET                              │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│ COMPUTE:                                                      │
│ • VMs: Full control (IaaS)                                   │
│ • App Service: Web apps (PaaS)                               │
│ • Functions: Event-driven (Serverless)                       │
│ • AKS: Containers (PaaS for Kubernetes)                      │
│                                                              │
│ STORAGE:                                                      │
│ • Blob: Files (Hot $0.018, Cool $0.010, Archive $0.002)     │
│ • File: SMB shares                                           │
│ • Queue: Messages                                            │
│ • Disk: VM disks                                             │
│                                                              │
│ DATABASES:                                                    │
│ • SQL Database: Managed SQL Server                           │
│ • Cosmos DB: Global, <10ms, NoSQL                           │
│ • MySQL/PostgreSQL: Open-source                             │
│                                                              │
│ NETWORKING:                                                   │
│ • VNet: Private network                                      │
│ • Load Balancer: Distribute traffic                          │
│ • VPN Gateway: On-prem connection                            │
│                                                              │
│ REDUNDANCY:                                                   │
│ • LRS: 3 copies, same DC (11 nines)                         │
│ • ZRS: 3 zones (12 nines)                                   │
│ • GRS: 2 regions (16 nines)                                 │
│ • GZRS: Best (highest cost)                                 │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

**End of Chapter 9** ✓  
**Most important chapter for AZ-900!** ⭐⭐⭐
-e 

---


