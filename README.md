<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منصة إيداع الطعون | كلية الآداب واللغات - جامعة تيبازة</title>
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root { 
            --primary: #1565c0; 
            --primary-dark: #0d47a1;
            --primary-light: #42a5f5;
            --success: #2e7d32;
            --warning: #ed6c02;
            --error: #d32f2f;
            --bg: #f0f4f8;
            --card-bg: #ffffff;
            --text: #1a237e;
            --text-secondary: #546e7a;
            --border: #e0e0e0;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body { 
            font-family: 'Tajawal', sans-serif; 
            background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%);
            min-height: 100vh;
            display: flex; 
            justify-content: center; 
            align-items: flex-start;
            padding: 20px;
            color: var(--text);
        }

        @keyframes slideIn {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-10px); }
            75% { transform: translateX(10px); }
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        .container {
            width: 100%;
            max-width: 600px;
            animation: slideIn 0.6s ease-out;
        }

        .header {
            text-align: center;
            margin-bottom: 25px;
            color: var(--primary-dark);
        }

        .header .logo {
            width: 80px;
            height: 80px;
            background: var(--primary);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 15px;
            color: white;
            font-size: 2em;
            box-shadow: 0 4px 15px rgba(21, 101, 192, 0.3);
        }

        .header h1 {
            font-size: 1.8em;
            margin-bottom: 5px;
            font-weight: 800;
        }

        .header p {
            color: var(--text-secondary);
            font-size: 1em;
            margin-bottom: 20px;
        }

        /* ----- تنسيق الأيقونات المتوسطة الجديدة ----- */
        .quick-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 15px;
            margin-bottom: 10px;
        }

        .link-btn {
            width: 55px; /* حجم متوسط */
            height: 55px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.4rem;
            text-decoration: none;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            box-shadow: 0 4px 10px rgba(0,0,0,0.15);
            position: relative;
        }

        .link-btn:hover {
            transform: translateY(-5px) scale(1.1);
            box-shadow: 0 8px 20px rgba(0,0,0,0.2);
        }

        /* ألوان الأيقونات */
        .link-student { background: var(--success); }
        .link-elearning { background: var(--warning); }
        .link-facebook { background: #1877f2; }

        /* تنسيق التلميحات (Tooltips) تظهر للأسفل */
        .link-btn::after {
            content: attr(data-tooltip);
            position: absolute;
            top: 115%; /* تظهر أسفل الأيقونة */
            left: 50%;
            transform: translateX(-50%);
            background: #333;
            color: white;
            padding: 5px 10px;
            border-radius: 6px;
            font-size: 0.8rem;
            white-space: nowrap;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
            font-family: 'Tajawal', sans-serif;
            pointer-events: none;
            z-index: 100;
        }

        /* السهم الصغير للتلميح */
        .link-btn::before {
            content: '';
            position: absolute;
            top: 105%;
            left: 50%;
            transform: translateX(-50%);
            border-width: 5px;
            border-style: solid;
            border-color: transparent transparent #333 transparent;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
        }

        .link-btn:hover::after,
        .link-btn:hover::before {
            opacity: 1;
            visibility: visible;
            top: 125%; /* حركة بسيطة للأسفل */
        }
        .link-btn:hover::before {
            top: 115%;
        }
        /* ------------------------------------------ */

        .stepper {
            display: flex;
            justify-content: space-between;
            margin-bottom: 30px;
            position: relative;
        }

        .stepper::before {
            content: '';
            position: absolute;
            top: 20px;
            left: 10%;
            right: 10%;
            height: 3px;
            background: var(--border);
            z-index: 0;
        }

        .step {
            display: flex;
            flex-direction: column;
            align-items: center;
            position: relative;
            z-index: 1;
            flex: 1;
        }

        .step-circle {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: white;
            border: 3px solid var(--border);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: var(--text-secondary);
            transition: all 0.3s ease;
        }

        .step.active .step-circle {
            background: var(--primary);
            border-color: var(--primary);
            color: white;
        }

        .step.completed .step-circle {
            background: var(--success);
            border-color: var(--success);
            color: white;
        }

        .step-label {
            margin-top: 8px;
            font-size: 0.85em;
            color: var(--text-secondary);
            font-weight: 500;
        }

        .step.active .step-label {
            color: var(--primary);
            font-weight: 700;
        }

        .card { 
            background: var(--card-bg); 
            padding: 35px; 
            border-radius: 20px; 
            box-shadow: 0 10px 40px rgba(0,0,0,0.1);
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 5px;
            background: linear-gradient(90deg, var(--primary), var(--primary-light));
        }

        .form-section {
            display: none;
        }

        .form-section.active {
            display: block;
            animation: slideIn 0.4s ease-out;
        }

        h2 { 
            color: var(--primary); 
            margin-bottom: 25px;
            font-size: 1.4em;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .input-group {
            margin-bottom: 20px;
            position: relative;
        }

        label { 
            display: block; 
            margin-bottom: 8px; 
            font-weight: 700;
            color: var(--text);
            font-size: 0.95em;
        }

        .required::after {
            content: ' *';
            color: var(--error);
        }

        input, select, textarea {
            width: 100%; 
            padding: 14px 16px;
            border: 2px solid var(--border); 
            border-radius: 12px; 
            font-family: 'Tajawal', sans-serif;
            font-size: 1em;
            transition: all 0.3s ease;
            background: #fafafa;
        }

        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: var(--primary);
            background: white;
            box-shadow: 0 0 0 4px rgba(21, 101, 192, 0.1);
        }

        input.error, select.error {
            border-color: var(--error);
            animation: shake 0.5s;
        }

        .error-message {
            color: var(--error);
            font-size: 0.85em;
            margin-top: 5px;
            display: none;
        }

        .error-message.show {
            display: block;
        }

        .row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        .btn {
            width: 100%; 
            padding: 16px; 
            border: none; 
            border-radius: 12px; 
            font-size: 1.1rem; 
            cursor: pointer; 
            font-weight: 700;
            font-family: 'Tajawal', sans-serif;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
            box-shadow: 0 4px 15px rgba(21, 101, 192, 0.3);
        }

        .btn-primary:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(21, 101, 192, 0.4);
        }

        .btn-primary:disabled {
            opacity: 0.7;
            cursor: not-allowed;
        }

        .btn-secondary {
            background: #f5f5f5;
            color: var(--text);
            margin-top: 10px;
        }

        .btn-secondary:hover {
            background: #e0e0e0;
        }

        .btn-group {
            display: flex;
            gap: 10px;
            margin-top: 25px;
        }

        .btn-group .btn {
            flex: 1;
        }

        .review-item {
            display: flex;
            justify-content: space-between;
            padding: 15px;
            background: #f8f9fa;
            border-radius: 10px;
            margin-bottom: 10px;
            border-right: 4px solid var(--primary);
        }

        .review-label {
            font-weight: 700;
            color: var(--text-secondary);
        }

        .review-value {
            color: var(--text);
            font-weight: 500;
        }

        .success-container {
            text-align: center;
            padding: 40px 20px;
            display: none;
        }

        .success-icon {
            width: 100px;
            height: 100px;
            background: var(--success);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 25px;
            color: white;
            font-size: 3em;
            animation: pulse 0.5s;
        }

        .toast-container {
            position: fixed;
            top: 20px;
            left: 20px;
            z-index: 1000;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .toast {
            background: white;
            padding: 16px 20px;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            display: flex;
            align-items: center;
            gap: 12px;
            min-width: 300px;
            animation: slideIn 0.3s ease-out;
            border-right: 4px solid;
        }

        .toast.success { border-right-color: var(--success); }
        .toast.error { border-right-color: var(--error); }
        .toast.warning { border-right-color: var(--warning); }

        .loading-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(255,255,255,0.9);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            flex-direction: column;
            gap: 20px;
        }

        .spinner {
            width: 60px;
            height: 60px;
            border: 4px solid #f3f3f3;
            border-top-color: var(--primary);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        .loading-text {
            color: var(--primary);
            font-size: 1.2em;
            font-weight: 700;
        }

        .auto-save {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: var(--success);
            color: white;
            padding: 10px 20px;
            border-radius: 25px;
            font-size: 0.9em;
            display: none;
            align-items: center;
            gap: 8px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        .auto-save.show {
            display: flex;
            animation: slideIn 0.3s ease-out;
        }

        @media (max-width: 600px) {
            .card {
                padding: 25px 20px;
            }
            
            .row {
                grid-template-columns: 1fr;
            }
            
            .header h1 {
                font-size: 1.4em;
            }
            
            .step-label {
                font-size: 0.75em;
            }
        }

        .confetti {
            position: fixed;
            width: 10px;
            height: 10px;
            background: #f00;
            position: absolute;
            animation: fall linear forwards;
        }

        @keyframes fall {
            to {
                transform: translateY(100vh) rotate(360deg);
                opacity: 0;
            }
        }
    </style>
</head>
<body>

    <div class="toast-container" id="toastContainer"></div>

    <div class="loading-overlay" id="loadingOverlay">
        <div class="spinner"></div>
        <div class="loading-text">جاري إرسال الطعن...</div>
    </div>

    <div class="auto-save" id="autoSave">
        <i class="fas fa-check-circle"></i>
        <span>تم الحفظ تلقائياً</span>
    </div>

    <div class="container">
        <div class="header">
            <div class="logo">
                <i class="fas fa-graduation-cap"></i>
            </div>
            <h1>منصة إيداع الطعون</h1>
            <p>كلية الآداب واللغات - جامعة تيبازة</p>

            <div class="quick-links">
                <a href="https://sets.cu-tipaza.dz/student/login?lang=ar" target="_blank" class="link-btn link-student" data-tooltip="فضاء الطالب">
                    <i class="fas fa-user-graduate"></i>
                </a>
                <a href="https://e-learning.cu-tipaza.dz/elearning/login/" target="_blank" class="link-btn link-elearning" data-tooltip="منصة التعليم عن بعد">
                    <i class="fas fa-laptop-code"></i>
                </a>
                <a href="https://www.facebook.com/profile.php?id=100069721026098" target="_blank" class="link-btn link-facebook" data-tooltip="الصفحة الرسمية للكلية">
                    <i class="fab fa-facebook-f"></i>
                </a>
            </div>
        </div>

        <div class="stepper">
            <div class="step active" id="step1-indicator">
                <div class="step-circle">1</div>
                <div class="step-label">البيانات الشخصية</div>
            </div>
            <div class="step" id="step2-indicator">
                <div class="step-circle">2</div>
                <div class="step-label">تفاصيل الطعن</div>
            </div>
            <div class="step" id="step3-indicator">
                <div class="step-circle">3</div>
                <div class="step-label">المراجعة</div>
            </div>
        </div>

        <div class="card" id="mainCard">
            <form id="appealForm">
                
                <div class="form-section active" id="step1">
                    <h2><i class="fas fa-user"></i> البيانات الشخصية</h2>
                    
                    <div class="input-group">
                        <label class="required">الاسم الكامل</label>
                        <input type="text" name="name" id="name" placeholder="اللقب والاسم" required>
                        <div class="error-message">الرجاء إدخال الاسم الكامل</div>
                    </div>

                    <div class="row">
                        <div class="input-group">
                            <label class="required">المستوى</label>
                            <input type="text" name="level" id="level" placeholder="مثال: المستوى الدراسي" required>
                            <div class="error-message">الرجاء إدخال المستوى</div>
                        </div>
                        <div class="input-group">
                            <label class="required">الفوج</label>
                            <input type="text" name="group" id="group" placeholder="رقم الفوج" required>
                            <div class="error-message">الرجاء إدخال رقم الفوج</div>
                        </div>
                    </div>

                    <div class="input-group">
                        <label class="required">التخصص</label>
                        <input type="text" name="specialty" id="specialty" placeholder="التخصص الدراسي" required>
                        <div class="error-message">الرجاء إدخال التخصص</div>
                    </div>

                    <button type="button" class="btn btn-primary" onclick="nextStep(1)">
                        التالي <i class="fas fa-arrow-left"></i>
                    </button>
                </div>

                <div class="form-section" id="step2">
                    <h2><i class="fas fa-file-alt"></i> تفاصيل الطعن</h2>
                    
                    <div class="input-group">
                        <label class="required">المقياس (المادة)</label>
                        <input type="text" name="module" id="module" placeholder="اسم المادة" required>
                        <div class="error-message">الرجاء إدخال اسم المقياس</div>
                    </div>

                    <div class="input-group">
                        <label class="required">الأستاذ</label>
                        <input type="text" name="prof" id="prof" placeholder="اسم الأستاذ" required>
                        <div class="error-message">الرجاء إدخال اسم الأستاذ</div>
                    </div>

                    <div class="input-group">
                        <label class="required">نوع الطعن</label>
                        <select name="type" id="type" required>
                            <option value="">-- اختر نوع الطعن --</option>
                            <option value="غياب النقطة">غياب النقطة</option>
                            <option value="خطأ في النقطة">خطأ في النقطة</option>
                            <option value="ديون">ديون</option>
                            <option value="أخرى">أخرى</option>
                        </select>
                        <div class="error-message">الرجاء اختيار نوع الطعن</div>
                    </div>

                    <div class="input-group">
                        <label>ملاحظات إضافية (اختياري)</label>
                        <textarea name="notes" id="notes" rows="3" placeholder="أي تفاصيل إضافية تريد ذكرها..."></textarea>
                    </div>

                    <div class="btn-group">
                        <button type="button" class="btn btn-secondary" onclick="prevStep(2)">
                            <i class="fas fa-arrow-right"></i> السابق
                        </button>
                        <button type="button" class="btn btn-primary" onclick="nextStep(2)">
                            التالي <i class="fas fa-arrow-left"></i>
                        </button>
                    </div>
                </div>

                <div class="form-section" id="step3">
                    <h2><i class="fas fa-check-circle"></i> مراجعة البيانات</h2>
                    
                    <div id="reviewContent"></div>

                    <div class="btn-group">
                        <button type="button" class="btn btn-secondary" onclick="prevStep(3)">
                            <i class="fas fa-arrow-right"></i> تعديل
                        </button>
                        <button type="submit" class="btn btn-primary" id="submitBtn">
                            <i class="fas fa-paper-plane"></i> إرسال الطعن
                        </button>
                    </div>
                </div>
            </form>

            <div class="success-container" id="successMessage">
                <div class="success-icon">
                    <i class="fas fa-check"></i>
                </div>
                <h2>تم إرسال الطعن بنجاح!</h2>
                <p>سيتم مراجعة طعنك من قبل الإدارة في أقرب وقت ممكن</p>
                
                <button class="btn btn-primary" onclick="resetForm()" style="margin-top: 25px;">
                    <i class="fas fa-plus"></i> طعن جديد
                </button>
            </div>
        </div>
    </div>

    <script>
        const SCRIPT_URL = "https://script.google.com/macros/s/AKfycbz_SpxyuJNepIRFj7BodR1Q8MEDzVPsI57fgrynvPLcsWL7KpElIwsS7goYTCfmBWGiMQ/exec";
        let currentStep = 1;
        let isSubmitting = false;

        document.addEventListener('DOMContentLoaded', function() {
            loadSavedData();
            setupAutoSave();
        });

        function showToast(message, type = 'success') {
            const container = document.getElementById('toastContainer');
            const toast = document.createElement('div');
            toast.className = `toast ${type}`;
            
            const icons = {
                success: 'fa-check-circle',
                error: 'fa-exclamation-circle',
                warning: 'fa-exclamation-triangle'
            };
            
            toast.innerHTML = `<i class="fas ${icons[type]}"></i><span>${message}</span>`;
            container.appendChild(toast);
            
            setTimeout(() => {
                toast.style.opacity = '0';
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        function nextStep(step) {
            if (!validateStep(step)) return;
            
            document.getElementById(`step${step}`).classList.remove('active');
            document.getElementById(`step${step + 1}`).classList.add('active');
            
            document.getElementById(`step${step}-indicator`).classList.remove('active');
            document.getElementById(`step${step}-indicator`).classList.add('completed');
            document.getElementById(`step${step + 1}-indicator`).classList.add('active');
            
            currentStep = step + 1;
            
            if (currentStep === 3) {
                populateReview();
            }
        }

        function prevStep(step) {
            document.getElementById(`step${step}`).classList.remove('active');
            document.getElementById(`step${step - 1}`).classList.add('active');
            
            document.getElementById(`step${step}-indicator`).classList.remove('active');
            document.getElementById(`step${step - 1}-indicator`).classList.remove('completed');
            document.getElementById(`step${step - 1}-indicator`).classList.add('active');
            
            currentStep = step - 1;
        }

        function validateStep(step) {
            const section = document.getElementById(`step${step}`);
            const inputs = section.querySelectorAll('input[required], select[required]');
            let isValid = true;

            inputs.forEach(input => {
                const errorMsg = input.parentElement.querySelector('.error-message');
                
                if (!input.value.trim()) {
                    input.classList.add('error');
                    errorMsg.classList.add('show');
                    isValid = false;
                } else {
                    input.classList.remove('error');
                    errorMsg.classList.remove('show');
                }
            });

            if (!isValid) {
                showToast('الرجاء تعبئة جميع الحقول المطلوبة', 'error');
            }

            return isValid;
        }

        document.querySelectorAll('input, select').forEach(input => {
            input.addEventListener('input', function() {
                this.classList.remove('error');
                this.parentElement.querySelector('.error-message').classList.remove('show');
            });
        });

        function populateReview() {
            const fields = {
                'الاسم': document.getElementById('name').value,
                'المستوى': document.getElementById('level').value,
                'الفوج': document.getElementById('group').value,
                'التخصص': document.getElementById('specialty').value,
                'المقياس': document.getElementById('module').value,
                'الأستاذ': document.getElementById('prof').value,
                'نوع الطعن': document.getElementById('type').value,
                'الملاحظات': document.getElementById('notes').value || 'لا يوجد'
            };

            const html = Object.entries(fields).map(([key, value]) => `
                <div class="review-item">
                    <span class="review-label">${key}</span>
                    <span class="review-value">${value}</span>
                </div>
            `).join('');

            document.getElementById('reviewContent').innerHTML = html;
        }

        document.getElementById('appealForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            if (isSubmitting) return;
            isSubmitting = true;

            const btn = document.getElementById('submitBtn');
            const loading = document.getElementById('loadingOverlay');
            
            btn.disabled = true;
            loading.style.display = 'flex';

            const formData = new FormData(this);
            formData.append('action', 'save');
            formData.append('date', new Date().toISOString());

            try {
                const res = await fetch(SCRIPT_URL, { 
                    method: 'POST', 
                    body: formData 
                });
                
                const data = await res.json();

                if(data.result === 'success') {
                    localStorage.removeItem('appealFormData');
                    
                    document.getElementById('mainCard').querySelector('form').style.display = 'none';
                    document.getElementById('successMessage').style.display = 'block';
                    
                    createConfetti();
                    showToast('تم إرسال الطعن بنجاح!', 'success');
                } else {
                    throw new Error(data.message || 'خطأ غير معروف');
                }
            } catch (error) {
                console.error('Error:', error);
                showToast('حدث خطأ في الإرسال: ' + error.message, 'error');
                btn.disabled = false;
            } finally {
                loading.style.display = 'none';
                isSubmitting = false;
            }
        });

        function setupAutoSave() {
            const inputs = document.querySelectorAll('input, select, textarea');
            let timeout;
            
            inputs.forEach(input => {
                input.addEventListener('input', () => {
                    clearTimeout(timeout);
                    timeout = setTimeout(saveFormData, 1000);
                });
            });
        }

        function saveFormData() {
            const data = {};
            document.querySelectorAll('input, select, textarea').forEach(input => {
                data[input.name] = input.value;
            });
            
            localStorage.setItem('appealFormData', JSON.stringify(data));
            
            const indicator = document.getElementById('autoSave');
            indicator.classList.add('show');
            setTimeout(() => indicator.classList.remove('show'), 2000);
        }

        function loadSavedData() {
            const saved = localStorage.getItem('appealFormData');
            if (saved) {
                const data = JSON.parse(saved);
                Object.entries(data).forEach(([key, value]) => {
                    const input = document.querySelector(`[name="${key}"]`);
                    if (input && value) {
                        input.value = value;
                    }
                });
                
                if (Object.keys(data).some(k => data[k])) {
                    showToast('تم استعادة البيانات المحفوظة', 'warning');
                }
            }
        }

        function resetForm() {
            document.getElementById('appealForm').reset();
            
            document.querySelectorAll('.form-section').forEach(s => s.classList.remove('active'));
            document.getElementById('step1').classList.add('active');
            
            document.querySelectorAll('.step').forEach(s => {
                s.classList.remove('active', 'completed');
            });
            document.getElementById('step1-indicator').classList.add('active');
            
            document.getElementById('mainCard').querySelector('form').style.display = 'block';
            document.getElementById('successMessage').style.display = 'none';
            
            currentStep = 1;
        }

        function createConfetti() {
            const colors = ['#1565c0', '#2e7d32', '#ed6c02', '#d32f2f', '#7b1fa2'];
            
            for (let i = 0; i < 50; i++) {
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                confetti.style.left = Math.random() * 100 + 'vw';
                confetti.style.background = colors[Math.floor(Math.random() * colors.length)];
                confetti.style.animationDuration = (Math.random() * 3 + 2) + 's';
                confetti.style.opacity = Math.random();
                document.body.appendChild(confetti);
                
                setTimeout(() => confetti.remove(), 5000);
            }
        }

        window.addEventListener('beforeunload', function(e) {
            const form = document.getElementById('appealForm');
            const hasData = Array.from(form.querySelectorAll('input, select, textarea')).some(input => input.value);
            
            if (hasData && document.getElementById('successMessage').style.display !== 'block') {
                e.preventDefault();
                e.returnValue = '';
            }
        });
    </script>
</body>
</html>
