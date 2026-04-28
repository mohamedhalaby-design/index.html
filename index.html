<script>
console.log("SCRIPT LOADED");

const apiURL = "https://script.google.com/macros/s/AKfycbxJYmc4L32APuiBRoTMGU7mlWmDd2O6JhiP8eq4eg_R3KhpXRVM7b0s-nruxHitildk_Q/exec";

fetch(apiURL)
  .then(res => {
    console.log("FETCH OK", res);
    return res.json();
  })
  .then(data => {
    console.log("DATA RECEIVED:", data);

    const table = document.getElementById("sheetTable");

    if (!table) {
      console.log("TABLE NOT FOUND");
      return;
    }

    table.innerHTML = "";

    if (!data || data.length === 0) {
      table.innerHTML = "<tr><td>No data</td></tr>";
      return;
    }

    const headers = Object.keys(data[0]);

    let headerRow = document.createElement("tr");
    headers.forEach(h => {
      let th = document.createElement("th");
      th.textContent = h;
      headerRow.appendChild(th);
    });
    table.appendChild(headerRow);

    data.forEach(row => {
      let tr = document.createElement("tr");

      headers.forEach(h => {
        let td = document.createElement("td");
        td.textContent = row[h];
        tr.appendChild(td);
      });

      table.appendChild(tr);
    });

  })
  .catch(err => {
    console.error("FETCH ERROR:", err);
    document.body.innerHTML = "<h3>Error loading dashboard (check console)</h3>";
  });
</script>
