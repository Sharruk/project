<!DOCTYPE html>
<html>
<body>

<h2>Salon Service System</h2>

<!-- LOGIN -->
<div id="login">
<h3>Login</h3>
Username: <input id="user"><br><br>
Password: <input type="password" id="pass"><br><br>
<button onclick="login()">Login</button>
<p id="msg"></p>
</div>

<!-- SERVICE SELECTION -->
<div id="servicePage" style="display:none;">
<h3>Select Service</h3>

<select id="service">
<option>Car Wash - 200</option>
<option>Oil Service - 500</option>
<option>Full Service - 1000</option>
</select>

<br><br>

Vehicle Type:
<input id="vehicle"><br><br>

<button onclick="book()">Book Appointment</button>
<p id="bookMsg"></p>
</div>

<!-- PAYMENT -->
<div id="paymentPage" style="display:none;">
<h3>Payment</h3>

Amount: <input id="amount"><br><br>

<button onclick="pay()">Pay</button>
<p id="payMsg"></p>
</div>

<!-- STAFF -->
<div id="staffPage" style="display:none;">
<h3>Service Completion (Staff)</h3>

<button onclick="complete()">Mark Completed</button>
<p id="staffMsg"></p>
</div>

<!-- REPORT -->
<div id="reportPage" style="display:none;">
<h3>Management Report</h3>

<button onclick="report()">Generate Report</button>
<p id="rep"></p>
</div>

<script>

// GLOBAL DATA
var totalVehicles = 0;
var totalRevenue = 0;
var lastService = "";

// LOGIN
function login() {
var u = document.getElementById("user").value;
var p = document.getElementById("pass").value;

if(u != "" && p != "") {
document.getElementById("login").style.display = "none";
document.getElementById("servicePage").style.display = "block";
}
else {
document.getElementById("msg").innerHTML = "Invalid Login";
}
}

// BOOKING
function book() {

var s = document.getElementById("service").value;
var v = document.getElementById("vehicle").value;

if(v == "") {
document.getElementById("bookMsg").innerHTML = "Enter vehicle";
return;
}

totalVehicles++;
lastService = s;

var price = Number(s.split("-")[1]);

document.getElementById("amount").value = price;

document.getElementById("bookMsg").innerHTML = "Booking Confirmed";

document.getElementById("paymentPage").style.display = "block";
}

// PAYMENT
function pay() {

var amt = Number(document.getElementById("amount").value);

if(amt <= 0) {
document.getElementById("payMsg").innerHTML = "Invalid Amount";
return;
}

totalRevenue += amt;

document.getElementById("payMsg").innerHTML = "Payment Successful";

document.getElementById("staffPage").style.display = "block";
}

// STAFF UPDATE
function complete() {

document.getElementById("staffMsg").innerHTML = "Service Completed";

document.getElementById("reportPage").style.display = "block";
}

// REPORT
function report() {

document.getElementById("rep").innerHTML =
"Vehicles Serviced: " + totalVehicles + "<br>" +
"Total Revenue: " + totalRevenue;

}

</script>

</body>
</html>
