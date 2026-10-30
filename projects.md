# Projects

A selection of projects I have worked on as an independent consultant and before. Clients are described by industry rather than by name.

- [🏭 System integration](#-system-integration): ERP, MES, WMS, e-commerce, data pipelines and LLM tooling for manufacturers
- [📈 Finance](#-finance): trading platforms, backtesting, forecasting and client reporting
- [🚁 Special projects](#-special-projects): edge computing, video transmission and other one-offs

## 🏭 System integration

Most of this work is built around **eSolver**, an Italian ERP widely used by small and mid-sized manufacturers, and extends it with web applications, shop-floor systems and machine connectivity.

### MES and shop-floor integration
**2015 – present** · *Manufacturers in several industries*

Production planning lived in the ERP while the shop floor ran on separate machines, terminals and spreadsheets, so orders and production data were re-keyed by hand.

- Built production-reporting MES web apps where operators declare produced and scrap quantities, lot and pallet movements and labels, written back to the ERP production documents
- Connected machines to the ERP over Modbus: counters, running hours and production phases, a clean-room data logger, a laser-marking station with serial-number traceability
- Processed time-clock events against shifts and job orders and fed them to the ERP
- Wrote .NET extension libraries that the ERP's scripting language calls for machine events and monitoring, plus a licensing and update server for the company's desktop MES (cloud-hosted, with an admin back office)
- Used change notifications on SQL Server (SqlTableDependency / Service Broker) and Hangfire background jobs to keep systems in sync

**Stack:** C#, .NET Framework → .NET 8/10, ASP.NET Core, NPoco, Hangfire, SQL Server, Angular (PWA), IIS, Azure App Service
**Outcome:** several systems in production, the most recent with xUnit test suites, health checks and scripted deploys

### Warehouse management system (WMS) product line
**2021 – present** · *Five manufacturers, including a lighting/polycarbonate producer and a laser-system maker*

A reusable WMS, developed for one customer and then adapted for each new one, that drives automated warehouses from the ERP.

- Picking tasks, withdrawals and deposits, lot transfers, returns and supplier delivery notes
- Integration with Modula and Ferretto vertical warehouses, an AGV and cutting machines
- Barcode scanning on mobile devices and Kanban barcodes for replenishment
- Evolved over five deployments from .NET Core 3.1 / Angular 12 to .NET 10 / Angular 21

**Stack:** C#, .NET 10, ASP.NET Core, Hangfire, NPoco, SQL Server, Angular + NgRx, xUnit, IIS
**Outcome:** in production at five sites; each new deployment started from the previous codebase

### Digital Kanban MES
**2021 – present** · *Manufacturer of engines and mechanical components (first customer), now several*

Paper Kanban cards on the shop floor were replaced by digital boards fed from the ERP.

- Production orders imported from the ERP become cards on department boards
- Operators declare progress on the boards; declarations go back to the ERP as progress records
- Real-time updates with SignalR, background jobs with Hangfire, customer-specific modules
- Data migration and analysis notebooks: routings and bills of materials imports, throughput times, stock simulations

**Stack:** C#, .NET 8, ASP.NET Core, SignalR, Redis, Hangfire, SQL Server, Angular 17 + NgRx, Playwright, Python (pandas)
**Outcome:** in production with release notes up to v1.9, a user manual and 19 test projects

### ERP–e-commerce integration and ERP APIs
**2015 – 2025** · *Manufacturers and distributors, including a lighting producer and a winery*

Connected the ERP to online shops and web front ends, so that catalogue, prices and stock stayed consistent and web orders reached the ERP without manual work.

- Developed a nopCommerce plugin and Windows service syncing catalogue, prices, stock and orders with the ERP, reused across three B2B/B2C shops
- Built a price-list and discount-policy engine and a catalogue printer driven by customer price lists
- Developed a reusable REST API over the ERP (accounts, items, customers, orders, e-invoicing fields) feeding web and B2B front ends, deployed for several customers

**Stack:** C#, ASP.NET MVC, nopCommerce, ASP.NET Core, .NET 6, NPoco, SQL Server, Azure
**Outcome:** the REST API family stayed in production from 2018 to 2025

### Data pipelines and analysis
**2017 – present** · *Manufacturers*

Moved data between operational systems and turned it into reports.

- Price-synchronisation ETL and demo-database anonymisation with Pentaho Kettle
- Scheduled ETL jobs from an AS400 ERP and SQL Server (moulds, maintenance, press hours), later moved to n8n workflows
- An ETL that pushes ERP parts, prices and stock to a SaaS BOM and quoting platform (Python, packaged as executables)
- Ad-hoc analyses and reports in Python notebooks

**Stack:** Python (pandas), SQL Server, AS400, Pentaho Kettle, n8n, .NET

### MCP tools connecting LLMs to business systems
**2026** · *Plastic injection-mould maker*

Gave Claude controlled access to company systems and data through the Model Context Protocol, to help engineers answer requests for quotation (RFQ).

- Developed MCP servers exposing historical job hours, the press catalogue, ERP pricing codes and supplier and customer prices as tools
- Added 3D STEP-file analysis of parts and moulds
- Built interactive UIs for MCP tools (MCP Apps): press selector, mould steel cost calculator, STEP analyser
- Built the companion web app for press and robot technical data (with STEP/SVG viewing) that replaced a shared spreadsheet

**Stack:** Python, FastMCP, FastAPI, SQLAlchemy, SQL Server, AS400, MongoDB, Angular, Docker, Entra ID
**Outcome:** in active development, exposed securely to the internet behind the company gateway

### Visual search over a mould archive
**2026** · *Plastic injection-mould maker*

Engineers quoting a new part wanted to find similar moulds the company had already built.

- Indexed about 24,000 images from 7,000 past jobs with DINOv3 image embeddings
- Visual similarity search and automatic classification, with tags synced back to the ERP
- Research notebooks on clustering (UMAP, HDBSCAN) that led to the production design

**Stack:** Python, FastAPI, DINOv3, Postgres + pgvector, Qdrant, Angular, Docker
**Outcome:** on-premise application with about 50 test files, including integration tests on containers

### LLM document extraction
**2024 – 2026** · *Public consortium, workplace-safety consultancy, manufacturers*

Turned paper and PDF documents into structured data with OCR and LLMs.

- Digitised funding-request forms: OCR with Azure Document Intelligence, field extraction with an LLM, upload to the customer's document management system
- Built an AI gateway service for OCR, document splitting and LLM extraction (Azure OpenAI, LandingAI, LlamaParse) with usage tracking, used by an incoming-documents application
- Prototyped RAG and graph RAG on risk-assessment documents and Italian workplace-safety law (Neo4j, ChromaDB, evaluation with ragas)

**Stack:** Python, FastAPI, Azure Document Intelligence, Azure OpenAI, LangChain, Neo4j, ChromaDB, Docker
**Outcome:** the form digitisation and the gateway went to production

## 📈 Finance

### Intraday futures trading platform
**2008 – 2017** · *Proprietary and client trading*

Designed, developed and ran intraday trading systems on futures markets (Eurex, CME Globex) end to end, starting from a desktop suite and growing into a modular platform.

- Market data capture, history servers and futures rollover
- Order execution through Interactive Brokers, Rithmic, NinjaTrader and FIX
- Real-time position and portfolio monitoring, strategies loaded as plugins
- Signal publishing to Collective2

**Stack:** C#, .NET Framework, WinForms, ZeroMQ, MySQL, Quartz
**Outcome:** an 84-project solution running in production with launchers and database jobs

### Sector forecasting and portfolio optimisation application
**2010 – 2017** · *Investment firm (consulting engagement)*

Monthly forecasts of the European equity sectors, used to drive a long/short sector allocation.

- Forecasts the 18 DJ Stoxx 600 sectors, plus the equal-weighted index and VDAX volatility
- Markov-switching models with 2 and 3 states (plain, with factors, and on volatility), estimated by maximum likelihood
- AR, error-correction and APT factor models, PCA factors and factor clustering, neural networks, seasonality, impulse-response analysis
- Dynamic time warping and Denton temporal disaggregation to align series of different frequencies
- Sector momentum signals, model combination and automatic model selection by Sharpe ratio
- Genetic-algorithm portfolio optimisation with custom operators and constraints, track record and tracking-error views
- Desktop GUI (about 170 MATLAB files) compiled into a standalone executable for the client; forecasts consumed by the C# trading platform for execution and position tracking

**Stack:** MATLAB (Statistics, Optimization, Global Optimization and Neural Network toolboxes, MATLAB Compiler), Excel
**Outcome:** production tool behind the client's long/short sector strategy

### Backtesting framework
**2014 – present** · *In-house*

A research environment to test strategies on historical data before going live.

- Single and multiple backtests, track analysis and stress-test reports in the C# platform
- Since 2024, a Python engine (`pytrading`) with daily data, indicators, FX rates and strategy classes
- Performance and risk reports per strategy

**Stack:** C#, Python (NumPy, pandas, matplotlib)

### Forecasting and machine-learning-driven trading
**2010 – 2017** · *In-house and investment firm*

Trading signals produced by statistical and machine learning models, executed automatically by the trading platform.

- Statistical and neural-network forecasting models (see [Sector forecasting and portfolio optimisation application](#sector-forecasting-and-portfolio-optimisation-application))
- Model outputs fed into the live execution platform, with monitoring

**Stack:** MATLAB, C#

### Quantitative long/short equity strategy
**2010 – 2017** · *Investment firm (consulting engagement), CTO role*

Managed a quantitative long/short strategy on European stocks with monthly reallocation.

- Sector forecasts and portfolio construction from the [sector forecasting application](#sector-forecasting-and-portfolio-optimisation-application)
- Execution and position tracking through the trading platform (CFDs on Interactive Brokers), monthly rebalancing and reporting

**Stack:** MATLAB (compiled application), C#, MySQL

### Systematic strategy-index research
**2024 – present** · *Investment firm*

Backtested portfolios of bank quantitative investment strategy (QIS) indices from several investment banks.

- Per-provider data preprocessing and validation
- "Ranking-balanced" strategy: rank indices by Sharpe ratio or return, hold the top N at equal weight, re-entry cooldown, T+1 execution, USD valuation with ECB FX rates
- Monthly historical-track deliverables for the client

**Stack:** Python 3.11, pandas, NumPy, matplotlib, `pytrading`
**Outcome:** recurring deliverables since 2024

### Crypto trading platform and client reporting
**2023 – present** · *Crypto asset manager*

Trading and reporting for managed client accounts on crypto exchanges (BTC/USD, BTC/EUR).

- NAV engine per client: money-weighted returns, contributions, management fees, and client PDF/HTML reports in English and Italian, in USD, EUR or BTC
- Multi-exchange trading platform (Bitstamp, then Kraken): REST and WebSocket feeds, order and position services, paper trading, strategies as state machines with runtime configuration
- Web back office to monitor orders, positions and balances and to start and stop strategies
- Deployed with Docker on AWS behind Cloudflare, with Auth0 login

**Stack:** Go, Angular, MySQL, Python (pandas, Jinja2, ReportLab), Docker, AWS EC2/ECR, Cloudflare, Auth0, GitHub Actions
**Outcome:** in production; about 60 Go test files with separate unit and integration suites

### Asset allocation and risk reporting
**2007 – 2010** · *Regulated family office*

- Implemented quantitative risk analysis and reporting procedures
- Developed asset allocation models to build and manage a portfolio of mutual funds
- Co-headed the systematic trading development division, advising a CTA managed futures portfolio

**Stack:** Mathematica

## 🚁 Special projects

### Data and video transmission platform for UAVs
**2023 – 2024** · about one year · *Drone-services company*

A platform to transmit telemetry and video between drones and the ground in order to guide UAVs remotely, with software deployed to edge devices as containers.

- Developed the on-board device agent, packaged as Docker images for amd64 and ARM
- Deployed and managed the containers on edge devices through Azure IoT Edge and Azure IoT Hub
- Built the cloud manager service that talks to devices through IoT Hub direct methods and handles WebRTC signalling
- Built the custom WebRTC video service in Go with GStreamer, including MAVLink telemetry and a TURN server on AWS
- Prototyped MAVLink routing, ZeroMQ and several WebRTC stacks before choosing the design; mission-planning portals were built by a colleague

**Stack:** C#, .NET 6, Go, GStreamer, WebRTC, MAVLink, Docker, Azure IoT Edge, Azure IoT Hub, Azure Event Hubs, AWS
**Outcome:** working platform prototype

### Tourism information platform
**2015 – 2025** · *Tourism software company*

A portal and API for tourism content, with a mobile API.

- Scheduled import jobs from regional and national tourism data feeds
- Web app and API with unit and integration tests
- A Facebook Messenger chatbot on Microsoft Bot Framework

**Stack:** C#, ASP.NET Core, Entity Framework Core, SQL Server, Azure Storage, Bot Framework
**Outcome:** in production and maintained from 2015
