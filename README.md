<script>
// ─── API CONFIG ─────────────────────────────────────────────────────────────
const API_URL = "https://script.google.com/macros/s/AKfycbxJYmc4L32APuiBRoTMGU7mlWmDd2O6JhiP8eq4eg_R3KhpXRVM7b0s-nruxHitildk_Q/exec";

let ALL_ROWS = [];
let filtered = [];

// ─── LOAD DATA FIRST ─────────────────────────────────────────────────────────
fetch(API_URL)
  .then(res => res.json())
  .then(data => {

    // normalize data عشان الداشبورد يفهمه
    ALL_ROWS = data.map(r => ({
      id: r.id || r.ID || "",
      name: r.name || r.Name || "",
      shift: r.shift || r.Shift || "",
      status: r.status || r.Status || "",
      week: Number(r.week || r.Week || 0),
      month: Number(r.month || r.Month || 0),

      // مهم للـ KPI calculations
      isWork: !["WO","OFF","PH","OFFDAY"].includes(r.status)
    }));

    filtered = ALL_ROWS;

    // تشغيل الداشبورد بعد تحميل البيانات
    initCharts();
    updateAll();

  })
  .catch(err => {
    console.log("API ERROR:", err);
    document.body.innerHTML =
      "<h2 style='color:red;text-align:center;margin-top:50px'>❌ Failed to load data from API</h2>";
  });

</script>
