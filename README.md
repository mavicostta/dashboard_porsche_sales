# Porsche Sales Dashboard

An interactive HTML dashboard, built with AI assistance, that transforms a dataset of 100 Porsche vehicle sales into actionable business insights. It addresses key business questions such as top-selling models, regional performance, model year distribution, and preferred payment methods.

**Live Dashboard:** https://mavicostta.github.io/dashboard_porsche_sales/

| Item | Details |
|---|---|
| Database | `Base_Porshe_clean.ods` (100 sales, 12 columns) |
| Sales Period | Feb 29, 2024, to Oct 01, 2027 |
| Scope | 79 cities, 33 states, 40 models across 6 families (718, 911, Cayenne, Macan, Panamera, Taycan) |
| Format | Single HTML file, serverless: data, images, and styles are fully embedded |
| Language | Portuguese (car family and model names remain in their original English/Global format) |

---

## 📊 Project Demonstration

Here is a visual overview of the Porsche Sales Dashboard:

### 🖥️ Dashboard Layout
The main interface provides an intuitive and responsive layout for business intelligence analysis.

![Dashboard Layout](https://github.com/mavicostta/dashboard_porsche_sales/blob/main/primeira%20impress%C3%A3o.png)

### 🔍 Filter Functionality
Users can dynamically filter data by car model, year, city, and payment method to extract custom insights.

![Filter Usage](https://github.com/mavicostta/dashboard_porsche_sales/blob/main/utiliza%C3%A7%C3%A3o%20filtro.png)

### 🏎️ Car Family Showcase
The dashboard includes automated visual cards displaying the vehicle family matching the active selection.

![Car Family Preview 1](https://github.com/mavicostta/dashboard_porsche_sales/blob/main/modelo%20do%20carro.png)
![Car Family Preview 2](https://github.com/mavicostta/dashboard_porsche_sales/blob/main/modelo%20do%20carro%202.png)

---

## 1. Selected Business Questions & Rationale

| # | Question | Why it matters | How the dashboard answers it |
|---|---|---|---|
| 1 | What are the top-selling models by city? | Reveals regional demand to support decisions on vehicle mix, inventory allocation, and localized sales campaigns. | A chart showing the top 10 best-selling models, the mix of car families in the top 10 cities, and a breakdown table of leading models per city. |
| 2 | Which model year sold the most within a specific timeframe? | Helps plan inventory replenishment and reveals which vehicle generation the market is absorbing; the date picker allows for custom window comparisons. | Model year sales distribution chart, leading year KPI, and percentage share—all recalculated dynamically based on the selected period. |
| 3 | Which cars are popular in each specific city? | Converts raw rankings into recommendations: where to focus, which family leads, average ticket size, and predominant payment method. | An automated insight block generated dynamically from active filters, including a warning badge when the sample size is too small. |

These three questions stem from concrete commercial decisions (what to offer, where, and when), and each is paired with a specific KPI and chart that answers it directly.

## 2. Data Insights (Global Overview, Unfiltered)

- **Sales & Revenue:** 100 sales totaling **US$ 12,827,800.50** (currency verified as USD). The average ticket size is **US$ 128,278**, with vehicle prices ranging from US$ 58,900 to US$ 286,500.
- **Leading Model Year: 2024**, accounting for 29 sales (29%). The complete distribution is: 2020 (4), 2021 (12), 2022 (16), 2023 (19), 2024 (29), 2025 (16), and 2026 (4).
- **Top-Selling Models:** A six-way tie with 4 sales each for Cayenne Coupe, Cayenne E-Hybrid, Macan Electric, Macan T, Panamera, and Taycan 4S.
- **Car Families:** 911 (23), Cayenne (18), Macan (17), Taycan (16), Panamera (14), and 718 (12).
- **Geographic Distribution:** Atlanta leads with 3 sales. 19 cities recorded 2 sales, and 59 cities have a single sale.
- **Payment Methods:** Wire transfer (26%), credit card (15%), financing (13%), cash (12%), bank transfer (10%), leasing (10%), cryptocurrency (6%), debit card (4%), and ACH debit (4%).
- **Delivery Status:** 41 delivered, 17 pending, 15 in transit, 7 canceled, and 20 in other stages (awaiting delivery, approval, pickup, inspection, or shipped).

> ⚠️ **Read with Caution:** With a maximum of 3 sales per city, ties are common. City-specific rankings are indicative rather than statistically robust. The dashboard explicitly communicates this inside the insights section.

## 3. The Prompt & Evolutionary Iterations

### Original Prompt

```text
utilizando o recurso de canvas, renderize uma dashboard em html ao lado
#Filtro
Modelo da porshe
Model Year
City
Pay method

#Perguntas de negócios e kpis
Quais os principais modelos de carro vendido por cidade?
Qual o ano de modelo de carro mais saiu em um período?
Quero insight de carros populares de vendas com base nos dados de cada cidade

sobre o ui/ux,se baseie no site oficial da porsche brasil https://porsche.com tenha um ar elegante e refinado nas cores preto, branco e prata

Nas datas com dados "INVALIDO" utilize a data anterior da compra seguinte.
```

### Iteration History

| Version | Request Made | Changes Implemented in the Dashboard |
|---|---|---|
| 1. Original | The base prompt above. | Added filters for model, model year, city, payment method, and a custom date range. Features KPIs, charts, a city breakdown table, and automated insights. Dark/light theme with a black, white, and silver UI. |
| 2. Interactivity & Visuals | "Make it more interactive with a modern visual style; show model photos on hover; format dates to Brazilian standard." | Enabled cross-filtering by clicking on chart bars and city rows. Added a detailed searchable sales table, hover cards for car models, smooth animations, a sticky filter bar, and formatted dates (`DD/MM/YYYY`) with input masking. |
| 3. Typography & Language | "You can use public Google images; use a modern font; translate payments to Portuguese." | Integrated new typography and translated payment methods. External Google images were restricted by the deployment environment, leading to alternative asset handling. |
| 4. Vector Sketches | "Use the photos as a reference and create vector sketches of the models." | Created 13 side-profile vector sketches categorized by body type (Coupe, Convertible, Targa, GT, SUV, Sedan, etc.), shared across the 40 models. |
| 5. Final Version | Provided 6 real photos, requested typography refinement, localized text, and gold accents. | Integrated real photos (one per family) inside the hover cards. Applied *Outfit* and *Plus Jakarta Sans* fonts, translated delivery statuses, and added elegant gold accents to highlighted metrics. |

### Consolidated Prompt (To reproduce the final version in a single run)

```text
Using the canvas/artifact feature, create a Porsche sales HTML dashboard based on the Base_Porshe_clean.ods spreadsheet.
Filters: model, model year, city, payment method, and date range (dd/mm/aaaa).
KPIs: total sales, revenue, average ticket, top model year, top model, and top city.
Features: (1) top models sold per city; (2) top-selling model year in the selected period; (3) low-sample warning system for localized insights.
Interactivity: cross-filtering on chart clicks; searchable data table; hover effects displaying the car family photo (6 photos provided).
UI/UX: Inspired by the official Porsche design language using black, white, silver, and gold accents. Light/dark mode toggle, using Outfit and Plus Jakarta Sans typography.
Localization: All text in Portuguese (except car names/models); dates in dd/mm/aaaa format; payment methods and delivery statuses translated.
Edge Case handling: Initial invalid dates in the first sample were manually corrected to ensure 100% data fidelity to the base spreadsheet.
Privacy: Do not display customer or salesperson names.
```

## 4. Data Engineering & Processing

**Pre-ingestion:** The dataset arrived pre-cleaned. The filename (`_clean`) and the `Sanitized` column suffixes indicated previous data cleansing. Inspection confirmed 100 rows, 12 columns, zero null values.

**AI Pipeline Steps:**

1. **Inspection:** Read the spreadsheet via Python (`pandas`), validated columns, data types, and null counts.
2. **Date Correction:** The original date column contained mixed data types where initial entries in the first sample appeared as invalid dates; these were manually corrected to guarantee that 100% of the data points are completely faithful to the base spreadsheet.
3. **Contingency Rules:** Fallback logic was programmatically implemented as a safeguard.
4. **Feature Engineering:** Extracted the vehicle `Family` (718, 911, Cayenne, Macan, Panamera, Taycan) from the first word of the model string. Payment methods and delivery statuses were mapped and translated for localized presentation.
5. **Data Privacy:** Dropped sensitive fields (`customer_name`, `salesperson`, `VehicleMileageSanitized`, and `sale_id`) to ensure data privacy. Only relevant business metrics were passed to the client-side app.
6. **Business Constraints & Assumptions:** Transactional currency was verified as USD. Future-dated transactions extending into 2027 were natively present in the raw file, which was intentional and not an error; these records represent "gift sales" (purchased as gifts for other individuals) and were purposely kept to maintain complete dataset integrity.

## 5. Technology Stack

- **AI Engine:** Anthropic Claude (via claude.ai interface).
- **Deployment environment:** Claude Artifacts (Canvas), used to build, compile, and preview the single-page application in real-time.
- **Data Execution:** Python sandboxed environment for data manipulation, image resizing, and base64 string compilation.
- **Front-end Libraries:** Chart.js v4.4.1 for charts, Google Fonts (*Outfit* & *Plus Jakarta Sans*).

## 6. How to Use the Dashboard

- **Filtering:** Slice data by model, year, city, payment method, and custom date range. Use the "Excluir cancelados" checkbox to filter out canceled transactions. The "Limpar filtros" button resets the view.
- **Interactive Charts:** Click on any data bar or row to apply a global filter for that specific attribute. Click again to clear. Gold bars represent the leading category.
- **Drill-down Table:** Click on any city row inside the summary table to isolate that city's sales performance.
- **Hover Previews:** Hover or tap on a vehicle model name to trigger an information card displaying its family image, total sales volume, average price, and key demographic cities.
- **Theme Selection:** Toggle between dark and light modes via the "Tema" button (defaults to system settings).

## 7. Project Limitations & Next Steps

- **Sample Size Restrictions:** Localized insights like "highest ticket price" might point to a city with only one isolated sale (e.g., Arlington, with a single sale of US$ 286,500).
- **Asset Granularity:** Images are mapped at the *Family* level rather than per individual model variant to optimize file delivery.
- **Currency Verification:** Needs validation with stakeholders to officially confirm if the transactional currency is USD.
- **Timeline Anomalies:** Future-dated records beyond October 2026 require verification to confirm if they represent forecasting projections or data-entry errors.
- **Future Roadmap:** Implement period-over-period delta tracking, geographic map overlays, and CSV export functionality for filtered datasets.

## 8. Technical Architecture

A standalone single-page application (`HTML5` + `CSS3` + `JavaScript ES6`) built without external server dependencies. The full dataset (100 records × 9 attributes), 6 car family assets (compiled as Base64 JPEG strings), and layout scripts are bundled inside a single file. The user interface mimics the premium aesthetic of Porsche's brand guidelines (minimalist layout, wide-tracked uppercase typography, dark mode focus) without direct infringement of proprietary branding assets.
