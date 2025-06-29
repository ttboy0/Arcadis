# Playwright Python Automation Scripts

This project contains Python-based Playwright automation scripts for testing the Arcadis website. The scripts validate the presence of 4 key elements on the website and provide detailed reporting.

## 📁 Project Structure

```
playwright_scripts_python/
├── common/
│   └── lib.py                 # Common functions and PlaywrightManager class
├── settings/
│   └── settings.py           # Global configuration settings
├── Locators/
│   └── locator.yaml          # Element locators and expected values
├── main_script.py            # Main execution script
├── requirements.txt          # Python dependencies
└── README.md                # This file
```

## 🎯 What This Script Does

1. **Opens Browser**: Launches a Chromium browser instance
2. **Navigates to URL**: Goes to https://www.arcadis.com/
3. **Validates Elements**: Checks for 4 key elements:
   - About Us navigation link
   - Insights navigation link  
   - Careers navigation link
   - Contact navigation link
4. **Reports Results**: Provides detailed success/failure reporting
5. **Cleanup**: Properly closes browser and resources

## 🛠️ Prerequisites

- Python 3.7 or higher
- pip (Python package installer)
- Internet connection

## 📦 Installation & Setup

### Step 1: Clone or Extract Project

Extract the project files to your desired directory.

### Step 2: Create Virtual Environment

```bash
# Navigate to project directory
cd playwright_scripts_python

# Create virtual environment
python -m venv playwright_env

# Activate virtual environment
# On Windows:
playwright_env\\Scripts\\activate

# On macOS/Linux:
source playwright_env/bin/activate
```

### Step 3: Install Dependencies

```bash
# Install Python packages
pip install -r requirements.txt

# Install Playwright browsers
playwright install chromium
```

### Step 4: Verify Installation

```bash
# Check if Playwright is installed correctly
playwright --version
```

## 🚀 Execution

### Basic Execution

```bash
# Make sure virtual environment is activated
source playwright_env/bin/activate  # macOS/Linux
# OR
playwright_env\\Scripts\\activate   # Windows

# Run the main script
python main_script.py
```

### Expected Output

```
🚀 Starting Playwright Automation Test
==================================================
Target URL: https://www.arcadis.com/
Browser: chromium
==================================================

📖 Step 1: Opening browser and navigating to URL...
Navigating to: https://www.arcadis.com/
Successfully navigated to: https://www.arcadis.com/

🔍 Step 2: Validating elements from locator data...

Validating 4 elements...

Validating: About Us navigation link
  Locator: text=About Us
  Expected text: 'About Us'
  ✅ SUCCESS: Text matches - 'About Us'

Validating: Insights navigation link
  Locator: text=Insights
  Expected text: 'Insights'
  ✅ SUCCESS: Text matches - 'Insights'

Validating: Careers navigation link
  Locator: text=Careers
  Expected text: 'Careers'
  ✅ SUCCESS: Text matches - 'Careers'

Validating: Contact navigation link
  Locator: text=Contact
  Expected text: 'Contact'
  ✅ SUCCESS: Text matches - 'Contact'

==================================================
🎉 All element validations PASSED!
==================================================

📊 Step 3: Final Results
==================================================
🎉 TEST PASSED: All elements validated successfully!
==================================================

🧹 Step 4: Cleaning up resources...
Browser closed successfully.

✅ Test execution completed.
```

## ⚙️ Configuration

### Modifying Target URL

Edit `settings/settings.py`:

```python
# Change the base URL or specific path
BASEURL = "https://www."
URL = BASEURL + "your-target-site.com/"
```

### Changing Browser

Edit `settings/settings.py`:

```python
# Options: chromium, firefox, webkit
BROWSER = "firefox"
```

### Modifying Elements to Test

Edit `Locators/locator.yaml`:

```yaml
elements:
  your_element:
    locator: "text=Your Element Text"
    expected_text: "Your Element Text"
    description: "Description of your element"
```

## 🧪 Running Tests

### Headless Mode

To run in headless mode, modify `common/lib.py`:

```python
# Change headless=False to headless=True
self.browser = self.playwright.chromium.launch(headless=True)
```

### Different Browsers

Install additional browsers:

```bash
# Install Firefox
playwright install firefox

# Install WebKit (Safari)
playwright install webkit
```

Then update `settings/settings.py` to use "firefox" or "webkit".

## 🐛 Troubleshooting

### Common Issues

1. **Browser not found**
   ```bash
   # Reinstall browsers
   playwright install
   ```

2. **Permission errors**
   ```bash
   # On Linux/macOS, you might need to install system dependencies
   playwright install-deps
   ```

3. **Import errors**
   - Ensure virtual environment is activated
   - Verify all dependencies are installed: `pip list`

4. **Element not found**
   - Check if website structure has changed
   - Update locators in `Locators/locator.yaml`
   - Use browser developer tools to inspect elements

### Debug Mode

For debugging, you can modify the script to add pauses:

```python
# Add this in main_script.py after opening URL
input("Press Enter to continue...")  # Manual pause
```

## 📝 Customization

### Adding New Elements

1. Open `Locators/locator.yaml`
2. Add new element following the existing pattern:

```yaml
elements:
  new_element:
    locator: "css=.your-css-selector"
    expected_text: "Expected Text"
    description: "Description of new element"
```

### Custom Validation Logic

Modify `common/lib.py` in the `validate_element_from_data` method to add custom validation logic.

## 🔧 Advanced Usage

### Running with Different Timeouts

Modify `settings/settings.py`:

```python
TIMEOUT = 60000  # 60 seconds
```

### Custom Viewport Size

```python
VIEWPORT = {"width": 1920, "height": 1080}
```

## 📊 Exit Codes

- `0`: All tests passed successfully
- `1`: One or more tests failed or error occurred

## 🤝 Support

For issues or questions:
1. Check the troubleshooting section above
2. Verify all prerequisites are met
3. Ensure virtual environment is properly activated
4. Check that all dependencies are installed correctly

## 📄 License

This project is provided as-is for educational and testing purposes.

