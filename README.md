<script>

// ─── API ─────────────────────────────────────────────────────────────
const API_URL = "https://script.google.com/macros/s/AKfycbxJYmc4L32APuiBRoTMGU7mlWmDd2O6JhiP8eq4eg_R3KhpXRVM7b0s-nruxHitildk_Q/exec";

// ─── GLOBAL SAFE STATE ───────────────────────────────────────────────
window.ALL_ROWS = [];
window.filtered = [];

// ─── SAFE INIT GUARD ────────────────────────────────────────────────
let chartsInitialized = false;

// ─── LOAD DATA FIRST (CRITICAL FIX) ──────────────────────────────────
fetch(API_URL)
  .then(res => res.json())
  .then(data => {

    if (!Array.isArray(data)) {
      throw new Error("Invalid API response");
    }

    // normalize data
    window.ALL_ROWS = data.map(r => ({
      id: String(r.id || r.ID || ""),
      name: String(r.name || r.Name || ""),
      shift: r.shift || "",
      status: r.status || "",
      week: Number(r.week || 0),
      month: Number(r.month || 0),
      isWork: !["WO","OFF","PH","OFFDAY"].includes(r.status)
    }));

    window.filtered = window.ALL_ROWS;

    // IMPORTANT: run dashboard ONLY after data loads
    if (!chartsInitialized) {
      initCharts();
      chartsInitialized = true;
    }

    updateAll();

  })
  .catch(err => {
    console.log("API ERROR:", err);
    document.body.innerHTML =
      "<h2 style='color:red;text-align:center;margin-top:50px'>❌ Failed to load data from API</h2>";
  });


// ─── PATCH: SAFE updateAll wrapper ───────────────────────────────────
const originalUpdateAll = updateAll;

updateAll = function() {
  if (!window.ALL_ROWS || window.ALL_ROWS.length === 0) return;
  return originalUpdateAll();
};

</script>
