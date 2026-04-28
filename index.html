fetch(https://script.google.com/macros/s/AKfycbxJYmc4L32APuiBRoTMGU7mlWmDd2O6JhiP8eq4eg_R3KhpXRVM7b0s-nruxHitildk_Q/exec)
  .then(res => res.json())
  .then(data => {

    window.ALL_ROWS = data.map(r => ({
      id: r.id || r.ID || "",
      name: r.name || r.Name || "",
      shift: r.shift || "",
      status: r.status || "",
      week: Number(r.week || 0),
      month: Number(r.month || 0),
      isWork: !["WO","OFF","PH"].includes(r.status)
    }));

    window.filtered = window.ALL_ROWS;
    window.dataReady = true;

    // IMPORTANT: شغل الداشبورد هنا فقط
    initCharts();
    updateAll();
  })
  .catch(err => {
    console.log("API ERROR:", err);
    document.body.innerHTML =
      "<h2 style='color:red;text-align:center;margin-top:50px'>API Load Failed</h2>";
  });
