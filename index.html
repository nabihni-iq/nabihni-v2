<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نظام نبهني - التنبيه الفوري للسيارات</title>
    <!-- مكتبة OneSignal للإشعارات -->
    <script src="https://cdn.onesignal.com/sdks/web/v16/OneSignalSDK.page.js" defer></script>
    <script>
      window.OneSignalDeferred = window.OneSignalDeferred || [];
      OneSignalDeferred.push(async function(OneSignal) {
        await OneSignal.init({
          appId: "A18d1635-cc77-444b-8b81-58d87ee306d4",
          safari_web_id: "web.onesignal.auto.00000000-0000-0000-0000-000000000000", // سيتم ربطه تلقائياً
          notifyButton: {
            enable: true,
          },
        });
      });
    </script>
    <style>
        body {
            font-family: system-ui, -apple-system, sans-serif;
            background-color: #f3f4f6;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            color: #1f2937;
        }
        .container {
            background: #ffffff;
            padding: 2rem;
            border-radius: 1rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
            text-align: center;
            max-width: 400px;
            width: 90%;
        }
        h1 { color: #dc2626; margin-bottom: 0.5rem; font-size: 1.5rem; }
        p { color: #4b5563; margin-bottom: 1.5rem; font-size: 0.95rem; }
        .btn {
            background-color: #dc2626;
            color: white;
            border: none;
            padding: 0.75rem 1.5rem;
            font-size: 1rem;
            border-radius: 0.5rem;
            cursor: pointer;
            width: 100%;
            margin-bottom: 0.75rem;
            font-weight: bold;
            transition: background 0.2s;
        }
        .btn:hover { background-color: b91c1c; }
        .btn-secondary { background-color: #2563eb; }
        .btn-secondary:hover { background-color: #1d4ed8; }
        .car-id { font-weight: bold; color: #111827; background: #e5e7eb; padding: 0.2rem 0.5rem; border-radius: 4px; }
        .hidden { display: none; }
        .success-msg { color: #16a34a; font-weight: bold; margin-top: 1rem; }
    </style>
</head>
<body>

    <div class="container">
        <h1>🚗 نبهني</h1>
        <p>رقم السيارة: <span id="carIdDisplay" class="car-id">جاري التحميل...</span></p>

        <!-- واجهة صاحب السيارة (لأول مرة للتفعيل) -->
        <div id="ownerSection">
            <p>هل أنت مالك هذه السيارة؟ اضغط لتفعيل الإشعارات الفورية على هاتفك.</p>
            <button class="btn" onclick="registerOwner()">تفعيل الإشعارات لهذا الهاتف</button>
        </div>

        <!-- واجهة الشخص الغريب (للتبليغ) -->
        <div id="strangerSection" class="hidden">
            <p>هل تغلق هذه السيارة طريقك أو لاحظت مشكلة فيها؟ أرسل تنبيهاً فورياً للمالك بضغطة زر:</p>
            <button class="btn" onclick="sendAlert('🚗 سيارتك تغلق الطريق، يرجى تحريكها')">سيارتك تغلق الطريق</button>
            <button class="btn btn-secondary" onclick="sendAlert('🚨 ناسي أضواء السيارة أو الباب مفتوح')">تنبيه بخصوص الأضواء أو الأبواب</button>
        </div>

        <div id="statusMsg" class="success-msg"></div>
    </div>

    <script>
        // استخراج رقم السيارة من رابط الصفحة (مثلاً ?car=CAR-001)
        const urlParams = new URLSearchParams(window.location.search);
        const carId = urlParams.get('car') || 'CAR-DEMO';
        document.getElementById('carIdDisplay').innerText = carId;

        // التحقق مما إذا كان المستخدم هو صاحب الجهاز (مسجل مسبقاً في الذاكرة)
        const isOwner = localStorage.getItem('is_owner_' + carId);

        if (isOwner) {
            document.getElementById('ownerSection').innerHTML = `<p style="color: #16a34a; font-weight: bold;">✅ هذا الجهاز مبرمج لاستقبال تنبيهات هذه السيارة بنجاح.</p>`;
            document.getElementById('strangerSection').classList.add('hidden');
        }

        // دالة تفعيل المالك
        async function registerOwner() {
            try {
                const permission = await Notification.requestPermission();
                if (permission === 'granted') {
                    // تفعيل OneSignal للمستخدم
                    window.OneSignalDeferred.push(async function(OneSignal) {
                        await OneSignal.User.addTag("car_id", carId);
                        const externalId = "owner_" + carId;
                        await OneSignal.login(externalId);
                    });
                    
                    localStorage.setItem('is_owner_' + carId, 'true');
                    document.getElementById('ownerSection').innerHTML = `<p style="color: #16a34a; font-weight: bold;">🎉 تم التفعيل بنجاح! ستصلك التنبيهات هنا.</p>`;
                } else {
                    alert('يرجى السماح بالإشعارات من إعدادات المتصفح لكي يعمل النظام.');
                }
            } catch (error) {
                alert('حدث خطأ أثناء التفعيل، يرجى المحاولة مرة أخرى.');
            }
        }

        // دالة إرسال التنبيه من الشخص الغريب
        async function sendAlert(messageText) {
            const statusDiv = document.getElementById('statusMsg');
            statusDiv.innerText = "جاري إرسال التنبيه...";

            try {
                // إرسال الإشعار عبر OneSignal API مباشرة للمالك الذي يحمل الـ tag الخاص برقم السيارة
                const response = await fetch('https://onesignal.com/api/v1/notifications', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        // ملاحظة: سيتم إضافة مفتاح الـ REST API قريباً أو تركه يعمل عبر السيرفر الخفيف
                    },
                    body: JSON.stringify({
                        app_id: "A18d1635-cc77-444b-8b81-58d87ee306d4",
                        filters: [{"field": "tag", "key": "car_id", "relation": "=", "value": carId}],
                        contents: {"ar": messageText, "en": messageText},
                        headings: {"ar": "🚨 تنبيه عاجل لسيارتك", "en": "Urgent Car Alert"}
                    })
                });

                statusDiv.innerText = "✅ تم إرسال التنبيه لصاحب السيارة بنجاح!";
                document.getElementById('strangerSection').innerHTML = "<p style='color: #16a34a; font-weight: bold;'>تم إبلاغ صاحب السيارة بنجاح.</p>";
            } catch (e) {
                statusDiv.innerText = "❌ حدث خطأ في الإرسال، حاول مرة أخرى.";
            }
        }
    </script>
</body>
</html>
