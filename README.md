<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Coin Income System</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial,sans-serif;
}

body{
    background:#0f172a;
    color:white;
}

/* Header */
header{
    background:linear-gradient(90deg,#2563eb,#7c3aed);
    padding:25px;
    text-align:center;
    box-shadow:0 5px 15px rgba(0,0,0,0.4);
}

header h1{
    font-size:35px;
}

header p{
    margin-top:8px;
    color:#e2e8f0;
}

/* Dashboard */
.dashboard{
    max-width:900px;
    margin:30px auto;
    padding:20px;
}

.balance-box{
    background:#1e293b;
    padding:25px;
    border-radius:20px;
    text-align:center;
    margin-bottom:30px;
    box-shadow:0 8px 20px rgba(0,0,0,0.4);
}

.balance-box h2{
    color:#facc15;
    font-size:40px;
    margin-top:10px;
}

.balance-box p{
    color:#cbd5e1;
}

/* Cards */
.cards{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
    gap:25px;
}

.card{
    background:#1e293b;
    padding:25px;
    border-radius:20px;
    text-align:center;
    transition:0.3s;
    box-shadow:0 8px 20px rgba(0,0,0,0.4);
}

.card:hover{
    transform:translateY(-8px);
}

.coin{
    font-size:60px;
    margin-bottom:15px;
}

.card h3{
    font-size:26px;
    color:#facc15;
}

.card p{
    color:#cbd5e1;
    margin:10px 0 20px;
}

.btn{
    display:inline-block;
    padding:14px 28px;
    background:linear-gradient(90deg,#22c55e,#16a34a);
    color:white;
    border:none;
    border-radius:12px;
    font-size:18px;
    cursor:pointer;
    text-decoration:none;
    transition:0.3s;
}

.btn:hover{
    opacity:0.9;
}

/* Withdraw */
.withdraw{
    margin-top:40px;
    background:#1e293b;
    padding:30px;
    border-radius:20px;
    box-shadow:0 8px 20px rgba(0,0,0,0.4);
}

.withdraw h2{
    text-align:center;
    color:#facc15;
    margin-bottom:20px;
}

input, select{
    width:100%;
    padding:14px;
    margin-bottom:15px;
    border:none;
    border-radius:10px;
    background:#334155;
    color:white;
    font-size:16px;
}

.withdraw-btn{
    width:100%;
    padding:15px;
    background:linear-gradient(90deg,#2563eb,#3b82f6);
    color:white;
    border:none;
    border-radius:12px;
    font-size:18px;
    cursor:pointer;
    font-weight:bold;
}

/* Footer */
footer{
    text-align:center;
    padding:25px;
    margin-top:40px;
    background:#111827;
    color:#94a3b8;
}
</style>
</head>

<body>

<header>
    <h1>💰 Coin Income Platform</h1>
    <p>১ কয়েন = ১ টাকা | ১০০০ কয়েন হলে উইথড্র</p>
</header>

<section class="dashboard">

    <!-- Balance -->
    <div class="balance-box">
        <p>আপনার মোট কয়েন</p>
        <h2 id="coinBalance">0</h2>
        <p>১ কয়েন = ১ টাকা</p>
    </div>

    <!-- Link Cards -->
    <div class="cards">

        <div class="card">
            <div class="coin">🪙</div>
            <h3>Income Link 1</h3>
            <p>ক্লিক করলে ১ কয়েন যোগ হবে</p>

            <button class="btn"
            onclick="earnCoin('https://instantshort.info/EoXZLD')">
            Earn Coin
            </button>
        </div>

        <div class="card">
            <div class="coin">💎</div>
            <h3>Income Link 2</h3>
            <p>ক্লিক করলে ১ কয়েন যোগ হবে</p>

            <button class="btn"
            onclick="earnCoin('https://instantshort.info/1oJwlg')">
            Earn Coin
            </button>
        </div>

        <div class="card">
            <div class="coin">🔥</div>
            <h3>Income Link 3</h3>
            <p>ক্লিক করলে ১ কয়েন যোগ হবে</p>

            <button class="btn"
            onclick="earnCoin('https://instantshort.info/p99SVY')">
            Earn Coin
            </button>
        </div>

    </div>

    <!-- Withdraw -->
    <div class="withdraw">
        <h2>💳 Withdraw Request</h2>

        <input type="text" id="name" placeholder="আপনার নাম">

        <select id="method">
            <option>bKash</option>
            <option>Nagad</option>
            <option>Rocket</option>
        </select>

        <input type="text" id="number" placeholder="মোবাইল নম্বর">

        <button class="withdraw-btn" onclick="withdrawMoney()">
            Withdraw Now
        </button>
    </div>

</section>

<footer>
    © 2026 Coin Income Platform | All Rights Reserved
</footer>

<script>

let coins = localStorage.getItem("coins")
? parseInt(localStorage.getItem("coins"))
: 0;

document.getElementById("coinBalance").innerText = coins;

/* Earn Coin */
function earnCoin(link){

    coins += 1;

    localStorage.setItem("coins", coins);

    document.getElementById("coinBalance").innerText = coins;

    window.open(link, "_blank");
}

/* Withdraw */
function withdrawMoney(){

    const name = document.getElementById("name").value;
    const method = document.getElementById("method").value;
    const number = document.getElementById("number").value;

    if(coins < 1000){
        alert("❌ Withdraw করতে কমপক্ষে 1000 Coins লাগবে!");
        return;
    }

    if(name === "" || number === ""){
        alert("⚠️ সব তথ্য পূরণ করুন!");
        return;
    }

    alert(
        "✅ Withdraw Request Submitted!\n\n" +
        "Name: " + name +
        "\nMethod: " + method +
        "\nNumber: " + number +
        "\nCoins: " + coins
    );

    coins = 0;

    localStorage.setItem("coins", coins);

    document.getElementById("coinBalance").innerText = coins;
}

</script>

</body>
</html>
