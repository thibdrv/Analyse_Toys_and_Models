# Data Architecture & Organization

## Data Modeling & Schema

The model does not follow a **star schema** which is the recommended standard for Power BI and instead retains a structure close to the original relational database.

**Technical Impact :**

While functional, this approach increases the complexity of writing DAX formulas and manipulating data.

**Justification :**

The main advantage lies in the initial setup phase keeping the source structure avoids designing heavy ETL transformations (via SQL or Power Query) prior to importing.

**Limitations :**

Conversely, this choice can affect aggregation performance and increase model complexity as future enhancements are made.

---

## Model Structure

The model is built around **5 main analytical axes** within the dashboard

1. **Revenue**
2. **Collections**
3. **Growth**
4. **Profitability**
5. **Average Payments**

### Additional Technical Tables
* **`Calendar Table` :** Provides a continuous time reference for time-based analysis (quarters, years, and period-over-period comparisons).
* **`Metrics Table` :** Centralizes parameters and measures to allow users to dynamically choose which indicator to display across specific visuals.

---

## Analysis by Axis & Areas for Improvement :

### 1. Revenue
* **Observation :** Revenue is heavily concentrated among a small number of clients and key geographic areas.
* **Areas for Improvement :** Track revenue trends by geography over time rather than relying solely on total volume to distinguish growing markets from declining ones.

### 2. Collections
* **Observation :** Outstanding balances and credit utilization rates are tracked by client, but lack context regarding aging receivables or geographic distribution.
* **Areas for Improvement :** Integrate overdue payment tracking by region and implement visual alerts for high risk accounts.

### 3. Growth
* **Observation :** Revenue growth is analyzed quarterly and annually, but lacks integration with overall margin and geographic data.
* **Areas for Improvement :** Plot margin trends alongside revenue growth while identifying the specific geographic zones driving real growth.

### 4. Profitability
* **Observation :** Gross and net margins are calculated by product and category, but are not cross referenced with geographic locations.
* **Areas for Improvement :** Add a profitability view by region to identify markets that are only superficially profitable (high revenue offset by high logistics costs or discounts).

### 5. Average Payments
* **Observation :** Average payment amounts are analyzed by client and region, but are not linked to credit risk metrics.
* **Areas for Improvement :** Cross reference average payment amounts with credit utilization rates to pinpoint high risk zones for default or non payment.
