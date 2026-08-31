<!DOCTYPE html>
<html lang="ar" dir="rtl" data-theme="dark">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Super Mini | المنصة المالية الرقمية المشفرة</title>
  <style>
    :root {
      --bg-main: #070a12;
      --card-bg: rgba(17, 24, 39, 0.92);
      --card-border: rgba(245, 158, 11, 0.35);
      --text-main: #f9fafb;
      --text-muted: #9ca3af;
      --accent-gold: #f59e0b;
      --accent-gold-glow: rgba(245, 158, 11, 0.6);
      --accent-green: #10b981;
      --accent-green-glow: rgba(16, 185, 129, 0.6);
      --accent-blue: #3b82f6;
      --accent-red: #ef4444;
      --accent-red-glow: rgba(239, 68, 68, 0.4);
      --qi-color: #fbbc04;
      --zain-color: #ff007f;
      --glass-bg: rgba(15, 23, 42, 0.92);
      --shadow-lux: 0 12px 35px -5px rgba(0, 0, 0, 0.8), 0 0 20px rgba(245, 158, 11, 0.2);
    }

    * { box-sizing: border-box; margin: 0; padding: 0; font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif; transition: all 0.22s ease-in-out; }
    body { background-color: var(--bg-main); color: var(--text-main); display: flex; justify-content: center; min-height: 100vh; overflow-x: hidden; }
    
    .app-container { width: 100%; max-width: 440px; background: var(--bg-main); position: relative; padding-bottom: 95px; min-height: 100vh; border-left: 1px solid var(--card-border); border-right: 1px solid var(--card-border); display: none; }
    .app-container.logged-in { display: block; }

    .live-ticker { background: linear-gradient(90deg, #111827, #1e1b4b, #111827); border-bottom: 1px solid var(--card-border); padding: 8px 12px; font-size: 11px; color: var(--accent-gold); overflow: hidden; white-space: nowrap; font-weight: 700; }
    .ticker-content { display: inline-block; animation: ticker 25s linear infinite; }
    @keyframes ticker { 0% { transform: translateX(100%); } 100% { transform: translateX(-100%); } }

    .login-overlay { position: fixed; top: 0; left: 0; right: 0; bottom: 0; background: rgba(3, 7, 18, 0.98); backdrop-filter: blur(25px); display: flex; justify-content: center; align-items: center; padding: 20px; z-index: 5000; }
    .login-card { width: 100%; max-width: 370px; background: var(--glass-bg); border: 1px solid var(--card-border); padding: 32px 24px; border-radius: 28px; text-align: center; box-shadow: var(--shadow-lux); position: relative; }
    .brand-badge { font-size: 28px; font-weight: 900; letter-spacing: 1px; color: var(--accent-gold); margin-bottom: 4px; text-shadow: 0 0 15px var(--accent-gold-glow); }
    .login-card p { font-size: 12px; color: var(--text-muted); margin-bottom: 22px; }

    .error-msg { background: rgba(239, 68, 68, 0.15); border: 1px solid var(--accent-red); color: var(--accent-red); font-size: 12px; font-weight: 800; padding: 10px; border-radius: 12px; margin-bottom: 16px; display: none; }

    .btn-ultra {
      position: relative;
      width: 100%;
      padding: 14px 20px;
      border-radius: 14px;
      font-weight: 800;
      font-size: 14px;
      cursor: pointer;
      border: none;
      outline: none;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      overflow: hidden;
      text-decoration: none;
      z-index: 1;
      box-shadow: 0 4px 15px rgba(0,0,0,0.3);
    }
    .btn-ultra::after {
      content: '';
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: linear-gradient(60deg, transparent, rgba(255,255,255,0.25), transparent);
      transform: rotate(30deg) translateX(-100%);
      transition: 0.6s;
    }
    .btn-ultra:hover::after { transform: rotate(30deg) translateX(100%); }
    .btn-ultra:active { transform: scale(0.96); }

    .btn-gold { background: linear-gradient(135deg, #f59e0b, #b45309); color: #fff; box-shadow: 0 4px 20px var(--accent-gold-glow); }
    .btn-green { background: linear-gradient(135deg, #10b981, #047857); color: #fff; box-shadow: 0 4px 20px var(--accent-green-glow); }
    .btn-red { background: linear-gradient(135deg, #ef4444, #991b1b); color: #fff; box-shadow: 0 4px 20px var(--accent-red-glow); }
    .btn-outline { background: rgba(255,255,255,0.03); color: var(--text-main); border: 1px solid var(--card-border); backdrop-filter: blur(10px); }
    .btn-outline:hover { border-color: var(--accent-gold); color: var(--accent-gold); }

    .input-group { margin-bottom: 16px; text-align: right; }
    .input-group label { display: block; font-size: 11px; font-weight: 700; margin-bottom: 6px; color: var(--text-muted); }
    .input-group input, .select-css { width: 100%; padding: 14px; border: 1px solid var(--card-border); border-radius: 12px; font-size: 13px; background: rgba(0,0,0,0.5); color: var(--text-main); outline: none; }
    .input-group input:focus, .select-css:focus { border-color: var(--accent-gold); box-shadow: 0 0 12px var(--accent-gold-glow); }

    .header { display: flex; justify-content: center; align-items: center; padding: 16px 20px; background: var(--card-bg); border-bottom: 1px solid var(--card-border); position: sticky; top: 0; z-index: 100; backdrop-filter: blur(12px); }
    .brand-title { font-size: 22px; font-weight: 900; color: var(--text-main); text-align: center; }
    .brand-title span { color: var(--accent-gold); }
    
    .tab-content { display: none; opacity: 0; transform: translateY(8px); }
    .tab-content.active { display: block; opacity: 1; transform: translateY(0); }

    .slider-wrapper { position: relative; width: calc(100% - 32px); height: 185px; margin: 16px auto; border-radius: 22px; overflow: hidden; border: 1px solid var(--card-border); box-shadow: var(--shadow-lux); }
    .slides-container { display: flex; width: 100%; height: 100%; transition: transform 0.5s ease-in-out; }
    .slide-item { min-width: 100%; height: 100%; position: relative; }
    .slide-item img { width: 100%; height: 100%; object-fit: cover; }
    .slide-caption { position: absolute; inset: 0; background: linear-gradient(to top, rgba(7, 10, 18, 0.95), rgba(7, 10, 18, 0.1)); display: flex; flex-direction: column; justify-content: flex-end; padding: 16px; }
    .slide-caption h3 { font-size: 15px; font-weight: 800; color: var(--accent-gold); }
    .slide-caption p { font-size: 11px; color: #d1d5db; margin-top: 2px; }

    .account-card { background: var(--card-bg); margin: 0 16px 16px 16px; padding: 18px; border-radius: 22px; border: 1px solid var(--card-border); box-shadow: var(--shadow-lux); }
    .acc-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px; }
    .acc-id { font-size: 13px; font-weight: 800; color: var(--text-main); display: flex; align-items: center; gap: 6px; }
    .verified-mark { width: 18px; height: 18px; background: var(--accent-blue); border-radius: 50%; color: #fff; display: inline-flex; align-items: center; justify-content: center; font-size: 11px; font-weight: bold; }
    .status-badge { background: rgba(16, 185, 129, 0.15); color: var(--accent-green); padding: 4px 10px; border-radius: 12px; font-size: 11px; font-weight: 800; border: 1px solid rgba(16, 185, 129, 0.3); }

    .balance-box { margin-top: 12px; padding: 12px; background: rgba(16, 185, 129, 0.1); border: 1px solid rgba(16, 185, 129, 0.3); border-radius: 14px; display: flex; justify-content: space-between; align-items: center; }
    .balance-title { font-size: 12px; color: var(--text-muted); font-weight: 700; }
    .balance-value { font-size: 16px; color: var(--accent-green); font-weight: 900; }

    .referral-box { background: rgba(0,0,0,0.4); border: 1px dashed var(--card-border); padding: 10px 12px; border-radius: 14px; margin-top: 10px; display: flex; justify-content: space-between; align-items: center; }
    .ref-text { font-size: 11px; color: var(--text-muted); overflow: hidden; text-overflow: ellipsis; white-space: nowrap; max-width: 200px; }

    .admin-card { background: rgba(15, 23, 42, 0.95); border: 2px dashed var(--accent-gold); border-radius: 22px; margin: 16px; padding: 18px; box-shadow: var(--shadow-lux); display: none; }
    .admin-head { font-size: 15px; font-weight: 900; color: var(--accent-gold); margin-bottom: 12px; text-align: center; border-bottom: 1px solid var(--card-border); padding-bottom: 8px; }
    .admin-user-item { background: rgba(0,0,0,0.4); border: 1px solid var(--card-border); padding: 12px; border-radius: 14px; margin-bottom: 10px; }
    .admin-user-info { display: flex; justify-content: space-between; margin-bottom: 8px; font-size: 12px; font-weight: 800; }
    .admin-actions { display: flex; gap: 8px; margin-top: 6px; }
    .admin-actions input { width: 50%; padding: 8px; font-size: 12px; border-radius: 8px; background: #000; color: #fff; border: 1px solid var(--card-border); }

    .section-head { font-size: 16px; font-weight: 900; margin: 24px 16px 14px 16px; display: flex; justify-content: space-between; align-items: center; color: var(--accent-gold); text-shadow: 0 0 10px var(--accent-gold-glow); }
    
    /* تصميم الباقات الفخم والجذاب جداً */
    .packages-list { display: flex; flex-direction: column; gap: 20px; padding: 0 16px; }
    
    .package-item {
      background: linear-gradient(145deg, rgba(26, 31, 46, 0.95), rgba(15, 23, 42, 0.98));
      border: 2px solid var(--accent-gold);
      border-radius: 24px;
      padding: 22px;
      position: relative;
      box-shadow: 0 10px 30px rgba(0,0,0,0.7), 0 0 25px rgba(245, 158, 11, 0.25);
      overflow: hidden;
    }
    .package-item::before {
      content: '🔥 باقة استثمارية VIP';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      background: linear-gradient(90deg, #f59e0b, #b45309);
      color: #fff;
      font-size: 11px;
      font-weight: 900;
      text-align: center;
      padding: 4px 0;
      letter-spacing: 1px;
    }
    
    .pkg-top { display: flex; justify-content: space-between; align-items: center; margin-top: 14px; margin-bottom: 16px; }
    .pkg-title { font-size: 24px; font-weight: 900; color: #ffffff; text-shadow: 0 0 10px rgba(255,255,255,0.3); }
    .pkg-tag { background: rgba(16, 185, 129, 0.2); color: var(--accent-green); padding: 6px 12px; border-radius: 12px; font-size: 12px; font-weight: 900; border: 1px solid var(--accent-green); box-shadow: 0 0 10px var(--accent-green-glow); }
    
    .pkg-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; background: rgba(0, 0, 0, 0.5); padding: 14px; border-radius: 16px; margin-bottom: 18px; border: 1px solid rgba(255, 255, 255, 0.08); }
    .grid-cell { text-align: center; }
    .grid-cell .label { font-size: 11px; color: var(--text-muted); font-weight: 700; margin-bottom: 4px; }
    .grid-cell .value { font-size: 17px; font-weight: 900; color: var(--accent-green); text-shadow: 0 0 8px var(--accent-green-glow); }

    .modal-overlay { position: fixed; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0, 0, 0, 0.9); backdrop-filter: blur(14px); display: none; justify-content: center; align-items: center; padding: 20px; z-index: 6000; }
    .modal-card { width: 100%; max-width: 360px; background: var(--card-bg); border: 1px solid var(--card-border); padding: 26px; border-radius: 24px; text-align: center; box-shadow: var(--shadow-lux); }
    .modal-card h3 { color: var(--accent-gold); margin-bottom: 12px; font-size: 18px; font-weight: 900; }
    .modal-card p { font-size: 13px; line-height: 1.6; color: var(--text-main); margin-bottom: 22px; }

    .payment-card { background: var(--card-bg); border: 1px solid var(--card-border); border-radius: 20px; padding: 18px; margin: 16px; box-shadow: var(--shadow-lux); }
    .pay-header { display: flex; align-items: center; gap: 12px; margin-bottom: 14px; }
    .pay-logo-box { width: 44px; height: 44px; border-radius: 12px; display: flex; align-items: center; justify-content: center; font-weight: 900; font-size: 13px; color: #fff; }
    .qi-style { background: #1e293b; border: 2px solid var(--qi-color); color: var(--qi-color); }
    .zain-style { background: linear-gradient(135deg, #d946ef, #8b5cf6); color: #fff; }

    .pay-details { background: rgba(0,0,0,0.4); padding: 12px 14px; border-radius: 12px; margin-bottom: 12px; font-size: 12px; }
    .pay-row { display: flex; justify-content: space-between; align-items: center; padding: 6px 0; border-bottom: 1px solid rgba(255,255,255,0.05); }
    .pay-row:last-child { border-bottom: none; }
    .pay-val { font-weight: 800; color: var(--accent-gold); font-size: 14px; }

    .file-css { width: 100%; padding: 12px; background: rgba(0,0,0,0.3); border: 1px dashed var(--card-border); color: var(--text-muted); border-radius: 12px; margin-bottom: 12px; font-size: 12px; cursor: pointer; }

    .image-preview-container { margin-bottom: 16px; display: none; text-align: center; border: 1px solid var(--accent-gold); padding: 8px; border-radius: 14px; background: rgba(0,0,0,0.4); }
    .image-preview-container img { max-width: 100%; max-height: 200px; border-radius: 10px; object-fit: contain; }

    .history-item { background: rgba(0,0,0,0.4); border: 1px solid var(--card-border); border-radius: 14px; padding: 12px; margin-bottom: 10px; display: flex; justify-content: space-between; align-items: center; font-size: 12px; }
    .status-pending { color: var(--accent-gold); background: rgba(245, 158, 11, 0.15); padding: 3px 8px; border-radius: 8px; font-weight: bold; }

    .profile-card { background: var(--card-bg); border: 1px solid var(--card-border); border-radius: 24px; padding: 24px; margin: 16px; text-align: center; box-shadow: var(--shadow-lux); }
    .avatar-ring { width: 75px; height: 75px; background: linear-gradient(135deg, var(--accent-gold), #b45309); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 30px; color: #fff; font-weight: 900; margin: 0 auto 14px auto; box-shadow: 0 0 20px var(--accent-gold-glow); }
    
    .info-list { margin-top: 22px; text-align: right; }
    .info-item { display: flex; justify-content: space-between; padding: 12px 0; border-bottom: 1px solid var(--card-border); font-size: 13px; }

    .nav-bar { position: fixed; bottom: 0; width: 100%; max-width: 440px; background: var(--card-bg); display: flex; justify-content: space-around; align-items: center; height: 72px; border-top: 1px solid var(--card-border); z-index: 100; backdrop-filter: blur(16px); }
    .nav-btn { display: flex; flex-direction: column; align-items: center; font-size: 10px; color: var(--text-muted); gap: 4px; text-decoration: none; font-weight: 800; cursor: pointer; border: none; background: transparent; flex: 1; }
    .nav-btn.active { color: var(--accent-gold); }
    .nav-btn.active svg { fill: var(--accent-gold); filter: drop-shadow(0 0 6px var(--accent-gold-glow)); }
    .nav-svg { width: 20px; height: 20px; fill: var(--text-muted); }
  </style>
</head>
<body>

  <!-- نافذة تسجيل الدخول -->
  <div class="login-overlay" id="loginModal">
    <div class="login-card">
      <div class="brand-badge">Super Mini</div>
      <p>منصة الاستثمار وحماية الحساب المشفرة</p>
      
      <div class="error-msg" id="loginError">⚠️ اسم المستخدم أو كلمة المرور غير صحيحة!</div>

      <div class="input-group">
        <label>اسم المستخدم / معرف الحساب الخاص</label>
        <input type="text" id="userInput" placeholder="أدخل اسم الحساب دقيقاً">
      </div>
      <div class="input-group">
        <label>كلمة المرور (الباسورد)</label>
        <input type="password" id="passInput" placeholder="أدخل كلمة المرور الحصرية">
      </div>
      
      <button class="btn-ultra btn-gold" id="loginBtn" onclick="handleSecureLogin()">تسجيل الدخول الآمن</button>
      <button class="btn-ultra btn-outline" style="margin-top:10px;" onclick="openRegisterModal()">إنشاء حساب جديد فوراً</button>
    </div>
  </div>

  <!-- نافذة إنشاء الحساب -->
  <div class="modal-overlay" id="registerModal">
    <div class="modal-card">
      <div class="brand-badge" style="font-size: 22px;">حساب جديد</div>
      <p style="margin-bottom: 16px;">أنشئ حسابك واستخدم المنصة فوراً</p>
      <div class="error-msg" id="regError"></div>
      
      <div class="input-group">
        <label>اختر اسم الحساب / المعرف الخاص بك</label>
        <input type="text" id="regUser" placeholder="مثال: Ahmed99 أو رقم معرف">
      </div>
      <div class="input-group">
        <label>اختر كلمة المرور</label>
        <input type="password" id="regPass" placeholder="كلمة المرور">
      </div>
      <div class="input-group">
        <label>تأكيد كلمة المرور</label>
        <input type="password" id="regPassConfirm" placeholder="أعِد كتابة كلمة المرور">
      </div>

      <button class="btn-ultra btn-green" onclick="handleRegister()">تأكيد وإنشاء الحساب</button>
      <button class="btn-ultra btn-outline" style="margin-top:10px;" onclick="closeModal('registerModal')">إلغاء والعودة</button>
    </div>
  </div>

  <!-- نافذة إشعار نجاح طلب السحب (24 إلى 48 ساعة) -->
  <div class="modal-overlay" id="withdrawNoticeModal">
    <div class="modal-card">
      <div style="font-size: 40px; margin-bottom: 10px;">✅</div>
      <h3 style="color: var(--accent-green);">تم إرسال طلب السحب بنجاح</h3>
      <p style="font-size: 14px; font-weight: bold; color: #fff; margin-top: 10px;">
        سوف تصلك الأموال إلى حسابك المرفق خلال <strong>24 ساعة إلى 48 ساعة</strong> كحد أقصى.
      </p>
      <button class="btn-ultra btn-gold" style="margin-top: 15px;" onclick="closeModal('withdrawNoticeModal')">موافق</button>
    </div>
  </div>

  <div class="modal-overlay" id="subModal">
    <div class="modal-card">
      <h3>تفاصيل الخطة الاستثمارية</h3>
      <p id="subDetailsText">تفاصيل الباقة...</p>
      <button class="btn-ultra btn-green" onclick="proceedToPayment()">متابعة وتأكيد الاشتراك</button>
      <button class="btn-ultra btn-outline" style="margin-top:10px;" onclick="closeModal('subModal')">إلغاء</button>
    </div>
  </div>

  <div class="modal-overlay" id="errModal">
    <div class="modal-card">
      <h3 style="color: var(--accent-red);">⚠️ تنبيه: لا يوجد رصيد كافٍ</h3>
      <p>عذراً، يرجى تعبئة حسابك بالمبلغ المباشر أولاً من قسم <strong>الأمور المالية</strong> وإرفاق إشعار التحويل لتفعيل الباقة.</p>
      <button class="btn-ultra btn-gold" onclick="goToFinance()">الانتقال إلى الأمور المالية</button>
    </div>
  </div>

  <div id="toast" style="position:fixed; top:20px; left:50%; transform:translateX(-50%); background:var(--accent-green); color:#fff; padding:10px 20px; border-radius:12px; font-weight:800; font-size:12px; display:none; z-index:9000; box-shadow:0 4px 15px rgba(0,0,0,0.4);">
    تم العملية بنجاح!
  </div>

  <div class="app-container" id="appContent">
    
    <div class="live-ticker">
      <div class="ticker-content">
        🔥 تم سحب 380,000 IQD عبر زين كاش للحساب 5143... • تم سحب 122,000 IQD عبر كي كارد للحساب 7781... • تم شحن 250,000 IQD بنجاح...
      </div>
    </div>

    <div class="header">
      <div class="brand-title">Super <span>Mini</span></div>
    </div>

    <!-- قسم الرئيسية -->
    <div id="tabHome" class="tab-content active">
      
      <div class="slider-wrapper">
        <div class="slides-container" id="slidesTrack">
          <div class="slide-item"><img src="https://images.unsplash.com/photo-1611974789855-9c2a0a7236a3?auto=format&fit=crop&w=800&q=80"><div class="slide-caption"><h3>تداول رقمي احترافي</h3><p>أعلى عوائد استثمارية بخطط 90 يوماً</p></div></div>
          <div class="slide-item"><img src="https://images.unsplash.com/photo-1590283603385-17ffb3a7f29f?auto=format&fit=crop&w=800&q=80"><div class="slide-caption"><h3>نمو الأرباح اليومية</h3><p>عوائد تنزل تلقائياً في محفظتك</p></div></div>
          <div class="slide-item"><img src="https://images.unsplash.com/photo-1618042164219-62c820f10723?auto=format&fit=crop&w=800&q=80"><div class="slide-caption"><h3>تداول الذهب والأصول</h3><p>إدارة مالية آمنة ومضمونة 100%</p></div></div>
        </div>
      </div>

      <div class="account-card">
        <div class="acc-header">
          <div class="acc-id">
            <span>المشترك: <strong id="userDisplay">--</strong></span>
            <span class="verified-mark">✓</span>
          </div>
          <div class="status-badge">حساب مشفر VIP</div>
        </div>

        <div class="balance-box">
          <span class="balance-title">رصيد المحفظة الحالي:</span>
          <span class="balance-value" id="homeUserBalance">0 IQD</span>
        </div>

        <div class="referral-box">
          <div class="ref-text" id="refLink">--</div>
          <button class="btn-ultra btn-gold" style="width:auto; padding:6px 14px; font-size:11px;" onclick="copyRef()">نسخ الإحالة</button>
        </div>
      </div>

      <div class="admin-card" id="adminPanel">
        <div class="admin-head">👑 لوحة الأدمن الخاصة (إدارة الشحن والسحوبات)</div>
        <button class="btn-ultra btn-green" style="margin-bottom:14px;" onclick="adminAddProfitToAll()">⚡ إشعار أرباح يومية لجميع المشتركين</button>
        <div id="adminUserList"></div>
      </div>

      <div class="section-head">🔥 أقوى باقات الاستثمار المتاحة (90 يوم)</div>
      <div class="packages-list" id="pkgContainer"></div>
    </div>

    <!-- قسم سحب الأموال -->
    <div id="tabWithdraw" class="tab-content">
      <div class="payment-card" style="border-color: var(--accent-gold); margin-top: 16px;">
        <h3 style="color: var(--accent-gold); font-size: 18px; margin-bottom: 6px; text-align: center; font-weight: 900;">💸 طلب سحب الأرباح والأموال</h3>
        <p style="font-size: 11px; color: var(--text-muted); text-align: center; margin-bottom: 16px;">اختر طريقة السحب وأدخل البيانات الخاصة بك لاستلام الأرباح</p>

        <div class="balance-box" style="margin-bottom: 16px; background: rgba(245, 158, 11, 0.1); border-color: rgba(245, 158, 11, 0.3);">
          <span class="balance-title" style="color: var(--accent-gold);">الرصيد المتاح للسحب:</span>
          <span class="balance-value" id="withdrawAvailableBal">0 IQD</span>
        </div>

        <div class="input-group">
          <label>اختر طريقة الاستلام السريع</label>
          <select class="select-css" id="withdrawMethodSelect">
            <option value="ZainCash (زين كاش)">ZainCash (زين كاش)</option>
            <option value="QiCard (بطاقة كي كارد)">Qi Card (بطاقة كي كارد)</option>
          </select>
        </div>

        <div class="input-group">
          <label id="withdrawAccountLabel">رقم الهاتف أو رقم البطاقة للاستلام</label>
          <input type="text" id="withdrawAccountNum" placeholder="أدخل رقم المحفظة أو البطاقة">
        </div>

        <div class="input-group">
          <label>المبلغ المراد سحبه (بالدينار العراقي IQD)</label>
          <input type="number" id="withdrawAmount" placeholder="أدخل المبلغ (الحد الأدنى 10,000 IQD)">
        </div>

        <button class="btn-ultra btn-gold" onclick="processWithdrawalRequest()">تأكيد وإرسال طلب السحب</button>
      </div>

      <div class="section-head">سجل طلبات السحب الخاصة بك</div>
      <div style="padding: 0 16px;" id="withdrawHistoryContainer">
        <p style="font-size:12px; color:var(--text-muted); text-align:center;">لا توجد عمليات سحب سابقة حتى الآن.</p>
      </div>
    </div>

    <!-- قسم الأمور المالية -->
    <div id="tabFinance" class="tab-content">
      <div class="account-card" style="border-color: var(--accent-green); margin-top: 16px;">
        <div class="acc-header">
          <h3 style="color: var(--accent-green); font-size: 16px;">حالة الحساب المالي</h3>
        </div>
        <div class="balance-box">
          <span class="balance-title">الرصيد المتوفر:</span>
          <span class="balance-value" id="financeBalance">0 IQD</span>
        </div>
        <div class="balance-box" style="background: rgba(245, 158, 11, 0.1); border-color: rgba(245, 158, 11, 0.3); margin-top: 10px;">
          <span class="balance-title" style="color: var(--accent-gold);">الاشتراك الحالي (الباقة):</span>
          <span class="balance-value" style="color: var(--accent-gold); font-size: 14px;" id="financeSub">لا يوجد اشتراك فعال</span>
        </div>
      </div>

      <div class="section-head">طرق الدفع والإيداع الرسمية</div>
      
      <div class="payment-card">
        <div class="pay-header">
          <div class="pay-logo-box qi-style">Qi</div>
          <div>
            <div style="font-weight: 900; font-size: 15px;">بطاقة كي كارد (Qi Card)</div>
            <div style="font-size: 11px; color: var(--text-muted);">دفع الكتروني مباشر</div>
          </div>
        </div>
        <div class="pay-details">
          <div class="pay-row">
            <span>رقم بطاقة كي كارد المعتمد:</span>
            <span class="pay-val">5143617453</span>
          </div>
        </div>
        <button class="btn-ultra btn-gold" onclick="copyText('5143617453')">نسخ رقم بطاقة كي كارد</button>
      </div>

      <div class="payment-card">
        <div class="pay-header">
          <div class="pay-logo-box zain-style">Zain</div>
          <div>
            <div style="font-weight: 900; font-size: 15px;">ZainCash (زين كاش)</div>
            <div style="font-size: 11px; color: var(--text-muted);">محفظة التحويل المالي السريع</div>
          </div>
        </div>
        <div class="pay-details">
          <div class="pay-row">
            <span>رقم الهاتف المعتمد:</span>
            <span class="pay-val">07888189070</span>
          </div>
        </div>
        <button class="btn-ultra btn-gold" onclick="copyText('07888189070')">نسخ رقم زين كاش</button>
      </div>

      <div class="payment-card" style="border-color: var(--accent-gold);">
        <h4 style="font-size:14px; color:var(--accent-gold); margin-bottom:14px; text-align:center;">إرفاق لقطة الشاشة وتأكيد الإيداع</h4>
        
        <div class="input-group">
          <label>رمز المستثمر / اسم الحساب الخاص بك</label>
          <input type="text" id="payUserId" readonly style="opacity:0.8; background:rgba(0,0,0,0.5);">
        </div>

        <div class="input-group">
          <label>اختر الباقة المراد تفعيلها</label>
          <select class="select-css" id="pkgSelect">
            <option value="30000">باقة 30,000 IQD (ربح يومي 10,000 IQD)</option>
            <option value="50000">باقة 50,000 IQD (ربح يومي 35,000 IQD)</option>
            <option value="75000">باقة 75,000 IQD (ربح يومي 55,000 IQD)</option>
            <option value="150000">باقة 150,000 IQD (ربح يومي 80,000 IQD)</option>
            <option value="250000">باقة 250,000 IQD (ربح يومي 122,000 IQD)</option>
            <option value="750000">باقة 750,000 IQD (ربح يومي 189,000 IQD)</option>
            <option value="1000000">باقة 1,000,000 IQD (ربح يومي 380,000 IQD)</option>
          </select>
        </div>

        <div class="input-group">
          <label>إرفاق صورة التحويل أو الإشعار (Screenshot)</label>
          <input type="file" id="receiptFileInput" class="file-css" accept="image/*" onchange="previewSelectedImage(event)">
        </div>

        <div class="image-preview-container" id="previewContainer">
          <p style="font-size:11px; color:var(--accent-gold); margin-bottom:6px;">معاينة صورة الإشعار المرفقة:</p>
          <img id="imagePreview" src="" alt="صورة الإشعار">
        </div>

        <button class="btn-ultra btn-green" onclick="submitReceiptWithImage()">إرسال صورة الإشعار والتفعيل عبر التليجرام</button>
      </div>
    </div>

    <!-- قسم الحساب -->
    <div id="tabProfile" class="tab-content">
      <div class="profile-card">
        <div class="avatar-ring" id="profAvatar">U</div>
        <h3 id="profName" style="font-size:18px; font-weight:900;">المشترك</h3>
        <p style="font-size:12px; color:var(--accent-green); font-weight:bold; margin-top:4px;">عضوية استثمارية موثقة ✓</p>

        <div class="info-list">
          <div class="info-item">
            <span style="color:var(--text-muted);">معرف الحساب الشخصي:</span>
            <strong id="profId">--</strong>
          </div>
          <div class="info-item">
            <span style="color:var(--text-muted);">رصيد الحساب:</span>
            <strong id="profBalance" style="color:var(--accent-green);">0 IQD</strong>
          </div>
          <div class="info-item">
            <span style="color:var(--text-muted);">التوثيق الرقمي:</span>
            <span style="color:var(--accent-blue); font-weight:bold;">مكتمل ومعتمد VIP</span>
          </div>
        </div>

        <button class="btn-ultra btn-outline" style="margin-top:22px; border-color:var(--accent-red); color:var(--accent-red);" onclick="logout()">تسجيل الخروج</button>
      </div>
    </div>

    <!-- شريط التنقل السفلي -->
    <div class="nav-bar">
      <button class="nav-btn active" onclick="switchTab('tabHome', this)">
        <svg class="nav-svg" viewBox="0 0 24 24"><path d="M10 20v-6h4v6h5v-8h3L12 3 2 12h3v8z"/></svg>
        <span>الرئيسية</span>
      </button>
      
      <button class="nav-btn" onclick="openTelegramSupport()">
        <svg class="nav-svg" viewBox="0 0 24 24"><path d="M20 2H4c-1.1 0-1.99.9-1.99 2L2 22l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2z"/></svg>
        <span>الدعم</span>
      </button>

      <button class="nav-btn" onclick="switchTab('tabWithdraw', this)">
        <svg class="nav-svg" viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 14h-2v-2h2v2zm0-4h-2V7h2v5z"/></svg>
        <span>سحب الأموال</span>
      </button>

      <button class="nav-btn" onclick="switchTab('tabFinance', this)">
        <svg class="nav-svg" viewBox="0 0 24 24"><path d="M21 18v1c0 1.1-.9 2-2 2H5c-1.11 0-2-.9-2-2V5c0-1.1.89-2 2-2h14c1.1 0 2 .9 2 2v1h-9c-1.11 0-2 .9-2 2v8c0 1.1.89 2 2 2h9zm-9-2h10V8H12v8zm4-2.5c-.83 0-1.5-.67-1.5-1.5s.67-1.5 1.5-1.5 1.5.67 1.5 1.5-.67 1.5-1.5 1.5z"/></svg>
        <span>الأمور المالية</span>
      </button>

      <button class="nav-btn" onclick="switchTab('tabProfile', this)">
        <svg class="nav-svg" viewBox="0 0 24 24"><path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/></svg>
        <span>حسابي</span>
      </button>
    </div>

  </div>

  <script>
    const ADMIN_ACCOUNT_ID = "5143617453";
    const DEFAULT_ACCOUNTS = { "5143617453": "5143617453" };

    function getUsersDatabase() {
      const stored = localStorage.getItem('SUPER_MINI_USERS');
      if (stored) return JSON.parse(stored);
      localStorage.setItem('SUPER_MINI_USERS', JSON.stringify(DEFAULT_ACCOUNTS));
      return DEFAULT_ACCOUNTS;
    }

    function getUserBalances() {
      const stored = localStorage.getItem('SUPER_MINI_BALANCES');
      if (stored) return JSON.parse(stored);
      const initBalances = { "5143617453": 1000000 };
      localStorage.setItem('SUPER_MINI_BALANCES', JSON.stringify(initBalances));
      return initBalances;
    }

    function saveUserBalances(balances) {
      localStorage.setItem('SUPER_MINI_BALANCES', JSON.stringify(balances));
    }

    function getUserSubscriptions() {
      const stored = localStorage.getItem('SUPER_MINI_SUBS');
      return stored ? JSON.parse(stored) : {};
    }

    function saveUserSubscription(subs) {
      localStorage.setItem('SUPER_MINI_SUBS', JSON.stringify(subs));
    }

    function getWithdrawHistory() {
      const stored = localStorage.getItem('SUPER_MINI_WITHDRAWS');
      return stored ? JSON.parse(stored) : {};
    }

    function saveWithdrawHistory(history) {
      localStorage.setItem('SUPER_MINI_WITHDRAWS', JSON.stringify(history));
    }

    const pkgList = [
      { price: 30000, daily: 10000, days: 90 },
      { price: 50000, daily: 35000, days: 90 },
      { price: 75000, daily: 55000, days: 90 },
      { price: 150000, daily: 80000, days: 90 },
      { price: 250000, daily: 122000, days: 90 },
      { price: 750000, daily: 189000, days: 90 },
      { price: 1000000, daily: 380000, days: 90 }
    ];

    let activeUser = null;
    let selectedPkg = null;
    let selectedImageFile = null;

    function handleSecureLogin() {
      const userField = document.getElementById('userInput').value.trim();
      const passField = document.getElementById('passInput').value.trim();
      const db = getUsersDatabase();

      if (db.hasOwnProperty(userField) && db[userField] === passField) {
        activeUser = userField;
        document.getElementById('loginError').style.display = 'none';
        document.getElementById('loginModal').style.display = 'none';
        document.getElementById('appContent').classList.add('logged-in');
        updateUserData();
      } else {
        showLoginError("⚠️ اسم المستخدم أو كلمة المرور غير صحيحة!");
      }
    }

    function openRegisterModal() {
      document.getElementById('regError').style.display = 'none';
      document.getElementById('regUser').value = '';
      document.getElementById('regPass').value = '';
      document.getElementById('regPassConfirm').value = '';
      document.getElementById('registerModal').style.display = 'flex';
    }

    function handleRegister() {
      const u = document.getElementById('regUser').value.trim();
      const p1 = document.getElementById('regPass').value.trim();
      const p2 = document.getElementById('regPassConfirm').value.trim();

      if (!u || !p1 || !p2) { showRegError("⚠️ يرجى ملء كافة الحقول!"); return; }
      if (p1 !== p2) { showRegError("⚠️ كلمات المرور غير متطابقة!"); return; }

      const db = getUsersDatabase();
      if (db.hasOwnProperty(u)) { showRegError("⚠️ اسم المستخدم هذا حُجز بالفعل، اختر اسماً آخر!"); return; }

      db[u] = p1;
      localStorage.setItem('SUPER_MINI_USERS', JSON.stringify(db));

      const balances = getUserBalances();
      balances[u] = 0;
      saveUserBalances(balances);

      activeUser = u;
      closeModal('registerModal');
      document.getElementById('loginModal').style.display = 'none';
      document.getElementById('appContent').classList.add('logged-in');
      updateUserData();
      showToast("تم إنشاء الحساب وتسجيل الدخول بنجاح! 🎉");
    }

    function showLoginError(msg) {
      const errBox = document.getElementById('loginError');
      errBox.innerText = msg;
      errBox.style.display = 'block';
    }

    function showRegError(msg) {
      const errBox = document.getElementById('regError');
      errBox.innerText = msg;
      errBox.style.display = 'block';
    }

    function updateUserData() {
      if(!activeUser) return;
      document.getElementById('userDisplay').innerText = activeUser;
      document.getElementById('refLink').innerText = `https://supermini.app/ref?id=${encodeURIComponent(activeUser)}`;
      document.getElementById('payUserId').value = activeUser;
      document.getElementById('profId').innerText = activeUser;
      document.getElementById('profName').innerText = activeUser;
      document.getElementById('profAvatar').innerText = activeUser.charAt(0).toUpperCase();

      const balances = getUserBalances();
      const subs = getUserSubscriptions();
      const currentBal = balances[activeUser] !== undefined ? balances[activeUser] : 0;
      
      const formattedBal = Number(currentBal).toLocaleString() + " IQD";

      document.getElementById('homeUserBalance').innerText = formattedBal;
      document.getElementById('profBalance').innerText = formattedBal;
      document.getElementById('financeBalance').innerText = formattedBal;
      document.getElementById('withdrawAvailableBal').innerText = formattedBal;

      const currentSub = subs[activeUser];
      if(currentSub) {
        document.getElementById('financeSub').innerText = `باقة ${Number(currentSub).toLocaleString()} IQD`;
      } else {
        document.getElementById('financeSub').innerText = "لا يوجد اشتراك فعال";
      }

      renderWithdrawHistory();

      const adminPanel = document.getElementById('adminPanel');
      if (activeUser === ADMIN_ACCOUNT_ID) {
        adminPanel.style.display = 'block';
        renderAdminUsersList();
      } else {
        adminPanel.style.display = 'none';
      }
    }

    function processWithdrawalRequest() {
      const method = document.getElementById('withdrawMethodSelect').value;
      const accountNum = document.getElementById('withdrawAccountNum').value.trim();
      const amount = parseFloat(document.getElementById('withdrawAmount').value);

      if (!accountNum) { alert("⚠️ يرجى كتابة رقم الهاتف أو البطاقة للاستلام!"); return; }
      if (isNaN(amount) || amount < 10000) { alert("⚠️ أدنى مبلغ مسموح بسحبه هو 10,000 IQD!"); return; }
      
      const balances = getUserBalances();
      const currentBal = balances[activeUser] || 0;

      if (amount > currentBal) {
        alert("⚠️ الرصيد المتاح لا يكفي لإتمام عملية السحب!");
        return;
      }

      // خصم الرصيد
      balances[activeUser] = currentBal - amount;
      saveUserBalances(balances);

      // حفظ العملية في السجل
      const allHistory = getWithdrawHistory();
      if (!allHistory[activeUser]) allHistory[activeUser] = [];
      allHistory[activeUser].unshift({
        id: Math.floor(1000 + Math.random() * 9000),
        method: method,
        account: accountNum,
        amount: amount,
        date: new Date().toLocaleDateString('ar-IQ'),
        status: 'قيد المعالجة'
      });
      saveWithdrawHistory(allHistory);

      updateUserData();

      // إظهار نافذة إشعار الوصول خلال 24 إلى 48 ساعة
      document.getElementById('withdrawAccountNum').value = '';
      document.getElementById('withdrawAmount').value = '';
      document.getElementById('withdrawNoticeModal').style.display = 'flex';
    }

    function renderWithdrawHistory() {
      const container = document.getElementById('withdrawHistoryContainer');
      const allHistory = getWithdrawHistory();
      const userHistory = allHistory[activeUser] || [];

      if (userHistory.length === 0) {
        container.innerHTML = `<p style="font-size:12px; color:var(--text-muted); text-align:center;">لا توجد عمليات سحب سابقة حتى الآن.</p>`;
        return;
      }

      container.innerHTML = '';
      userHistory.forEach(item => {
        container.innerHTML += `
          <div class="history-item">
            <div>
              <div style="font-weight:bold; color:var(--accent-gold);">${item.method}</div>
              <div style="font-size:10px; color:var(--text-muted);">${item.account} • ${item.date}</div>
            </div>
            <div style="text-align:left;">
              <div style="font-weight:bold; color:var(--accent-green);">${item.amount.toLocaleString()} IQD</div>
              <span class="status-pending">${item.status}</span>
            </div>
          </div>
        `;
      });
    }

    function adminAddProfitToAll() {
      const db = getUsersDatabase();
      const balances = getUserBalances();
      const subs = getUserSubscriptions();

      let count = 0;
      Object.keys(db).forEach(u => {
        const sub = subs[u];
        if (sub) {
          const dailyProfit = Math.round(sub * 0.35);
          balances[u] = (balances[u] || 0) + dailyProfit;
          count++;
        }
      });
      saveUserBalances(balances);
      updateUserData();
      showToast(`تم توزيع الأرباح اليومية لـ ${count} مشتركين بنجاح!`);
    }

    function renderAdminUsersList() {
      const container = document.getElementById('adminUserList');
      const db = getUsersDatabase();
      const balances = getUserBalances();
      const subs = getUserSubscriptions();
      container.innerHTML = '';

      Object.keys(db).forEach(userKey => {
        const uBalance = balances[userKey] || 0;
        const uSub = subs[userKey] ? `باقة ${Number(subs[userKey]).toLocaleString()}` : 'لا يوجد';
        container.innerHTML += `
          <div class="admin-user-item">
            <div class="admin-user-info">
              <span>🆔 الحساب: <strong style="color:var(--accent-gold);">${userKey}</strong></span>
              <span>💰 الرصيد: <strong style="color:var(--accent-green);">${Number(uBalance).toLocaleString()} IQD</strong></span>
            </div>
            <div style="font-size:11px; margin-bottom:8px; color:#ccc;">الاشتراك الفعال: <strong style="color:var(--accent-gold);">${uSub}</strong></div>
            <div class="admin-actions">
              <input type="number" id="amt_${userKey}" placeholder="المبلغ (IQD)" />
              <button class="btn-ultra btn-green" style="padding:6px 10px; font-size:11px;" onclick="modifyUserBalance('${userKey}', 'add')">شحن (+)</button>
              <button class="btn-ultra btn-red" style="padding:6px 10px; font-size:11px;" onclick="modifyUserBalance('${userKey}', 'sub')">خصم (-)</button>
            </div>
          </div>
        `;
      });
    }

    function modifyUserBalance(targetUser, action) {
      const inputEl = document.getElementById(`amt_${targetUser}`);
      const val = parseFloat(inputEl.value);
      if (isNaN(val) || val <= 0) { alert("⚠️ يرجى إدخال مبلغ صحيح أكبر من 0"); return; }
      const balances = getUserBalances();
      const current = balances[targetUser] || 0;
      if (action === 'add') {
        balances[targetUser] = current + val;
        showToast(`تم شحن ${val.toLocaleString()} IQD للحساب ${targetUser}`);
      } else if (action === 'sub') {
        balances[targetUser] = Math.max(0, current - val);
        showToast(`تم خصم ${val.toLocaleString()} IQD من الحساب ${targetUser}`);
      }
      saveUserBalances(balances);
      updateUserData();
    }

    function previewSelectedImage(event) {
      const file = event.target.files[0];
      if (file) {
        selectedImageFile = file;
        const reader = new FileReader();
        reader.onload = function(e) {
          document.getElementById('imagePreview').src = e.target.result;
          document.getElementById('previewContainer').style.display = 'block';
        }
        reader.readAsDataURL(file);
      }
    }

    function submitReceiptWithImage() {
      const selectedAmount = document.getElementById('pkgSelect').value;
      if (!selectedImageFile) {
        alert("⚠️ يرجى اختيار صورة الإشعار أو لقطة الشاشة أولاً قبل الإرسال!");
        return;
      }
      showToast("جاري تجهيز الرسالة للتليجرام...");
      const msgText = `📥 إشعار إيداع جديد:\n• اسم المستثمر/ID: ${activeUser}\n• قيمة الباقة المراد تفعيلها: ${Number(selectedAmount).toLocaleString()} IQD`;
      const tgUrl = `https://t.me/oosbsu?text=${encodeURIComponent(msgText)}`;
      setTimeout(() => { window.open(tgUrl, '_blank'); }, 800);
    }

    function switchTab(tabId, btn) {
      document.querySelectorAll('.tab-content').forEach(t => t.classList.remove('active'));
      document.querySelectorAll('.nav-btn').forEach(n => n.classList.remove('active'));
      document.getElementById(tabId).classList.add('active');
      if(btn) btn.classList.add('active');
    }

    function openTelegramSupport() {
      window.open('https://t.me/oosbsu', '_blank');
    }

    function renderPackages() {
      const container = document.getElementById('pkgContainer');
      container.innerHTML = '';
      pkgList.forEach((pkg, index) => {
        const total = pkg.daily * pkg.days;
        container.innerHTML += `
          <div class="package-item">
            <div class="pkg-top">
              <div class="pkg-title">${pkg.price.toLocaleString()} <span style="font-size:14px; color:var(--accent-gold);">IQD</span></div>
              <div class="pkg-tag">عوائد لمدة 90 يوم</div>
            </div>
            <div class="pkg-grid">
              <div class="grid-cell">
                <div class="label">الربح اليومي المستحق</div>
                <div class="value">${pkg.daily.toLocaleString()} IQD</div>
              </div>
              <div class="grid-cell">
                <div class="label">إجمالي العائد النهائي</div>
                <div class="value" style="color:var(--accent-gold);">${total.toLocaleString()} IQD</div>
              </div>
            </div>
            <button class="btn-ultra btn-gold" style="font-size:15px; padding:16px;" onclick="openSubscribeModal(${index})">🚀 اشترك الآن واستلم أرباحك اليومية</button>
          </div>
        `;
      });
    }

    function openSubscribeModal(idx) {
      selectedPkg = pkgList[idx];
      const total = selectedPkg.daily * selectedPkg.days;
      document.getElementById('subDetailsText').innerHTML = `
        سوف تدفع مبلغ استثماري قدره <strong>${selectedPkg.price.toLocaleString()} IQD</strong> لمدة <strong>90 يوماً</strong>.<br>
        ينزل لك ربح يومي قدره <strong>${selectedPkg.daily.toLocaleString()} IQD</strong> لمجموع أرباح صافية <strong>${total.toLocaleString()} IQD</strong>.
      `;
      document.getElementById('subModal').style.display = 'flex';
    }

    function closeModal(id) {
      document.getElementById(id).style.display = 'none';
    }

    function proceedToPayment() {
      closeModal('subModal');
      const balances = getUserBalances();
      const subs = getUserSubscriptions();
      const userBal = balances[activeUser] || 0;

      if (userBal >= selectedPkg.price) {
        balances[activeUser] -= selectedPkg.price;
        subs[activeUser] = selectedPkg.price;
        saveUserBalances(balances);
        saveUserSubscription(subs);
        updateUserData();
        showToast("🎉 تم تفعيل الباقة بنجاح وخصم قيمتها من رصيدك!");
      } else {
        document.getElementById('errModal').style.display = 'flex';
      }
    }

    function goToFinance() {
      closeModal('errModal');
      if(selectedPkg) { document.getElementById('pkgSelect').value = selectedPkg.price; }
      const navBtns = document.querySelectorAll('.nav-btn');
      switchTab('tabFinance', navBtns[3]);
    }

    function showToast(msg) {
      const t = document.getElementById('toast');
      t.innerText = msg;
      t.style.display = 'block';
      setTimeout(() => { t.style.display = 'none'; }, 3000);
    }

    function copyText(val) {
      navigator.clipboard.writeText(val);
      showToast('تم نسخ الرقم بنجاح: ' + val);
    }

    function copyRef() {
      const link = document.getElementById('refLink').innerText;
      navigator.clipboard.writeText(link);
      showToast('تم نسخ رابط الإحالة بنجاح!');
    }

    function logout() {
      activeUser = null;
      document.getElementById('appContent').classList.remove('logged-in');
      document.getElementById('loginModal').style.display = 'flex';
      document.getElementById('userInput').value = '';
      document.getElementById('passInput').value = '';
    }

    let currentSlide = 0;
    const slidesTrack = document.getElementById('slidesTrack');
    setInterval(() => {
      currentSlide = (currentSlide + 1) % 3;
      slidesTrack.style.transform = `translateX(${currentSlide * 100}%)`;
    }, 4000);

    renderPackages();
  </script>
</body>
</html>
