# 📊 Interactive Sales Performance Dashboard

A high-fidelity, responsive Sales Performance Dashboard built using **Vanilla JavaScript**, **Tailwind CSS**, and **Chart.js**. This project demonstrates advanced frontend concepts like reactive state management, dynamic UI rendering, chart lifecycle management, and client-side data exporting—all implemented without external JavaScript frameworks.

▶️ **[Live Demo Link](https://akshityagi703760-source.github.io/sales-dashboard/)** *(Replace with your exact live link if different)*

---

## 🚀 Key Features

*   **Reactive State Pattern:** Implements a central data array (`SALES_DATA`) that acts as the single source of truth. Any state mutation (adding data, filtering, searching) automatically triggers a UI repaint loop.
*   **Robust Chart Lifecycle Management:** Avoids the common Chart.js canvas flashing/ghosting bug by explicitly destroying existing chart instances using `.destroy()` before rendering updated datasets.
*   **Real-time Multi-Filtering:** Allows simultaneous filtering by Date Range, Region, Product Category, and a global search bar.
*   **Dynamic Data Insertion:** Users can add new sales records via an interactive modal form, which immediately updates metrics, KPIs, and graphs in real-time.
*   **Dual-Theme Rendering:** Full native support for Light and Dark modes. The chart grids, tooltips, axis labels, and borders dynamically redraw colors based on the active theme.
*   **Client-Side Pagination:** Smooth data table navigation utilizing exact array slicing (`.slice()`) to handle scalability efficiently.
*   **Instant CSV Export:** Generates and downloads a clean comma-separated values (CSV) file completely client-side using data URI links.

---

## 🛠️ Tech Stack & Libraries

*   **HTML5:** Structured semantic layout.
*   **Tailwind CSS:** Utility-first framework for rapid responsive styling and seamless dark mode configuration.
*   **Chart.js:** Used for complex, reactive configurations of Line and Bar charts.
*   **Lucide Icons:** Clean, scalable vector icons injected dynamically.

---

## 🧠 Technical Highlights (Interview-Ready Concepts)

### 1. Centralized Repaint Architecture
Instead of spaghetti DOM manipulation, the application relies on a unidirectional flow. When a user interacts with a filter:
1. The event listener captures the input.
2. The dataset is filtered into a localized array using JS `.filter()`.
3. A centralized execution function passes the sliced metrics to the KPI cards, table grid, and Chart rendering methods sequentially.

### 2. Preventing Memory Leaks in Canvas
```javascript
// Safely resetting chart instances before recreation
if (chartInstances.revenueTrend) {
    chartInstances.revenueTrend.destroy();
}
chartInstances.revenueTrend = new Chart(ctx, configuration);
