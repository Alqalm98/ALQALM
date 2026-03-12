<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width,initial-scale=1">
    <title>School Manager Pro X | النظام المتكامل</title>
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #2563eb;
            --primary-dark: #1e40af;
            --secondary: #64748b;
            --success: #22c55e;
            --danger: #ef4444;
            --bg: #f8fafc;
            --card: #ffffff;
            --text: #1e293b;
        }

        * { box-sizing: border-box; }
        body { font-family: 'Tajawal', sans-serif; background: var(--bg); color: var(--text); margin: 0; line-height: 1.6; }
        
        /* Login Layer */
        #login { position: fixed; inset: 0; background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%); display: flex; align-items: center; justify-content: center; z-index: 1000; transition: 0.5s; }
        .loginBox { background: var(--card); padding: 40px; border-radius: 16px; width: 90%; max-width: 400px; box-shadow: 0 20px 25px -5px rgba(0,0,0,0.3); text-align: center; }
        
        /* Header & Navigation */
        header { background: var(--card); padding: 15px 20px; text-align: center; font-size: 22px; font-weight: bold; border-bottom: 2px solid var(--primary); color: var(--primary); display: flex; justify-content: space-between; align-items: center; }
        .logout-btn { font-size: 14px; color: var(--danger); cursor: pointer; border: 1px solid var(--danger); padding: 5px 10px; border-radius: 5px; }

        nav { display: flex; gap: 8px; flex-wrap: wrap; margin: 20px 0; background: var(--card); padding: 10px; border-radius: 12px; box-shadow: 0 1px 3px rgba(0,0,0,0.1); }
        nav button { flex: 1; padding: 12px; border-radius: 8px; border: none; background: transparent; color: var(--secondary); cursor: pointer; font-weight: 600; transition: 0.3s; min-width: 110px; font-family: inherit; }
        nav button:hover { background: #f1f5f9; color: var(--primary); }
        nav button.active { background: var(--primary); color: white; }

        /* Main Content */
        .container { padding: 0 20px 40px; max-width: 1200px; margin: auto; }
        .card { background: var(--card); padding: 20px; border-radius: 12px; margin-bottom: 20px; box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05); border: 1px solid #e2e8f0; }
        .section-title { margin-top: 0; color: var(--primary); border-right: 4px solid var(--primary); padding-right: 10px; margin-bottom: 20px; }
        
        /* Stats Dashboard */
        .statGrid { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 20px; margin-bottom: 25px; }
        .stat { background: var(--card); padding: 20px; border-radius: 16px; text-align: center; box-shadow: 0 4px 12px rgba(0,0,0,0.05); transition: 0.3s; }
        .stat:hover { transform: translateY(-5px); }
        .stat h3 { margin: 0; font-size: 32px; color: var(--primary); }
        .stat p { margin: 5px 0 0; color: var(--secondary); font-size: 16px; }

        /* Forms & Interactive Elements */
        .form-group { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 10px; margin-bottom: 15px; }
        input, select { padding: 12px; border-radius: 8px; border: 1px solid #cbd5e1; width: 100%; font-family: inherit; font-size: 14px; }
        input:focus { outline: none; border-color: var(--primary); box-shadow: 0 0 0 3px rgba(37,99,235,0.1); }
        
        button { padding: 12px 20px; border-radius: 8px; border: none; cursor: pointer; font-weight: bold; transition: 0.2s; font-family: inherit; }
        .btn-main { background: var(--primary); color: white; }
        .btn-main:hover { background: var(--primary-dark); }
        .btn-danger { background: #fee2e2; color: var(--danger); }
        .btn-danger:hover { background: var(--danger); color: white; }

        /* Tables */
        .table-container { overflow-x: auto; }
        table { width: 100%; border-collapse: collapse; }
        th { background: #f1f5f9; color: var(--secondary); padding: 12px; text-align: right; }
        td { padding: 12px; border-bottom: 1px solid #f1f5f9; }
        tr:hover { background: #f8fafc; }

        /* Toast Message */
        #toast { position: fixed; bottom: 20px; right: 20px; background: #1e293b; color: white; padding: 12px 25px; border-radius: 8px; display: none; z-index: 2000; box-shadow: 0 10px 15px rgba(0,0,0,0.2); }
    </style>
</head>
<body>

<div id="toast"></div>

<div id="login">
    <div class="loginBox">
        <h2 style="color:var(--primary); margin-bottom:10px;">تسجيل الدخول</h2>
        <p style="color:var(--secondary); margin-bottom:25px;">نظام إدارة المدرسة الاحترافي</p>
        <input id="user" placeholder="اسم المستخدم" style="margin-bottom:15px">
        <input id="pass" type="password" placeholder="كلمة المرور" style="margin-bottom:20px">
        <button class="btn-main" style="width:100%" onclick="login()">دخول النظام</button>
        <p style="font-size:12px; color:#94a3b8; margin-top:20px;">البيانات الافتراضية: admin / 1234</p>
    </div>
</div>

<header>
    <span>School Manager <small style="color:var(--secondary)">v4.0</small></span>
    <span class="logout-btn" onclick="location.reload()">تسجيل خروج</span>
</header>

<div class="container" id="app" style="display:none">
    <nav id="mainNav">
        <button onclick="show('dashboard', this)" class="active">لوحة التحكم</button>
        <button onclick="show('students', this)">الطلاب</button>
        <button onclick="show('teachers', this)">المعلمين</button>
        <button onclick="show('classes', this)">الصفوف</button>
        <button onclick="show('attendance', this)">الحضور</button>
        <button onclick="show('fees', this)">الأقساط</button>
        <button onclick="show('reports', this)">الإعدادات</button>
    </nav>

    <div id="dashboard" class="section">
        <h3 class="section-title">ملخص إحصائي</h3>
        <div class="statGrid">
            <div class="stat"><h3 id="statStudents">0</h3><p>طالب</p></div>
            <div class="stat"><h3 id="statTeachers">0</h3><p>معلم</p></div>
            <div class="stat"><h3 id="statClasses">0</h3><p>صف دراسي</p></div>
            <div class="stat"><h3 id="statMoney">0</h3><p>التحصيل المالي</p></div>
        </div>
    </div>

    <div id="students" class="section" style="display:none">
        <div class="card">
            <h3 class="section-title">إضافة طالب</h3>
            <div class="form-group">
                <input id="s_name" placeholder="اسم الطالب بالكامل">
                <select id="s_class"></select>
                <input id="s_parent" placeholder="اسم ولي الأمر">
                <input id="s_phone" placeholder="رقم الهاتف">
            </div>
            <button class="btn-main" onclick="addStudent()">حفظ البيانات</button>
        </div>
        <div class="card">
            <input id="studentSearch" placeholder="بحث سريع عن طالب..." oninput="render()" style="margin-bottom:15px; border-color: var(--primary);">
            <div class="table-container">
                <table>
                    <thead><tr><th>الاسم</th><th>الصف</th><th>ولي الأمر</th><th>الهاتف</th><th>حذف</th></tr></thead>
                    <tbody id="studentsTable"></tbody>
                </table>
            </div>
        </div>
    </div>

    <div id="teachers" class="section" style="display:none">
        <div class="card">
            <h3 class="section-title">إضافة معلم</h3>
            <div class="form-group">
                <input id="t_name" placeholder="اسم المعلم">
                <input id="t_subject" placeholder="التخصص / المادة">
                <button class="btn-main" onclick="addTeacher()">إضافة معلم</button>
            </div>
        </div>
        <div class="card table-container">
            <table>
                <thead><tr><th>الاسم</th><th>المادة</th><th>الإجراء</th></tr></thead>
                <tbody id="teachersTable"></tbody>
            </table>
        </div>
    </div>

    <div id="classes" class="section" style="display:none">
        <div class="card">
            <h3 class="section-title">إدارة الصفوف</h3>
            <div style="display:flex; gap:10px">
                <input id="class_name" placeholder="اسم الصف (مثال: سادس - ب)">
                <button class="btn-main" onclick="addClass()">إضافة</button>
            </div>
        </div>
        <div class="card">
            <div id="classesList" style="display:grid; grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); gap:10px;"></div>
        </div>
    </div>

    <div id="attendance" class="section" style="display:none">
        <div class="card">
            <h3 class="section-title">تسجيل الغياب اليومي</h3>
            <div class="form-group">
                <select id="att_student"></select>
                <select id="att_status">
                    <option value="حاضر">حاضر ✅</option>
                    <option value="غائب">غائب ❌</option>
                </select>
                <button class="btn-main" onclick="markAttendance()">تسجيل الحالة</button>
            </div>
        </div>
        <div class="card table-container">
            <table>
                <thead><tr><th>الطالب</th><th>الحالة</th><th>التاريخ والوقت</th></tr></thead>
                <tbody id="attendanceTable"></tbody>
            </table>
        </div>
    </div>

    <div id="fees" class="section" style="display:none">
        <div class="card">
            <h3 class="section-title">المحاسبة والرسوم</h3>
            <div class="form-group">
                <select id="fee_student"></select>
                <input id="fee_amount" type="number" placeholder="المبلغ المدفوع">
                <button class="btn-main" onclick="payFee()">تأكيد العملية</button>
            </div>
        </div>
        <div class="card table-container">
            <table>
                <thead><tr><th>الطالب</th><th>المبلغ</th><th>التاريخ</th></tr></thead>
                <tbody id="feesTable"></tbody>
            </table>
        </div>
    </div>

    <div id="reports" class="section" style="display:none">
        <div class="card">
            <h3 class="section-title">إدارة النظام</h3>
            <p>يمكنك تصدير نسخة من البيانات لاستخدامها لاحقاً أو حذف جميع السجلات لبدء سنة دراسية جديدة.</p>
            <div style="display:flex; gap:10px; margin-top:20px;">
                <button class="btn-main" onclick="backup()">تحميل نسخة احتياطية</button>
                <button class="btn-danger" onclick="clearAll()">تصفير كافة البيانات</button>
            </div>
        </div>
    </div>
</div>

<script>
    // Database Manager
    const db = {
        get: (key) => JSON.parse(localStorage.getItem('smx_v4_'+key) || "[]"),
        set: (key, val) => localStorage.setItem('smx_v4_'+key, JSON.stringify(val))
    };

    function notify(text) {
        const toast = document.getElementById('toast');
        toast.innerText = text;
        toast.style.display = 'block';
        setTimeout(() => toast.style.display = 'none', 3000);
    }

    function login(){
        if(user.value === "admin" && pass.value === "1234"){
            document.getElementById('login').style.opacity = "0";
            setTimeout(() => {
                document.getElementById('login').style.display = "none";
                document.getElementById('app').style.display = "block";
                render();
            }, 500);
        } else {
            alert("بيانات الدخول خاطئة!");
        }
    }

    function show(id, btn){
        document.querySelectorAll('.section').forEach(s => s.style.display = 'none');
        document.querySelectorAll('nav button').forEach(b => b.classList.remove('active'));
        document.getElementById(id).style.display = 'block';
        btn.classList.add('active');
    }

    // CRUD Operations
    function addStudent(){
        if(!s_name.value || s_class.value === "") return alert("أكمل البيانات");
        let list = db.get("students");
        list.push({name: s_name.value, cls: s_class.value, parent: s_parent.value, phone: s_phone.value});
        db.set("students", list);
        s_name.value = s_parent.value = s_phone.value = "";
        render();
        notify("تمت إضافة الطالب بنجاح");
    }

    function addTeacher(){
        if(!t_name.value) return;
        let list = db.get("teachers");
        list.push({name: t_name.value, sub: t_subject.value});
        db.set("teachers", list);
        t_name.value = t_subject.value = "";
        render();
        notify("تمت إضافة المعلم");
    }

    function addClass(){
        if(!class_name.value) return;
        let list = db.get("classes");
        list.push({name: class_name.value});
        db.set("classes", list);
        class_name.value = "";
        render();
    }

    function deleteItem(key, i){
        if(!confirm("هل أنت متأكد من الحذف؟")) return;
        let list = db.get(key);
        list.splice(i, 1);
        db.set(key, list);
        render();
    }

    function markAttendance(){
        let list = db.get("attendance");
        list.unshift({student: att_student.value, status: att_status.value, date: new Date().toLocaleString('ar-EG')});
        db.set("attendance", list);
        render();
        notify("تم تسجيل الحضور");
    }

    function payFee(){
        if(!fee_amount.value) return;
        let list = db.get("fees");
        list.unshift({student: fee_student.value, amount: fee_amount.value, date: new Date().toLocaleDateString('ar-EG')});
        db.set("fees", list);
        fee_amount.value = "";
        render();
        notify("تم استلام المبلغ");
    }

    function render(){
        const students = db.get("students");
        const teachers = db.get("teachers");
        const classes = db.get("classes");
        const attendance = db.get("attendance");
        const fees = db.get("fees");

        // Stats
        statStudents.innerText = students.length;
        statTeachers.innerText = teachers.length;
        statClasses.innerText = classes.length;
        statMoney.innerText = fees.reduce((a,b) => a + Number(b.amount), 0).toLocaleString() + " ج.م";

        // Lists
        const q = studentSearch.value.toLowerCase();
        studentsTable.innerHTML = "";
        att_student.innerHTML = "";
        fee_student.innerHTML = "";
        students.forEach((s, i) => {
            if(s.name.toLowerCase().includes(q)){
                studentsTable.innerHTML += `<tr><td>${s.name}</td><td>${s.cls}</td><td>${s.parent}</td><td>${s.phone}</td><td><button class="btn-danger" onclick="deleteItem('students',${i})">حذف</button></td></tr>`;
            }
            att_student.innerHTML += `<option>${s.name}</option>`;
            fee_student.innerHTML += `<option>${s.name}</option>`;
        });

        teachersTable.innerHTML = "";
        teachers.forEach((t, i) => {
            teachersTable.innerHTML += `<tr><td>${t.name}</td><td>${t.sub}</td><td><button class="btn-danger" onclick="deleteItem('teachers',${i})">حذف</button></td></tr>`;
        });

        classesList.innerHTML = "";
        s_class.innerHTML = `<option value="">اختر الصف...</option>`;
        classes.forEach((c, i) => {
            classesList.innerHTML += `<div class="stat" style="padding:10px; display:flex; justify-content:space-between; align-items:center;"><span>${c.name}</span><button class="btn-danger" style="padding:4px 8px" onclick="deleteItem('classes',${i})">×</button></div>`;
            s_class.innerHTML += `<option>${c.name}</option>`;
        });

        attendanceTable.innerHTML = "";
        attendance.slice(0, 15).forEach(a => {
            attendanceTable.innerHTML += `<tr><td>${a.student}</td><td style="color:${a.status==='غائب'?'red':'green'}">${a.status}</td><td style="font-size:12px">${a.date}</td></tr>`;
        });

        feesTable.innerHTML = "";
        fees.slice(0, 15).forEach(f => {
            feesTable.innerHTML += `<tr><td>${f.student}</td><td>${f.amount} ج.م</td><td>${f.date}</td></tr>`;
        });
    }

    function backup(){
        const data = JSON.stringify(localStorage);
        const blob = new Blob([data], {type: 'application/json'});
        const a = document.createElement('a');
        a.href = URL.createObjectURL(blob);
        a.download = 'school_data_backup.json';
        a.click();
    }

    function clearAll(){
        if(confirm("سيتم حذف كل البيانات نهائياً! هل أنت متأكد؟")){
            localStorage.clear();
            location.reload();
        }
    }
</script>

</body>
</html>
