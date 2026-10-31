# Projects

Software engineer and architect with about 19 years of experience across two domains: **manufacturing system integration** (ERP, MES, WMS and machine connectivity) and **quantitative finance** (trading platforms, forecasting models and client reporting). I have held senior roles in finance, including CTO and co-head of a systematic trading division. Today I focus on **applied AI**: connecting LLMs, computer vision and document extraction to real business systems. I have worked as an independent consultant since May 2010.

- [🤖 Applied AI](#-applied-ai): LLM tools over business systems, visual search, document extraction
- [🏭 System integration](#-system-integration): ERP, MES, WMS, e-commerce and data pipelines for manufacturers
- [📈 Finance](#-finance): trading platforms, quantitative strategies, backtesting and client reporting
- [🚁 Edge computing and IoT](#-edge-computing-and-iot): telemetry and video transmission for drones

## 🤖 Applied AI

### MCP tools connecting LLMs to business systems
**2026** · *Plastic injection-mould maker*\
**Role:** Sole developer

Gave Claude controlled access to company systems and data through the Model Context Protocol (MCP), to help engineers answer requests for quotation (RFQ) faster.

- Developed MCP servers that expose historical job hours, the press catalogue, ERP pricing codes and supplier and customer prices as tools
- Added 3D STEP-file analysis of parts and moulds
- Built interactive UIs for the tools (MCP Apps): a press selector, a mould-steel cost calculator and a STEP analyser
- Built a companion web app for press and robot technical data, with STEP/SVG viewing, that replaced a shared spreadsheet

**Stack:** Python, FastMCP, FastAPI, SQLAlchemy, SQL Server, AS400, MongoDB, Angular, Docker, Entra ID\
**Outcome:** in pilot with the engineering team

### Visual search over a mould archive
**2026** · *Plastic injection-mould maker*\
**Role:** Sole developer

Engineers quoting a new part wanted to find similar moulds the company had already built.

- Indexed about 24,000 images from 7,000 past jobs with DINOv3 image embeddings
- Visual similarity search and automatic classification, with tags synced back to the ERP
- Research notebooks on clustering (UMAP, HDBSCAN) that led to the production design

**Stack:** Python, FastAPI, DINOv3, Postgres + pgvector, Qdrant, Angular, Docker\
**Outcome:** in daily use; it turned a search that relied on people's memory ("have we ever produced something like this?") into a structured process

### LLM document extraction
**2024 – 2026** · *Public consortium, workplace-safety consultancy, manufacturers*\
**Role:** Sole developer

Turned paper and PDF documents into structured data with OCR and LLMs.

- Digitised funding-request forms: OCR with Azure Document Intelligence, field extraction with an LLM, upload to the customer's document management system
- Built an AI gateway service for OCR, document splitting and LLM extraction (Azure OpenAI, LandingAI, LlamaParse) with usage tracking, used by an incoming-documents application
- Prototyped RAG and graph RAG on risk-assessment documents and Italian workplace-safety law (Neo4j, ChromaDB, evaluation with ragas)

**Stack:** Python, FastAPI, Azure Document Intelligence, Azure OpenAI, LangChain, Neo4j, ChromaDB, Docker\
**Outcome:** form digitisation and the AI gateway in production, processing about 10 documents a week and extending to new document types without further development

## 🏭 System integration

Most of this work is built around **eSolver**, an Italian ERP widely used by small and mid-sized manufacturers. I extend it with web applications, shop-floor systems and machine connectivity.

### MES and shop-floor integration
**2015 – present** · *Manufacturers in several industries*\
**Role:** Sole developer

Production planning lived in the ERP while the shop floor ran on separate machines, terminals and spreadsheets, so orders and production data were re-keyed by hand.

- Built production-reporting MES web apps where operators declare produced and scrap quantities, lot and pallet movements and labels, written back to the ERP production documents
- Connected machines to the ERP over Modbus: counters, running hours and production phases, a clean-room data logger, and a laser-marking station with serial-number traceability
- Processed time-clock events against shifts and job orders and fed them to the ERP
- Wrote .NET extension libraries for machine events and monitoring, called from the ERP's scripting language
- Built a cloud-hosted licensing and update server, with an admin back office, for a desktop MES product

**Stack:** C#, .NET Framework → .NET 8/10, ASP.NET Core, Hangfire, SQL Server (Service Broker), Angular (PWA), IIS, Azure App Service\
**Outcome:** the MES is in use at about 80 manufacturing companies, rolled out together with a team of analysts and sales staff; the most recent systems have xUnit test suites, health checks and scripted deploys

### Warehouse management system (WMS) product line
**2021 – present** · *Several manufacturers, including a lighting/polycarbonate producer and a laser-system maker*\
**Role:** Sole developer

A WMS that drives automated warehouses from the ERP.

- Picking tasks, withdrawals and deposits, lot transfers, returns and supplier delivery notes
- Integration with Modula and Ferretto vertical warehouses, an AGV and cutting machines
- Barcode scanning on mobile devices and Kanban barcodes for replenishment

**Stack:** C#, .NET 10, ASP.NET Core, Hangfire, SQL Server, Angular + NgRx, xUnit, IIS\
**Outcome:** in production at 5 companies

### Digital Kanban MES
**2021 – present** · *Eyewear manufacturer*\
**Role:** Sole developer

Paper Kanban cards on the shop floor were replaced by digital boards fed from the ERP.

- Production orders imported from the ERP become cards on department boards
- Operators declare progress on the boards; declarations go back to the ERP as progress records
- Real-time updates with SignalR, background jobs with Hangfire, customer-specific modules
- Data migration and analysis notebooks: routing and bill-of-materials imports, throughput times, stock simulations

**Stack:** C#, .NET 8, ASP.NET Core, SignalR, Redis, Hangfire, SQL Server, Angular 17 + NgRx, Playwright, Python (pandas)\
**Outcome:** runs the full production cycle of a plant shipping about 40,000 pieces a week

### ERP–e-commerce integration and ERP APIs
**2015 – 2025** · *Manufacturers and distributors, including a lighting producer and a winery*\
**Role:** Sole developer

Connected the ERP to online shops and web front ends, so that catalogue, prices and stock stayed consistent and web orders reached the ERP without manual work.

- Developed a nopCommerce plugin and Windows service that sync catalogue, prices, stock and orders with the ERP, reused across three B2B/B2C shops
- Built a price-list and discount-policy engine, and a catalogue printer driven by customer price lists
- Developed a reusable REST API over the ERP (accounts, items, customers, orders, e-invoicing fields) feeding web and B2B front ends, deployed for several customers

**Stack:** C#, ASP.NET Core, .NET 6, ASP.NET MVC, nopCommerce, SQL Server, Azure\
**Outcome:** in production for several customers

### Data pipelines and analysis
**2017 – present** · *Manufacturers*\
**Role:** Sole developer

Moved data between operational systems and turned it into reports.

- Scheduled ETL jobs from an AS400 ERP and SQL Server (moulds, maintenance, press hours), later moved to n8n workflows
- An ETL that pushes ERP parts, prices and stock to a SaaS BOM and quoting platform (Python, packaged as executables)
- Price-synchronisation ETL and demo-database anonymisation with Pentaho Kettle
- Ad-hoc analyses and reports in Python notebooks

**Stack:** Python (pandas), n8n, SQL Server, AS400, Pentaho Kettle, .NET\
**Outcome:** recurring data flows between the ERP, the shop floor and external platforms run fully automated

### Tourism information platform
**2015 – present** · *Tourism software company*\
**Role:** Lead developer

A tourism-content portal with a web and mobile API, fed by scheduled imports from regional and national tourism data feeds, with unit and integration tests.

**Stack:** C#, ASP.NET Core, Entity Framework Core, SQL Server, Azure Storage\
**Outcome:** in production and maintained since 2015

## 📈 Finance

### Quantitative long/short sector strategy (CTO)
**2010 – 2017** · *Investment firm (consulting engagement)*\
**Role:** CTO

Designed and ran the systematic engine behind the client's long/short strategy on European equities: monthly sector forecasts, portfolio construction, and automated execution through the trading platform.

- Forecast the 18 DJ Stoxx 600 sectors, the equal-weighted index and VDAX volatility every month
- Models: Markov-switching (2 and 3 states, with factors and on volatility, estimated by maximum likelihood), AR, error-correction and APT factor models, PCA factors and factor clustering, neural networks, seasonality, impulse-response analysis
- Dynamic time warping and Denton temporal disaggregation to align series of different frequencies
- Sector momentum signals, model combination and automatic model selection by Sharpe ratio
- Genetic-algorithm portfolio optimisation with custom operators and constraints, track-record and tracking-error views
- Delivered as a standalone desktop application (MATLAB Compiler); forecasts fed the C# trading platform, which executed CFDs on Interactive Brokers, tracked positions and produced monthly rebalancing reports

**Stack:** MATLAB (Statistics, Optimization, Global Optimization and Neural Network toolboxes, MATLAB Compiler), C#, MySQL, Excel\
**Outcome:** production tool behind the client's strategy for about seven years

### Intraday futures trading platform
**2010 – 2017** · *Proprietary trading and systems operated for clients*\
**Role:** Sole developer

Designed, developed and ran intraday trading systems on futures markets (Eurex, CME Globex) end to end. The work started as a desktop suite and grew into a modular platform.

- Market data capture, history servers and futures rollover
- Order execution through Interactive Brokers, Rithmic, NinjaTrader and FIX
- Best-execution platform routing orders across these brokers and venues
- Real-time position and portfolio monitoring, with strategies loaded as plugins
- Executed the signals of the statistical and machine-learning models above, with live monitoring

**Stack:** C#, .NET Framework, WinForms, ZeroMQ, MySQL, Quartz\
**Outcome:** in production for about seven years, running live strategies on CME index futures (S&P 500, Nasdaq, Dow Jones) and FX futures (EUR/USD, GBP/USD, JPY/USD)

### Crypto trading platform and client reporting
**2023 – present** · *Crypto asset manager*\
**Role:** Sole developer

Trading and reporting for managed client accounts on crypto exchanges (BTC/USD, BTC/EUR).

- NAV engine per client: money-weighted returns, contributions, management fees, and client PDF/HTML reports in English and Italian, in USD, EUR or BTC
- Multi-exchange trading platform (Bitstamp, then Kraken): REST and WebSocket feeds, order and position services, paper trading, strategies as state machines with runtime configuration
- Web back office to monitor orders, positions and balances and to start and stop strategies
- Deployed with Docker on AWS behind Cloudflare, with Auth0 login

**Stack:** Go, Angular, MySQL, Python (pandas, Jinja2, ReportLab), Docker, AWS EC2/ECR, Cloudflare, Auth0, GitHub Actions\
**Outcome:** in production, with unit and integration test suites and CI/CD on GitHub Actions

### Systematic strategy-index research
**2024 – present** · *Investment firm*\
**Role:** Lead developer

Backtested portfolios of quantitative investment strategy (QIS) indices from several investment banks.

- Per-provider data preprocessing and validation
- "Ranking-balanced" strategy: rank indices by Sharpe ratio or return, hold the top N at equal weight, with a re-entry cooldown, T+1 execution and USD valuation using ECB FX rates
- Monthly historical-track deliverables for the client

**Stack:** Python, pandas, NumPy, matplotlib, `pytrading`\
**Outcome:** recurring monthly deliverables since 2024

### Backtesting framework
**2014 – present** · *Own framework, reused in client work*

A research environment for testing strategies on historical data before going live.

- Single and multiple backtests, track analysis and stress-test reports in the C# platform
- Since 2024, a Python engine (`pytrading`) with daily data, indicators, FX rates and strategy classes, which powers the strategy-index research above
- Performance and risk reports per strategy

**Stack:** C#, Python (NumPy, pandas, matplotlib)

### Asset allocation and risk reporting
**2007 – April 2010** · *Regulated family office*\
**Role:** Co-head of the systematic trading development division

- Advised a CTA managed-futures portfolio
- Developed asset allocation models to build and manage a portfolio of mutual funds
- Implemented quantitative risk analysis and reporting procedures

**Stack:** Mathematica

## 🚁 Edge computing and IoT

### Data and video transmission platform for UAVs
**2023 – 2024** · *Drone-services company*\
**Role:** Sole developer of the device, cloud and video components; the mission-planning portals were built by a colleague

A platform that transmits telemetry and video between drones and the ground to guide UAVs remotely, with software deployed to edge devices as containers.

- Developed the on-board device agent, packaged as Docker images for amd64 and ARM
- Deployed and managed the containers on edge devices through Azure IoT Edge and Azure IoT Hub
- Built the cloud manager service that talks to devices through IoT Hub direct methods and handles WebRTC signalling
- Built the custom WebRTC video service in Go with GStreamer, including MAVLink telemetry and a TURN server on AWS
- Evaluated MAVLink routing, ZeroMQ and several WebRTC stacks before choosing the design

**Stack:** C#, .NET 6, Go, GStreamer, WebRTC, MAVLink, Docker, Azure IoT Edge, Azure IoT Hub, Azure Event Hubs, AWS\
**Outcome:** working platform prototype, successfully field-tested
