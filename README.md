<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Advanced Boyfriend Booking Platform</title>
<meta name="description" content="Advanced Online Boyfriend Booking Platform – Chat, Call, Virtual Date. 18+ Entertainment only.">
<style>
:root{--bg:#f4f6fb;--card:#fff;--text:#111;--accent:#ff4d6d}
body.dark{--bg:#0e0e14;--card:#1b1b24;--text:#fff;--accent:#ff7a9c}
body{margin:0;font-family:Arial;background:var(--bg);color:var(--text);transition:.3s}
header{background:linear-gradient(135deg,#ff4d6d,#ff8fa3);color:#fff;padding:50px 20px;text-align:center}
section{max-width:1150px;margin:auto;padding:20px}
.card{background:var(--card);border-radius:16px;padding:20px;margin-bottom:25px;box-shadow:0 6px 15px rgba(0,0,0,.15)}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:18px}
.profile{text-align:center;border:1px solid #ddd;border-radius:14px;padding:12px}
.profile img{width:100%;border-radius:14px}
button{background:var(--accent);color:#fff;border:none;padding:12px 18px;border-radius:10px;cursor:pointer;font-size:15px}
button:hover{opacity:.9}
input,select{width:100%;padding:12px;margin:8px 0;border-radius:8px;border:1px solid #ccc}
footer{background:#111;color:#fff;text-align:center;padding:25px}
.toggle{position:fixed;top:15px;right:15px}
.lang{position:fixed;top:15px;left:15px}
.badge{background:#0a0;color:#fff;padding:4px 10px;border-radius:8px;font-size:12px}
.faq h4{margin-bottom:5px}
</style>
</head>
<body>
<button class="toggle" onclick="toggleDark()">🌙</button>
<select class="lang" onchange="changeLang(this.value)">
<option value="en">EN</option>
<option value="bn">BN</option>
</select>
<header>
<h1 id="heroTitle">💖 Find Your Virtual Companion</h1>
<p id="heroSub">Safe • Private • Entertainment Only</p>
<button onclick="scrollToBook()">Book Now</button>
</header>
<section>
<div class="card">
<h2>💰 Pricing</h2>
<p><b>Chat:</b> ₹199 | <b>Call / Virtual Date:</b> ₹499</p>
</div>
<div class="card">
<h2>👨 Available Profiles</h2>
<div class="grid">
<div class="profile"><img src="https://via.placeholder.com/300"><h3>Rahul</h3><p>Romantic • Bengali</p><span class="badge">⭐ 4.8</span><br><button onclick="selectBoy('Rahul')">Book</button></div>
<div class="profile"><img src="https://via.placeholder.com/300"><h3>Amit</h3><p>Funny • Hindi</p><span class="badge">⭐ 4.7</span><br><button onclick="selectBoy('Amit')">Book</button></div>
<div class="profile"><img src="https://via.placeholder.com/300"><h3>Arjun</h3><p>Supportive • English</p><span class="badge">⭐ 4.9</span><br><button onclick="selectBoy('Arjun')">Book</button></div>
</div>
</div>
<div class="card" id="book">
<h2>📅 Book Your Slot</h2>
<form id="bookForm">
<input id="name" placeholder="Your Name" required>
<input id="email" type="email" placeholder="Email" required>
<input id="boy" placeholder="Selected Profile" readonly required>
<select id="plan"><option value="Chat ₹199">Chat ₹199</option><option value="Call/Date ₹499">Call / Virtual Date ₹499</option></select>
<input type="date" id="date" required>
<input type="time" id="time" required>
<label><input type="checkbox" required> I am 18+ & agree to terms</label>
<button type="submit">Confirm & Pay</button>
<p class="small">(Payment gateway will open here)</p>
</form>
</div>
<div class="card">
<h2>⭐ Reviews</h2>
<p>“Very respectful & caring” – User A</p>
<p>“Amazing experience ❤️” – User B</p>
</div>
<div class="card faq">
<h2>❓ FAQ</h2>
<h4>Is this real dating?</h4><p>No, entertainment only.</p>
<h4>Is my data safe?</h4><p>Yes, never shared.</p>
<h4>Refund?</h4><p>No refund after booking.</p>
</div>
<div class="card">
<h2>📄 Legal</h2>
<p>Entertainment purpose only. No emotional dependency. 18+ users only.</p>
</div>
</section>
<footer>
<p>© 2026 Advanced Boyfriend Booking Platform</p>
</footer>
<script>
var whatsappNumber='919832002852';
function selectBoy(n){boy.value=n;scrollToBook()}
function scrollToBook(){document.getElementById('book').scrollIntoView({behavior:'smooth'})}
document.getElementById('bookForm').addEventListener('submit',function(e){
e.preventDefault();
var msg=`New Booking%0AName:${name.value}%0ABoy:${boy.value}%0APlan:${plan.value}%0ADate:${date.value}%0ATime:${time.value}`;
window.open(`https://wa.me/${whatsappNumber}?text=${msg}`,'_blank');
window.location=`mailto:${email.value}?subject=Booking Confirmation&body=Your booking request received.`;
});
function toggleDark(){document.body.classList.toggle('dark')}
function changeLang(l){if(l==='bn'){heroTitle.innerText='💖 আপনার ভার্চুয়াল সঙ্গী খুঁজুন';heroSub.innerText='নিরাপদ • ব্যক্তিগত • বিনোদনের জন্য';}else{heroTitle.innerText='💖 Find Your Virtual Companion';heroSub.innerText='Safe • Private • Entertainment Only';}}
</script>
</body>
</html>

<!-- ================= BACKEND SETUP GUIDE =================
OPTION A SELECTED: Backend + Payment + Admin

STACK:
- Node.js + Express
- Razorpay Payment Gateway
- MongoDB (or JSON for demo)

FILES YOU NEED:
1) server.js
2) admin.html
3) .env

---------------- server.js ----------------
const express = require('express');
const Razorpay = require('razorpay');
const bodyParser = require('body-parser');
const fs = require('fs');
const app = express();
app.use(bodyParser.json());
app.use(express.static('public'));

const razorpay = new Razorpay({
  key_id: process.env.RAZORPAY_KEY,
  key_secret: process.env.RAZORPAY_SECRET
});

app.post('/create-order', async (req,res)=>{
  const options = {
    amount: req.body.amount * 100,
    currency: 'INR',
    receipt: 'booking_'+Date.now()
  };
  const order = await razorpay.orders.create(options);
  res.json(order);
});

app.post('/save-booking',(req,res)=>{
  const data = JSON.stringify(req.body)+"
";
  fs.appendFileSync('bookings.txt',data);
  res.json({status:'saved'});
});

app.get('/admin-data',(req,res)=>{
  const data = fs.readFileSync('bookings.txt','utf-8');
  res.send(data);
});

app.listen(3000,()=>console.log('Server running'));

---------------- admin.html ----------------
<h2>Admin Panel</h2>
<button onclick="load()">Load Bookings</button>
<pre id="data"></pre>
<script>
function load(){fetch('/admin-data').then(r=>r.text()).then(d=>data.innerText=d)}
</script>

---------------- .env ----------------
RAZORPAY_KEY=your_key_here
RAZORPAY_SECRET=your_secret_here

HOW TO RUN:
1) Install Node.js
2) npm install express razorpay body-parser dotenv
3) node server.js
4) Deploy on Render / Railway / VPS

=========================================================== -->
