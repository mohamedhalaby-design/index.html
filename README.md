<!DOCTYPE html>
<html>
<head>
  <title>Live Attendance Dashboard</title>
  <style>
    body {
      font-family: Arial;
      padding: 20px;
    }
    table {
      border-collapse: collapse;
      width: 100%;
      margin-top: 20px;
    }
    th, td {
      border: 1px solid #ddd;
      padding: 8px;
      text-align: left;
    }
    th {
      background: #f4f4f4;
    }
  </style>
</head>

<body>

<h2>📊 Live Attendance Dashboard</h2>

<table id="sheetTable"></table>

<script>
const sheetID = "1JAhpJhrqixjnEsRsdGXIueNxgNSST2a26EpXcRVwWf4";
const sheetName = encodeURIComponent("live Attendance DB"); // مهم جدًا

const url = `https://sheets.googleapis.com/v4/spreadsheets/${sheetID}/values/${sheetName}?key=YOUR_API_KEY`;

fetch(url)
  .then(res => res.json())
  .then(data => {
    const table = document.getElementById("sheetTable");
    const rows = data.values;

    if (!rows) {
      table.innerHTML = "<tr><td>No data found</td></tr>";
      return;
    }

    rows.forEach((row, i) => {
      let tr = document.createElement("tr");

      row.forEach(cell => {
        let td = document.createElement(i === 0 ? "th" : "td");
        td.textContent = cell;
        tr.appendChild(td);
      });

      table.appendChild(tr);
    });
  })
  .catch(err => {
    console.log(err);
    document.getElementById("sheetTable").innerHTML =
      "<tr><td>Error loading data</td></tr>";
  });
</script>

</body>
</html>
