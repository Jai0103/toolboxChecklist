<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Construction Toolbox Checklist</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #eef1f5;
      color: #1f2933;
    }

    .app {
      min-height: 100vh;
      padding: 24px;
    }

    .container {
      max-width: 1100px;
      margin: 0 auto;
      background: #ffffff;
      border: 1px solid #d8dee8;
      border-radius: 8px;
      box-shadow: 0 16px 40px rgba(0, 0, 0, 0.08);
      overflow: hidden;
    }

    header {
      background: #17202a;
      color: #ffffff;
      padding: 24px;
      display: flex;
      justify-content: space-between;
      gap: 16px;
      align-items: center;
    }

    header h1 {
      margin: 0;
      font-size: 26px;
    }

    header p {
      margin: 6px 0 0;
      color: #cbd5e1;
    }

    .status {
      background: #d98e18;
      color: #111827;
      padding: 10px 14px;
      border-radius: 6px;
      font-weight: bold;
      white-space: nowrap;
    }

    .content {
      padding: 24px;
    }

    .form-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
      margin-bottom: 22px;
    }

    label {
      display: grid;
      gap: 7px;
      font-size: 13px;
      font-weight: bold;
      color: #374151;
    }

    input,
    select,
    textarea {
      width: 100%;
      border: 1px solid #cfd7e3;
      border-radius: 6px;
      padding: 11px 12px;
      font: inherit;
      background: #ffffff;
    }

    textarea {
      resize: vertical;
    }

    .summary {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      border: 1px solid #d8dee8;
      border-radius: 8px;
      overflow: hidden;
      margin-bottom: 22px;
    }

    .summary div {
      padding: 16px;
      background: #f8fafc;
      border-right: 1px solid #d8dee8;
    }

    .summary div:last-child {
      border-right: 0;
    }

    .summary strong {
      display: block;
      font-size: 28px;
    }

    .summary span {
      color: #64748b;
      font-size: 13px;
      font-weight: bold;
    }

    .toolbar {
      display: flex;
      justify-content: space-between;
      gap: 12px;
      align-items: center;
      margin-bottom: 14px;
    }

    .toolbar h2 {
      margin: 0;
      font-size: 21px;
    }

    .checklist {
      border-top: 1px solid #d8dee8;
    }

    .item {
      display: grid;
      grid-template-columns: minmax(220px, 1fr) 280px minmax(220px, 1fr);
      gap: 14px;
      align-items: center;
      padding: 15px 0;
      border-bottom: 1px solid #d8dee8;
    }

    .item-title strong,
    .item-title span {
      display: block;
    }

    .item-title span {
      margin-top: 4px;
      color: #64748b;
      font-size: 13px;
    }

    .result {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      border: 1px solid #cfd7e3;
      border-radius: 6px;
      overflow: hidden;
    }

    .result button {
      border-radius: 0;
      background: #f8fafc;
      color: #1f2933;
      border-right: 1px solid #cfd7e3;
      padding: 10px 8px;
      font-size: 13px;
    }

    .result button:last-child {
      border-right: 0;
    }

    .result button.active {
      background: #126a5b;
      color: #ffffff;
    }

    .actions {
      display: flex;
      justify-content: flex-end;
      gap: 12px;
      margin-top: 22px;
    }

    button {
      border: 0;
      border-radius: 6px;
      padding: 12px 16px;
      font: inherit;
      font-weight: bold;
      cursor: pointer;
    }

    .primary {
      background: #126a5b;
      color: #ffffff;
    }

    .primary:hover {
      background: #0b4f45;
    }

    .secondary {
      background: #e5eaf1;
      color: #1f2933;
    }

    .danger {
      background: #b83232;
      color: #ffffff;
    }

    .notice {
      margin-top: 14px;
      padding: 12px 14px;
      background: #dcf5ea;
      color: #166344;
      border-radius: 6px;
      font-weight: bold;
      display: none;
    }

    @media (max-width: 900px) {
      header,
      .toolbar {
        flex-direction: column;
        align-items: stretch;
      }

      .form-grid,
      .item {
        grid-template-columns: 1fr;
      }

      .summary {
        grid-template-columns: repeat(2, 1fr);
      }

      .actions {
        flex-direction: column;
      }

      button {
        width: 100%;
      }
    }
  </style>
</head>

<body>
  <div class="app">
    <div class="container">
      <header>
        <div>
          <h1>Construction Toolbox Checklist</h1>
          <p>Daily site safety inspection interface</p>
        </div>

        <div class="status">
          <span id="completedCount">0</span> / <span id="totalCount">0</span> checked
        </div>
      </header>

      <main class="content">
        <section class="form-grid">
          <label>
            Project Name
            <input id="project" placeholder="Example: Tower A Construction" />
          </label>

          <label>
            Site / Location
            <input id="site" placeholder="Example: Level 5, Block B" />
          </label>

          <label>
            Supervisor
            <input id="supervisor" placeholder="Supervisor name" />
          </label>

          <label>
            Crew / Contractor
            <input id="crew" placeholder="Crew or contractor name" />
          </label>

          <label>
            Date
            <input id="date" type="date" />
          </label>

          <label>
            Shift
            <select id="shift">
              <option>Morning</option>
              <option>Afternoon</option>
              <option>Night</option>
            </select>
          </label>
        </section>

        <section class="summary">
          <div>
            <strong id="passCount">0</strong>
            <span>Pass</span>
          </div>

          <div>
            <strong id="failCount">0</strong>
            <span>Fail</span>
          </div>

          <div>
            <strong id="naCount">0</strong>
            <span>N/A</span>
          </div>

          <div>
            <strong id="pendingCount">0</strong>
            <span>Pending</span>
          </div>
        </section>

        <section class="toolbar">
          <h2>Checklist Items</h2>
          <button class="secondary" onclick="markAllPass()">Mark All Pass</button>
        </section>

        <section id="checklist" class="checklist"></section>

        <label style="margin-top: 20px;">
          General Remarks
          <textarea id="remarks" rows="4" placeholder="Overall toolbox talk notes, hazards, attendees, or follow-up actions"></textarea>
        </label>

        <div class="actions">
          <button class="secondary" onclick="saveChecklist()">Save</button>
          <button class="danger" onclick="clearChecklist()">Clear</button>
          <button class="primary" onclick="window.print()">Print</button>
        </div>

        <div id="message" class="notice"></div>
      </main>
    </div>
  </div>

  <script>
    const checklist = [
      { id: 1, category: "PPE", title: "Hard hats, safety boots, gloves, and high-visibility vests are worn.", result: "", note: "" },
      { id: 2, category: "PPE", title: "Eye, hearing, respiratory, or fall protection is available where required.", result: "", note: "" },
      { id: 3, category: "Work Area", title: "Access routes, walkways, stairs, and ladders are clear and safe.", result: "", note: "" },
      { id: 4, category: "Work Area", title: "Barricades, warning signs, and edge protection are properly installed.", result: "", note: "" },
      { id: 5, category: "Tools", title: "Hand tools and power tools are inspected and in good condition.", result: "", note: "" },
      { id: 6, category: "Electrical Safety", title: "Electrical cords, plugs, and temporary power connections are safe.", result: "", note: "" },
      { id: 7, category: "Equipment", title: "Machinery and equipment pre-start checks are completed.", result: "", note: "" },
      { id: 8, category: "Equipment", title: "Spotters and exclusion zones are assigned for moving equipment.", result: "", note: "" },
      { id: 9, category: "Housekeeping", title: "Materials are stacked safely and waste is removed from the work area.", result: "", note: "" },
      { id: 10, category: "Emergency", title: "First aid kit, fire extinguishers, and emergency contacts are available.", result: "", note: "" },
      { id: 11, category: "Communication", title: "Daily hazards, permits, and work method statements are discussed.", result: "", note: "" },
      { id: 12, category: "Environment", title: "Dust, noise, spills, weather, and environmental risks are controlled.", result: "", note: "" }
    ];

    document.getElementById("date").value = new Date().toISOString().slice(0, 10);

    function renderChecklist() {
      const checklistContainer = document.getElementById("checklist");
      checklistContainer.innerHTML = "";

      checklist.forEach((item, index) => {
        const row = document.createElement("article");
        row.className = "item";

        row.innerHTML = `
          <div class="item-title">
            <strong>${item.title}</strong>
            <span>${item.category}</span>
          </div>

          <div class="result">
            <button class="${item.result === "Pass" ? "active" : ""}" onclick="setResult(${index}, 'Pass')">Pass</button>
            <button class="${item.result === "Fail" ? "active" : ""}" onclick="setResult(${index}, 'Fail')">Fail</button>
            <button class="${item.result === "N/A" ? "active" : ""}" onclick="setResult(${index}, 'N/A')">N/A</button>
          </div>

          <input value="${item.note}" placeholder="Notes or corrective action" oninput="setNote(${index}, this.value)" />
        `;

        checklistContainer.appendChild(row);
      });

      updateSummary();
    }

    function setResult(index, result) {
      checklist[index].result = result;
      renderChecklist();
    }

    function setNote(index, note) {
      checklist[index].note = note;
    }

    function updateSummary() {
      const completed = checklist.filter(item => item.result).length;
      const pass = checklist.filter(item => item.result === "Pass").length;
      const fail = checklist.filter(item => item.result === "Fail").length;
      const na = checklist.filter(item => item.result === "N/A").length;
      const pending = checklist.length - completed;

      document.getElementById("completedCount").textContent = completed;
      document.getElementById("totalCount").textContent = checklist.length;
      document.getElementById("passCount").textContent = pass;
      document.getElementById("failCount").textContent = fail;
      document.getElementById("naCount").textContent = na;
      document.getElementById("pendingCount").textContent = pending;
    }

    function markAllPass() {
      checklist.forEach(item => {
        item.result = "Pass";
      });

      renderChecklist();
      showMessage("All checklist items marked as Pass.");
    }

    function saveChecklist() {
      const data = {
        form: {
          project: document.getElementById("project").value,
          site: document.getElementById("site").value,
          supervisor: document.getElementById("supervisor").value,
          crew: document.getElementById("crew").value,
          date: document.getElementById("date").value,
          shift: document.getElementById("shift").value,
          remarks: document.getElementById("remarks").value
        },
        checklist: checklist
      };

      localStorage.setItem("toolboxChecklist", JSON.stringify(data));
      showMessage("Checklist saved in this browser.");
    }

    function loadChecklist() {
      const saved = localStorage.getItem("toolboxChecklist");

      if (!saved) {
        renderChecklist();
        return;
      }

      const data = JSON.parse(saved);

      document.getElementById("project").value = data.form.project || "";
      document.getElementById("site").value = data.form.site || "";
      document.getElementById("supervisor").value = data.form.supervisor || "";
      document.getElementById("crew").value = data.form.crew || "";
      document.getElementById("date").value = data.form.date || new Date().toISOString().slice(0, 10);
      document.getElementById("shift").value = data.form.shift || "Morning";
      document.getElementById("remarks").value = data.form.remarks || "";

      if (data.checklist) {
        data.checklist.forEach((savedItem, index) => {
          if (checklist[index]) {
            checklist[index].result = savedItem.result || "";
            checklist[index].note = savedItem.note || "";
          }
        });
      }

      renderChecklist();
    }

    function clearChecklist() {
      if (!confirm("Clear the checklist?")) return;

      document.getElementById("project").value = "";
      document.getElementById("site").value = "";
      document.getElementById("supervisor").value = "";
      document.getElementById("crew").value = "";
      document.getElementById("date").value = new Date().toISOString().slice(0, 10);
      document.getElementById("shift").value = "Morning";
      document.getElementById("remarks").value = "";

      checklist.forEach(item => {
        item.result = "";
        item.note = "";
      });

      localStorage.removeItem("toolboxChecklist");
      renderChecklist();
      showMessage("Checklist cleared.");
    }

    function showMessage(text) {
      const message = document.getElementById("message");
      message.textContent = text;
      message.style.display = "block";
    }

    loadChecklist();
  </script>
</body>
</html>
