<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TimeHero – Premium Web MVP</title>
<style>
body { margin:0; font-family: 'Segoe UI', sans-serif; background:#f0f4ff; color:#1f2937; }
header { background: linear-gradient(90deg,#5b4b8a,#7f5ce3); color:white; padding:20px; text-align:center; font-size:24px; font-weight:bold; box-shadow:0 4px 8px rgba(0,0,0,0.1); }
.container { padding:20px; max-width:960px; margin:auto; display:grid; grid-gap:20px; }
.card { background:white; border-radius:16px; padding:20px; box-shadow:0 8px 20px rgba(0,0,0,0.1); transition: transform 0.2s; }
.card:hover { transform: translateY(-4px); }
.card h3 { margin-top:0; color:#5b4b8a; }
button { background: linear-gradient(90deg,#5b4b8a,#7f5ce3); color:white; border:none; padding:12px 20px; border-radius:10px; cursor:pointer; font-weight:bold; transition: opacity 0.2s; }
button:hover { opacity:0.9; }
.task { display:flex; justify-content:space-between; padding:12px 0; border-bottom:1px solid #eee; align-items:center; }
.task:last-child { border-bottom:none; }
input[type=text], input[type=number] { width:100%; padding:10px; margin-bottom:10px; border-radius:10px; border:1px solid #d1d5db; }
.focus { background: #e0e7ff; border-left:6px solid #5b4b8a; padding-left:14px; }
.progress-bar { width:100%; background:#e5e7eb; border-radius:10px; overflow:hidden; margin-top:10px; }
.progress { height:12px; background: linear-gradient(90deg,#5b4b8a,#7f5ce3); width:0%; transition: width 0.5s; }
.motivation { font-style:italic; color:#4f46e5; font-weight:bold; text-align:center; margin-top:10px; }
</style>
</head>
<body>
<header>TimeHero – Premium Web MVP</header>
<div class="container">

<div class="card">
<h3>🎯 Today’s Focus</h3>
<p id="today-focus">IELTS Speaking Practice – 40 minutes</p>
<button onclick="startFocus()">Start Focus Session</button>
<div class="progress-bar"><div class="progress" id="focus-progress"></div></div>
</div>

<div class="card">
<h3>📝 Tasks</h3>
<div id="task-list">
<div class="task"><span>📘 Study Vocabulary</span><span>✔</span></div>
<div class="task"><span>🗣 Speaking Practice</span><span>⏳</span></div>
<div class="task"><span>📚 Homework</span><span>⏳</span></div>
</div>
<input type="text" id="new-task-name" placeholder="Task name">
<input type="number" id="new-task-time" placeholder="Time (minutes)">
<button onclick="addTask()">Add Task</button>
</div>

<div class="card focus">
<h3>🔒 Screen Control</h3>
<p>During focus mode, social media and distractions are minimized.</p>
<strong>Status: <span id="focus-status">OFF</span></strong>
</div>

<div class="card motivation">
<h3>🔥 Motivation</h3>
<p id="motivation-text">“Small steps every day lead to big results.”</p>
</div>
</div>
<script>
let focusProgress = 0;
let focusInterval;
const motivationQuotes = [
  'Small steps every day lead to big results.',
  'Consistency is the key to mastery.',
  'Focus on what matters most.',
  'Your effort compounds over time.'
];
function addTask(){
let name=document.getElementById('new-task-name').value;
let taskList=document.getElementById('task-list');
if(name){
let div=document.createElement('div');
div.className='task';
div.innerHTML=`<span>📌 ${name}</span><span>⏳</span>`;
taskList.appendChild(div);
}
}
function startFocus(){
alert('Focus Mode Started! Avoid distractions.');
document.getElementById('focus-status').innerText='ON';
focusProgress = 0;
const progressBar=document.getElementById('focus-progress');
focusInterval=setInterval(()=>{
if(focusProgress>=100){ clearInterval(focusInterval); alert('Focus Session Completed!'); document.getElementById('focus-status').innerText='OFF'; return; }
focusProgress+=2;
progressBar.style.width=focusProgress+'%';
},600);
// change motivation
document.getElementById('motivation-text').innerText = motivationQuotes[Math.floor(Math.random()*motivationQuotes.length)];
}
</script>
</body>
</html>
