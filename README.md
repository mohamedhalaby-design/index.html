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

const apiURL = "https://script.google.com/macros/s/AKfycbxJYmc4L32APuiBRoTMGU7mlWmDd2O6JhiP8eq4eg_R3KhpXRVM7b0s-nruxHitildk_Q/exec";

fetch(apiURL)
  .then(res => res.json())
  .then(data => {
    const table = document.getElementById("sheetTable");

    table.innerHTML = "";

    if (!data || data.length === 0) {
      table.innerHTML = "<tr><td>No data found</td></tr>";
      return;
    }

    // headers
    const headers = Object.keys(data[0]);

    let headerRow = document.createElement("tr");
    headers.forEach(h => {
      let th = document.createElement("th");
      th.textContent = h;
      headerRow.appendChild(th);
    });
    table.appendChild(headerRow);

    // rows
    data.forEach(row => {
      let tr = document.createElement("tr");

      headers.forEach(h => {
        let td = document.createElement("td");
        td.textContent = row[h] ?? "";
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
