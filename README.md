# Cookie Consent Implementation

This repository contains a customizable cookie consent bar with settings modal for a website, designed to comply with privacy regulations (such as GDPR). It allows users to accept cookies or configure their cookie preferences, including strictly necessary cookies, performance cookies, and functional cookies.<br>

## Features
<br>
- Cookie Consent Bar: Displays a banner at the bottom of the website to inform users about the use of cookies.<br>
- Cookie Preferences Modal: A modal allows users to manage their cookie preferences, enabling or disabling performance and functional cookies.<br>
- Privacy Compliant: Follows privacy regulations like GDPR by requesting explicit user consent before enabling cookies.<br>
- LocalStorage Management: The user’s preferences are saved in localStorage, ensuring cookies are only enabled based on user consent.<br>
- Customizable: You can modify the cookie preferences and style the consent bar to fit your website's design.<br>

## Usage<br>

### 1. Integrating the Cookie Consent Banner<br><br>

Include the following code in the HTML file for the website to load the cookie consent functionality:

```html
<!-- Custom HTML for Cookie Consent Bar -->
<link href="https://fonts.googleapis.com/css2?family=Dosis:wght@400&display=swap" rel="stylesheet">
<div id="cookieConsentContainer" style="position: fixed; bottom: 0; width: 100%; color: #000; text-align: center; padding: 15px 0 0; display: none; z-index: 1000; font-family: 'Dosis', sans-serif; background: linear-gradient(to bottom, rgba(0,0,0,0) 0%,rgba(0,0,0,0) 1%,rgba(0,0,0,0.15) 100%);"> 
    <div style="padding-bottom: 15px;">
        <hr style="border: none; border-top: 2px dashed #ccc; margin: 0;">
    </div>
    <p style="margin: 0; font-size: 18px; color: #000; font-weight: 400; padding: 15px 0;">
        This website uses cookies to ensure you get the best experience on this website.
        <a href="https://your_lovely_domain.com/copyright.html#cookies" id="cookiePolicy" style="color: #4cbedf; text-decoration: none; margin-left: 10px;">Cookie Policy</a>
        <button id="acceptCookies" style="background-color: #4cbedf; color: white; border: 1px solid #4cbedf; padding: 10px 20px; margin-left: 10px; cursor: pointer;">Accept</button>
        <button id="cookieSettings" style="color: #4cbedf; text-decoration: none; border: 1px solid #4cbedf; padding: 10px 20px; margin-left: 10px; background-color: white; cursor: pointer;">Settings</button>
    </p>
</div>

<!-- Cookie Settings Modal -->
<div id="cookieSettingsModal" style="display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background-color: rgba(0, 0, 0, 0.5); z-index: 1001;">
    <div style="background-color: #fff; padding: 20px 20px 20px 20px; margin: 10% auto; width: 80%; max-width: 400px; border-radius: 8px; font-family: 'Dosis', sans-serif;">
        <h2 style="margin-top: 0;">Cookie Preferences</h2>
        <label style="display: block; margin-bottom: 10px;">
            <input type="checkbox" id="strictlyNecessary" disabled checked style="margin-right: 10px;">Strictly Necessary Cookies (Always Active)
        </label>
        <label style="display: block; margin-bottom: 10px;">
            <input type="checkbox" id="performanceCookies" style="margin-right: 10px;">Performance Cookies
        </label>
        <label style="display: block; margin-bottom: 10px;">
            <input type="checkbox" id="functionalCookies" style="margin-right: 10px;">Functional Cookies
        </label>
        <button id="saveSettings" style="background-color: #4cbedf; color: white; border: 1px solid #4cbedf; padding: 10px 20px; cursor: pointer;">Save Preferences</button>
        <button id="closeSettings" style="background-color: white; color: #4cbedf; border: 1px solid #4cbedf; padding: 10px 20px; cursor: pointer;">Cancel</button>
    </div>
</div>

<script>
    document.addEventListener("DOMContentLoaded", function() {
        var cookieConsentContainer = document.getElementById('cookieConsentContainer');
        var acceptCookies = document.getElementById('acceptCookies');
        var cookieSettings = document.getElementById('cookieSettings');
        var cookieSettingsModal = document.getElementById('cookieSettingsModal');
        var saveSettings = document.getElementById('saveSettings');
        var closeSettings = document.getElementById('closeSettings');

        // Check if the user has already accepted cookies
        if (!localStorage.getItem('cookiesAccepted')) {
            cookieConsentContainer.style.display = 'block';
        }

        // Accept cookies and save preference
        acceptCookies.addEventListener('click', function() {
            localStorage.setItem('cookiesAccepted', 'true');
            // Enable cookies based on consent (can be extended for performance/functional cookies)
            enableCookies();
            cookieConsentContainer.style.display = 'none';
        });

        // Show cookie settings modal
        cookieSettings.addEventListener('click', function() {
            cookieSettingsModal.style.display = 'block';
        });

        // Close settings modal
        closeSettings.addEventListener('click', function() {
            cookieSettingsModal.style.display = 'none';
        });

        // Save cookie preferences from settings modal
        saveSettings.addEventListener('click', function() {
            var performanceCookies = document.getElementById('performanceCookies').checked;
            var functionalCookies = document.getElementById('functionalCookies').checked;

            // Store user preferences in localStorage
            localStorage.setItem('performanceCookies', performanceCookies);
            localStorage.setItem('functionalCookies', functionalCookies);

            // Enable cookies based on selected preferences
            if (performanceCookies) {
                enablePerformanceCookies();
            }
            if (functionalCookies) {
                enableFunctionalCookies();
            }

            cookieSettingsModal.style.display = 'none';
            cookieConsentContainer.style.display = 'none';
            localStorage.setItem('cookiesAccepted', 'true');
        });

        // Function to enable strictly necessary cookies
        function enableCookies() {
            // Add code to enable strictly necessary cookies
            console.log("Strictly necessary cookies enabled");
        }

        // Function to enable performance cookies
        function enablePerformanceCookies() {
            // Add code to enable performance cookies (e.g., load analytics scripts)
            console.log("Performance cookies enabled");
        }

        // Function to enable functional cookies
        function enableFunctionalCookies() {
            // Add code to enable functional cookies (e.g., load personalized content)
            console.log("Functional cookies enabled");
        }
    });
</script>
```

<br>
2. How It Works<br>
- Initial Load: When the user first visits your website, they will see the cookie consent bar at the bottom of the page. The banner informs the user about the cookies used by the site.<br>
- Cookie Acceptance: When the user clicks on "Accept", the cookies will be enabled, and their consent will be saved in localStorage.<br>
- Settings: The user can access a settings modal by clicking the "Settings" button. In the modal, they can enable or disable performance and functional cookies.<br>
- Saving Preferences: Upon clicking "Save Preferences", the settings are saved in localStorage, and cookies are enabled accordingly.<br><br>
3. Customization<br>
- Styling: The cookie consent bar and modal are fully customizable through CSS. Modify the style tags and classes to match your website's design.<br>
- Cookie Logic: Modify the JavaScript functions (such as enablePerformanceCookies() and enableFunctionalCookies()) to implement your own logic for loading cookies, such as third-party scripts (e.g., Google Analytics).<br>
- Cookie Policy: Update the cookie policy link (href="https://your-site.com/cookie-policy") to point to your website’s cookie policy page.<br><br>
4. LocalStorage Consent Management<br>
The user's cookie preferences are stored in localStorage, meaning the settings are persistent across page loads and sessions. This helps ensure that cookies are only enabled after user consent, and users can change their preferences at any time.<br><br>

- Cookies Accepted: Stored as cookiesAccepted in localStorage.<br>
- Performance Cookies: Stored as performanceCookies.<br>
- Functional Cookies: Stored as functionalCookies.<br><br>
5. Privacy Compliance<br>
This implementation is designed to help your website comply with privacy laws like GDPR. By asking for explicit consent, users can control the type of cookies they wish to accept, ensuring better data privacy.<br>

Integrating with Cloudflare Zaraz<br>
Cloudflare Zaraz is a tool designed to streamline the management of third-party scripts, improving speed, privacy, and security. To integrate the cookie consent code with Zaraz, follow these steps:<br><br>

Steps for Integration<br>
Log in to Cloudflare Dashboard: Go to your Cloudflare Dashboard.<br><br>

Navigate to Zaraz:<br><br>

From your Cloudflare account, select the website you want to configure.<br>
Go to the Zaraz tab in the left-hand menu (under Performance or Speed).<br>
Create a New Zaraz Integration:<br>

In Zaraz, you can manage and control third-party tools like cookie consent scripts. To add the cookie consent banner, click on the "Add New" button or "Create Integration".<br>
Add Custom HTML Code:<br><br>

Choose Custom Code (HTML, CSS, JS).<br>
Paste the HTML for the cookie consent banner (the code inside the <div id="cookieConsentContainer"> section) and JavaScript (the script that handles cookie consent logic) into the respective fields in Zaraz.<br>
Example of the code to add:<br>

```html
<!-- Custom HTML for Cookie Consent Bar -->
<link href="https://fonts.googleapis.com/css2?family=Dosis:wght@400&display=swap" rel="stylesheet">
<div id="cookieConsentContainer" style="position: fixed; bottom: 0; width: 100%; color: #000; text-align: center; padding: 15px 0 0; display: none; z-index: 1000; font-family: 'Dosis', sans-serif; background: linear-gradient(to bottom, rgba(0,0,0,0) 0%,rgba(0,0,0,0) 1%,rgba(0,0,0,0.15) 100%);"> 
    <div style="padding-bottom: 15px;">
        <hr style="border: none; border-top: 2px dashed #ccc; margin: 0;">
    </div>
    <p style="margin: 0; font-size: 18px; color: #000; font-weight: 400; padding: 15px 0;">
        This website uses cookies to ensure you get the best experience on this website.
        <a href="https://your_lovely_domain.com/copyright.html#cookies" id="cookiePolicy" style="color: #4cbedf; text-decoration: none; margin-left: 10px;">Cookie Policy</a>
        <button id="acceptCookies" style="background-color: #4cbedf; color: white; border: 1px solid #4cbedf; padding: 10px 20px; margin-left: 10px; cursor: pointer;">Accept</button>
        <button id="cookieSettings" style="color: #4cbedf; text-decoration: none; border: 1px solid #4cbedf; padding: 10px 20px; margin-left: 10px; background-color: white; cursor: pointer;">Settings</button>
    </p>
</div>

<!-- Cookie Settings Modal -->
<div id="cookieSettingsModal" style="display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background-color: rgba(0, 0, 0, 0.5); z-index: 1001;">
    <div style="background-color: #fff; padding: 20px 20px 20px 20px; margin: 10% auto; width: 80%; max-width: 400px; border-radius: 8px; font-family: 'Dosis', sans-serif;">
        <h2 style="margin-top: 0;">Cookie Preferences</h2>
        <label style="display: block; margin-bottom: 10px;">
            <input type="checkbox" id="strictlyNecessary" disabled checked style="margin-right: 10px;">Strictly Necessary Cookies (Always Active)
        </label>
        <label style="display: block; margin-bottom: 10px;">
            <input type="checkbox" id="performanceCookies" style="margin-right: 10px;">Performance Cookies
        </label>
        <label style="display: block; margin-bottom: 10px;">
            <input type="checkbox" id="functionalCookies" style="margin-right: 10px;">Functional Cookies
        </label>
        <button id="saveSettings" style="background-color: #4cbedf; color: white; border: 1px solid #4cbedf; padding: 10px 20px; cursor: pointer;">Save Preferences</button>
        <button id="closeSettings" style="background-color: white; color: #4cbedf; border: 1px solid #4cbedf; padding: 10px 20px; cursor: pointer;">Cancel</button>
    </div>
</div>

<script>
    document.addEventListener("DOMContentLoaded", function() {
        var cookieConsentContainer = document.getElementById('cookieConsentContainer');
        var acceptCookies = document.getElementById('acceptCookies');
        var cookieSettings = document.getElementById('cookieSettings');
        var cookieSettingsModal = document.getElementById('cookieSettingsModal');
        var saveSettings = document.getElementById('saveSettings');
        var closeSettings = document.getElementById('closeSettings');

        // Check if the user has already accepted cookies
        if (!localStorage.getItem('cookiesAccepted')) {
            cookieConsentContainer.style.display = 'block';
        }

        // Accept cookies and save preference
        acceptCookies.addEventListener('click', function() {
            localStorage.setItem('cookiesAccepted', 'true');
            // Enable cookies based on consent (can be extended for performance/functional cookies)
            enableCookies();
            cookieConsentContainer.style.display = 'none';
        });

        // Show cookie settings modal
        cookieSettings.addEventListener('click', function() {
            cookieSettingsModal.style.display = 'block';
        });

        // Close settings modal
        closeSettings.addEventListener('click', function() {
            cookieSettingsModal.style.display = 'none';
        });

        // Save cookie preferences from settings modal
        saveSettings.addEventListener('click', function() {
            var performanceCookies = document.getElementById('performanceCookies').checked;
            var functionalCookies = document.getElementById('functionalCookies').checked;

            // Store user preferences in localStorage
            localStorage.setItem('performanceCookies', performanceCookies);
            localStorage.setItem('functionalCookies', functionalCookies);

            // Enable cookies based on selected preferences
            if (performanceCookies) {
                enablePerformanceCookies();
            }
            if (functionalCookies) {
                enableFunctionalCookies();
            }

            cookieSettingsModal.style.display = 'none';
            cookieConsentContainer.style.display = 'none';
            localStorage.setItem('cookiesAccepted', 'true');
        });

        // Function to enable strictly necessary cookies
        function enableCookies() {
            // Add code to enable strictly necessary cookies
            console.log("Strictly necessary cookies enabled");
        }

        // Function to enable performance cookies
        function enablePerformanceCookies() {
            // Add code to enable performance cookies (e.g., load analytics scripts)
            console.log("Performance cookies enabled");
        }

        // Function to enable functional cookies
        function enableFunctionalCookies() {
            // Add code to enable functional cookies (e.g., load personalized content)
            console.log("Functional cookies enabled");
        }
    });
</script>
```

Configure Script Settings:<br><br>

You can set the script to run on specific pages or globally. Adjust the timing of when the cookie consent script is loaded, typically on DOMContentLoaded or when the page is fully loaded.<br>
You can also specify any domain-specific settings, such as making sure the banner only appears for users from certain regions or IP ranges if you need to comply with regional privacy regulations.<br>
Set Up Cookie Consent Logic:<br><br>

With Zaraz, you can control when certain third-party tools (e.g., Google Analytics, Facebook Pixel) are activated based on the user's cookie preferences.<br>
For example, configure Zaraz to load performance cookies (like Google Analytics) only if the user enables them through the cookie settings modal.<br>
Save and Publish:<br><br>

After adding the custom code and configuring the script's behavior, click Save.<br>
Ensure you publish the changes so the cookie consent bar and settings modal are active on your website.<br><br>
Benefits of Using Zaraz:<br>
- Performance: Zaraz helps manage third-party tools like cookie consent scripts without slowing down your website by executing scripts in parallel.<br>
- Privacy: Zaraz allows you to load only the necessary scripts after receiving consent, helping to improve user privacy and comply with GDPR.<br>
- Security: Zaraz runs third-party scripts in a secure and controlled environment, minimizing security risks from third-party tools.<br><br>
License:<br>
This project is licensed under the Apache License - see the LICENSE file for details.<br><br>

Contributing:<br>
If you have suggestions for improvements or find any issues, feel free to submit a pull request or open an issue in the GitHub repository.<br>
<br>
Acknowledgments:<br>
This project was inspired by the need for a simple, privacy-compliant cookie consent implementation for websites.<br>
