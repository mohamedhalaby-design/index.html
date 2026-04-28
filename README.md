<script>
const sheetID = "1JAhpJhrqixjnEsRsdGXIueNxgNSST2a26EpXcRVwWf4";
const sheetName = "live Attendance DB";

// مهم: نحولها Range صح
const range = encodeURIComponent(`'${sheetName}'`);

const apiKey = "YOUR_API_KEY";

const url = `https://sheets.googleapis.com/v4/spreadsheets/${sheetID}/values/${range}?key=${apiKey}`;

fetch(url)
  .then(res => res.json())
  .then(data => {
    const table = document.getElementById("sheetTable");
    const rows = data.values;

    if (!rows) {
      table.innerHTML = "<tr><td>No data found</td></tr>";
      return;
    }

    table.innerHTML = "";

    rows.forEach((row, i) => {
      let tr = document.createElement("tr");

      row.forEach(cell => {
        let td = document.createElement(i === 0 ? "th" : "td");
        td.textContent = cell || "";
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
