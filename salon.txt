<!DOCTYPE html>
<html>
<body>

<h2>Salon Management System</h2>

<!-- LOGIN -->
<div id="login">

<h3>Customer Login</h3>

Username: <input id="user"><br><br>
Password: <input type="password" id="pass"><br><br>

<button onclick="login()">Login</button>

<p id="msg"></p>

</div>


<!-- SERVICE SELECTION -->
<div id="menu" style="display:none;">

<h3>Service Selection</h3>

<select id="service">
<option>Hair Cut - 200</option>
<option>Facial - 500</option>
<option>Hair Color - 800</option>
</select>

<br><br>

Booking Type:
<select id="type">
<option>Walk-in</option>
<option>Home Service</option>
</select>

<br><br>

<button onclick="book()">Book Service</button>

<p id="bookMsg"></p>

</div>


<!-- STAFF UPDATE -->
<div id="staff" style="display:none;">

<h3>Service Execution (Staff)</h3>

<button onclick="complete()">Mark Service Completed</button>

<p id="staffMsg"></p>

</div>


<!-- REPORT -->
<div id="report" style="display:none;">

<h3>Management Report</h3>

<button onclick="showReport()">Generate Report</button>

<p id="rep"></p>

</div>


<script>

var totalCustomers = 0;
var totalRevenue = 0;
var lastService = "";

// LOGIN
function login() {

var u = document.getElementById("user").value;
var p = document.getElementById("pass").value;

if(u != "" && p != "") {

document.getElementById("login").style.display = "none";
document.getElementById("menu").style.display = "block";

}
else {
document.getElementById("msg").innerHTML = "Enter login details";
}

}


// BOOKING
function book() {

var s = document.getElementById("service").value;
var t = document.getElementById("type").value;

totalCustomers++;
lastService = s;

// extract price
var price = Number(s.split("-")[1]);
totalRevenue += price;

document.getElementById("bookMsg").innerHTML =
"Booked: " + s + " (" + t + ")";

document.getElementById("staff").style.display = "block";

}


// STAFF UPDATE
function complete() {

document.getElementById("staffMsg").innerHTML =
"Service Completed: " + lastService;

document.getElementById("report").style.display = "block";

}


// REPORT
function showReport() {

document.getElementById("rep").innerHTML =
"Total Customers: " + totalCustomers + "<br>" +
"Total Revenue: " + totalRevenue;

}

</script>

</body>
</html>
