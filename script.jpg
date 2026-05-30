let tasks = JSON.parse(localStorage.getItem('hd_tasks_v3')||'[]');
let stats = JSON.parse(localStorage.getItem('hd_stats_v3')||'{"sessions":0,"mins":0,"date":""}');

function renderTasks() {
    const list = document.getElementById('taskList');
    if(!list) return;
    list.innerHTML = '';
    tasks.forEach((t, i) => {
        const done = t.sessions >= t.target;
        list.innerHTML += `
            <div class="task-item ${done ? 'done' : ''}">
                <span class="task-name">${t.text}</span>
                <div class="sess-ctrl">
                    <button class="sess-btn" onclick="chSess(${i}, -1)">−</button>
                    <span class="sess-num">${t.sessions}/${t.target}</span>
                    <button class="sess-btn" onclick="chSess(${i}, 1)">+</button>
                </div>
            </div>
        `;
    });
}

function chSess(i, d) {
    tasks[i].sessions = Math.max(0, Math.min(tasks[i].target, tasks[i].sessions + d));
    if(d > 0) { stats.sessions++; stats.mins += 25; }
    localStorage.setItem('hd_tasks_v3', JSON.stringify(tasks));
    localStorage.setItem('hd_stats_v3', JSON.stringify(stats));
    renderTasks();
}

renderTasks();
