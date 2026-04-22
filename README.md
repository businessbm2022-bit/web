<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Task Web</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Segoe UI;
}

body{
    background:#0b1220;
    color:#e5e7eb;
}

/* HEADER */
header{
    background:#0f172a;
    padding:20px 40px;
    display:flex;
    justify-content:space-between;
    align-items:center;
    border-bottom:1px solid #1e293b;
}

header h1{
    color:#38bdf8;
}

.info{
    text-align:right;
    font-size:13px;
    color:#94a3b8;
}

/* HERO */
.hero{
    text-align:center;
    padding:30px;
}

.hero h2{
    color:#f8fafc;
    font-size:28px;
}

.hero p{
    color:#94a3b8;
    margin-top:5px;
}

/* SEARCH */
.search-box{
    text-align:center;
    margin:20px;
}

.search-box input{
    padding:10px;
    width:60%;
    border:none;
    border-radius:6px;
    outline:none;
}

/* TABLE */
.container{
    width:92%;
    margin:auto;
}

table{
    width:100%;
    border-collapse:collapse;
    background:#0f172a;
    border-radius:10px;
    overflow:hidden;
}

th{
    background:#1e3a8a;
    padding:12px;
    color:white;
    font-size:13px;
}

td{
    padding:12px;
    text-align:center;
    border-bottom:1px solid #1e293b;
}

tr:hover{
    background:#1e293b;
    cursor:pointer;
    transition:0.3s;
}

/* BADGE */
.badge{
    background:#38bdf8;
    color:#0b1220;
    padding:5px 10px;
    border-radius:6px;
    font-size:12px;
    font-weight:bold;
}

/* POPUP */
.popup{
    position:fixed;
    top:0;left:0;
    width:100%;height:100%;
    background:rgba(0,0,0,0.8);
    display:none;
    justify-content:center;
    align-items:center;
}

.popup-content{
    background:#0f172a;
    padding:20px;
    width:320px;
    border:1px solid #1e293b;
    border-radius:10px;
}

.popup-content h3{
    color:#38bdf8;
}

button{
    margin-top:10px;
    padding:8px 12px;
    background:#38bdf8;
    border:none;
    cursor:pointer;
    border-radius:6px;
}

/* FOOTER */
footer{
    text-align:center;
    padding:20px;
    margin-top:30px;
    color:#64748b;
    border-top:1px solid #1e293b;
}
</style>
</head>

<body>

<header>
    <h1>Task Web</h1>
    <div class="info">
        Bahaa Eldin Mohamed<br>
        1221453
    </div>
</header>

<div class="hero">
    <h2>Well Known Ports Dashboard</h2>
    <p>Service • Protocol • Usage (Dynamic Professional View)</p>
</div>

<div class="search-box">
    <input type="text" id="search" onkeyup="filterTable()" placeholder="Search ports, service, or protocol...">
</div>

<div class="container">
<table id="table">
<tr>
    <th>Port</th>
    <th>Service</th>
    <th>Protocol</th>
    <th>Usage</th>
</tr>

<tr onclick="show('FTP','20/21 used for file transfer between devices')">
<td><span class="badge">20/21</span></td>
<td>FTP</td>
<td>TCP</td>
<td>File Transfer</td>
</tr>

<tr onclick="show('SSH','Secure remote login encrypted connection')">
<td><span class="badge">22</span></td>
<td>SSH</td>
<td>TCP</td>
<td>Secure Access</td>
</tr>

<tr onclick="show('DNS','Converts domain names to IP addresses')">
<td><span class="badge">53</span></td>
<td>DNS</td>
<td>TCP/UDP</td>
<td>Name Resolution</td>
</tr>

<tr onclick="show('HTTP','Used for loading websites (not secure)')">
<td><span class="badge">80</span></td>
<td>HTTP</td>
<td>TCP</td>
<td>Web Browsing</td>
</tr>

<tr onclick="show('HTTPS','Secure encrypted web browsing')">
<td><span class="badge">443</span></td>
<td>HTTPS</td>
<td>TCP</td>
<td>Secure Web</td>
</tr>

</table>
</div>

<!-- POPUP -->
<div class="popup" id="popup">
    <div class="popup-content">
        <h3 id="title"></h3>
        <p id="desc"></p>
        <button onclick="closePopup()">Close</button>
    </div>
</div>

<footer>
© Task Web | Bahaa Eldin Mohamed | 1221453
</footer>

<script>
function show(title, desc){
    document.getElementById("popup").style.display="flex";
    document.getElementById("title").innerText=title;
    document.getElementById("desc").innerText=desc;
}

function closePopup(){
    document.getElementById("popup").style.display="none";
}

/* SEARCH FILTER */
function filterTable(){
    let input = document.getElementById("search").value.toLowerCase();
    let rows = document.querySelectorAll("#table tr");

    rows.forEach((row, index)=>{
        if(index===0) return;
        let text = row.innerText.toLowerCase();
        row.style.display = text.includes(input) ? "" : "none";
    });
}
</script>

</body>
</html>
