# Google Workspace & Analytics Integration Guide

## SAPS Police Clearance NZ - Complete Setup Instructions

### Phase 1: Google Workspace Setup (Initial Admin Configuration)

#### 1.1 Create Google Workspace Account

**Steps:**
1. Go to https://workspace.google.com
2. Click "Sign up for Google Workspace"
3. Enter domain: **sapspoliceclearance.com**
4. Fill company information:
   - Organization Name: EM Services
   - Company Size: 1-50 employees
   - Country: New Zealand
5. Verify domain ownership (choose verification method):
   - **Option A (Recommended):** Add DNS TXT record to domain registrar
   - **Option B:** Upload HTML file to hosting
   - **Option C:** Use domain registrar connection (if available)

#### 1.2 Set Up Primary Admin Account

**Email:** elanza@sapspoliceclearance.com

**Steps:**
1. Workspace Admin > Users and accounts > Manage users
2. Click "Add new user"
3. Fill details:
   - First Name: Elanza
   - Last Name: Admin
   - Primary Email: elanza@sapspoliceclearance.com
   - Password: [Generate strong password]
   - Secondary Email: [Personal recovery email]
4. Click "Add new user"
5. Set as Super Admin in security settings

#### 1.3 Create Additional Service Accounts

1. **support@sapspoliceclearance.com** (Customer Support)
   - Admin console access: View only
   - Gmail, Drive, Meet, Forms access

2. **admin@sapspoliceclearance.com** (Operations)
   - Admin console access: Full (after elanza)
   - Gmail, Drive, Calendar, Docs/Sheets access

3. **marketing@sapspoliceclearance.com** (Marketing & Campaigns)
   - Gmail, Drive, Analytics read access
   - Google Ads management

4. **analytics@sapspoliceclearance.com** (Analytics & Reporting)
   - GA4 full access
   - Google Search Console access
   - Data visualization tools

#### 1.4 Enable Workspace Apps

**Admin Console > Apps > Google Workspace:**
- ✅ Gmail
- ✅ Calendar
- ✅ Drive
- ✅ Meet
- ✅ Docs
- ✅ Sheets
- ✅ Forms
- ✅ Slides
- ✅ Sites

#### 1.5 Configure Security Settings

**Admin Console > Security:**

**Enable 2-Step Verification:**
1. Go to Security > 2-Step Verification
2. Click "Enforce 2-Step Verification"
3. Set compliance deadline: 30 days
4. Allowed factors:
   - ✅ Authenticator app (Google Authenticator, Microsoft Authenticator)
   - ✅ Phone (SMS, voice call)
   - ✅ Security keys (optional)

**Configure Password Policy:**
1. Go to Security > Password settings
2. Minimum length: 12 characters
3. Password strength requirements: Strong
4. Password expiration: 90 days
5. Password history: 5 previous passwords

**Set Up Account Recovery Options:**
1. Recovery phone number for each admin
2. Recovery email address (external)
3. Backup codes download (store securely)

---

### Phase 2: Google Analytics 4 (GA4) Setup

#### 2.1 Create GA4 Property

**Steps:**
1. Go to https://analytics.google.com
2. Click "Admin" (bottom left)
3. Click "Create Property"
4. Property name: **SAPS Police Clearance NZ**
5. Reporting timezone: **(UTC+12:00) New Zealand Standard Time**
6. Currency: **NZD (New Zealand Dollar)**
7. Business type: **Services**
8. Industry category: **Professional Services**

#### 2.2 Create Data Stream

**Steps:**
1. Under Property > Data streams > Create stream
2. Select **Web**
3. Enter details:
   - Website URL: **https://www.sapspoliceclearance.com**
   - Stream name: **Main Website**
4. Click "Create stream"
5. Copy **Measurement ID** (Format: G-XXXXXXXXXX)

**Repeat for secondary domains:**
- https://fingerprintservices.co.nz (Stream: Fingerprint Services)
- https://forensic-insight.com (Stream: Forensic Insights)

#### 2.3 Add Google Analytics Code to Website

**Replace [GA4_MEASUREMENT_ID] with actual ID:**

```html
<!-- Google Analytics 4 -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

#### 2.4 Configure Conversion Goals

**In GA4, create these conversion events:**

1. **form_submission** (Primary)
   - Trigger: Form submit event
   - Value: Track submission count
   - Goal value: 1 conversion per submission

2. **phone_call** (Secondary)
   - Trigger: Click on phone link
   - Goal value: 1 conversion per call

3. **service_selection** (Tertiary)
   - Trigger: Click service selection button
   - Goal value: Track service interest

4. **document_upload** (Application)
   - Trigger: File upload completion
   - Goal value: 1 conversion per upload

5. **payment_completed** (Revenue)
   - Trigger: Payment confirmation page
   - Goal value: Track transaction amount

#### 2.5 Set Up Events Tracking

**Custom Events to Track:**

```javascript
// Form Submission
gtag('event', 'form_submission', {
  'form_type': 'clearance_application',
  'service_type': 'police_clearance',
  'user_email': 'user@example.com'
});

// Phone Call
gtag('event', 'phone_call', {
  'phone_number': '+64800SAPS-NZ',
  'source': 'contact_page'
});

// Service Selection
gtag('event', 'service_selection', {
  'service_name': 'Police Clearance',
  'service_category': 'clearance'
});

// Scroll Depth
gtag('event', 'scroll_depth', {
  'depth_percent': '50%'
});

// Page Time
gtag('event', 'page_time', {
  'page': '/services',
  'time_seconds': 120
});
```

#### 2.6 Create Custom Dashboards

**Dashboard 1: Executive Overview**
- Total sessions (all devices)
- New vs returning users
- Top traffic sources
- Conversion rate
- Average session duration

**Dashboard 2: Conversion Tracking**
- Form submissions (daily)
- Phone calls (daily)
- Service inquiries (by service type)
- Conversion funnel
- Geographic distribution

**Dashboard 3: Traffic Sources**
- Organic search traffic
- Direct traffic
- Referral traffic
- Google Ads performance
- Social media traffic

---

### Phase 3: Google Search Console (GSC) Setup

#### 3.1 Verify Primary Domain

**Steps:**
1. Go to https://search.google.com/search-console
2. Click "Add property"
3. Enter: **https://www.sapspoliceclearance.com**
4. Click "Continue"
5. Choose verification method:
   - **Recommended:** HTML tag (paste in <head> tag)
   - **Alternative:** DNS record (if you have DNS access)
6. Click "Verify"

#### 3.2 Add Secondary Domains

**Repeat for each domain:**
- https://fingerpoliceclearance.co.nz
- https://forensic-insight.com
- https://proteus.iamstiaan.github.io

#### 3.3 Submit Sitemaps

**For each property:**
1. Go to Sitemaps section
2. Enter sitemap URL: **https://domain.com/sitemap.xml**
3. Click "Submit"
4. Check status (processing may take 24-48 hours)

#### 3.4 Configure Settings

**Coverage Report:**
- Monitor for crawl errors
- Check for missing pages
- Resolve indexing issues

**Performance Report:**
- Track click-through rate (CTR)
- Monitor average position
- Identify best-performing keywords

**Mobile Usability:**
- Test mobile compatibility
- Fix mobile usability issues
- Monitor Core Web Vitals

**Manual Actions:**
- Check for spam or policy violations
- Address any manual actions immediately

---

### Phase 4: Google Ads Setup

#### 4.1 Create Google Ads Account

**Steps:**
1. Go to https://ads.google.com
2. Sign in with Google Workspace account
3. Click "Start now"
4. Create first campaign

#### 4.2 Set Up Conversion Tracking

**Install Global Site Tag:**

```html
<!-- Google Ads Conversion Tracking -->
<script async src="https://www.googletagmanager.com/gtag/js?id=AW-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'AW-XXXXXXXXXX');
</script>
```

**Create Conversion Actions:**
1. **Form Submission** (Conversion Value: NZD 50)
2. **Phone Call** (Conversion Value: NZD 100)
3. **Page View** (Specific landing page)
4. **Newsletter Signup** (Conversion Value: NZD 10)

#### 4.3 Campaign Structure

**Campaign 1: Police Clearance - Search**
- Budget: $500/month
- Keywords: "police clearance NZ", "SAPS clearance"
- Target CPC: NZD 2-5
- Ad groups: 3-5 per campaign

**Campaign 2: Fingerprinting - Display**
- Budget: $300/month
- Target audience: HR professionals
- Placements: Business/HR websites
- Display remarketing

**Campaign 3: Local Services Ads**
- Budget: $200/month
- Geographic: New Zealand
- Lead quality requirements

**Campaign 4: Remarketing**
- Budget: $150/month
- Audience: Website visitors (30 days)
- Conversion focused

#### 4.4 Monthly Budget & Bidding

**Total Monthly Budget: $1,150**
- Police Clearance: $500 (43%)
- Fingerprinting: $300 (26%)
- Local Services: $200 (17%)
- Remarketing: $150 (13%)

**Bidding Strategy:**
- Use Target CPA (Cost Per Acquisition)
- Target CPA: NZD 50-100 per conversion
- Max CPC: NZD 5-10
- Adjust based on monthly performance

---

### Phase 5: Google Cloud Console Setup (Optional - Advanced)

#### 5.1 Create Cloud Project

**Steps:**
1. Go to https://console.cloud.google.com
2. Create new project: **SAPS Police Clearance NZ**
3. Enable APIs:
   - ✅ Cloud Functions API
   - ✅ Firestore API
   - ✅ Cloud Storage API
   - ✅ Cloud Logging API

#### 5.2 Set Up Cloud Functions

**Function 1: Form Submission Handler**
```python
# Process SAPS clearance form submissions
def process_form(request):
    data = request.json
    # Send confirmation email
    # Store in Firestore
    # Log event to GA4
    return {'status': 'success'}
```

**Function 2: Email Notification**
- Trigger: Form submission
- Action: Send email to support team
- Template: HTML email with form details

#### 5.3 Firestore Database

**Collections:**
1. **applications** - All form submissions
2. **users** - User profiles
3. **documents** - Uploaded files metadata
4. **tracking** - Analytics events backup

---

### Phase 6: Daily Monitoring & Reporting

#### 6.1 Daily Dashboard Checks

**Every Morning (9 AM NZST):**

```
Checklist:
1. GA4 Sessions: Target 50+ daily
2. Form Submissions: Target 5+ daily
3. Error Rate: <1%
4. Page Load Speed: <3 seconds
5. Uptime Status: 99.9%+
6. Google Ads: CTR 5%+, Spend tracking
```

#### 6.2 Weekly Reporting (Every Monday)

**Metrics to Review:**
- Total sessions & users
- Conversion rate & revenue
- Top traffic sources
- Google Ads ROI
- Top performing pages
- User demographic breakdown

**Action Items:**
- Update GA4 custom dashboard
- Review underperforming pages
- Optimize high-bounce-rate pages
- Check ad performance

#### 6.3 Monthly Performance Review

**First Friday of Month - Full Analysis:**

| Metric | Target | Actual | Status | Action |
|--------|--------|--------|--------|--------|
| Sessions | 500+ | | | |
| Conversions | 25+ | | | |
| Conv. Rate | 5%+ | | | |
| Avg. Session Duration | 2m+ | | | |
| Organic Traffic % | 40%+ | | | |
| Paid Traffic ROI | 3:1+ | | | |

---

### Phase 7: Tools & Dashboards

#### 7.1 Data Studio Dashboard

**Connect data sources:**
1. Google Analytics 4
2. Google Ads
3. Google Search Console
4. Custom Google Sheet (manual tracking)

**Key Visualizations:**
- Line chart: Daily sessions & conversions
- Scorecard: Current month metrics
- Pie chart: Traffic source breakdown
- Table: Top pages by engagement
- Geo chart: User locations (NZ focus)

#### 7.2 Google Sheets Integration

**Automated Reporting Sheet:**
```
Column A: Date
Column B: Sessions
Column C: Users
Column D: Conversions
Column E: Revenue
Column F: Ads Spend
Column G: ROI
```

**Use GA4 add-on:**
- Install "Google Analytics" add-on
- Connect to GA4 property
- Auto-update daily metrics

---

### Phase 8: Compliance & Data Protection

#### 8.1 GDPR & Privacy Compliance

**Privacy Policy Must Include:**
- Data collection methods (GA4 tracking)
- User consent mechanisms
- Data retention policy (90 days for GA4)
- User rights (access, deletion)
- Contact information

**Implement Consent Banner:**
```html
<!-- Cookie Consent Banner -->
<div id="consent-banner">
  <p>We use Google Analytics to improve your experience.</p>
  <button onclick="acceptCookies()">Accept</button>
  <button onclick="declineCookies()">Decline</button>
</div>
```

#### 8.2 Data Retention

**Set up automatic data deletion:**
- GA4: 2 months (balance: data needs vs privacy)
- Forms: Delete after 90 days (compliance)
- Backups: 30-day retention
- Logs: 7-day retention

---

### Troubleshooting & Support

**Common Issues & Solutions:**

1. **GA4 not tracking events**
   - Verify Measurement ID is correct
   - Check browser console for errors
   - Test using GA4 debugger

2. **Google Search Console shows errors**
   - Re-verify domain ownership
   - Resubmit sitemap
   - Check robots.txt syntax

3. **Ads not getting impressions**
   - Review keyword bids
   - Check landing page quality score
   - Test in incognito mode

4. **Email forwarding not working**
   - Verify MX records at domain registrar
   - Check spam folder
   - Test with different email providers

**Support Contacts:**
- Google Workspace Support: https://support.google.com/workspace
- GA4 Community: https://support.google.com/analytics
- Google Ads Help: https://support.google.com/google-ads
- GitHub Issues: https://github.com/Iammypictures/Sapspoliceclearancenz/issues

---

**Document Version:** 1.0  
**Last Updated:** 2026-05-17  
**Owner:** EM Services / SAPS Police Clearance NZ  
**Status:** Complete - Ready for Implementation
