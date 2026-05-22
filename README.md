<!DOCTYPE html>
<html lang="en">

<head>

  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>RecruitFlow - Interview Scheduler</title>

  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">

  <style>

    *{
      margin:0;
      padding:0;
      box-sizing:border-box;
      font-family:'Inter',sans-serif;
    }

    body{
      background:#f1f5f9;
      color:#1e293b;
    }

    .container{
      display:flex;
      min-height:100vh;
    }

    /* SIDEBAR */

    .sidebar{
      width:260px;
      background:#0f172a;
      color:white;
      padding:25px;
      display:flex;
      flex-direction:column;
    }

    .logo h1{
      font-size:30px;
      font-weight:800;
    }

    .logo p{
      margin-top:8px;
      color:#94a3b8;
      font-size:14px;
    }

    .menu{
      margin-top:40px;
    }

    .menu button{
      width:100%;
      padding:14px;
      border:none;
      border-radius:14px;
      background:transparent;
      color:#cbd5e1;
      margin-bottom:10px;
      text-align:left;
      cursor:pointer;
      transition:0.3s;
      font-size:15px;
      font-weight:500;
    }

    .menu button:hover,
    .menu .active{
      background:#4f46e5;
      color:white;
    }

    /* MAIN */

    .main{
      flex:1;
      padding:30px;
    }

    .topbar{
      background:white;
      padding:25px;
      border-radius:24px;
      display:flex;
      justify-content:space-between;
      align-items:center;
      margin-bottom:30px;
      box-shadow:0 2px 10px rgba(0,0,0,0.05);
      flex-wrap:wrap;
      gap:20px;
    }

    .topbar h2{
      font-size:28px;
      margin-bottom:5px;
    }

    .topbar p{
      color:#64748b;
    }

    .top-actions{
      display:flex;
      gap:12px;
      flex-wrap:wrap;
    }

    .top-actions input{
      padding:12px;
      border-radius:12px;
      border:1px solid #cbd5e1;
      width:250px;
    }

    .primary-btn{
      border:none;
      background:#4f46e5;
      color:white;
      padding:12px 18px;
      border-radius:12px;
      font-weight:600;
      cursor:pointer;
    }

    /* DASHBOARD STATS */

    .stats-grid{
      display:grid;
      grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
      gap:20px;
      margin-bottom:30px;
    }

    .stat-card{
      background:white;
      padding:25px;
      border-radius:24px;
      box-shadow:0 2px 10px rgba(0,0,0,0.05);
    }

    .stat-card p{
      color:#64748b;
      margin-bottom:10px;
      font-size:14px;
      line-height:1.5;
    }

    .stat-card h3{
      font-size:42px;
      color:#0f172a;
    }

    /* TABLE */

    .card{
      background:white;
      border-radius:24px;
      padding:25px;
      box-shadow:0 2px 10px rgba(0,0,0,0.05);
      overflow:auto;
    }

    table{
      width:100%;
      border-collapse:collapse;
    }

    table th,
    table td{
      padding:16px;
      text-align:left;
      border-bottom:1px solid #e2e8f0;
    }

    table th{
      color:#64748b;
      font-size:14px;
    }

    .status{
      padding:6px 12px;
      border-radius:20px;
      font-size:12px;
      font-weight:600;
    }

    .pending{
      background:#fef9c3;
      color:#a16207;
    }

    .manager{
      background:#dbeafe;
      color:#1d4ed8;
    }

    .hr{
      background:#ede9fe;
      color:#6d28d9;
    }

    .offered{
      background:#dcfce7;
      color:#166534;
    }

    .rejected{
      background:#fee2e2;
      color:#b91c1c;
    }

    .action-btn{
      padding:10px 14px;
      border:none;
      border-radius:10px;
      cursor:pointer;
      font-size:13px;
      margin-right:8px;
      font-weight:600;
    }

    .schedule-btn{
      background:#eef2ff;
      color:#4f46e5;
    }

    .details-btn{
      background:#f1f5f9;
    }

    /* MODALS */

    .modal-overlay{
      display:none;
      position:fixed;
      inset:0;
      background:rgba(0,0,0,0.5);
      z-index:999;
      align-items:center;
      justify-content:center;
      overflow-y:auto;
      padding:20px;
    }

    .modal{
      background:white;
      width:90%;
      max-width:550px;
      border-radius:24px;
      padding:30px;
      max-height:90vh;
      overflow-y:auto;
    }

    .modal h2{
      margin-bottom:20px;
    }

    .form-group{
      margin-bottom:18px;
    }

    .form-group label{
      display:block;
      margin-bottom:8px;
      font-size:14px;
      font-weight:600;
    }

    .form-group input,
    .form-group select{
      width:100%;
      padding:12px;
      border-radius:12px;
      border:1px solid #cbd5e1;
    }

    .modal-actions{
      display:flex;
      gap:12px;
      margin-top:20px;
    }

    .secondary-btn{
      flex:1;
      padding:12px;
      border:none;
      border-radius:12px;
      background:#e2e8f0;
      cursor:pointer;
      font-weight:600;
    }

    @media(max-width:1000px){

      .sidebar{
        display:none;
      }

    }

  </style>

</head>

<body>

<div class="container">

  <!-- SIDEBAR -->

  <aside class="sidebar">

    <div class="logo">
      <h1>RecruitFlow</h1>
      <p>Interview Scheduling Platform</p>
    </div>

    <div class="menu">
      <button class="active">Dashboard</button>
      <button>Candidates</button>
      <button>Interview Calendar</button>
      <button>Reports</button>
      <button>Settings</button>
    </div>

  </aside>

  <!-- MAIN -->

  <main class="main">

    <!-- TOPBAR -->

    <div class="topbar">

      <div>
        <h2>Interview Scheduler Dashboard</h2>
        <p>Manage recruiter operations and candidate interviews</p>
      </div>

      <div class="top-actions">

        <input type="text" placeholder="Search candidates...">

        <button class="primary-btn"
                onclick="openCandidateModal()">

          + Add New Candidate

        </button>

      </div>

    </div>

    <!-- DASHBOARD STATS -->

    <div class="stats-grid">

      <div class="stat-card">
        <p>No. of Interviews Scheduled</p>
        <h3>148</h3>
      </div>

      <div class="stat-card">
        <p>No. of Candidates at Manager Stage</p>
        <h3>32</h3>
      </div>

      <div class="stat-card">
        <p>No. of Rejects at Manager Stage</p>
        <h3>7</h3>
      </div>

      <div class="stat-card">
        <p>No. of Candidates at HR Stage</p>
        <h3>18</h3>
      </div>

      <div class="stat-card">
        <p>No. of Candidates Offered</p>
        <h3>11</h3>
      </div>

    </div>

    <!-- TABLE -->

    <div class="card">

      <table>

        <thead>

          <tr>
            <th>Candidate</th>
            <th>Skill Set</th>
            <th>Mobile</th>
            <th>Location</th>
            <th>Status</th>
            <th>Actions</th>
          </tr>

        </thead>

        <tbody id="candidateTableBody">

          <tr>

            <td>Rahul Sharma</td>
            <td>Java, Spring Boot</td>
            <td>+91 9876543210</td>
            <td>Hyderabad</td>

            <td>
              <span class="status manager">
                Manager Stage
              </span>
            </td>

            <td>

              <button
                class="action-btn schedule-btn"
                onclick="openScheduleModal('Rahul Sharma')">

                Schedule Interview

              </button>

              <button class="action-btn details-btn">
                Details
              </button>

            </td>

          </tr>

          <tr>

            <td>Anjali Verma</td>
            <td>React, JavaScript</td>
            <td>+91 9988776655</td>
            <td>Bangalore</td>

            <td>
              <span class="status hr">
                HR Stage
              </span>
            </td>

            <td>

              <button
                class="action-btn schedule-btn"
                onclick="openScheduleModal('Anjali Verma')">

                Schedule Interview

              </button>

              <button class="action-btn details-btn">
                Details
              </button>

            </td>

          </tr>

          <tr>

            <td>Kiran Kumar</td>
            <td>AWS, Kubernetes</td>
            <td>+91 9876501234</td>
            <td>Pune</td>

            <td>
              <span class="status offered">
                Offered
              </span>
            </td>

            <td>

              <button
                class="action-btn schedule-btn"
                onclick="openScheduleModal('Kiran Kumar')">

                Schedule Interview

              </button>

              <button class="action-btn details-btn">
                Details
              </button>

            </td>

          </tr>

          <tr>

            <td>Vikas Singh</td>
            <td>Python, Django</td>
            <td>+91 9123456789</td>
            <td>Chennai</td>

            <td>
              <span class="status rejected">
                Rejected at Manager Stage
              </span>
            </td>

            <td>

              <button class="action-btn details-btn">
                Details
              </button>

            </td>

          </tr>

        </tbody>

      </table>

    </div>

  </main>

</div>

<!-- ADD CANDIDATE MODAL -->

<div class="modal-overlay" id="candidateModal">

  <div class="modal">

    <h2>Add New Candidate</h2>

    <div class="form-group">
      <label>Candidate Name</label>
      <input type="text" id="candidateName">
    </div>

    <div class="form-group">
      <label>Email Address</label>
      <input type="email" id="candidateEmail">
    </div>

    <div class="form-group">
      <label>Mobile Number</label>
      <input type="tel" id="candidateMobile">
    </div>

    <div class="form-group">
      <label>Skill Set</label>
      <input type="text" id="candidateSkill">
    </div>

    <div class="form-group">
      <label>Location</label>
      <input type="text" id="candidateLocation">
    </div>

    <div class="modal-actions">

      <button class="primary-btn"
              style="flex:1"
              onclick="addCandidate()">

        Save Candidate

      </button>

      <button class="secondary-btn"
              onclick="closeCandidateModal()">

        Cancel

      </button>

    </div>

  </div>

</div>

<!-- SCHEDULE INTERVIEW MODAL -->

<div class="modal-overlay" id="scheduleModal">

  <div class="modal">

    <h2>Schedule Interview</h2>

    <div class="form-group">

      <label>Candidate Name</label>

      <input type="text"
             id="scheduledCandidate"
             readonly>

    </div>

    <div class="form-group">

      <label>Interview Round</label>

      <select id="interviewRound">

        <option value="">Select Interview Round</option>

        <option>Technical Interview - 1</option>
        <option>Technical Interview - 2</option>
        <option>Manager Interview</option>
        <option>HR Interview</option>

      </select>

    </div>

    <div class="form-group">

      <label>Interview Date</label>

      <input type="date"
             id="interviewDate">

    </div>

    <div class="form-group">

      <label>Interview Time</label>

      <input type="time"
             id="interviewTime">

    </div>

    <div class="form-group">

      <label>Interviewer Email ID</label>

      <input
        type="email"
        id="interviewerEmail"
        placeholder="Enter interviewer email address"
      >

    </div>

    <div class="form-group">

      <label>Interview Mode</label>

      <select id="interviewMode">

        <option>Virtual</option>
        <option>In-Person</option>

      </select>

    </div>

    <div class="modal-actions">

      <button class="primary-btn"
              style="flex:1"
              onclick="confirmInterviewSchedule()">

        Confirm Schedule

      </button>

      <button class="secondary-btn"
              onclick="closeScheduleModal()">

        Cancel

      </button>

    </div>

  </div>

</div>

<script>

  /* ADD CANDIDATE */

  function openCandidateModal(){

    document.getElementById('candidateModal').style.display='flex';

  }

  function closeCandidateModal(){

    document.getElementById('candidateModal').style.display='none';

  }

  function addCandidate(){

    const name =
      document.getElementById('candidateName').value;

    const email =
      document.getElementById('candidateEmail').value;

    const mobile =
      document.getElementById('candidateMobile').value;

    const skill =
      document.getElementById('candidateSkill').value;

    const location =
      document.getElementById('candidateLocation').value;

    if(
      name === '' ||
      email === '' ||
      mobile === '' ||
      skill === '' ||
      location === ''
    ){

      alert('Please fill all candidate details');

      return;
    }

    const table =
      document.getElementById('candidateTableBody');

    const row =
      document.createElement('tr');

    row.innerHTML = `

      <td>${name}</td>
      <td>${skill}</td>
      <td>${mobile}</td>
      <td>${location}</td>

      <td>
        <span class="status pending">
          Pending
        </span>
      </td>

      <td>

        <button
          class="action-btn schedule-btn"
          onclick="openScheduleModal('${name}')">

          Schedule Interview

        </button>

        <button class="action-btn details-btn">
          Details
        </button>

      </td>
    `;

    table.prepend(row);

    closeCandidateModal();

    document.getElementById('candidateName').value='';
    document.getElementById('candidateEmail').value='';
    document.getElementById('candidateMobile').value='';
    document.getElementById('candidateSkill').value='';
    document.getElementById('candidateLocation').value='';

  }

  /* SCHEDULE INTERVIEW */

  function openScheduleModal(candidateName){

    document.getElementById('scheduleModal').style.display='flex';

    document.getElementById('scheduledCandidate').value =
      candidateName;

  }

  function closeScheduleModal(){

    document.getElementById('scheduleModal').style.display='none';

  }

  function confirmInterviewSchedule(){

    const candidate =
      document.getElementById('scheduledCandidate').value;

    const round =
      document.getElementById('interviewRound').value;

    const date =
      document.getElementById('interviewDate').value;

    const time =
      document.getElementById('interviewTime').value;

    const interviewerEmail =
      document.getElementById('interviewerEmail').value;

    const mode =
      document.getElementById('interviewMode').value;

    if(
      round === '' ||
      date === '' ||
      time === '' ||
      interviewerEmail === ''
    ){

      alert('Please fill all interview details');

      return;
    }

    const emailPattern =
      /^[^ ]+@[^ ]+\.[a-z]{2,}$/;

    if(!interviewerEmail.match(emailPattern)){

      alert('Please enter valid interviewer email');

      return;
    }

    alert(
`Interview Scheduled Successfully

Candidate: ${candidate}
Interview Round: ${round}
Date: ${date}
Time: ${time}
Mode: ${mode}
Interviewer Email: ${interviewerEmail}`
    );

    closeScheduleModal();

    document.getElementById('interviewRound').selectedIndex=0;
    document.getElementById('interviewDate').value='';
    document.getElementById('interviewTime').value='';
    document.getElementById('interviewerEmail').value='';
    document.getElementById('interviewMode').selectedIndex=0;

  }

</script>

</body>
</html>
