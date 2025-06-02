# API Integrations for SEO Audits

## Overview
This guide covers API integrations that can automate and enhance your SEO audit process, from data collection to reporting and monitoring.

## 🔌 Core SEO Tool APIs

### Google APIs

#### Google Search Console API
- **Purpose**: Access organic search performance data directly from Google
- **Key Endpoints**:
  - Search Analytics: Query performance, impressions, clicks, CTR
  - URL Inspection: Index status, mobile usability, rich results
  - Sitemaps: Submission status and error reporting
  - Core Web Vitals: Real user experience data

**Setup Process**:
```python
# Installation
pip install google-api-python-client google-auth

# Authentication
from google.oauth2.credentials import Credentials
from googleapiclient.discovery import build

# Usage Example
service = build('searchconsole', 'v1', credentials=creds)
request = {
    'startDate': '2024-01-01',
    'endDate': '2024-01-31',
    'dimensions': ['query', 'page'],
    'rowLimit': 1000
}
response = service.searchanalytics().query(
    siteUrl='https://example.com', 
    body=request
).execute()
```

#### Google PageSpeed Insights API
- **Purpose**: Automated performance auditing
- **Key Features**:
  - Core Web Vitals scores
  - Performance recommendations
  - Field and lab data
  - Mobile and desktop analysis

**API Integration**:
```python
import requests

def get_pagespeed_data(url, api_key):
    api_url = f"https://www.googleapis.com/pagespeedonline/v5/runPagespeed"
    params = {
        'url': url,
        'key': api_key,
        'strategy': 'mobile',  # or 'desktop'
        'category': ['performance', 'seo', 'best-practices']
    }
    response = requests.get(api_url, params=params)
    return response.json()
```

#### Google Analytics 4 API
- **Purpose**: Website traffic and behavior analysis
- **SEO-Relevant Metrics**:
  - Organic traffic trends
  - Page performance metrics
  - User engagement data
  - Conversion tracking

### SEO Platform APIs

#### Ahrefs API
- **Purpose**: Comprehensive SEO data including backlinks, keywords, and rankings
- **Key Features**:
  - Backlink profile analysis
  - Keyword difficulty and volume
  - SERP analysis
  - Site audit data

**Usage Example**:
```python
import requests

def get_ahrefs_backlinks(target_domain, api_token):
    url = "https://apiv2.ahrefs.com"
    params = {
        'token': api_token,
        'from': 'backlinks',
        'target': target_domain,
        'mode': 'domain',
        'limit': 1000,
        'select': 'url_from,domain_from,ahrefs_rank,domain_rating'
    }
    response = requests.get(url, params=params)
    return response.json()
```

#### SEMrush API
- **Purpose**: Keyword research, competitive analysis, and site auditing
- **Key Features**:
  - Domain analytics
  - Keyword gap analysis
  - Backlink audit
  - Position tracking

**Integration Example**:
```python
def get_semrush_domain_overview(domain, api_key):
    url = "https://api.semrush.com/"
    params = {
        'type': 'domain_overview',
        'key': api_key,
        'domain': domain,
        'export_columns': 'Ot,Oc,Ad,At'
    }
    response = requests.get(url, params=params)
    return response.text
```

#### Moz API
- **Purpose**: Domain authority, page authority, and link metrics
- **Key Features**:
  - Domain/Page Authority scores
  - Link metrics
  - Keyword difficulty
  - SERP analysis

**Setup Example**:
```python
import hashlib
import hmac
import base64
import time

def get_moz_metrics(url, access_id, secret_key):
    expires = int(time.time()) + 300
    string_to_sign = f"{access_id}\n{expires}"
    signature = base64.b64encode(
        hmac.new(secret_key.encode(), string_to_sign.encode(), hashlib.sha1).digest()
    ).decode()
    
    headers = {
        'Authorization': f'Basic {base64.b64encode(f"{access_id}:{signature}".encode()).decode()}'
    }
    
    api_url = f"https://lsapi.seomoz.com/v2/url_metrics"
    data = {"targets": [url]}
    
    response = requests.post(api_url, json=data, headers=headers)
    return response.json()
```

## 🛠️ Technical SEO APIs

### Screaming Frog SEO Spider API
- **Purpose**: Technical site crawling and analysis
- **Integration Options**:
  - Command line automation
  - Custom crawl configurations
  - Export automation

**Command Line Integration**:
```bash
# Windows
ScreamingFrogSEOSpiderCli.exe --crawl https://example.com --headless --save-crawl --export-tabs "Internal:All"

# Mac/Linux
./screamingfrogseospider --crawl https://example.com --headless --save-crawl --export-tabs "Internal:All"
```

### Lighthouse CI API
- **Purpose**: Automated performance and SEO auditing
- **Integration Benefits**:
  - Continuous monitoring
  - Historical performance tracking
  - Automated reporting

**Setup Configuration**:
```json
{
  "ci": {
    "collect": {
      "url": ["https://example.com"],
      "numberOfRuns": 3
    },
    "upload": {
      "target": "lhci",
      "serverBaseUrl": "https://your-lhci-server.com"
    }
  }
}
```

## 📊 Data Processing & Analysis APIs

### OpenAI API for Content Analysis
- **Purpose**: AI-powered content optimization and analysis
- **Use Cases**:
  - Content gap analysis
  - Meta description optimization
  - Keyword density analysis
  - Content quality scoring

**Implementation Example**:
```python
import openai

def analyze_content_seo(content, target_keywords):
    prompt = f"""
    Analyze this content for SEO optimization:
    Content: {content}
    Target Keywords: {target_keywords}
    
    Provide:
    1. Keyword density analysis
    2. Content quality score (1-10)
    3. Missing SEO elements
    4. Optimization recommendations
    """
    
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}]
    )
    
    return response.choices[0].message.content
```

### Pandas for Data Processing
- **Purpose**: Process and analyze SEO data from multiple APIs
- **Key Functions**:
  - Data cleaning and normalization
  - Metric calculations
  - Trend analysis
  - Report generation

**Data Processing Example**:
```python
import pandas as pd

def process_seo_data(gsc_data, ahrefs_data, pagespeed_data):
    # Combine data from multiple sources
    df_gsc = pd.DataFrame(gsc_data['rows'])
    df_backlinks = pd.DataFrame(ahrefs_data['backlinks'])
    
    # Calculate key metrics
    organic_traffic = df_gsc['clicks'].sum()
    avg_position = df_gsc['position'].mean()
    total_referring_domains = df_backlinks['domain_from'].nunique()
    
    # Create summary report
    summary = {
        'organic_traffic': organic_traffic,
        'avg_position': avg_position,
        'referring_domains': total_referring_domains,
        'core_web_vitals': pagespeed_data['loadingExperience']['metrics']
    }
    
    return summary
```

## 🔄 Automation Workflows

### Daily Monitoring Automation
```python
import schedule
import time

def daily_seo_check():
    # Collect data from multiple APIs
    gsc_data = get_search_console_data()
    rankings = get_ranking_data()
    backlinks = get_backlink_updates()
    
    # Process and analyze
    alerts = check_for_anomalies(gsc_data, rankings, backlinks)
    
    # Send notifications if issues detected
    if alerts:
        send_slack_notification(alerts)
        send_email_report(alerts)

# Schedule daily checks
schedule.every().day.at("09:00").do(daily_seo_check)

while True:
    schedule.run_pending()
    time.sleep(3600)  # Check every hour
```

### Weekly Reporting Automation
```python
def generate_weekly_report():
    # Data collection
    performance_data = collect_performance_metrics()
    ranking_changes = get_ranking_movements()
    backlink_changes = get_new_backlinks()
    technical_issues = run_technical_audit()
    
    # Generate visualizations
    create_performance_charts(performance_data)
    create_ranking_report(ranking_changes)
    
    # Compile report
    report = compile_seo_report({
        'performance': performance_data,
        'rankings': ranking_changes,
        'backlinks': backlink_changes,
        'technical': technical_issues
    })
    
    # Distribute report
    send_stakeholder_report(report)
    archive_report(report)
```

## 📈 Custom Dashboard Creation

### Streamlit Dashboard Example
```python
import streamlit as st
import plotly.express as px

def create_seo_dashboard():
    st.title("SEO Performance Dashboard")
    
    # Sidebar for filters
    date_range = st.sidebar.date_input("Select Date Range")
    domains = st.sidebar.multiselect("Select Domains", get_domains())
    
    # Main metrics
    col1, col2, col3, col4 = st.columns(4)
    
    with col1:
        st.metric("Organic Traffic", get_organic_traffic(), delta="12.5%")
    
    with col2:
        st.metric("Avg Position", get_avg_position(), delta="-0.8")
    
    with col3:
        st.metric("Referring Domains", get_referring_domains(), delta="23")
    
    with col4:
        st.metric("Core Web Vitals", get_cwv_score(), delta="5.2")
    
    # Charts
    st.plotly_chart(create_traffic_trend_chart())
    st.plotly_chart(create_ranking_distribution_chart())
    
    # Data tables
    st.subheader("Top Performing Pages")
    st.dataframe(get_top_pages())
    
    st.subheader("Recent Backlinks")
    st.dataframe(get_recent_backlinks())

if __name__ == "__main__":
    create_seo_dashboard()
```

## 🔒 Security & Best Practices

### API Key Management
```python
import os
from dotenv import load_dotenv

# Load environment variables
load_dotenv()

class APIConfig:
    GOOGLE_API_KEY = os.getenv('GOOGLE_API_KEY')
    AHREFS_API_TOKEN = os.getenv('AHREFS_API_TOKEN')
    SEMRUSH_API_KEY = os.getenv('SEMRUSH_API_KEY')
    MOZ_ACCESS_ID = os.getenv('MOZ_ACCESS_ID')
    MOZ_SECRET_KEY = os.getenv('MOZ_SECRET_KEY')
```

### Rate Limiting Implementation
```python
import time
from functools import wraps

def rate_limit(calls_per_minute=60):
    def decorator(func):
        last_called = [0.0]
        
        @wraps(func)
        def wrapper(*args, **kwargs):
            elapsed = time.time() - last_called[0]
            left_to_wait = 60.0 / calls_per_minute - elapsed
            if left_to_wait > 0:
                time.sleep(left_to_wait)
            ret = func(*args, **kwargs)
            last_called[0] = time.time()
            return ret
        return wrapper
    return decorator

@rate_limit(calls_per_minute=30)
def api_call_with_rate_limit():
    # Your API call here
    pass
```

### Error Handling & Logging
```python
import logging
import requests
from requests.adapters import HTTPAdapter
from urllib3.util.retry import Retry

# Configure logging
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def robust_api_call(url, params, max_retries=3):
    session = requests.Session()
    
    # Configure retry strategy
    retry_strategy = Retry(
        total=max_retries,
        backoff_factor=1,
        status_forcelist=[429, 500, 502, 503, 504]
    )
    
    adapter = HTTPAdapter(max_retries=retry_strategy)
    session.mount("http://", adapter)
    session.mount("https://", adapter)
    
    try:
        response = session.get(url, params=params, timeout=30)
        response.raise_for_status()
        logger.info(f"API call successful: {url}")
        return response.json()
    
    except requests.exceptions.RequestException as e:
        logger.error(f"API call failed: {url}, Error: {str(e)}")
        return None
```

## 📋 Implementation Checklist

### Initial Setup
- [ ] Create API accounts for primary SEO tools
- [ ] Generate and securely store API keys
- [ ] Set up development environment with required libraries
- [ ] Configure rate limiting and error handling
- [ ] Test basic API connections

### Data Collection Setup
- [ ] Implement Google Search Console API integration
- [ ] Set up PageSpeed Insights API calls
- [ ] Configure SEO tool APIs (Ahrefs, SEMrush, Moz)
- [ ] Create data processing pipelines
- [ ] Set up automated data collection schedules

### Analysis & Reporting
- [ ] Build data analysis functions
- [ ] Create visualization templates
- [ ] Set up automated reporting
- [ ] Configure alert systems
- [ ] Test end-to-end workflows

### Monitoring & Maintenance
- [ ] Implement monitoring for API quotas
- [ ] Set up error alerting
- [ ] Schedule regular data validation
- [ ] Create backup data collection methods
- [ ] Document all processes and configurations

## 🚀 Advanced Integration Examples

### Multi-Tool Correlation Analysis
```python
def correlate_seo_metrics():
    # Collect data from multiple sources
    gsc_data = get_search_console_metrics()
    ahrefs_data = get_ahrefs_metrics()
    pagespeed_data = get_pagespeed_metrics()
    
    # Create correlation matrix
    df = pd.DataFrame({
        'organic_traffic': gsc_data['clicks'],
        'avg_position': gsc_data['position'],
        'referring_domains': ahrefs_data['ref_domains'],
        'page_speed_score': pagespeed_data['performance_score']
    })
    
    correlation_matrix = df.corr()
    
    # Identify strongest correlations
    strong_correlations = correlation_matrix[
        (correlation_matrix > 0.7) | (correlation_matrix < -0.7)
    ]
    
    return strong_correlations
```

### Predictive Analysis Integration
```python
from sklearn.linear_model import LinearRegression
import numpy as np

def predict_traffic_trend(historical_data, days_ahead=30):
    # Prepare data
    X = np.array(range(len(historical_data))).reshape(-1, 1)
    y = np.array(historical_data)
    
    # Train model
    model = LinearRegression()
    model.fit(X, y)
    
    # Make predictions
    future_X = np.array(range(len(historical_data), 
                             len(historical_data) + days_ahead)).reshape(-1, 1)
    predictions = model.predict(future_X)
    
    return predictions
```

---

**Integration Priority:**
1. **Google APIs** - Essential for authentic SEO data
2. **Primary SEO Tool** - Choose one main platform (Ahrefs/SEMrush)
3. **Technical Monitoring** - PageSpeed and Core Web Vitals
4. **Automation Framework** - Daily checks and weekly reports
5. **Custom Analytics** - Correlation analysis and predictions

**Maintenance Schedule:**
- **Daily**: Monitor API quotas and error logs
- **Weekly**: Review data quality and completeness
- **Monthly**: Update API integrations and test workflows
- **Quarterly**: Evaluate new API opportunities and optimize performance
