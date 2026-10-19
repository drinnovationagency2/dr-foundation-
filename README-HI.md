# DR Foundation — Website Starter (Hindi + English)

यह एक responsive, static-first वेबसाइट प्रोजेक्ट है जिसमें Premium Blue & White डिज़ाइन, हिंदी/English भाषा toggle, पाँच program areas, enquiry form का सुरक्षित configuration point और Supabase-आधारित admin/database starter शामिल है।

## वर्तमान स्थिति: क्या काम करता है?
- Responsive public website: हाँ
- Hindi/English toggle: हाँ (ब्राउज़र localStorage में भाषा प्राथमिकता रखता है)
- Mobile navigation: हाँ
- Form validation: हाँ
- Form submission: **नहीं, जब तक वास्तविक endpoint configure न हो**
- Admin login: **नहीं, जब तक Supabase project, credentials, Auth user और database policies configure न हों**
- Database: **schema starter उपलब्ध; कोई लाइव database इस ZIP में शामिल नहीं है**
- Project editing: Admin पेज अभी read-only शुरुआती dashboard है; create/edit/delete UI अभी नहीं है।

## फाइलें
- `index.html` — सार्वजनिक वेबसाइट
- `css/style.css` — responsive design
- `js/main.js` — भाषा, मेनू, form submission
- `js/config.js` — सार्वजनिक config placeholders
- `admin/index.html`, `admin/admin.js` — Supabase Auth login और read-only dashboard
- `database/schema.sql` — Supabase tables और RLS policies
- `privacy.html` — privacy policy starter; publish से पहले संपादित करें

## Android से Netlify पर deploy
1. ZIP डाउनलोड करके Android के Files/Downloads ऐप से extract करें।
2. GitHub पर login करके `dr-foundation` नाम का नया repository बनाएँ।
3. repository में extracted project की सभी files और folders upload करें। सुनिश्चित करें कि `index.html` repository root में हो, किसी अतिरिक्त nested folder के अंदर नहीं।
4. `https://app.netlify.com/` खोलें और Git provider के रूप में GitHub चुनकर repository import करें।
5. Static HTML site के लिए build command खाली रखें और publish directory `.` रखें। Deploy करें।
6. Netlify द्वारा दिए गए HTTPS URL पर Home, language toggle, mobile menu, links और admin page जाँचें।
7. संपर्क ईमेल को सत्यापित वास्तविक ईमेल से बदलें। `contact@drfoundation.example` placeholder है और काम करने वाला ईमेल नहीं है।

## Formspree जोड़ना
1. Formspree या अन्य उपयुक्त form provider में account और form बनाएँ।
2. provider द्वारा दिया गया वास्तविक HTTPS endpoint कॉपी करें।
3. `js/config.js` में `formEndpoint: ""` की जगह उस endpoint को डालें।
4. commit/upload और redeploy करें। फिर एक test submission करें।
5. provider dashboard में submission प्राप्त होने की पुष्टि करें और privacy/retention settings जाँचें।

इस starter में कोई submission endpoint pre-configured नहीं है। endpoint खाली होने पर वेबसाइट स्पष्ट संदेश दिखाती है और डेटा भेजने का दावा नहीं करती।

## Supabase सुरक्षित Admin जोड़ना
1. Supabase में नया project बनाएँ; free-plan availability/limits की जाँच करें।
2. Project URL और public anon/publishable key लें। `js/config.js` में `supabaseUrl` और `supabaseAnonKey` भरें। **service_role key, database password या कोई secret browser code में कभी न डालें।**
3. Supabase Authentication में email/password provider की settings जाँचें। अपने admin user को Auth > Users के माध्यम से बनाएँ।
4. Supabase SQL Editor में `database/schema.sql` चलाएँ। पहले test project में परीक्षण करें।
5. Auth > Users में अपने admin user की UUID कॉपी करें। SQL Editor में schema file के अंत में दिए गए INSERT उदाहरण में UUID और नाम बदलकर चलाएँ, ताकि `profiles.role = 'admin'` बने।
6. RLS policies जाँचें। public visitor केवल published projects पढ़ सके; enquiries केवल insert कर सके; enquiries पढ़ना/बदलना admin-only रहे।
7. `admin/` खोलकर admin email/password से login test करें।
8. अलग test account से पुष्टि करें कि वह enquiries या draft projects नहीं पढ़ सकता। RLS को production में लगाने से पहले परीक्षण अनिवार्य है।

## Admin सीमाएँ
यह अभी एक सुरक्षित आधारभूत, read-only dashboard है। इसमें project create/edit, enquiry status बदलना, exports, email alerts, password reset UI या audit log शामिल नहीं हैं। इन्हें अलग से विकसित और परीक्षण करना होगा। Browser में public anon key सामान्य है, पर सुरक्षा RLS policies से आती है।

## Launch checklist
- [ ] वास्तविक संस्था का नाम, कानूनी स्थिति और पता सत्यापित
- [ ] वास्तविक contact email सेट
- [ ] कार्यक्रमों/परियोजनाओं के सभी दावे सत्यापित
- [ ] Privacy policy संस्था की वास्तविक प्रक्रिया के अनुसार संशोधित
- [ ] Form endpoint configured और test किया
- [ ] Supabase Auth, admin profile और RLS परीक्षण पूरा
- [ ] मोबाइल और कंप्यूटर पर परीक्षण
- [ ] किसी HTML/JS फाइल में password या secret key नहीं
