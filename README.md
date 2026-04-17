AI 캐릭터 채팅 앱 body { font-family: sans-serif; background:#111; color:#fff; margin:0; } .container { display:flex; height:100vh; } .sidebar { width:250px; background:#1e1e1e; padding:10px; overflow:auto; } .chat { flex:1; display:flex; flex-direction:column; } .messages { flex:1; padding:10px; overflow:auto; } .input { display:flex; } input { flex:1; padding:10px; } button { padding:10px; cursor:pointer; } .char { border:1px solid #444; padding:5px; margin:5px 0; cursor:pointer; } img { width:100%; border-radius:10px; } 

캐릭터 

추가 

전송 

let characters = []; let current = null; function addCharacter() { const name = document.getElementById('charName').value; const file = document.getElementById('charImg').files[0]; const reader = new FileReader(); reader.onload = function(e) { const char = { name, img:e.target.result }; characters.push(char); render(); // 링크 생성 const link = location.href + "#" + btoa(JSON.stringify(char)); alert("공유 링크: " + link); } if(file) reader.readAsDataURL(file); } function render() { const div = document.getElementById('characters'); div.innerHTML = ''; characters.forEach((c,i)=>{ const el = document.createElement('div'); el.className='char'; el.innerHTML = `

${c.name}

`; el.onclick = ()=>{ current=c; }; div.appendChild(el); }); } function send() { const msg = document.getElementById('msg').value; const box = document.getElementById('messages'); box.innerHTML += `

나: ${msg}

`; if(current) { // 간단 AI 응답 const reply = current.name + 
