# 📞 TeleSpot 🔍

```
████████╗███████╗██╗     ███████╗███████╗██████╗  ██████╗ ████████╗
╚══██╔══╝██╔════╝██║     ██╔════╝██╔════╝██╔══██╗██╔═══██╗╚══██╔══╝
   ██║   █████╗  ██║     █████╗  ███████╗██████╔╝██║   ██║   ██║   
   ██║   ██╔══╝  ██║     ██╔══╝  ╚════██║██╔═══╝ ██║   ██║   ██║   
   ██║   ███████╗███████╗███████╗███████║██║     ╚██████╔╝   ██║   
   ╚═╝   ╚══════╝╚══════╝╚══════╝╚══════╝╚═╝      ╚═════╝    ╚═╝   
                                                         version 2.0
```

[![GitHub](https://img.shields.io/badge/GitHub-thumpersecure/Telespot-blue?logo=github)](https://github.com/thumpersecure/Telespot)
[![Python](https://img.shields.io/badge/Python-3.6+-blue?logo=python)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](https://github.com/thumpersecure/Telespot/blob/main/LICENSE)

A Python script that searches **Google, Bing, and DuckDuckGo** for phone numbers using multiple format variations and focuses on identifying **names and locations** in the results.

## ✨ Features

- **Multi-Engine Search**: Searches Google, Bing, AND DuckDuckGo simultaneously 🔍
- **Multiple Format Searching**: Automatically generates 4 different phone number format variations
- **Focused Pattern Analysis**: Identifies common patterns:
  - 📛 **Associated names** (people mentioned with the number)
  - 📍 **Geographic locations** (cities, states, zip codes)
  - ✅ **Results by source** (which search engine found what)
- **Rate Limiting**: Built-in delays between searches to avoid throttling
- **Colored Terminal Output**: Easy-to-read results with color coding
- **JSON Export**: Option to save detailed results for further analysis

## 🎯 Key Differences from v1.x

- ✅ **No more ddgr dependency** - Uses direct web scraping instead
- ✅ **3 search engines** instead of just DuckDuckGo
- ✅ **Focused on names & locations** - Removed domain analysis
- ✅ **More reliable results** - Web scraping gives consistent output

## 📋 Prerequisites

1. **Python 3.6+** 🐍
2. **Required Python packages** (included in requirements.txt):
   - `requests` - For HTTP requests to search engines
   - `beautifulsoup4` - For parsing HTML search results
   - `lxml` - HTML/XML parser

### Setting Up Python Virtual Environment (Recommended) 🔧

It's recommended to use a virtual environment to keep dependencies isolated:

```bash
# Create a virtual environment
python3 -m venv telespot-env

# Activate the virtual environment
# On Linux/macOS:
source telespot-env/bin/activate

# On Windows:
telespot-env\Scripts\activate
```

### Installing Dependencies

Once your virtual environment is activated:

```bash
# Install from requirements.txt
pip install -r requirements.txt
```

## 📥 Installation

### Automated Setup (Easiest) ⚡

Use the provided setup script to automatically create the virtual environment and install dependencies:

```bash
# Clone the repository
git clone https://github.com/thumpersecure/Telespot.git
cd Telespot

# Run the setup script
chmod +x setup.sh
./setup.sh
```

Or download directly:
```bash
# Download all files
wget https://raw.githubusercontent.com/thumpersecure/Telespot/main/telespot.py
wget https://raw.githubusercontent.com/thumpersecure/Telespot/main/requirements.txt
wget https://raw.githubusercontent.com/thumpersecure/Telespot/main/setup.sh

# Run the setup script
chmod +x setup.sh
./setup.sh
```

The setup script will:
- ✅ Check Python version
- ✅ Create virtual environment (telespot-env)
- ✅ Install all dependencies
- ✅ Make telespot.py executable
- ✅ Offer to run TeleSpot immediately

### Manual Setup (Recommended for Learning)

1. **Clone or download TeleSpot:**
```bash
# Clone the repository
git clone https://github.com/thumpersecure/Telespot.git
cd Telespot

# Or download individual files
wget https://raw.githubusercontent.com/thumpersecure/Telespot/main/telespot.py
wget https://raw.githubusercontent.com/thumpersecure/Telespot/main/requirements.txt
```

2. **Create and activate virtual environment:**
```bash
python3 -m venv telespot-env
source telespot-env/bin/activate  # On Linux/macOS
# telespot-env\Scripts\activate   # On Windows
```

3. **Install dependencies:**
```bash
pip install -r requirements.txt
```

4. **Make the script executable:**
```bash
chmod +x telespot.py
```

5. **Run TeleSpot:**
```bash
./telespot.py
# or
python telespot.py
```

### Quick Install (Without Virtual Environment)

1. Download the script:
```bash
wget https://raw.githubusercontent.com/thumpersecure/Telespot/main/telespot.py
# or
curl -O https://raw.githubusercontent.com/thumpersecure/Telespot/main/telespot.py
```

2. Install ddgr globally:
```bash
pip install ddgr
```

3. Make it executable:
```bash
chmod +x telespot.py
```

## 🚀 Usage

> **Note:** Make sure your virtual environment is activated before running TeleSpot:
> ```bash
> source telespot-env/bin/activate  # Linux/macOS
> # telespot-env\Scripts\activate   # Windows
> ```

### Basic Usage

Run the script and enter the phone number when prompted:

```bash
./telespot.py
```

### Command-Line Usage

Pass the phone number as an argument:

```bash
./telespot.py 5555551212
./telespot.py "(555) 555-1212"
./telespot.py 1-555-555-1212
```

### Debug Mode 🐛

If you're getting no results, run in debug mode to see what's happening:

```bash
./telespot.py --debug 5555551212
# or
python telespot.py -d 5555551212
```

This will show:
- Exact ddgr commands being run
- Sample results from each search
- Error messages and warnings

The script accepts phone numbers in any format - it will strip out non-digit characters automatically.

## 🔢 Search Formats

The script searches for the following format variations across **all three search engines**:

1. `555-555-1212` - Dashes
2. `(555) 555-1212` - Parentheses and dashes
3. `5555551212` - Digits only
4. `1 555-555-1212` - Country code with dashes

Each format is searched on:
- 🔵 **Google** (5 results per format)
- 🟢 **Bing** (5 results per format)
- 🦆 **DuckDuckGo** (5 results per format)

**Total**: Up to 60 results per search (4 formats × 3 engines × 5 results)

## 📊 Output

### Pattern Analysis Summary 📈

The script provides:

- **Total results found** across all search engines
- **Results by source** (Google, Bing, DuckDuckGo breakdown)
- **📛 Names found** - People's names associated with the number
- **📍 Locations mentioned** - Cities, states, and zip codes
- **🔍 Key insights** - Most frequently appearing name and location

### Example Output

```
================================================================================
PATTERN ANALYSIS SUMMARY
================================================================================

Total Results Found: 42

Results by Source:
  • Google: 18 results
  • Bing: 15 results
  • DuckDuckGo: 9 results

📛 Names Found:
  • John Smith: mentioned 8 time(s)
  • Jane Doe: mentioned 3 time(s)
  • Mike Johnson: mentioned 2 time(s)

📍 Locations Mentioned:
  • Philadelphia, PA: 12 occurrence(s)
  • PA: 8 occurrence(s)
  • 19102: 3 occurrence(s)

🔍 Key Insights:
  • Most associated name: John Smith
  • Most associated location: Philadelphia, PA
================================================================================
```

## 💾 Saving Results

After the analysis, you'll be prompted to save detailed results to a JSON file:

```
Save detailed results to file? (y/n): y
Results saved to: telespot_results_5555551212.json
```

The JSON file contains:
- Original phone number
- All search format variations used
- Complete search results from all engines
- Full pattern analysis data (names and locations)

## ⏱️ Rate Limiting

The script includes **smart rate limiting** to avoid being blocked:
- 1 second delay between search engines (Google → Bing → DuckDuckGo)
- 3 second delay between phone number formats
- Total search time: ~1-2 minutes for a complete search

This ensures:
- ✅ Respectful to search engines
- ✅ Avoids IP blocks or CAPTCHAs
- ✅ Consistent, reliable results

## 🎯 Use Cases

- **OSINT investigations** 🕵️: Gather information about unknown phone numbers
- **Spam identification** 🚫: Check if a number is associated with spam/scam reports
- **Contact verification** ✅: Verify the legitimacy of business phone numbers
- **Skip tracing** 🔎: Locate associated names and addresses
- **Fraud investigation** ⚖️: Part of your legal work gathering evidence

## 🔒 Privacy & Legal Considerations

- This tool uses publicly available search data
- Use responsibly and in compliance with applicable laws
- Respect privacy and data protection regulations
- Intended for legitimate investigative purposes

## 🔧 Troubleshooting

### Getting "0 results" for all searches 🔍

**1. Check your internet connection:**
```bash
ping google.com
```

**2. Test the dependencies:**
```bash
# Activate your venv first
source telespot-env/bin/activate

# Test if packages are installed
python -c "import requests; import bs4; print('Dependencies OK')"
```

**3. Run in debug mode:**
```bash
./telespot.py --debug 5555551212
```

**4. Try a well-known number:**
Test with a business number you can verify has results online, like a major company's customer service line.

### Search engines blocking requests 🚫

If you're getting blocked or seeing CAPTCHAs:
- **Wait 10-15 minutes** before running again
- **Use a VPN** to change your IP address
- **Reduce search frequency** - Don't run multiple searches back-to-back

### ImportError or Module Not Found 🚨
This usually means your virtual environment isn't activated or dependencies aren't installed:
```bash
# Activate venv
source telespot-env/bin/activate

# Install/reinstall requirements
pip install -r requirements.txt
```

### No results found 🤷
- The phone number may not be publicly indexed
- Try searching manually in a browser to confirm
- Number might be new, unlisted, or private

### Connection timeout errors ⏳
If searches are timing out:
- Check your internet connection
- The search engine might be temporarily down
- Try again in a few minutes

## ⚙️ Technical Details

- **Language**: Python 3 🐍
- **Dependencies**: requests, beautifulsoup4, lxml (specified in requirements.txt)
- **Recommended Setup**: Python virtual environment
- **Output**: Colored terminal text + optional JSON export
- **Search engines**: Google, Bing, DuckDuckGo 🔍
- **Method**: Web scraping with BeautifulSoup

### How It Works 🛠️

1. **Format Generation**: Creates 4 variations of the phone number
2. **Multi-Engine Search**: Queries Google, Bing, and DuckDuckGo for each format
3. **HTML Parsing**: Extracts titles and snippets from search results using BeautifulSoup
4. **Pattern Analysis**: 
   - Identifies names using capitalization patterns
   - Detects locations via state codes, city names, and zip codes
   - Counts frequency of mentions
5. **Result Summary**: Displays most common names and locations

### Project Structure 📁
```
telespot/
├── telespot.py          # Main script
├── requirements.txt     # Python dependencies
├── setup.sh            # Automated setup script
└── README.md           # Documentation
```

## 👤 Author

Created by **Spin Apin** ([@thumpersecure](https://github.com/thumpersecure))

Designed for legal marketing and investigative purposes. Particularly useful for:
- Personal injury case investigations
- Verifying contact information
- Identifying spam/harassment sources
- Evidence gathering with proper documentation

## 🤝 Contributing

Contributions are welcome! Feel free to:
- 🐛 Report bugs via [GitHub Issues](https://github.com/thumpersecure/Telespot/issues)
- 💡 Suggest features or enhancements
- 🔧 Submit pull requests
- ⭐ Star the repository if you find it useful

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

**Disclaimer:** This tool is intended for legitimate investigative and OSINT purposes only. Users are responsible for ensuring their use complies with all applicable laws and regulations.

## 🔗 Links

- **GitHub Repository**: [https://github.com/thumpersecure/Telespot](https://github.com/thumpersecure/Telespot)
- **Report Issues**: [https://github.com/thumpersecure/Telespot/issues](https://github.com/thumpersecure/Telespot/issues)
- **Latest Release**: Check the [Releases page](https://github.com/thumpersecure/Telespot/releases)

---

Made with 💻 for OSINT and investigative work
