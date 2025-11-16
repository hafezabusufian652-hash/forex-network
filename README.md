<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>The Forex Network</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
<style>
/* Design kept as requested */
body { margin:0; padding:0; font-family:'Poppins',sans-serif; background: linear-gradient(200deg,#ff5f6d,#ffc371); color:#333; display:flex; justify-content:center; align-items:flex-start; min-height:100vh; overflow-y:auto; scroll-behavior:smooth;}
.container { width:100%; max-width:520px; background:rgba(255,255,255,0.96); border-radius:18px; box-shadow:0 8px 50px rgba(0,0,0,0.15); padding:26px 20px 140px 20px; backdrop-filter:blur(8px); margin:60px auto 80px auto; position:relative;}
/* Floating Logo - Control visibility */
.floating-logo-wrap { 
    position:fixed; 
    top:8px; 
    left:50%; 
    transform:translateX(-50%); 
    z-index:1000;
    text-align: center;
}
.floating-logo { 
    background:white; 
    border-radius:50%; 
    box-shadow:0 4px 15px rgba(0,0,0,0.18); 
    padding:8px; 
    display: inline-block;
}
.floating-logo img { width:70px; height:70px; border-radius:50%; object-fit:cover; }

/* H1 Header Adjusted for spacing - Control visibility */
h1 { 
    font-size:24px; 
    background: linear-gradient(90deg,#ff5f6d,#ffc371); 
    -webkit-background-clip:text; 
    color:transparent; 
    margin-bottom:6px; 
    text-align:center;
    margin-top: 50px; /* লোগোর নিচে নামানোর জন্য */
}
.topbar { display:flex; justify-content:space-between; align-items:center; gap:10px; margin-bottom:12px; }
.user-head { display:flex; align-items:center; gap:12px; }
.user-pic { width:56px; height:56px; border-radius:50%; overflow:hidden; box-shadow:0 3px 10px rgba(0,0,0,0.08); }
.user-pic img { width:100%; height:100%; object-fit:cover; display:block; }
.small-menu { display:none; }
.hidden { display:none; }
input,select,button,textarea { width:100%; padding:10px; margin:8px 0; border-radius:12px; border:1px solid #ccc; box-sizing:border-box; font-size:15px; }
input:focus, select:focus, textarea:focus { border-color:#e65100; box-shadow:0 0 6px rgba(230,81,0,0.18); outline:none; }
.balance-card { background: linear-gradient(90deg,#ff5f6d,#ffc371); padding:14px; border-radius:14px; text-align:center; font-size:18px; font-weight:700; color:#fff; margin:10px 0 10px; }
.notice-card { background:linear-gradient(90deg,#ff5f6d,#ffc371); padding:12px; border-radius:12px; margin-bottom:12px; color:white; font-weight:600; }
.task, .trans { border:1px solid #eee; padding:12px; border-radius:12px; background:#fff8e6; margin:10px 0; }
.task:hover, .trans:hover { background:#fff6e0; }
table { width:100%; border-collapse:collapse; font-size:14px; background:#fff; border-radius:10px; overflow:hidden; margin:10px 0; }
th, td { padding:8px; text-align:left; border-bottom:1px solid #f2f2f2; }
th { background:#ff5f6d; color:white; font-weight:700; }
tr:nth-child(even){ background:#fafafa; }
.action-btn { display:inline-block; margin:2px; padding:6px 10px; border:none; border-radius:8px; color:#fff; font-size:13px; font-weight:600; cursor:pointer; }
.approve { background:#4caf50; }
.reject { background:#e53935; }
.block, .unblock { background:#4caf50; }
.delete { background:#ff5252; }
.card { background:rgba(255,255,255,0.96); padding:14px; border-radius:12px; box-shadow:0 3px 10px rgba(0,0,0,0.06); margin-bottom:12px; }
#helpList, #adminHelpList { max-height:260px; overflow-y:auto; }
#signupDiv button{ background: linear-gradient(90deg,#ff416c,#ff4b2b); color:white; font-weight:700; border:none; padding:12px; border-radius:12px; }
#loginDiv button{ background: linear-gradient(90deg,#ff6a88,#ff4b2b); color:white; font-weight:700; border:none; padding:12px; border-radius:12px; }
@media(max-width:760px){ .small-menu button{ padding:8px; } .container{ padding:18px 16px 160px 16px; } h1{font-size:20px;} }
.small { font-size:13px; color:#555; }
.status-pill { display:inline-block; padding:6px 8px; border-radius:999px; font-weight:700; font-size:12px; color:#fff; }
.status-pending { background:#ffb74d; }
.status-approved { background:#4caf50; }
.status-rejected { background:#e53935; }
.muted { color:#666; font-size:13px; }
a { color: #d84315; text-decoration: none; font-weight:700; }
/* Bottom nav */
.bottom-nav { 
    position:fixed; 
    left:50%; 
    transform:translateX(-50%); 
    bottom:0; 
    width:100%; 
    max-width:520px; 
    display:flex; 
    justify-content:space-around; 
    gap:4px; 
    padding:8px 0; 
    background:rgba(255,255,255,0.96); 
    backdrop-filter:blur(8px); 
    box-shadow:0 -4px 20px rgba(0,0,0,0.08); 
    z-index:1200; 
}
.nav-btn { flex:1; margin:0 4px; padding:10px 6px; border-radius:12px; border:none; background:transparent; display:flex; flex-direction:column; align-items:center; justify-content:center; font-weight:600; cursor:pointer; font-size:14px; color:#666; transition:color 0.2s; }
.nav-btn span { font-size: 22px; margin-bottom: 2px; }
.nav-active { color:#ff5f6d; background:rgba(255,95,109,0.1); }
.nav-active span { color:#ff5f6d; }
.center-space { display:none; }
.action-grid { display:grid; grid-template-columns:repeat(3, 1fr); gap:10px; margin-top:10px; }
.action-grid button { padding:12px 8px; border-radius:10px; border:none; background:linear-gradient(90deg,#ff5f6d10,#ffc37110); box-shadow:0 3px 10px rgba(0,0,0,0.06); font-weight:700; cursor:pointer; color:#d84315; }
.action-grid button span { display:block; font-size:20px; margin-bottom:4px; }
.right-small { display:none; }

/* FIX: লগআউট বাটন ও ইউজার হেডের জন্য নতুন ফ্লেক্স কন্টেইনার */
#userHeaderContainer {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 12px;
}
#logoutBtnWrap {
    text-align: right;
    margin-left: 10px;
}
/* Updated Income Card Grid for 3 items */
#incomeGrid {
    display:grid;
    grid-template-columns: repeat(3, 1fr); /* 3 কলামে ভাগ করা হলো */
    gap: 10px;
    padding: 14px;
    border-radius: 12px;
    box-shadow:0 3px 10px rgba(0,0,0,0.06);
    background:rgba(255,255,255,0.96);
    margin-bottom: 12px;
    text-align: center;
}
#incomeGrid > div {
    padding: 8px 4px;
    border-radius: 8px;
    background: #f7f7f7; 
}
#incomeGrid .income-label {
    font-size: 11px;
    color: #555;
    font-weight: 600;
}
#incomeGrid .income-amount {
    font-size: 16px;
    font-weight: 800;
    color: #d84315; /* Matching the action button color */
}
/* Deposit Amount Options CSS */
#depositAmountOptions {
    display: flex;
    gap: 10px;
    margin-bottom: 10px;
}
#depositAmountOptions button {
    flex: 1;
    padding: 10px;
    border: 2px solid #ff5f6d;
    background: #fff0f0;
    color: #ff5f6d;
    font-weight: 700;
    border-radius: 10px;
    cursor: pointer;
    transition: background 0.2s;
}
#depositAmountOptions button.selected {
    background: #ff5f6d;
    color: white;
}
/* Transaction History Style */
#transactionHistoryDetails .card {
    padding: 10px;
}

/* Home Action Grid for 4 buttons */
#homeActionGrid {
    display:grid; 
    grid-template-columns:repeat(2, 1fr); 
    gap:10px; 
    margin-top:10px;
}
#homeActionGrid button {
    padding:20px 8px; 
    border-radius:12px; 
    border:none; 
    background:linear-gradient(90deg,#ff5f6d10,#ffc37110); 
    box-shadow:0 3px 10px rgba(0,0,0,0.06); 
    font-weight:700; 
    cursor:pointer; 
    color:#d84315; 
}
#homeActionGrid button span { 
    display:block; 
    font-size:24px; 
    margin-bottom:4px; 
}

/* Back button style */
.back-btn {
    background: #ff5f6d;
    color: white;
    padding: 8px 12px;
    border: none;
    border-radius: 8px;
    font-weight: 600;
    margin-bottom: 15px;
    display: inline-block;
}
/* Wallet Income History Button */
#showIncomeHistoryBtn {
    width: 100%;
    padding: 12px;
    border: none;
    border-radius: 12px;
    background: linear-gradient(90deg,#f0f4c3,#e1e9a3); 
    color: #555;
    font-weight: 700;
    margin-top: 10px;
    box-shadow: 0 2px 5px rgba(0,0,0,0.05);
}

</style>

</head>
<body>
    <div class="floating-logo-wrap" id="logoWrap">
        <div class="floating-logo"><img src="logo.png" id="platformLogo" alt="Logo"></div>
    </div>

    <div class="container" id="mainContainer">
        
        <h1 id="websiteTitle">The Forex Network</h1>

        <div id="authDiv">
            <div id="signupDiv">
                <h2>Sign Up</h2>
                <input id="signupName" placeholder="Full name" />
                <input id="signupPhone" placeholder="Phone number" />
                <input id="signupPass" type="password" placeholder="Password" />
                <input id="signupRefCode" placeholder="Referral code (optional)" />
                <button onclick="signup()">Sign Up</button>
                <p class="muted">Already have an account? <a href="#" onclick="showLogin()">Login</a></p>
            </div>

            <div id="loginDiv" class="hidden">
                <h3>Login</h3>
                <input id="loginPhone" placeholder="Phone number" />
                <input id="loginPass" type="password" placeholder="Password" />
                <button onclick="login()">Login</button>
                <p class="muted">Don't have an account? <a href="#" onclick="showSignup()">Sign Up</a></p>
            </div>
        </div>

        <div id="userDashboard" class="hidden">
            
            <div id="userHeaderContainer">
                <div class="user-head">
                    <div class="user-pic" id="headerPicWrap"><img id="headerPic" src="logo.png" alt="pic"></div>
                    <div>
                        <div style="font-weight:800" id="userName">User</div>
                        <div class="small muted" id="userPhoneDisplay"></div>
                    </div>
                </div>

                <div id="logoutBtnWrap">
                    <button id="logoutBtn" style="background:linear-gradient(90deg,#ff5f6d,#ffc371);color:#fff;padding:8px 12px;border-radius:8px;border:none;font-weight:600;" onclick="logout()">Logout</button>
                </div>
            </div>


            <div id="coverPicCard" class="card" style="padding:0; overflow:hidden; margin-bottom:12px;">
                <img id="websiteCoverPic" src="default_cover.jpg" alt="Website Cover" style="width:100%; height:100px; object-fit:cover; display:block;">
            </div>

            <div id="userNotice" class="notice-card hidden"></div>

            <div id="home">
                <div class="card">
                    <h4>Quick Access</h4>
                    <div class="action-grid">
                        <button onclick="showSection('plans')"><span>📜</span> My Plan</button>
                        <button onclick="showSection('tasks')"><span>⚒️</span> My Work</button>
                        <button onclick="showSection('refer')"><span>👥</span> My Team</button>
                    </div>
                </div>

                <div class="card">
                    <h4>Wallet & History</h4>
                    <div id="homeActionGrid">
                        <button onclick="showSection('depositSection')"><span>📥</span> Deposit Now</button>
                        <button onclick="showSection('withdrawSection')"><span>📤</span> Withdraw Now</button>
                        <button onclick="showSection('depositHistorySection')"><span>🧾</span> Deposit History</button>
                        <button onclick="showSection('withdrawHistorySection')"><span>💵</span> Withdraw History</button>
                        </div>
                </div>
            </div>

            <div id="depositSection" class="hidden">
                <button onclick="goHome()" class="back-btn">← Back to Home</button>
                <h2>Deposit</h2>
                <div class="card">
                    <h4 class="small">Mobile: Bkash / Nagad number: <b>01734625071</b></h4>
                    
                    <div id="depositAmountOptions">
                        <button id="deposit300" onclick="selectDepositAmount(300)">৳300</button>
                        <button id="deposit1000" onclick="selectDepositAmount(1000)">৳1000</button>
                    </div>
                    <input id="depositAmount" type="number" placeholder="Amount (Selected from options)" readonly style="display:none;"/>
                    
                    <select id="depositMethod"><option>Bkash</option><option>Nagad</option></select>
                    <input id="depositCode" placeholder="Transaction code (from your mobile payment)" />
                    <button onclick="submitDeposit()">Send Deposit Request</button>
                    <p id="depositRule" class="small muted">নিয়ম: ডিপোজিট শুধুমাত্র প্ল্যান ক্রয়ের জন্য (৳300 বা ৳1000)।</p>
                </div>
            </div>

            <div id="withdrawSection" class="hidden">
                <button onclick="goHome()" class="back-btn">← Back to Home</button>
                <h2>Withdraw</h2>
                <div class="card">
                    <select id="withdrawMethod"><option>Bkash</option><option>Nagad</option></select>
                    <input id="withdrawNumber" placeholder="Your mobile number" />
                    <input id="withdrawAmount" type="number" placeholder="Amount (minimum ৳1000)" />
                    <button onclick="submitWithdraw()">Request Withdraw</button>
                    <p id="withdrawNote" class="small muted">প্রথম উইথড্রের জন্য: আপনাকে কমপক্ষে ৫ জন রেফার করতে হবে যারা প্ল্যান ক্রয় করে কাজ করেছে।</p>
                </div>
            </div>

            <div id="withdrawSuccessSection" class="hidden">
                <h2>উইথড্র রিকোয়েষ্ট সফল!</h2>
                <div class="card" id="withdrawSuccessDetails">
                    </div>
                <button onclick="goHome()" class="back-btn" style="width:100%; margin-top:15px; font-size:18px;">← Back to Home</button> 
            </div>

            <div id="depositHistorySection" class="hidden">
                <button onclick="goHome()" class="back-btn">← Back to Home</button>
                <h2>Deposit History</h2>
                <div class="card"><div id="depositHistory"></div></div>
            </div>

            <div id="withdrawHistorySection" class="hidden">
                <button onclick="goHome()" class="back-btn">← Back to Home</button>
                <h2>Withdraw History</h2>
                <div class="card"><div id="withdrawHistory"></div></div>
            </div>

            <div id="incomeHistorySection" class="hidden">
                <button onclick="showSection('wallet')" class="back-btn">← Back to Wallet</button>
                <h2>Income History (Task Reward)</h2>
                <div class="card"><div id="otherHistory"></div></div>
            </div>


            <div id="plans" class="hidden">
                <button onclick="goHome()" class="back-btn">← Back to Home</button>
                <h2>Buy a Plan</h2>
                <div id="currentPlanInfo" class="card"></div>
                <div class="card"><h4>৳300 Plan</h4><p class="small">3 tasks/day • reward per task set by admin</p><button onclick="buyPlan(300)">Buy Now (৳300)</button></div>
                <div class="card"><h4>৳1000 Plan</h4><p class="small">10 tasks/day • reward per task set by admin</p><button onclick="buyPlan(1000)">Buy Now (৳1000)</button></div>
            </div>

            <div id="tasks" class="hidden">
                <button onclick="goHome()" class="back-btn">← Back to Home</button>
                <h2>My Work</h2><div id="taskList"></div>
            </div>

            <div id="wallet" class="hidden">
                <button onclick="goHome()" class="back-btn">← Back to Home</button>
                <h2>Wallet</h2>
                <div style="display:flex; justify-content:space-between; gap:10px; align-items:center;">
                    <div class="balance-card">Balance: ৳ <span id="userBalance">0.00</span></div>
                </div>

                <div id="incomeGrid">
                    <div>
                        <div class="income-label">আজকের ইনকাম</div>
                        <div class="income-amount">৳ <span id="todayIncome">0.00</span></div>
                    </div>
                    <div>
                        <div class="income-label">গতকালকের ইনকাম</div>
                        <div class="income-amount">৳ <span id="yesterdayIncome">0.00</span></div>
                    </div>
                    <div>
                        <div class="income-label">সর্বমোট ইনকাম</div>
                        <div class="income-amount">৳ <span id="totalIncome">0.00</span></div>
                    </div>
                </div>
                
                <button id="showIncomeHistoryBtn" onclick="showSection('incomeHistorySection')">Income History (Task Reward)</button>

                <div id="transactionHistoryDetails" class="hidden">
                    <div id="planHistory"></div>
                </div>
            </div>

            <div id="support" class="hidden">
                <button onclick="goHome()" class="back-btn">← Back to Home</button>
                <h2>Support Center</h2>
                <p class="small">Send a message to admin. Admin can reply from Admin Panel. Useful links below.</p>
                <input id="helpMessage" placeholder="Type your message" />
                <button onclick="sendHelp()">Send</button>
                <div id="helpList"></div>

                <div class="card">
                    <h4>Useful Links</h4>
                    <p>Income Review Group: <a id="reviewGroupLink" href="#" target="_blank">Visit Group</a></p>
                    <p>YouTube Channel: <a id="youtubeLink" href="#" target="_blank">Visit Channel</a></p>
                    <p>Admin Telegram: <a id="telegramLink" href="#" target="_blank">Message Admin</a></p>
                </div>
            </div>

            <div id="account" class="hidden">
                <button onclick="goHome()" class="back-btn">← Back to Home</button>
                <h2>Account Settings</h2>

                <div class="card">
                    <h4>Profile Picture</h4>
                    <div style="display:flex; gap:12px; align-items:center;">
                        <div style="width:72px; height:72px; border-radius:50%; overflow:hidden; box-shadow:0 3px 10px rgba(0,0,0,0.06);">
                            <img id="settingsPic" src="logo.png" style="width:100%;height:100%;object-fit:cover;">
                        </div>
                        <div style="flex:1">
                            <input id="profilePicInput" type="file" accept="image/*" />
                            <button onclick="changeProfilePic()">Upload & Save</button>
                        </div>
                    </div>
                </div>

                <div class="card">
                    <h4>Change name</h4>
                    <input id="changeNameInput" placeholder="Your name" />
                    <button onclick="changeName()">Save Name</button>
                </div>

                <div class="card">
                    <h4>Change password</h4>
                    <input id="oldPass" type="password" placeholder="Current password" />
                    <input id="newPass" type="password" placeholder="New password" />
                    <button onclick="changePassword()">Change Password</button>
                </div>
            </div>

            <div id="refer" class="hidden">
                <button onclick="goHome()" class="back-btn">← Back to Home</button>
                <h2>My Team (Referrals)</h2>
                <div id="myReferLink" class="card"></div>
                <div id="referHistory" class="card"></div>
            </div>

        </div>

        <div id="adminPanel" class="hidden">
            <h2>Admin Panel</h2>
            <div style="text-align:right;margin-bottom:10px;"><button style="background:#e53935;color:#fff;padding:8px;border-radius:8px;border:none;" onclick="logout()">Logout</button></div>

            <div class="menu" style="display:flex; gap:8px; flex-wrap:wrap; margin-bottom:12px;">
                <button onclick="showAdminSection('adminTasks')">Tasks</button>
                <button onclick="showAdminSection('adminUsers')">Users</button>
                <button onclick="showAdminSection('adminDeposits')">Deposit Requests</button>
                <button onclick="showAdminSection('adminWithdraws')">Withdraw Requests</button>
                <button onclick="showAdminSection('adminHelp')">Support Desk</button>
                <button onclick="showAdminSection('adminNotice')">Send Notice</button>
                <button onclick="showAdminSection('adminMedia')">Media</button>
            </div>

            <div id="adminNotice" class="hidden card">
                <h3>Send Notice to All Users</h3>
                <input id="noticeMessage" placeholder="Type your notice here (বাংলায় লিখুন)" />
                <button onclick="sendNotice()">Send Notice</button>
                <p class="small muted">নোটিশটি সর্বসাধারণকে বাংলা ভাষায় দেখাবে।</p>
            </div>

            <div id="adminMedia" class="hidden card">
                <h3>Change Website Media</h3>
                <div style="margin-bottom:15px;">
                    <h4>Platform Logo (Small)</h4>
                    <input id="logoInput" type="file" accept="image/*" /><button onclick="changeLogo()">Upload Logo</button>
                </div>
                <div>
                    <h4>Website Cover Picture (Banner)</h4>
                    <input id="coverPicInput" type="file" accept="image/*" /><button onclick="changeCoverPic()">Upload Cover Pic</button>
                </div>
            </div>

            <div id="adminTasks" class="hidden card">
                <h3>Manage Tasks (Add / Delete) + Set Reward</h3>
                <input id="taskTitle" placeholder="Task title" />
                <input id="taskLink" placeholder="Task link (https://...)" />
                <input id="taskReward" type="number" placeholder="Reward per task (৳) — e.g. 10" />
                <button onclick="addTask()">Add Task</button>
                <div id="adminTaskList"></div>
            </div>

            <div id="adminUsers" class="hidden card">
                <h3>Users List</h3>
                <table id="usersTable"><thead><tr><th>Name</th><th>Phone</th><th>Balance</th><th>Password</th><th>Status</th><th>Action</th></tr></thead><tbody></tbody></table>
            </div>

            <div id="adminDeposits" class="hidden card">
                <h3>Deposit Requests</h3>
                <table id="depositTable"><thead><tr><th>User</th><th>Amount</th><th>Method</th><th>Code</th><th>Status</th><th>Action</th></tr></thead><tbody></tbody></table>
            </div>

            <div id="adminWithdraws" class="hidden card">
                <h3>Withdraw Requests</h3>
                <table id="withdrawTable"><thead><tr><th>User</th><th>Amount</th><th>Method</th><th>Number</th><th>Status</th><th>Action</th></tr></thead><tbody></tbody></table>
            </div>

            <div id="adminHelp" class="hidden card">
                <h3>Support Desk</h3>
                <div id="adminHelpList"></div>
            </div>

        </div>

    </div>
    
    <div class="bottom-nav hidden" id="bottomNav">
        <button class="nav-btn nav-active" id="navHome" onclick="navTo('home', this)"><span>🏠</span> Home</button>
        <button class="nav-btn" id="navWallet" onclick="navTo('wallet', this)"><span>💰</span> Wallet</button>
        <button class="nav-btn" id="navAccount" onclick="navTo('account', this)"><span>⚙️</span> Settings</button>
        <button class="nav-btn" id="navSupport" onclick="navTo('support', this)"><span>💬</span> Support</button>
    </div>
    
<script>
/* ========== Data & constants (using localStorage as provided) ========== */
let users = JSON.parse(localStorage.getItem('users')) || [];
let tasks = JSON.parse(localStorage.getItem('tasks')) || [];
let deposits = JSON.parse(localStorage.getItem('deposits')) || [];
let withdraws = JSON.parse(localStorage.getItem('withdraws')) || [];
let helps = JSON.parse(localStorage.getItem('helps')) || [];
let noticeText = localStorage.getItem('notice') || '';
let currentUser = null;
let selectedDepositAmount = null; // New state variable

// admin credentials (change if you want)
const adminPhone = "01700000000";
const adminPass = "admin123";

const ONE_DAY_MS = 24 * 60 * 60 * 1000;
const MIN_WITHDRAW_AMOUNT = 1000;
const PLAN_AMOUNTS = [300, 1000]; // allowed deposit amounts (and plan amounts)
const PLAN_COOLDOWN_DAYS = 30; 

/* ========== helpers ========== */
function saveAll(){
    localStorage.setItem('users', JSON.stringify(users));
    localStorage.setItem('tasks', JSON.stringify(tasks));
    localStorage.setItem('deposits', JSON.stringify(deposits));
    localStorage.setItem('withdraws', JSON.stringify(withdraws));
    localStorage.setItem('helps', JSON.stringify(helps));
}
function findUserIndexByPhone(phone){ return users.findIndex(u => u.phone === phone); }
function findUserByPhone(phone){ return users.find(u => u.phone === phone); }
function todayISO(){ return (new Date()).toISOString().split('T')[0]; }
function yesterdayISO(){
    let d = new Date();
    d.setDate(d.getDate() - 1);
    return d.toISOString().split('T')[0];
}
function nowMs(){ return Date.now(); }
function generateId(prefix='id'){ return prefix + '_' + nowMs() + '_' + Math.floor(Math.random()*10000); }
function escapeHtml(s){ if(s===null||s===undefined) return ''; return String(s).replace(/[&<>"'`=\/]/g, ch=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;','/':'&#x2F;','`':'&#x3D;'})[ch]); }
function capitalize(s){ if(!s) return ''; return String(s).charAt(0).toUpperCase()+String(s).slice(1); }
function statusPill(status){
    status = (status||'').toString().toLowerCase();
    if(status==='approved') return '<span class="status-pill status-approved">Approved</span>';
    if(status==='rejected') return '<span class="status-pill status-rejected">Rejected</span>';
    return '<span class="status-pill status-pending">Pending</span>';
}
/**
 * Formats a number with comma separators (e.g., 10000.50 -> 10,000.50)
 * Uses en-US localization for formatting.
 */
function formatNumber(n, decimals = 2) {
    if (typeof n !== 'number' || isNaN(n)) return '0.00';
    try {
        return n.toLocaleString('en-US', {
            minimumFractionDigits: decimals,
            maximumFractionDigits: decimals
        });
    } catch (e) {
        // Fallback for older browsers
        const [integerPart, decimalPart] = n.toFixed(decimals).split('.');
        const regex = /\B(?=(\d{3})+(?!\d))/g;
        return integerPart.replace(regex, ',') + (decimalPart ? '.' + decimalPart : '');
    }
}


/* ====== Logo & Cover Loader ====== */
function loadMedia(){ 
    let logo = localStorage.getItem('platformLogo'); 
    if(logo) { let el = document.getElementById('platformLogo'); if(el) el.src = logo; } 

    let cover = localStorage.getItem('websiteCoverPic');
    const defaultCover = 'default_cover.jpg'; 
    if(cover) { let el = document.getElementById('websiteCoverPic'); if(el) el.src = cover; }
    else { let el = document.getElementById('websiteCoverPic'); if(el) el.src = defaultCover; }
}
function changeLogo(){
    let file = document.getElementById('logoInput').files[0];
    if(!file) return alert('Select an image first');
    let reader = new FileReader();
    reader.onload = function(e){
        localStorage.setItem('platformLogo', e.target.result);
        document.getElementById('platformLogo').src = e.target.result;
        saveAll();
        alert('Logo updated');
    };
    reader.readAsDataURL(file);
}
function changeCoverPic(){
    let file = document.getElementById('coverPicInput').files[0];
    if(!file) return alert('Select an image first');
    let reader = new FileReader();
    reader.onload = function(e){
        localStorage.setItem('websiteCoverPic', e.target.result);
        let el = document.getElementById('websiteCoverPic');
        if(el) el.src = e.target.result;
        saveAll();
        alert('Cover Picture updated');
    };
    reader.readAsDataURL(file);
}
loadMedia();

/* ====== Persist current user between reloads ====== */
function setLoggedUser(phone){
    if(!phone) localStorage.removeItem('currentUserPhone');
    else localStorage.setItem('currentUserPhone', phone);
}
function clearLoggedUser(){
    localStorage.removeItem('currentUserPhone');
}
function restoreLoggedUser(){
    let phone = localStorage.getItem('currentUserPhone');
    if(!phone) return null;
    let u = findUserByPhone(phone);
    if(u) currentUser = u;
}
restoreLoggedUser();

/* control bottom nav visibility */
function setBottomNavVisible(visible){
    const el = document.getElementById('bottomNav');
    if(!el) return;
    if(visible) { el.classList.remove('hidden'); } else { el.classList.add('hidden'); }
}

/* ====== Auth UI (Updated to control nav visibility) ====== */
function showSignup(){ 
    document.getElementById('signupDiv').classList.remove('hidden'); 
    document.getElementById('loginDiv').classList.add('hidden'); 
    setBottomNavVisible(false); // Hide nav on Signup
    controlHeaderVisibility(false, true); 
}
function showLogin(){ 
    document.getElementById('signupDiv').classList.add('hidden'); 
    document.getElementById('loginDiv').classList.remove('hidden'); 
    setBottomNavVisible(false); // Hide nav on Login
    controlHeaderVisibility(false, true); 
}
function logout(){
    currentUser = null;
    clearLoggedUser();
    document.getElementById('userDashboard').classList.add('hidden');
    document.getElementById('adminPanel').classList.add('hidden');
    document.getElementById('authDiv').classList.remove('hidden');
    saveAll();
    setBottomNavVisible(false); // Hide nav on Logout
    controlHeaderVisibility(false, true); 
    showSignup(); 
}

/* ====== Signup / Login ====== */
function signup(){
    let name = document.getElementById('signupName').value.trim();
    let phone = document.getElementById('signupPhone').value.trim();
    let pass = document.getElementById('signupPass').value;
    let ref = document.getElementById('signupRefCode').value.trim();
    if(!name || !phone || !pass) return alert('Please fill required fields');
    if(users.find(u => u.phone === phone)) return alert('Phone already registered');
    users.push({
        name: name,
        phone: phone,
        pass: pass,
        balance: 0,
        plan: null,
        status: 'active',
        ref: ref || '',
        transactions: [],
        tasksDone: 0,
        completedTasks: [],
        firstWithdrawDone: false,
        pic: ''
    });
    saveAll();
    alert('Sign up done — please login');
    showLogin();
}

function login(){
    let phone = document.getElementById('loginPhone').value.trim();
    let pass = document.getElementById('loginPass').value;
    if(phone === adminPhone && pass === adminPass){
        document.getElementById('authDiv').classList.add('hidden');
        document.getElementById('adminPanel').classList.remove('hidden');
        loadAdminTasks(); loadAdminUsers(); loadAdminDeposits(); loadAdminWithdraws(); loadAdminHelp();
        setLoggedUser('');
        setBottomNavVisible(false); // Admin panel does not use bottom nav
        return;
    }
    let uIndex = findUserIndexByPhone(phone);
    if(uIndex === -1) return alert('Invalid credentials');
    let u = users[uIndex];
    if(u.pass !== pass) return alert('Invalid credentials');
    if(u.status !== 'active') return alert('Your account is blocked');
    currentUser = u;
    setLoggedUser(currentUser.phone);
    document.getElementById('userDashboard').classList.remove('hidden');
    document.getElementById('adminPanel').classList.add('hidden'); // Ensure admin panel is hidden
    document.getElementById('authDiv').classList.add('hidden');
    
    // set home nav active
    navActiveClear();
    document.getElementById('navHome').classList.add('nav-active');
    updateDashboard(); // Calls showSection('home') implicitly
}

/* ====== Header/UI Control (Updated Function) ====== */
function controlHeaderVisibility(show, isAuth=false) {
    // show: Header elements will only show if 'show' is true (i.e., when on 'home')
    const title = document.getElementById('websiteTitle');
    const logo = document.getElementById('logoWrap');
    const notice = document.getElementById('userNotice');
    const cover = document.getElementById('coverPicCard');
    const userHeaderContainer = document.getElementById('userHeaderContainer');
    
    if(isAuth) { // If it's auth page, hide everything 
        if(title) title.classList.remove('hidden'); // Title and Logo on Auth are desired.
        if(logo) logo.classList.remove('hidden');
        if(notice) notice.classList.add('hidden');
        if(cover) cover.classList.add('hidden');
        if(userHeaderContainer) userHeaderContainer.classList.add('hidden');
        return;
    }

    // For user dashboard
    if(title) title.classList.toggle('hidden', !show);
    if(logo) logo.classList.toggle('hidden', !show);
    // Notice only shows on home if noticeText exists
    if(notice) {
        const shouldShowNotice = show && noticeText && noticeText.trim() !== ''; 
        notice.classList.toggle('hidden', !shouldShowNotice);
    }
    if(cover) cover.classList.toggle('hidden', !show);
    
    // userHeaderContainer (Name, Pic, Logout) is only visible if 'show' is true (i.e., on Home)
    if(userHeaderContainer) userHeaderContainer.classList.toggle('hidden', !show); 
}


/* ====== Dashboard UI & Nav (Updated) ====== */
function navActiveClear(){
    const navButtons = document.querySelectorAll('#bottomNav .nav-btn');
    navButtons.forEach(btn => btn.classList.remove('nav-active'));
}
function navTo(section, btnEl){
    navActiveClear();
    if(btnEl) btnEl.classList.add('nav-active');
    showSection(section);
}
function updateDashboard(){
    if(!currentUser) return;
    document.getElementById('userName').innerText = currentUser.name;
    document.getElementById('userBalance').innerText = formatNumber(Number(currentUser.balance || 0), 2);
    document.getElementById('userPhoneDisplay').innerText = currentUser.phone;
    document.getElementById('myReferLink').innerHTML = '<b>Your referral code:</b> ' + escapeHtml(currentUser.phone);

    let pic = currentUser.pic || localStorage.getItem('platformLogo') || 'logo.png';
    setHeaderPic(pic);

    loadMedia();

    // Load notice text into the element
    let noticeEl = document.getElementById('userNotice');
    if (noticeEl) {
        noticeEl.innerHTML = `⚠️ Notice: ${escapeHtml(noticeText)}`;
    }

    setIncomes();

    loadTasks();
    loadTransactions(); 
    loadCurrentPlan();
    loadReferHistory();
    loadHelp();

    showSection('home');
}
function goHome(){ 
    showSection('home'); 
    navActiveClear();
    document.getElementById('navHome').classList.add('nav-active');
    // setBottomNavVisible(true); // showSection(home) এর মধ্যে এটি নিয়ন্ত্রিত হচ্ছে
}

// All sections are hidden/shown based on navigation to ensure only one is visible
function showSection(sec){
    // All sections in the dashboard that can be displayed
    let sections = ['home','plans','wallet','refer','tasks','account','support',
                    'depositSection', 'withdrawSection', 'depositHistorySection', 
                    'withdrawHistorySection', 'incomeHistorySection', 'withdrawSuccessSection']; 
                    
    sections.forEach(s => { let el=document.getElementById(s); if(el) el.classList.add('hidden'); });
    let el = document.getElementById(sec);
    if(el) el.classList.remove('hidden');

    // **FINAL FIX: Control Bottom Nav Visibility**
    // শুধুমাত্র এই চারটি স্ক্রিনের জন্যই নেভিগেশন বার দৃশ্যমান হবে।
    const showNav = (sec === 'home' || sec === 'wallet' || sec === 'account' || sec === 'support');
    setBottomNavVisible(showNav);
    
    // **Control Header Elements (Name, Pic, Logout, Title, Logo, Cover) Visibility**
    // Show these elements ONLY if the section is 'home'
    const isHome = (sec === 'home');
    controlHeaderVisibility(isHome);

    // update some views on display
    if(sec === 'refer') loadReferHistory();
    if(sec === 'wallet') {
        if(currentUser) {
            document.getElementById('userBalance').innerText = formatNumber(Number(currentUser.balance || 0), 2);
            setIncomes();
        }
    }
    // For all history sections, ensure transactions are loaded
    if(['depositHistorySection', 'withdrawHistorySection', 'incomeHistorySection'].includes(sec)) {
        loadTransactions();
    }
}
function showAdminSection(sec){
    let sections = ['adminTasks','adminUsers','adminDeposits','adminWithdraws','adminHelp','adminNotice','adminMedia'];
    sections.forEach(s => document.getElementById(s).classList.add('hidden'));
    document.getElementById(sec).classList.remove('hidden');
}

/* ====== compute incomes (today & total) ====== */
function parseTxDateISO(tx){
    if(!tx) return null;
    let iso = tx.dateISO || tx.date;
    if(!iso) return null;
    try {
        let d = new Date(iso);
        if(isNaN(d)) return null;
        return d.toISOString().split('T')[0];
    } catch(e){ return null; }
}
function setIncomes(){
    if(!currentUser) return;
    let today = todayISO();
    let yesterday = yesterdayISO();
    let total = 0;
    let todaySum = 0;
    let yesterdaySum = 0;
    
    (currentUser.transactions || []).forEach(t=>{
        let amt = Number(t.amount) || 0;
        
        // Task rewards are the primary income source (type 'Task Reward')
        if(t.type === 'Task Reward' && amt > 0) total += amt;

        let txISO = parseTxDateISO(t);
        
        if(txISO === today && t.type === 'Task Reward' && amt > 0) {
            todaySum += amt;
        } else if (txISO === yesterday && t.type === 'Task Reward' && amt > 0) {
            yesterdaySum += amt;
        }
    });
    // Formatting added
    document.getElementById('todayIncome').innerText = formatNumber(todaySum, 2);
    document.getElementById('yesterdayIncome').innerText = formatNumber(yesterdaySum, 2);
    document.getElementById('totalIncome').innerText = formatNumber(total, 2);
}

/* ====== Profile picture update (user) ====== */
function setHeaderPic(dataUrl){
    let header = document.getElementById('headerPic');
    let settings = document.getElementById('settingsPic');
    if(header) header.src = dataUrl || 'logo.png';
    if(settings) settings.src = dataUrl || 'logo.png';
}
function changeProfilePic(){
    if(!currentUser) return alert('Login first');
    let file = document.getElementById('profilePicInput').files[0];
    if(!file) return alert('Select an image');
    let reader = new FileReader();
    reader.onload = function(e){
        let data = e.target.result;
        currentUser.pic = data;
        let idx = findUserIndexByPhone(currentUser.phone);
        if(idx !== -1){ users[idx] = currentUser; saveAll(); setLoggedUser(currentUser.phone); }
        setHeaderPic(data);
        alert('Profile picture updated');
    };
    reader.readAsDataURL(file);
}
function changeName(){
    if(!currentUser) return alert('Login first');
    let newName = document.getElementById('changeNameInput').value.trim();
    if(!newName) return alert('Enter a name');
    currentUser.name = newName;
    let idx = findUserIndexByPhone(currentUser.phone);
    if(idx !== -1){ users[idx] = currentUser; saveAll(); setLoggedUser(currentUser.phone); }
    updateDashboard();
    alert('Name updated');
}

/* ====== Password change (placeholder logic) ====== */
function changePassword(){
    if(!currentUser) return alert('Login first');
    let oldPass = document.getElementById('oldPass').value;
    let newPass = document.getElementById('newPass').value;
    if(currentUser.pass !== oldPass) return alert('Current password incorrect.');
    if(!newPass || newPass.length < 4) return alert('New password must be at least 4 characters.');

    currentUser.pass = newPass;
    let idx = findUserIndexByPhone(currentUser.phone);
    if(idx !== -1){ users[idx] = currentUser; saveAll(); setLoggedUser(currentUser.phone); }
    document.getElementById('oldPass').value = '';
    document.getElementById('newPass').value = '';
    alert('Password changed successfully.');
}

/* ====== Plans & buying ====== */
function buyPlan(amount){
    if(!currentUser) return alert('Please login first');
    
    if(currentUser.balance < amount) return alert('Insufficient balance. Deposit first (exactly 300 or 1000).');
    
    currentUser.balance = Number((currentUser.balance - amount).toFixed(2));
    
    currentUser.plan = { amount: amount, dateMs: nowMs(), tasksAllowed: (amount === 300 ? 3 : 10), lastResetISO: todayISO() };
    
    currentUser.transactions.push({ type: 'Plan Buy', amount: -amount, date: new Date().toLocaleString(), dateISO: todayISO(), details: `Bought ${amount} Plan` });

    let idx = findUserIndexByPhone(currentUser.phone);
    if(idx !== -1){ users[idx] = currentUser; saveAll(); setLoggedUser(currentUser.phone); }
    
    updateDashboard();
    alert(`Plan bought successfully for ৳${formatNumber(amount, 0)}`);
}
function loadCurrentPlan(){
    let infoDiv = document.getElementById('currentPlanInfo');
    if(!currentUser || !currentUser.plan){
        infoDiv.innerHTML = '<h4>No Active Plan</h4><p class="small">Buy a plan to start earning.</p>';
        return;
    }
    let p = currentUser.plan;
    let days = Math.floor((nowMs() - p.dateMs) / ONE_DAY_MS);
    let remainingDays = PLAN_COOLDOWN_DAYS - days;
    
    infoDiv.innerHTML = `
        <h4>Current Plan: ৳${formatNumber(p.amount, 0)}</h4>
        <p class="small">Daily Tasks: <b>${p.tasksAllowed}</b></p>
        <p class="small">Plan purchased: ${new Date(p.dateMs).toLocaleDateString()}</p>
        <p class="small">Tasks Done Today: <b>${currentUser.tasksDone}</b></p>
    `;
}

/* ====== Tasks (user) ====== */
function loadTasks(){
    let list = document.getElementById('taskList');
    list.innerHTML = '';
    
    if(!currentUser.plan){
        list.innerHTML = '<p class="muted">You must buy a plan first to see and complete tasks.</p>';
        return;
    }

    if(currentUser.plan.lastResetISO !== todayISO()){
        currentUser.tasksDone = 0;
        currentUser.plan.lastResetISO = todayISO();
        currentUser.completedTasks = currentUser.completedTasks.filter(ct => ct.dateISO !== yesterdayISO()); 
        let idx = findUserIndexByPhone(currentUser.phone);
        if(idx !== -1){ users[idx] = currentUser; saveAll(); setLoggedUser(currentUser.phone); }
    }

    const availableTasks = tasks;
    const maxTasks = currentUser.plan.tasksAllowed;
    
    if(currentUser.tasksDone >= maxTasks){
        list.innerHTML = `<p class="notice-card" style="background:#4caf50;">✅ Daily task limit reached: ${maxTasks}/${maxTasks}</p>`;
        return;
    }

    if(availableTasks.length === 0){
        list.innerHTML = '<p class="muted">Admin has not added any tasks yet.</p>';
        return;
    }
    
    list.innerHTML += `<p class="small muted">You have completed ${currentUser.tasksDone} out of ${maxTasks} tasks today.</p>`;

    availableTasks.forEach((t, index) => {
        let isCompleted = currentUser.completedTasks.some(ct => ct.taskId === t.id && ct.dateISO === todayISO());
        list.innerHTML += `
            <div class="task" id="task_${t.id}">
                <p style="font-weight:700; margin-bottom:4px;">Task ${index + 1}: ${escapeHtml(t.title)}</p>
                <p class="small muted">Reward: ৳${formatNumber(Number(t.reward), 2)}</p>
                ${isCompleted 
                    ? '<button style="background:#4caf50; color:white; border:none; padding:8px; border-radius:8px;" disabled>Completed Today ✅</button>'
                    : `<button style="background:#ff5f6d; color:white; border:none; padding:8px; border-radius:8px;" onclick="completeTask('${t.id}', '${t.link}', ${t.reward})">Start Task</button>`
                }
            </div>
        `;
    });
}
function completeTask(taskId, taskLink, reward){
    if(currentUser.tasksDone >= currentUser.plan.tasksAllowed) {
        return alert('Daily task limit reached!');
    }
    
    let isCompleted = currentUser.completedTasks.some(ct => ct.taskId === taskId && ct.dateISO === todayISO());
    if(isCompleted) {
         return alert('This task is already completed today.');
    }

    window.open(taskLink, '_blank');
    
    currentUser.tasksDone += 1;
    currentUser.balance = Number((currentUser.balance + reward).toFixed(2));
    currentUser.completedTasks.push({ taskId: taskId, dateISO: todayISO(), reward: reward });
    
    currentUser.transactions.push({ type: 'Task Reward', amount: reward, date: new Date().toLocaleString(), dateISO: todayISO(), details: `Task: ${tasks.find(t=>t.id===taskId).title}` });

    let idx = findUserIndexByPhone(currentUser.phone);
    if(idx !== -1){ users[idx] = currentUser; saveAll(); setLoggedUser(currentUser.phone); }
    
    alert(`Task completed! ৳${formatNumber(reward, 2)} added to your balance.`);
    updateDashboard(); 
}

/* ====== Deposit Amount Selection (New Function) ====== */
function selectDepositAmount(amount){
    selectedDepositAmount = amount;
    
    document.getElementById('deposit300').classList.remove('selected');
    document.getElementById('deposit1000').classList.remove('selected');

    if(amount === 300) {
        document.getElementById('deposit300').classList.add('selected');
    } else if (amount === 1000) {
        document.getElementById('deposit1000').classList.add('selected');
    }
}

/* ====== Wallet & Transactions (user) ====== */
function submitDeposit(){
    if(!currentUser) return alert('Login first');
    let amount = selectedDepositAmount;
    let code = document.getElementById('depositCode').value.trim();
    let method = document.getElementById('depositMethod').value;
    
    if(!amount || !PLAN_AMOUNTS.includes(amount)) return alert('Please select a valid amount (300 or 1000) first.');
    if(!code) return alert('Please enter the transaction code.');
    
    deposits.push({ 
        id: generateId('deposit'), 
        userId: currentUser.phone, 
        userName: currentUser.name,
        amount: amount, 
        method: method, 
        code: code, 
        status: 'pending', 
        date: new Date().toLocaleString(),
        dateISO: todayISO()
    });
    
    currentUser.transactions.push({ type: 'Deposit Request', amount: 0, date: new Date().toLocaleString(), dateISO: todayISO(), details: `Deposit Request ৳${amount} via ${method}` });
    
    let idx = findUserIndexByPhone(currentUser.phone);
    if(idx !== -1){ users[idx] = currentUser; saveAll(); setLoggedUser(currentUser.phone); }
    
    alert('Deposit request sent. Admin will review it shortly.');
    document.getElementById('depositCode').value = '';
    selectDepositAmount(null); 
    loadTransactions(); 
    goHome(); // Go back to home after deposit request
}

function submitWithdraw(){
    if(!currentUser) return alert('Login first');
    let amount = Number(document.getElementById('withdrawAmount').value.trim());
    let number = document.getElementById('withdrawNumber').value.trim();
    let method = document.getElementById('withdrawMethod').value;

    if(amount < MIN_WITHDRAW_AMOUNT) return alert(`Minimum withdraw amount is ৳${formatNumber(MIN_WITHDRAW_AMOUNT, 0)}`);
    if(amount > currentUser.balance) return alert('Insufficient balance.');
    if(!number) return alert('Please enter your mobile number for payment.');

    // 1. Create withdraw request
    withdraws.push({
        id: generateId('withdraw'),
        userId: currentUser.phone,
        userName: currentUser.name,
        amount: amount,
        method: method,
        number: number,
        status: 'pending',
        date: new Date().toLocaleString(),
        dateISO: todayISO()
    });
    
    // 2. Deduct amount from user balance and record transaction (request stage)
    currentUser.balance = Number((currentUser.balance - amount).toFixed(2));
    currentUser.transactions.push({ type: 'Withdraw Request', amount: -amount, date: new Date().toLocaleString(), dateISO: todayISO(), details: `Requested Withdraw ৳${amount} via ${method}` });

    let idx = findUserIndexByPhone(currentUser.phone);
    if(idx !== -1){ users[idx] = currentUser; saveAll(); setLoggedUser(currentUser.phone); }

    // 3. **Show Success Screen**
    showWithdrawSuccess(amount, number, method); 
    
    // Clear form fields
    document.getElementById('withdrawAmount').value = '';
    document.getElementById('withdrawNumber').value = '';
    
    // Reload transactions so the history is updated
    loadTransactions(); 
}

function showWithdrawSuccess(amount, number, method) {
    if(!currentUser) return;
    const detailsDiv = document.getElementById('withdrawSuccessDetails');
    const now = new Date().toLocaleString();
    // Use the already updated balance
    const currentBalance = Number(currentUser.balance || 0); 
    
    detailsDiv.innerHTML = `
        <p style="font-size:18px; font-weight:700; color:#4caf50;">✅ উইথড্র রিকোয়েষ্ট সফল!</p>
        <hr style="border:none; border-top:1px solid #eee;">
        <p><b>একাউন্ট নম্বর:</b> ${escapeHtml(number)}</p>
        <p><b>মেথড:</b> ${method}</p>
        <p><b>পরিমাণ:</b> ৳${formatNumber(amount, 2)}</p>
        <p style="font-size:16px; color:#d84315;"><b>বর্তমান বেলেন্স:</b> ৳${formatNumber(currentBalance, 2)}</p>
        <p class="small muted"><b>সময়:</b> ${now}</p>
    `;
    // Show only the success section
    showSection('withdrawSuccessSection');
    // Nav visibility is controlled by showSection but we ensure it's hidden here for clarity
    setBottomNavVisible(false); 
}


function loadTransactions(){
    if(!currentUser) return;

    let depositHtml = '<p class="muted">No deposits found.</p>';
    let withdrawHtml = '<p class="muted">No withdraws found.</p>';
    let otherHtml = '<p class="muted">No income (Task Reward) transactions.</p>';

    if(currentUser.transactions.length > 0){
        let allTx = currentUser.transactions.slice().reverse(); 

        const formatTx = (t) => {
            const statusIndicator = t.type.includes('Approved') ? '<span style="color:green; font-weight:700;">(Approved)</span>' : 
                                  t.type.includes('Rejected') ? '<span style="color:red; font-weight:700;">(Rejected)</span>' : 
                                  t.type.includes('Request') ? '<span style="color:#ffb74d; font-weight:700;">(Pending)</span>' : '';
            return `
            <div class="trans" style="padding:8px; margin:4px 0;">
                <div style="display:flex; justify-content:space-between; font-weight:600;">
                    <span>${t.details} ${statusIndicator}</span>
                    <span style="${t.amount >= 0 ? 'color:#4caf50' : 'color:#e53935'}">${t.amount >= 0 ? '+' : ''}৳${formatNumber(Math.abs(t.amount), 2)}</span>
                </div>
                <div class="small muted">${t.date}</div>
            </div>
        `;
        };
        
        let depositList = allTx.filter(t => t.type.includes('Deposit'));
        depositHtml = depositList.map(formatTx).join('') || depositHtml;
        
        let withdrawList = allTx.filter(t => t.type.includes('Withdraw'));
        withdrawHtml = withdrawList.map(formatTx).join('') || withdrawHtml;
        
        // Income History (Task Rewards only)
        let otherList = allTx.filter(t => t.type === 'Task Reward');
        otherHtml = otherList.map(formatTx).join('') || otherHtml;
    }

    document.getElementById('depositHistory').innerHTML = depositHtml;
    document.getElementById('withdrawHistory').innerHTML = withdrawHtml;
    document.getElementById('otherHistory').innerHTML = otherHtml; // Used for Income History
    // Plan History remains loaded but hidden within wallet
}

/* ====== Referrals (user) ====== */
function loadReferHistory(){
    let refDiv = document.getElementById('referHistory');
    refDiv.innerHTML = '<h4>Referral List</h4>';

    let myPhone = currentUser.phone;
    let myRefs = users.filter(u => u.ref === myPhone);
    
    refDiv.innerHTML += `<p class="small muted">Total referrals: <b>${myRefs.length}</b></p>`;

    if(myRefs.length === 0){
        refDiv.innerHTML += '<p class="muted">No referrals found.</p>';
        return;
    }

    let table = '<table><thead><tr><th>Name</th><th>Phone</th><th>Plan</th></tr></thead><tbody>';
    myRefs.forEach(ref => {
        table += `<tr><td>${escapeHtml(ref.name)}</td><td>${escapeHtml(ref.phone)}</td><td>${ref.plan ? `৳${formatNumber(ref.plan.amount, 0)}` : 'None'}</td></tr>`;
    });
    table += '</tbody></table>';
    refDiv.innerHTML += table;
}

/* ====== Support (user) ====== */
function sendHelp(){
    if(!currentUser) return alert('Login first');
    let msg = document.getElementById('helpMessage').value.trim();
    if(!msg) return alert('Enter your message.');

    helps.push({
        id: generateId('help'),
        userId: currentUser.phone,
        userName: currentUser.name,
        message: msg,
        reply: null,
        status: 'pending',
        date: new Date().toLocaleString(),
        dateISO: todayISO()
    });
    saveAll();
    alert('Support message sent!');
    document.getElementById('helpMessage').value = '';
    loadHelp();
}
function loadHelp(){
    if(!currentUser) return;
    let list = document.getElementById('helpList');
    list.innerHTML = '';
    
    let userHelps = helps.filter(h => h.userId === currentUser.phone).reverse();

    if(userHelps.length === 0){
        list.innerHTML = '<p class="muted">No previous messages.</p>';
        return;
    }

    userHelps.forEach(h => {
        list.innerHTML += `
            <div class="card" style="border:1px solid #ddd; padding:10px;">
                <div style="font-weight:700;">You: ${escapeHtml(h.message)}</div>
                <div class="small muted">${escapeHtml(h.date)} ${statusPill(h.status)}</div>
                ${h.reply ? `<div style="margin-top:8px; padding-left:10px; border-left:3px solid #ff5f6d;"><b>Admin Reply:</b> ${escapeHtml(h.reply)}</div>` : ''}
            </div>
        `;
    });
}


/* ####################### ADMIN FUNCTIONS ####################### */

function loadAdminUsers(){
    let table = document.getElementById('usersTable').getElementsByTagName('tbody')[0];
    table.innerHTML = '';
    
    users.forEach(u => {
        let row = table.insertRow();
        row.insertCell().innerText = u.name;
        row.insertCell().innerText = u.phone;
        row.insertCell().innerText = formatNumber(u.balance, 2); 
        row.insertCell().innerText = u.pass; 
        row.insertCell().innerHTML = u.status === 'active' ? '<span style="color:green;font-weight:700;">Active</span>' : '<span style="color:red;font-weight:700;">Blocked</span>';
        
        let actionCell = row.insertCell();
        
        let blockBtn = document.createElement('button');
        blockBtn.className = u.status === 'active' ? 'action-btn block' : 'action-btn unblock';
        blockBtn.innerText = u.status === 'active' ? 'Block' : 'Unblock';
        blockBtn.onclick = () => toggleUserStatus(u.phone);
        actionCell.appendChild(blockBtn);
        
        let deleteBtn = document.createElement('button');
        deleteBtn.className = 'action-btn delete';
        deleteBtn.innerText = 'Delete';
        deleteBtn.onclick = () => deleteUser(u.phone);
        actionCell.appendChild(deleteBtn);
    });
}
function toggleUserStatus(phone){
    let idx = findUserIndexByPhone(phone);
    if(idx !== -1){
        users[idx].status = users[idx].status === 'active' ? 'blocked' : 'active';
        saveAll();
        loadAdminUsers();
        alert(`User ${phone} status updated.`);
    }
}
function deleteUser(phone){
    if(!confirm(`Are you sure you want to delete user ${phone}?`)) return;
    users = users.filter(u => u.phone !== phone);
    deposits = deposits.filter(d => d.userId !== phone);
    withdraws = withdraws.filter(w => w.userId !== phone);
    helps = helps.filter(h => h.userId !== phone);
    saveAll();
    loadAdminUsers();
    alert(`User ${phone} deleted.`);
}

function addTask(){
    let title = document.getElementById('taskTitle').value.trim();
    let link = document.getElementById('taskLink').value.trim();
    let reward = Number(document.getElementById('taskReward').value.trim());
    
    if(!title || !link || !reward || reward <= 0) return alert('Fill all fields with valid data.');

    tasks.push({ id: generateId('task'), title: title, link: link, reward: reward });
    saveAll();
    document.getElementById('taskTitle').value = '';
    document.getElementById('taskLink').value = '';
    document.getElementById('taskReward').value = '';
    loadAdminTasks();
    alert('New task added!');
}
function loadAdminTasks(){
    let list = document.getElementById('adminTaskList');
    list.innerHTML = '';
    tasks.forEach(t => {
        list.innerHTML += `
            <div class="task" style="display:flex; justify-content:space-between; align-items:center;">
                <div>
                    <b>${escapeHtml(t.title)}</b> (৳${formatNumber(Number(t.reward), 2)})<br>
                    <span class="small muted">${escapeHtml(t.link)}</span>
                </div>
                <button class="action-btn delete" onclick="deleteTask('${t.id}')">Delete</button>
            </div>
        `;
    });
}
function deleteTask(id){
    tasks = tasks.filter(t => t.id !== id);
    saveAll();
    loadAdminTasks();
    alert('Task deleted.');
}

function loadAdminDeposits(){
    let table = document.getElementById('depositTable').getElementsByTagName('tbody')[0];
    table.innerHTML = '';
    
    deposits.filter(d => d.status === 'pending').forEach(d => {
        let row = table.insertRow();
        row.insertCell().innerText = d.userName;
        row.insertCell().innerText = `৳${formatNumber(d.amount, 2)}`;
        row.insertCell().innerText = d.method;
        row.insertCell().innerText = d.code;
        row.insertCell().innerHTML = statusPill(d.status);
        
        let actionCell = row.insertCell();
        actionCell.innerHTML = `
            <button class="action-btn approve" onclick="approveDeposit('${d.id}')">Approve</button>
            <button class="action-btn reject" onclick="rejectDeposit('${d.id}')">Reject</button>
        `;
    });
}
function approveDeposit(id){
    let dIndex = deposits.findIndex(d => d.id === id);
    if(dIndex === -1) return;
    let deposit = deposits[dIndex];
    
    let uIndex = findUserIndexByPhone(deposit.userId);
    if(uIndex !== -1){
        let user = users[uIndex];
        
        user.balance = Number((user.balance + deposit.amount).toFixed(2));
        deposits[dIndex].status = 'approved';
        
        user.transactions.push({ type: 'Deposit Approved', amount: deposit.amount, date: new Date().toLocaleString(), dateISO: todayISO(), details: `Deposit ৳${deposit.amount} via ${deposit.method}` });
        
        users[uIndex] = user;
        saveAll();
        loadAdminDeposits();
        
        if(currentUser && currentUser.phone === user.phone) updateDashboard(); 
        
        alert(`Deposit ৳${formatNumber(deposit.amount, 2)} for ${deposit.userName} approved! Balance updated.`);
    } else {
        alert('User not found!');
    }
}
function rejectDeposit(id){
    let dIndex = deposits.findIndex(d => d.id === id);
    if(dIndex === -1) return;
    
    let deposit = deposits[dIndex];
    let uIndex = findUserIndexByPhone(deposit.userId);
    
    deposits[dIndex].status = 'rejected';
    
    if(uIndex !== -1) {
        let user = users[uIndex];
        user.transactions.push({ type: 'Deposit Rejected', amount: 0, date: new Date().toLocaleString(), dateISO: todayISO(), details: `Deposit Rejected ৳${deposit.amount}` });
        users[uIndex] = user;
        setLoggedUser(user.phone);
        if(currentUser && currentUser.phone === user.phone) updateDashboard(); 
    }
    
    saveAll();
    loadAdminDeposits();
    alert('Deposit request rejected.');
}

function loadAdminWithdraws(){
    let table = document.getElementById('withdrawTable').getElementsByTagName('tbody')[0];
    table.innerHTML = '';
    
    withdraws.filter(w => w.status === 'pending').forEach(w => {
        let row = table.insertRow();
        row.insertCell().innerText = w.userName;
        row.insertCell().innerText = `৳${formatNumber(w.amount, 2)}`;
        row.insertCell().innerText = w.method;
        row.insertCell().innerText = w.number;
        row.insertCell().innerHTML = statusPill(w.status);
        
        let actionCell = row.insertCell();
        actionCell.innerHTML = `
            <button class="action-btn approve" onclick="approveWithdraw('${w.id}')">Approve</button>
            <button class="action-btn reject" onclick="rejectWithdraw('${w.id}')">Reject</button>
        `;
    });
}
function approveWithdraw(id){
    let wIndex = withdraws.findIndex(w => w.id === id);
    if(wIndex === -1) return;
    let withdraw = withdraws[wIndex];
    
    let uIndex = findUserIndexByPhone(withdraw.userId);
    if(uIndex !== -1){
        let user = users[uIndex];

        withdraws[wIndex].status = 'approved';
        
        if(!user.firstWithdrawDone){
            user.firstWithdrawDone = true;
        }
        user.transactions.push({ type: 'Withdraw Approved', amount: -withdraw.amount, date: new Date().toLocaleString(), dateISO: todayISO(), details: `Withdraw Approved ৳${withdraw.amount}` });
        
        users[uIndex] = user;
        saveAll();
        loadAdminWithdraws();
        
        if(currentUser && currentUser.phone === user.phone) updateDashboard();
        
        alert(`Withdraw ৳${formatNumber(withdraw.amount, 2)} for ${withdraw.userName} approved!`);
    } else {
        alert('User not found!');
    }
}
function rejectWithdraw(id){
    let wIndex = withdraws.findIndex(w => w.id === id);
    if(wIndex === -1) return;
    let withdraw = withdraws[wIndex];
    
    let uIndex = findUserIndexByPhone(withdraw.userId);
    
    if(uIndex !== -1){
        let user = users[uIndex];
        // Refund the amount that was deducted in submitWithdraw()
        user.balance = Number((user.balance + withdraw.amount).toFixed(2)); 
        
        user.transactions.push({ type: 'Withdraw Rejected (Refund)', amount: withdraw.amount, date: new Date().toLocaleString(), dateISO: todayISO(), details: `Refund ৳${withdraw.amount} (Withdraw Rejected)` });
        
        users[uIndex] = user;
        setLoggedUser(user.phone);
        
        if(currentUser && currentUser.phone === user.phone) updateDashboard();
    }
    
    withdraws[wIndex].status = 'rejected';
    saveAll();
    loadAdminWithdraws();
    alert('Withdraw request rejected and amount refunded (if user exists).');
}

function loadAdminHelp(){
    let list = document.getElementById('adminHelpList');
    list.innerHTML = '';
    
    helps.filter(h => h.status === 'pending').forEach(h => {
        list.innerHTML += `
            <div class="card" style="border:1px solid #ffc371; padding:12px; margin-bottom:10px;">
                <div style="display:flex; justify-content:space-between;">
                    <b>${escapeHtml(h.userName)} (${escapeHtml(h.userId)})</b>
                    <span class="small muted">${escapeHtml(h.date)}</span>
                </div>
                <p style="margin:5px 0;">Message: ${escapeHtml(h.message)}</p>
                <textarea id="reply_${h.id}" placeholder="Type your reply here"></textarea>
                <button onclick="sendReply('${h.id}')">Send Reply</button>
            </div>
        `;
    });
    
    if(list.innerHTML === '') list.innerHTML = '<p class="muted">No pending support requests.</p>';
}
function sendReply(id){
    let reply = document.getElementById(`reply_${id}`).value.trim();
    if(!reply) return alert('Enter a reply message.');
    
    let hIndex = helps.findIndex(h => h.id === id);
    if(hIndex === -1) return;
    
    helps[hIndex].reply = reply;
    helps[hIndex].status = 'answered';
    saveAll();
    
    loadAdminHelp();
    alert('Reply sent!');
}

function sendNotice(){
    let notice = document.getElementById('noticeMessage').value.trim();
    localStorage.setItem('notice', notice);
    noticeText = notice; // Update local variable for checking
    
    // Ensure the dashboard view is updated for logged-in users if needed
    if(currentUser) {
        let noticeEl = document.getElementById('userNotice');
        if (noticeEl) {
            noticeEl.innerHTML = `⚠️ Notice: ${escapeHtml(noticeText)}`;
            // Make sure visibility is checked again if it's the home screen
            const isHome = !document.getElementById('home').classList.contains('hidden');
            controlHeaderVisibility(isHome);
        }
    }
    
    alert('Notice sent to all users.');
    document.getElementById('noticeMessage').value = '';
}


// Initial checks on page load
if(currentUser){
    document.getElementById('userDashboard').classList.remove('hidden');
    document.getElementById('adminPanel').classList.add('hi
