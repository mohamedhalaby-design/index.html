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
    console.log("ERROR:", err);
    document.getElementById("sheetTable").innerHTML =
      "<tr><td>Error loading data</td></tr>";
  });
